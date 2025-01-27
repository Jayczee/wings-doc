---
home: true
icon: home
heroImage: /logo.png
heroText: BKB+BoT+SpringBoot
tagline: 🎉Fast delivery 🧩Safe refactor 🍵Low tech-debt
actions:
  - text: Project Style 🔖
    link: /en/0-wings/0a-code-style.html
    type: primary

  - text: Data/DB Version 💡
    link: /en/2-faceless/2a-flywave.html

  - text: Property Config 🧭
    link: /en/0-wings/0h-prop-index.html

features:
  - icon: config
    title: Shard and Cascade Configigruation
    details: Properties can be broken down into separate files that take effect after cascading
    link: /en/1-silencer/1a-wings-conf.html

  - icon: language
    title: Multi Language and Timezone
    details: Automatic timezone config and adjustment, static and dynamic i18n config and conversion
    link: /en/1-silencer/1b-wings-i18n.html

  - icon: mysql
    title: Versioning of Data and Schema
    details: Manage schema and data changes with a git-like and sql-based tool called flywave
    link: /en/2-faceless/2a-flywave.html

  - icon: software
    title: Powful Type-safe SqlMapping
    details: Achieve business goals faster, pay off tech-debt faster, and refactor safely
    link: /en/2-faceless/2b-jooq.html

  - icon: storage
    title: Distrib, Spliting and Sharding
    details: Efficient distributed ID, on-demand data sharding and read/write splitting
    link: /en/2-faceless/2c-shard.html

  - icon: json
    title: Engineered Jackson Configuration
    details: Compatible convention and secure check for biz types, eg. number, datetime, timezone
    link: /en/3-slardar/3a-jackson.html

  - icon: extend
    title: Host extension and URL override
    details: Domain-based skin, inherit and override URL without reverse proxy, just SpringMVC
    link: /en/3-slardar/3c-host-ext.html

  - icon: token
    title: Distrib Session and Multi-Auth
    details: Hazelcast-based distributed Session, cookie encryption, and alias name
    link: /en/3-slardar/3e-auth-session.html

  - icon: stack
    title: JVM/Distrib Cache, Lock, and Objects
    details: JVM and distributed objects, locks, and events with Cache2k and  Hazelcast
    link: /en/3-slardar/3f-cache-event.html

  - icon: compare
    title: Throttle, Debounce, Tamper Proof
    details: Backend debounce, service throttle, content tamper proof, captcha protection
    link: /en/3-slardar/3g-fun-server.html

  - icon: command
    title: 3rd Login, Role/Perm Management
    details: Oauth2 Integration, fine-grained permission based on app, feature and domain
    link: /en/4-warlock/4c-security.html

  - icon: more
    title: Pluggable modules, OOTB features 
    details: Pluggable module, Out-of-the-box feature, script, manual and code generator
    link: /en/8-radiant/
---

<!-- markdownlint-disable MD025 -->
# 🥾 WingsBoot

> WingsBoot=BKB + BootsOfTravel + SpringBoot. if you've liked Dota, you know.
>
> We advocate defensive programming, May The `false` Be With You !

![mirana](/mirana_minimap_icon.png)
![meepo](/meepo_minimap_icon.png)
![silencer](/silencer_minimap_icon.png)
![faceless](/faceless_minimap_icon.png)
![slardar](/slardar_minimap_icon.png)
![warlock](/warlock_minimap_icon.png)
![batrider](/batrider_minimap_icon.png)
![tiny](/tiny_minimap_icon.png)

It is suitable for growing teams to smoothly achieve business growth, technology evolution, team pulling and business upgrading.
The core values are: ① quickly achieve business goals; ② timely repay technical debt; ③ safely refactor programs and business.
For example, starting from a single app, to sharding, to micro service and to cloud, the team is able to:

* Rapidly refactor the business and its code, safely change the data models - strongly typed and defensive style
* Use git and sql to manage versioning of data and schema - Flywave tool (not Flyway)
* Trace, review and recover online data changes - logging system and tracing strategy

## 📦 Tech Architecture

<!-- markdownlint-disable MD013 -->
* [![SpringBoot-3.0](https://img.shields.io/badge/springboot-3.0-green?logo=springboot)](https://spring.io/projects/spring-boot) Philosophy and Conventions, Non-Intrusion Enhancement 🌱 [Apache2]
* [![Java-17](https://img.shields.io/badge/java-17-gold)](https://adoptium.net/temurin/releases/?version=11) Main business language, OpenJDK long-time running ☕️ [GPLv2+CE]
* [![Kotlin-1.7](https://img.shields.io/badge/kotlin-1.7-gold)](https://kotlinlang.org/docs/reference/) Assisted language, as a better Java [Apache2]
* [![Jooq-3.17](https://img.shields.io/badge/jooq-3.17-cyan)](https://www.jooq.org/download/)  The main type-safe SqlMapping 🏅 [Apache2]
* [![Mysql-8](https://img.shields.io/badge/mysql-8.0-blue)](https://dev.mysql.com/downloads/mysql/) Main business database, 8 recommended, 5.7 compatible 💡 [GPLv2]
* [![H2Database-2.1](https://img.shields.io/badge/h2db-2.1-blue)](https://h2database.com/html/main.html) Standalone database for offline and disconnected operations [MPL2] or [EPL1]
* [![Hazelcast-5.1](https://img.shields.io/badge/hazelcast-5.1-violet)](https://hazelcast.org/imdg/) IMDG，Distributed caching, messaging, streaming, etc. [Apache2]
* [![ServiceComb-2.8](https://img.shields.io/badge/servicecomb-2.8-violet)](https://servicecomb.apache.org) More engineering and compact Cloud solution [Apache2]
* [![ShardingSphere-5.3](https://img.shields.io/badge/shardingsphere-5.3-violet)](https://shardingsphere.apache.org) Database RW splitting, data sharding and elastic scaling [Apache2]


[Apache2]: https://www.apache.org/licenses/LICENSE-2.0
[GPLv2+CE]: https://openjdk.org/legal/gplv2+ce.html
[GPLv2]: http://www.gnu.org/licenses/old-licenses/gpl-2.0.html
[MPL2]: https://www.mozilla.org/MPL/2.0
[EPL1]: https://opensource.org/licenses/eclipse-1.0.php

## 🐵 Mindless Use

Use directly as a parent, occasional `SNAPSHOT` are available through OSS.

```xml
<parent>
    <groupId>pro.fessional</groupId>
    <artifactId>wings</artifactId>
    <version>${wings.version}</version>
</parent>
```

## 🦁 Hands-on Use

It's recommended that you get your hands on the code to avoid low-level use and failure to achieve the original purpose, even if you have the potential to get it.

```bash
# ① get source code
git clone --depth 1 https://github.com/\
trydofor/pro.fessional.wings.git
# ② install dependency useing java8
# sdk use java 8.0.352-tem
git submodule update --remote --init
(cd observe/meepo && mvn package install)
(cd observe/mirana && mvn package install)
# ③ install wings using java-17
sdk use java 17.0.6-tem
mvn package install
```

🚀 Built on <a :href="'https://github.com/fessionalpro/wings-doc/commits/' + $frontmatter.GIT_REPO_HEAD.substring(11)" target="_blank"> {{ $frontmatter.GIT_REPO_HEAD.substring(0, 21) }} </a> Commit
