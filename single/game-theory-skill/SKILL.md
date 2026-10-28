---
name: game-theory-skill
description: |
  《博弈论》(弗登博格&梯若尔)能力总入口——把行业竞争、公司行为与市场共识问题化为可求解的博弈模型并给出可检验的判断。覆盖16个能力单元(7个已晋级独立入口+9个router能力卡), 收录338条三重验证通过的能力候选与94个原书例题/64个反例边界。当问题落在博弈论投资分析但不确定具体分支时由此进入, 按 intents/keywords 路由到对应能力卡; 每张卡的 B 段(边界)与 A1 段(书中例题)保证判断有出处、不越界。
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.variant: single
  cangjie.bundle-id: bundle.game-theory-fudenberg-tirole
  cangjie.capability-count: 16
  cangjie.entrypoint-count: 1
---
# 博弈论(Game Theory) — 全书能力入口

## 触发与不触发

**适用**：与本书能力域相关的咨询与任务（见下方路由表的意图列）。
**不适用**：
- 行为金融/投资者情绪建模(本书成书于行为博弈论兴起前, 理性假设需要外部修正)
- 具体标的的估值定价(本包提供博弈结构判断, 不替代财务与估值分析)
- 反垄断法律分析(现实合谋的法律维度需另行叠加)

## 核心原则（常驻速览，概览类问题读到这里即可回答）

1. 预测对手行为靠建模找均衡, 不靠外生信念; 先数有效参与人、按时序×信息两维选均衡概念
2. 合作可持续 ⟺ 未来惩罚损失的贴现和 > 当期背离利得; 期限结构与信息结构与阈值同等重要
3. 信号可信 ⟺ 信号成本随类型系统性不同(单交叉); 威胁可信 ⟺ 兑现条件下执行仍是自身最优
4. 声誉价值 = 未来关系租金流 vs 欺骗一次的短期利得; 微小先验×长期限即可支撑威慑
5. 均衡常常多重, 预测输出区间+稳健度而非点位; 信息结构的微小差异可翻转结论

## 能力路由（先读本表，按意图加载 1 张能力卡）

