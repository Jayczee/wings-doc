---
isOriginal: true
icon: news
category:
  - Tiny
  - Mail
---

# 8C.TinyMail Component

基于Spring Mail提供了以database为中心的邮件发送

* 同步/异步，单件/批量的发送
* 限频，按错误类型进行发送等待
* 按成功，失败次数终止
* 多应用竞争发送或隔离发送
* 支持多邮件账号
* 支持dryrun，按app，runmode发送

## 8C.1.设计要求

对邮件的发送，有一定的事务性保证，能够限频，处理常见错误

* 以Spring mail为核心，对其兼容和增强
* 补发邮件时，避免定时任务全扫描database
* 处理常见邮件服务商的限频，锁账号情况
* 可根据异常特征，自行停止或延期发送
* 支持多账户，比如区分海外和国内账户
* 支持业务性的邮件Header，以便接受时定位

## 8C.2.核心服务

核心功能和组件，不依赖于database，进行无事务性的邮件发送。

* MailNotice - 无事务性的同步异步邮件通知
* MailConfigProvider - 根据名称，提供兼容spring.mail的配置
* MailSenderProvider - 根据配置，提供单例的JavaMailSender
* MailSenderManager - 统一管理邮件发送，处理host级别的限频
* MailWaitException - 需要延期发送的异常

基于database，有一定事务性的邮件发送服务，能够对邮件异常做自动识别。

* TinyMailService - 同步/异步，重试/批量补发

## 8C.3.基本使用

不重要的邮件通知，主要是无事务性要求，可以直接使用MailNotice。
具有一定的事务要求，如保证不丢失，失败要重试的，则使用TinyMailService。

两者对外提供了3类方法，行为上一致，优于满足同步异步，数据库事务或性能要求。

* send - 同步发送，会抛异常，影响当前线程的性能和事务
* post - 同步发送，记录异常，影响当前线程的性能，但不影响事务
* emit - 异步发送，不影响当前线程的性能和事务

使用事务性的TinyMailService时，遵循以下的执行逻辑，

* 邮件先存入database，但不检查重复，相同邮件可以存在多份
* 发送前，检查乐观锁(netxLock)，成功则发送，否则忽略
* 首次时，单件发送。重试时，则异步批量发送
* 处理异常，根据特征，确定host或mail级等待时间
* 更新database，主要为计数，本次结果，下次发送时间
* 若需要重试，则加入优先队列，启动定时的异步发送

## 8C.4.邮件补发

当邮件发送未成功时，遭遇了宕机，程序停止等情况，通过以下机制进行补发，

* 手动调用TinyMailService.scan方法
* 应用启动时，TinyMailServiceImpl自动scan一次

重发没有采用定时任务的方式，主要基于以下情况，没有必要定时扫描，

* 邮件都是以TinyMailService为入口的
* 若无宕机或停止，mail最终都会发送或正常终止
* 短期宕机，应用再次启动时，进行了scan
* 应用无法重启，可通过其他App进行scan补救

以下情况不进行补发，主要为邮件本身格式问题，

* 邮件解析异常，比如收发件人错误等
* 具有特征标记的异常，判断为stopRetry的时候

## 8C.5.邮件限频

邮件服务商一般都有限频机制，付费的比免费的阈值要大一些，比如qq邮箱

> 腾讯邮箱对相同的发件人有一定的频率限制：
> 1、超过每分钟发信量限制，被禁止发信若干分钟。
> 2、超过每小时发信量限制，被禁止发信若干小时。
> 3、超过每日发信量限制，本日内禁止再发信。
> 4、以上频率限制数值属于腾讯邮箱保密数据，恕不公开。

触发限频，可按邮件件数和链接登录次数，两者不相等。

* 单件发送时，一封一次登录，链接，登录，发送，关闭
* 批量发送时，一批一次登录，链接，登录，发送xN，关闭

wings在异步emit和补发时，采用批量发送，可减少登录次数。
此外可设置两次登录间的等待间隔，单发或批量都会自动等待。

等待间隔，在设定的阈值内为sleep，否则抛出MailWaitException

## 8C.6.Error Handling

Email exceptions, mainly have three categories

* Format error - the mail itself problem, the same error when resending.
* Account error - by mail provider, such as frequency limit, account lock, can resend when unlocked.
* Network error - depending on the network, usually can retry soon

according to the above types and the server response message,
throw MailWaitException  and leave it to the caller to handle.

## 8C.7.Status Hook

use StatusHook to handle success/failure status when sending emails with TinyMailService,

* stop() - true, it will stop retrying the email and set NextSend to empty.
