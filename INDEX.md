# Skill 地图 — 博弈论

《博弈论》共蒸馏出 16 张能力卡：7 张晋级为可独立触发的 skill，9 张留在路由入口内按需加载。本文件是这张地图的全量索引，列出每张卡的标识、去向，以及卡与卡之间的 `also_read` 依赖关系。

## 能力总表

| capability_id | slug | 中文标题 | 重要度 | 去向 |
|---|---|---|---|---|
| `cap.game-theory.collusion-price-war` | `collusion-price-war` | 合谋可持续性与价格战分析 | critical | promoted → 独立 skill |
| `cap.game-theory.signal-reading-pbe` | `signal-reading-pbe` | 信号解读与动态不完全信息分析 | critical | promoted → 独立 skill |
| `cap.game-theory.commitment-deterrence-credibility` | `commitment-deterrence-credibility` | 承诺与威慑可信性分析 | critical | promoted → 独立 skill |
| `cap.game-theory.competition-pattern-comparative-statics` | `competition-pattern-comparative-statics` | 竞争格局判别与比较静态分析 | high | promoted → 独立 skill |
| `cap.game-theory.timing-war-attrition-preemption` | `timing-war-attrition-preemption` | 时机竞争：消耗战、抢先与退出分析 | high | promoted → 独立 skill |
| `cap.game-theory.long-run-relationship-assets` | `long-run-relationship-assets` | 品牌、平台与长期关系资产评估 | high | promoted → 独立 skill |
| `cap.game-theory.reputation-tough-talk` | `reputation-tough-talk` | 声誉与强硬表态分析 | high | promoted → 独立 skill |
| `cap.game-theory.industry-game-modeling-foundations` | `industry-game-modeling-foundations` | 行业博弈建模与预测基础 | high | router → 路由入口 |
| `cap.game-theory.monitoring-cooperation-discipline` | `monitoring-cooperation-discipline` | 监督结构与合作纪律 | medium | router → 路由入口 |
| `cap.game-theory.auctions-bidding` | `auctions-bidding` | 拍卖与竞价分析 | medium | router → 路由入口 |
| `cap.game-theory.bargaining-durable-pricing` | `bargaining-durable-pricing` | 议价、交易破裂与耐用品定价 | high | router → 路由入口 |
| `cap.game-theory.mechanism-reverse-engineering` | `mechanism-reverse-engineering` | 机制反推与筛选定价 | medium | router → 路由入口 |
| `cap.game-theory.truthful-mechanisms-collective-action` | `truthful-mechanisms-collective-action` | 说真话机制与集体行动 | medium | router → 路由入口 |
| `cap.game-theory.multiple-equilibria-consensus` | `multiple-equilibria-consensus` | 多重均衡与共识稳定性 | medium | router → 路由入口 |
| `cap.game-theory.information-structure-common-knowledge` | `information-structure-common-knowledge` | 信息结构敏感性与共同知识 | medium | router → 路由入口 |
| `cap.game-theory.markov-state-variables` | `markov-state-variables` | 马尔可夫状态变量 | low | router → 路由入口 |

> 去向为 `promoted → 独立 skill` 的卡在 `pack/` 下各有一个同名目录，可被 skill 列表直接命中；
> 去向为 `router → 路由入口` 的卡只存在于入口的 `references/capabilities/` 里，经路由入口访问。

## 依赖关系

下表是 `verified.yaml` 中每张卡的 `also_read` 字段，表示“主卡之外建议补读的卡”。
它是补读建议，不是前置条件——任何一张卡都能单独使用。

