---
isOriginal: true
icon: speed
category:
  - Slardar
  - Home
---

# 3.Slardar

![slardar](/slardar_icon.png)

> The big fish, a sailor, will starlight your way.

SpringMvc (not WebFlux) wrappers and extensions,
such as multi-language, multi-timezone, security, caching, sessions, etc.

## 3.1.Module Project

* slardar - basic features eg. caching, event, serializing
* slardar-hazel-caching - distributed cache on hazelcast
* slardar-hazel-session - distributed session on hazelcast
* slardar-webmvc - webmvc, session, security-web
* slardar-sprint - hazelcast, security-conf, admin, actuator
* slardar-test - testing utility including login

## 3.2.Solution and Configuration

Slardar is configured by default according to the following architecture and performance,

* Nginx(reverse proxy), mainly post+json service
* `Undertow` as the default Servlet container
* `Hazelcast` as `Cache` and `Session`
* 80% service can `30ms` end, blocking factor `0.9`
* `8-core 3GHz` cloud hosting, simulating `10k*50` requests, single application
* `95th`，response=`2s`，`tps`=`2k-5k`

## 3.3.SpringMvc Enhancement

Base on springmvc, Salrdar provides potential capabilities and out-of-the-box features,

* concurrency control, multi-level caching, event publish/subscribe
* spring-boot-admin and actuator management and monitoring capability
* sentry log collection capability
* Terminal and Security's Context
* login, permission, session, token and other control capabilities

## 3.4.Preconfigured ThreadPool

SlardarAsyncConfiguration provides 4 pre-config Ttl threadpools, prefix and purpose are,

* `win-async-` - `spring.task.execution.` properties for `@Async`
* `win-task-` - `spring.task.scheduling.` properties for `@Scheduled`
* `win-event-` - `wings.slardar.async.event.` properties for Spring's Event
* `win-heavy-` - `wings.slardar.async.heavy.` properties for Wings heavy task

## 3.5.More Sections

* [Jackson Convention](3a-jackson.md) - Json convertion and i18n message
* [Hazelcast Middleware](3b-hazelcast.md) - distributed session, chaching, messaging
* [Host Extend and URL Override](3c-host-ext.md) - Override URL，Multiple Hosts and skinning
* [Multiple Time and Lang](3d-i18n-zone.md) - DateTime, Validation, Locale
* [Session and Authn](3e-auth-session.md) - Multiple logins, credentials, hierarchical permissions
* [Multiple Caching and Event](3f-cache-event.md) - Multi-level cache, lock, message
* [Backend Protection](3g-fun-server.md) - backend debounce, CAPTCHA, anti-tamper
* [Backend Faq Topic](3h-qa-slardar.md) - backend topic
