---
isOriginal: true
icon: geometry
category:
  - 神翼
  - 模型
---

# 0G.幽灵船模型

WingsBoot体系的基本架构思路是，纵向做模型，横向贴功能。
曾用代号【邮轮模型】，后在Dota系，改为GhostShip，更wings一点。

## 0G.1.上船下海 GoSea

俗话说，`Go And Sea`，`Let's Me See Sea`

在我所知的创业实践中，几乎什么都是短缺的，一切都是不确定的。
整个团队都在一条船上，要在海上生存和探寻，防止迷失和沉船。

## 0G.2.纵向模型 Floor

业务架构，业务模型，程序架构，数据模型，有严格的边界和依赖要求。
通常，从下至上像楼层一样，分别称之为Floor-N（N为自然数）

### 单向调用，避免跨层

通常，上层可以调用同层及下层，反之不可。如 Dao/Ser/Mvc的结构中，

* Service中可以调用Dao和Service，反之则应避免。^推荐^
* Controller可以调用Service，反之则禁止。^必须^
* Controller不可调用Dao。^推荐^

### 单向流动，事件溯源

数据流，业务流，要求单向流动。乱流时，以明确的Event传播和溯源。
如数据的从下向上构建，业务的从上到下传播。

## 0G.3.横向功能 Layer

功能或模块可以通过组合，继承，叠加或过滤后对外提供合适的服务。
通常，从内到外，分别称为Layer-N（N为自然数）