| 主卡 | 补读（also_read） |
|---|---|
| `collusion-price-war` — 合谋可持续性与价格战分析 | `monitoring-cooperation-discipline`、`competition-pattern-comparative-statics`、`reputation-tough-talk`、`multiple-equilibria-consensus` |
| `signal-reading-pbe` — 信号解读与动态不完全信息分析 | `commitment-deterrence-credibility`、`reputation-tough-talk`、`information-structure-common-knowledge` |
| `commitment-deterrence-credibility` — 承诺与威慑可信性分析 | `signal-reading-pbe`、`timing-war-attrition-preemption`、`reputation-tough-talk`、`bargaining-durable-pricing` |
| `competition-pattern-comparative-statics` — 竞争格局判别与比较静态分析 | `collusion-price-war`、`timing-war-attrition-preemption`、`markov-state-variables`、`industry-game-modeling-foundations` |
| `timing-war-attrition-preemption` — 时机竞争：消耗战、抢先与退出分析 | `commitment-deterrence-credibility`、`competition-pattern-comparative-statics`、`bargaining-durable-pricing` |
| `long-run-relationship-assets` — 品牌、平台与长期关系资产评估 | `collusion-price-war`、`reputation-tough-talk`、`signal-reading-pbe` |
| `reputation-tough-talk` — 声誉与强硬表态分析 | `signal-reading-pbe`、`commitment-deterrence-credibility`、`long-run-relationship-assets` |
| `industry-game-modeling-foundations` — 行业博弈建模与预测基础 | `competition-pattern-comparative-statics`、`multiple-equilibria-consensus`、`information-structure-common-knowledge` |
| `monitoring-cooperation-discipline` — 监督结构与合作纪律 | `collusion-price-war`、`information-structure-common-knowledge`、`truthful-mechanisms-collective-action` |
| `auctions-bidding` — 拍卖与竞价分析 | `mechanism-reverse-engineering`、`bargaining-durable-pricing`、`signal-reading-pbe` |
| `bargaining-durable-pricing` — 议价、交易破裂与耐用品定价 | `commitment-deterrence-credibility`、`mechanism-reverse-engineering`、`timing-war-attrition-preemption` |
| `mechanism-reverse-engineering` — 机制反推与筛选定价 | `auctions-bidding`、`bargaining-durable-pricing`、`truthful-mechanisms-collective-action` |
| `truthful-mechanisms-collective-action` — 说真话机制与集体行动 | `mechanism-reverse-engineering`、`monitoring-cooperation-discipline` |
| `multiple-equilibria-consensus` — 多重均衡与共识稳定性 | `industry-game-modeling-foundations`、`information-structure-common-knowledge`、`collusion-price-war` |
| `information-structure-common-knowledge` — 信息结构敏感性与共同知识 | `signal-reading-pbe`、`multiple-equilibria-consensus`、`monitoring-cooperation-discipline` |
| `markov-state-variables` — 马尔可夫状态变量 | `competition-pattern-comparative-statics`、`collusion-price-war` |

被引用次数最多的卡（跨卡枢纽）：

- `signal-reading-pbe` — 信号解读与动态不完全信息分析（被 5 张卡列为补读）
- `collusion-price-war` — 合谋可持续性与价格战分析（被 5 张卡列为补读）
- `competition-pattern-comparative-statics` — 竞争格局判别与比较静态分析（被 4 张卡列为补读）
- `reputation-tough-talk` — 声誉与强硬表态分析（被 4 张卡列为补读）
- `commitment-deterrence-credibility` — 承诺与威慑可信性分析（被 4 张卡列为补读）

## 加载顺序

1. **先读入口 SKILL.md**。single 模式读 `single/game-theory-skill/SKILL.md`；pack 模式读 `pack/game-theory-skill-router/SKILL.md`。入口里有触发条件、核心原则、路由表与加载规则，是唯一的必经环节。
2. **按路由表加载 1 张能力卡**。用路由表的“用户意图”列命中主卡；single 模式的路径是 `references/capabilities/<slug>.md`，pack 模式里已晋级的卡直接读它自己的 `SKILL.md`。
3. **跨域时最多补读 1 张**。依据上表的 `also_read` 选补读卡，总计不超过 2 张能力卡——一次分析里堆三张以上，判断会互相污染。
4. **概览与术语类问题不加载能力卡**。书名/章节/整书概览读 `references/overview.md`，术语读 `references/glossary.md`，只要规则速查读 `references/cheatsheet.md`。
5. **路由表与 `capability-index.md` 都命中不了的意图**，明确告知超出本书范围，不要硬套。

## 两种打包模式下的入口数量

| | 入口数 | 具体入口 |
|---|---|---|
| single | 1 | `game-theory-skill`（内含全部 16 张卡） |
| pack | 8 | `game-theory-skill-router`（路由入口，内含全部 16 张卡）+ 7 个晋级独立 skill |

pack 里被晋级为独立 skill 的 7 张卡：

- `collusion-price-war` — 合谋可持续性与价格战分析
- `signal-reading-pbe` — 信号解读与动态不完全信息分析
- `commitment-deterrence-credibility` — 承诺与威慑可信性分析
- `competition-pattern-comparative-statics` — 竞争格局判别与比较静态分析
- `timing-war-attrition-preemption` — 时机竞争：消耗战、抢先与退出分析
- `long-run-relationship-assets` — 品牌、平台与长期关系资产评估
- `reputation-tough-talk` — 声誉与强硬表态分析

留在路由入口 `references/capabilities/` 下的 9 张卡：

- `industry-game-modeling-foundations` — 行业博弈建模与预测基础
- `monitoring-cooperation-discipline` — 监督结构与合作纪律
- `auctions-bidding` — 拍卖与竞价分析
- `bargaining-durable-pricing` — 议价、交易破裂与耐用品定价
- `mechanism-reverse-engineering` — 机制反推与筛选定价
- `truthful-mechanisms-collective-action` — 说真话机制与集体行动
- `multiple-equilibria-consensus` — 多重均衡与共识稳定性
- `information-structure-common-knowledge` — 信息结构敏感性与共同知识
- `markov-state-variables` — 马尔可夫状态变量
