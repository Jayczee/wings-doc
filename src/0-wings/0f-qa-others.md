---
isOriginal: true
icon: question
category:
  - 神翼
  - 话题
---

# 0F.其他话题

未归类的话题。

## 0F.01.为什么是dota的英雄

有这样一个团队，她是做对日金融的，穿拖鞋裤衩上班，课间可以团dota，cs，跑跑卡丁车。
日本人组团爱上了瓜子，黄飞红，米线，火锅。团队只有一个要求，活干的漂亮，快，零缺陷。

我本人与dota有缘无分，现在也就连直播都不爱看了，只是心中有个地方，叫dota

* TI6，她在西雅图，我在特拉华
* TI9，她在奔驰馆，我在大虹桥

## 0F.02.项目文档有很多错别字

如果非要找个理由的话，

* 输入法不给力，候选词提示歪了
* 我是个理科生，语文不好
* 脑子转的快，手指头跟不上

## 0F.03.一个功能居然写到情绪奔溃

从来没有那个功能写到我有点奔溃，TinyTask算第一个，记录一下。

这个功能本身需求不是那么强烈，搁置了很久，最后还是捡了起来，因为

* spring batch有点笨重
* xxl-job目前用不上
* @Scheduled不能取消，没有通知和并发控制

所以就慢慢的设计了TinyTask的基本框框，当处理Misfire和并发的时候，
自己🐑了，脑子不够用，一遍一遍在脑子里推演，却陷了进去，死活出不来。

当时非常绝望，想删了代码，反悔为啥要做这个鸡肋的功能。

最后，移除了Misfire，简化了并发控制，🐑也好了，心情也恢复了些。
但当我准备写TinyTask文档时，心里有点空荡荡的，那是奔溃爆炸，夷为平地的地方。

TinyTask目前设计的很勉强，仅仅是@Scheduled的加强版。