| 用户意图 | 先读 | 补读/备注 |
|---|---|---|
| 判断行业合谋可持续性；预测价格战触发条件；评估限产保价联盟稳定性；解读价格战成因 | references/capabilities/collusion-price-war.md | references/capabilities/monitoring-cooperation-discipline.md、references/capabilities/competition-pattern-comparative-statics.md、references/capabilities/reputation-tough-talk.md、references/capabilities/multiple-equilibria-consensus.md |
| 解读公司反常行动的信息含义；判断信号可信性；推演市场对公告的解读；评估口头表态信息量 | references/capabilities/signal-reading-pbe.md | references/capabilities/commitment-deterrence-credibility.md、references/capabilities/reputation-tough-talk.md、references/capabilities/information-structure-common-knowledge.md |
| 评价威胁可信性；判断资本开支是承诺还是失误；评估时间一致性；判断先动利弊 | references/capabilities/commitment-deterrence-credibility.md | references/capabilities/signal-reading-pbe.md、references/capabilities/timing-war-attrition-preemption.md、references/capabilities/reputation-tough-talk.md、references/capabilities/bargaining-durable-pricing.md |
| 判别行业竞争模式；求解均衡产量价格；推演成本需求冲击传导；判断涨价跟随还是份额争夺 | references/capabilities/competition-pattern-comparative-statics.md | references/capabilities/collusion-price-war.md、references/capabilities/timing-war-attrition-preemption.md、references/capabilities/markov-state-variables.md、references/capabilities/industry-game-modeling-foundations.md |
| 预测消耗战谁先退；判断补贴战持续性；预估夕阳行业退出顺序；评价新品发布时机 | references/capabilities/timing-war-attrition-preemption.md | references/capabilities/commitment-deterrence-credibility.md、references/capabilities/competition-pattern-comparative-statics.md、references/capabilities/bargaining-durable-pricing.md |
| 评估品牌溢价真实性；评估平台信誉资产；判断供应链关系可持续性；识别一次性博弈行业 | references/capabilities/long-run-relationship-assets.md | references/capabilities/collusion-price-war.md、references/capabilities/reputation-tough-talk.md、references/capabilities/signal-reading-pbe.md |
| 判断管理层强硬表态约束力；评估威慑可持续期；识别廉价磋商；判断多市场威慑放大效应 | references/capabilities/reputation-tough-talk.md | references/capabilities/signal-reading-pbe.md、references/capabilities/commitment-deterrence-credibility.md、references/capabilities/long-run-relationship-assets.md |
| 行业博弈建模；选择均衡概念；判断博弈工具适用性；评估预测稳健性 | references/capabilities/industry-game-modeling-foundations.md | references/capabilities/competition-pattern-comparative-statics.md、references/capabilities/multiple-equilibria-consensus.md、references/capabilities/information-structure-common-knowledge.md |
| 审计行业信息透明度；检查监督结构可归因性；诊断高频考核失败；评估信息披露改动影响 | references/capabilities/monitoring-cooperation-discipline.md | references/capabilities/collusion-price-war.md、references/capabilities/information-structure-common-knowledge.md、references/capabilities/truthful-mechanisms-collective-action.md |
| 参与拍卖出价决策；解读卖方保留价与机制；比较拍卖制度；判断流拍原因 | references/capabilities/auctions-bidding.md | references/capabilities/mechanism-reverse-engineering.md、references/capabilities/bargaining-durable-pricing.md、references/capabilities/signal-reading-pbe.md |
| 核算谈判份额；判断交易破裂的结构性原因；解读持续降价与去库存；评估租赁与长期合同 | references/capabilities/bargaining-durable-pricing.md | references/capabilities/commitment-deterrence-credibility.md、references/capabilities/mechanism-reverse-engineering.md、references/capabilities/timing-war-attrition-preemption.md |
| 反推薪酬合同与返点政策意图；解读版本划分与差别定价；判断规则在筛选什么类型；识别棘轮效应 | references/capabilities/mechanism-reverse-engineering.md | references/capabilities/auctions-bidding.md、references/capabilities/bargaining-durable-pricing.md、references/capabilities/truthful-mechanisms-collective-action.md |
| 诊断集体行动失败；设计说真话机制；判断公共投入融资需求；解释搭便车现象 | references/capabilities/truthful-mechanisms-collective-action.md | references/capabilities/mechanism-reverse-engineering.md、references/capabilities/monitoring-cooperation-discipline.md |
| 诊断共识稳定性；预判市场好坏均衡切换；找共识锚；评估协调失败风险 | references/capabilities/multiple-equilibria-consensus.md | references/capabilities/industry-game-modeling-foundations.md、references/capabilities/information-structure-common-knowledge.md、references/capabilities/collusion-price-war.md |
| 评估披露对均衡的冲击；判断信息链协调可靠性；识别层级升格效应；检测市场结构异常 | references/capabilities/information-structure-common-knowledge.md | references/capabilities/signal-reading-pbe.md、references/capabilities/multiple-equilibria-consensus.md、references/capabilities/monitoring-cooperation-discipline.md |
| 设计行业跟踪清单；判断哪些历史可忽略；审查简化模型被扔掉的变量 | references/capabilities/markov-state-variables.md | references/capabilities/competition-pattern-comparative-statics.md、references/capabilities/collusion-price-war.md |

**非能力类查询**：
- 书名/作者/章节/整书概览 → references/overview.md
- 术语解释 → references/glossary.md
- 决策规则速查（不需要原文依据时） → references/cheatsheet.md
- 完整意图与关键词索引（本表未覆盖的意图先查这里） → references/capability-index.md

## 加载规则

- 每次任务先读本文件，再按路由表加载 **1** 张能力卡；任务明确跨域时最多加载 2 张。
- 概览/书名类问题不加载能力卡，用「核心原则」与 overview.md 回答。
- 路由表与 capability-index.md 都无法命中的意图，明确告知超出本书范围，不要硬套。

## 边界与判停

- 无法还原博弈规则三要素(竞争变量/时序/信息)时停止, 先补齐建模材料
- 收益参数(利润/成本/耐心)完全无法估计时只输出定性区间, 不做数值结论
- 现实情形含本书不建模的维度(法律、行为偏差、多物品动态)时明确标注并建议叠加外部框架
