---
isOriginal: true
icon: enum
category:
  - Slardar
  - Property
---

# 3L.Hazelcast Properties

有关Slardar中提供的Hazelcast的设置

* <https://docs.hazelcast.com/imdg/4.2/system-properties>
* <https://docs.hazelcast.com/imdg/4.2/management/diagnostics>

## 3L.1.wings-prop-promotion.cnf

* spring.session.hazelcast.map-name
* wings.slardar.hazelcast.cluster-name
* spring.boot.admin.hazelcast.event-store
* spring.boot.admin.hazelcast.sent-notifications
* hazelcast.jmx
* hazelcast.diagnostics.enabled
* hazelcast.diagnostics.metric.level
* hazelcast.diagnostics.pending.invocations.period.seconds
* hazelcast.diagnostics.slowoperations.period.seconds
* hazelcast.diagnostics.directory
* hazelcast.diagnostics.filename.prefix
* hazelcast.diagnostics.max.rolled.file.size.mb
* hazelcast.diagnostics.max.rolled.file.count
* hazelcast.diagnostics.metrics.period.seconds
* hazelcast.diagnostics.invocation.sample.period.seconds
* hazelcast.diagnostics.invocation.slow.threshold.seconds
* hazelcast.diagnostics.invocation-profiler.period.seconds
* hazelcast.diagnostics.operation-profiler.period.seconds
* hazelcast.diagnostics.memberinfo.period.second
* hazelcast.diagnostics.event.queue.period.seconds
* hazelcast.diagnostics.event.queue.threshold
* hazelcast.diagnostics.event.queue.samples
* hazelcast.diagnostics.systemlog.enabled
* hazelcast.diagnostics.systemlog.partitions
* hazelcast.diagnostics.storeLatency.period.seconds
* hazelcast.diagnostics.storeLatency.reset.period.seconds
* hazelcast.diagnostics.operation-heartbeat.seconds
* hazelcast.diagnostics.operation-heartbeat.max-deviation-percentage
* hazelcast.diagnostics.member-heartbeat.seconds
* hazelcast.diagnostics.member-heartbeat.max-deviation-percentage
* hazelcast.diagnostics.operationthreadsamples.period.seconds
* hazelcast.diagnostics.operationthreadsamples.sampler.period.millis
* hazelcast.diagnostics.operationthreadsamples.includeName
* hazelcast.diagnostics.wan.period.seconds

## 3L.2.spring-hazelcast-77.properties

若xml中使用spring变量，需要wings-prop-promotion.cnf提升到system
Resource, `file:/data/xxx`, `http://www`, `classpath:/xxx`

### spring.hazelcast.config

* `classpath:/extra-conf/hazelcast-client.xml` - 客户端配置
* `classpath:/extra-conf/hazelcast-server.xml` - 服务端配置

## 3L.3.spring-session-77.properties

引入hazelcast后，则默认使用Hazelcast管理session，编号77优先级高于默认。

### spring.session.store-type

`String`=`hazelcast`

## 3L.4.wings-hazelcast-77.properties

Hazelcast默认值，监控及诊断设置，

* <https://docs.hazelcast.com/imdg/4.2/management/diagnostics>
* <https://codecentric.github.io/spring-boot-admin/current/#clustering-support>

### wings.slardar.hazelcast.cluster-name

`String`=`wings-${git.commit.id.full}`，自行修改集群名字。

因社区版无安全设置，仅通过集群名便可加入，因此建议使用密码强度的名字，如32字符随机数，避开扫描。

### wings.slardar.hazelcast.diagnostics.period-seconds

`Integer`=`600`，diagnostics周期

### spring.boot.admin.hazelcast.event-store

`String`=`spring-boot-admin-event-store`

Name of the Hazelcast-map to store the events

### spring.boot.admin.hazelcast.sent-notifications

`String`=`spring-boot-admin-sent-notifications`

Name of the Hazelcast-map used to deduplicate the notifications.

### hazelcast.jmx

`Boolean`=`${spring.jmx.enabled:false}`，是否开启jmx

### hazelcast.diagnostics.enabled

`Boolean`=`false`，默认关闭，因CPU消耗过高

### hazelcast.diagnostics 其他设置

通过属性提示，为Hazelcast设置spring设置的属性值。

* `hazelcast.diagnostics.metric.level`=`info`
* `hazelcast.diagnostics.filename.prefix`=`${spring.application.name:wings-default}`
* `hazelcast.diagnostics.pending.invocations.period.seconds`=`${wings.slardar.hazelcast.diagnostics.period-seconds}`
* `hazelcast.diagnostics.slowoperations.period.seconds`=`${wings.slardar.hazelcast.diagnostics.period-seconds}`
* `hazelcast.diagnostics.metrics.period.seconds`=`${wings.slardar.hazelcast.diagnostics.period-seconds}`
* `hazelcast.diagnostics.invocation.sample.period.seconds`=`${wings.slardar.hazelcast.diagnostics.period-seconds}`
* `hazelcast.diagnostics.invocation-profiler.period.seconds`=`${wings.slardar.hazelcast.diagnostics.period-seconds}`
* `hazelcast.diagnostics.operation-profiler.period.seconds`=`${wings.slardar.hazelcast.diagnostics.period-seconds}`
* `hazelcast.diagnostics.memberinfo.period.second`=`${wings.slardar.hazelcast.diagnostics.period-seconds}`
* `hazelcast.diagnostics.storeLatency.period.seconds`=`${wings.slardar.hazelcast.diagnostics.period-seconds}`
* `hazelcast.diagnostics.operationthreadsamples.period.seconds`=`${wings.slardar.hazelcast.diagnostics.period-seconds}`
