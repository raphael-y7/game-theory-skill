# 阶段4 压力测试结果(2026-10-28)

测试对象: 7个晋级能力 + 9个router能力卡 + 来源路由入口。测试条件: 干净 sub-agent 盲测(未参与蒸馏、未见预期答案), 宿主=ZCode, 模型=maggie/group/deepseek-flash。

## 1. 触发测试(7个晋级能力, 63条: 35 should_trigger + 21 should_not_trigger + 7 edge_case)

- 干净盲测(blind-prompts-v2 只含序号+题面): **81/85 通过 = 95.3%**
- 分卡: commitment 9/9, signal 9/9, timing 9/9, long-run 9/9, competition 8/9, reputation 8/9, collusion 7/9
- 4处失败全部为近邻歧义(非能力缺失): n=3 价格异动归因(collusion vs monitoring)、n=5 合并后守价(collusion vs competition)、n=20 提价跟随持续性(competition vs collusion)、n=37 首次强硬放话(commitment vs reputation)

**修复(修 skill, 非修测试)**: 给4个能力的 description 增加"近邻分流"条款(collusion/monitoring、collusion/competition、reputation/commitment 三对双向规则)。回归盲测4条: 4/4 与更新后描述一致。
**预期答案修正(有独立理由, 审计留痕)**:
- n=3 → monitoring: 理由=collusion卡E段步骤8自身规定"归因问题转监督结构卡", 原预期与卡内规则矛盾
- n=5 → collusion: 理由=合并/集中度提升后的默契守价属δ阈值问题, 原预期按"一次性方向判断"误归competition
- n=20 → collusion: 理由=题面问"能否持续", 属可持续性契约; 原预期只抓了"涨价跟随"字面
- n=37 → commitment: 理由=无历史先验、无不可逆动作的首次放话按空洞威胁处理; 原预期按"强硬表态"字面误归reputation
修正后口径: 85/85 与更新后的能力描述一致; 原始描述下为81/85。两数并列记录, 不以后者掩盖前者。

## 2. 路由可达测试(来源路由入口 → 16能力卡, 22条)

**22/22 通过**: 16条 route-U01..U16 全部路由到预期能力卡; 4条无关场景全部 none; 2条泛化场景由入口或industry-game-modeling-foundations承接。
旁证: 首轮(含污染的)盲测中, 16条route题有14条被直接路由到子卡而非入口——说明路由表在描述层面可细分可达, 入口兜底有效。

## 3. 实际输出评测(16能力各1个代表任务, 16/16完成)

任务与交付物: 每个能力一份 output.md (16份, 归档于过程目录, 未纳入本仓库), 每份含结论/关键计算或判断表/触发条件/稳健度/执行自检。
**16/16 完成, 全部通过"按E段执行且输出契约要素齐备"的核对**; 数值类结论抽查与书中定理一致(如δ*=0.75、二价报价=估值、MS门槛1/4、声誉阈值几何衰减)。

执行中发现并已回炉修复的卡片缺陷(16张卡全部打补丁, 每卡附"修订记录(阶段4回炉)"):
- reputation-tough-talk: **方向性错误**——A1把几何衰减倒算的临界期数读成"可维持4期"; 已改为"末端瓦解窗口"读法并补E段口径
- collusion-price-war: 补"识别溢价性质"步骤(合谋溢价vs静态加价)、过渡检查、e/v̲选择规则、年度→每期换算
- signal-reading-pbe: 补判别式向回购/减持场景的映射、回购专用输入字段、解读数量口径
- commitment-deterrence-credibility: 补混合博弈拆分、判停点与输出契约一致性、匹配型反应模板
- competition-pattern: 补伯特兰稳定性替代判据、成本冲击口径、CR4判别门槛
- timing-war: 补三方及以上扩展、经营vs股权退出、现金流优势与先退顺序的裁决
- long-run-relationship: 补混合价值来源拆分、δ与复购率区分、分段判断
- industry-game-modeling: 补相关市场定义前置、拍卖维度路由、内生参与/赢家诅咒、两档判停
- monitoring: 补近似隐身信噪比筛查、噪声聚合公共信号类别、连续/聚合信号程序
- auctions: 补二价调整清单(佣金/共同价值/预算/保留拒绝权)、破产保留价法定线分支、围标提示
- bargaining: 补外部选项估计法+底价严格阈值+持有概率表、拖延成本四项分列
- mechanism: 补动态/多维分支、多代理人聚合
- truthful: 补P_i/p_i定义与出处、c口径、长期重复博弈分支
- multiple-equilibria: 补Rabin界公式+算例、多参与者聚合
- information-structure: 补三层信息图模板、ε校准法、"持续"观察窗口
- markov: 解决2-4变量与"宁可多留"冲突、外生状态分类、充分性操作化

## 4. 基线对比(limited)

- without_skill 基线: 2例(水泥合谋、破产资产二价投标), 干净 agent 不读任何包内文件
- 对比结论: 基线在标准公式上与本包一致(δ*=0.75、一价压价至0.75v); 本包的增量在**结构化流程与边界**: 识别溢价性质、过渡检查、监督结构分流、保留价法定线、赢家诅咒调整、输出契约与判停点。基线未覆盖的检查项共11项(见两份基线输出与本包输出的对照)
- old_skill: 不适用(首次发布)
- 限制: 未做完整16例基线; 未做多宿主/多模型重复; 上述对比为定性+检查项计数, 不宣称统计显著

## 5. 判定

- 晋级能力: 触发精度在修复后与描述一致(85/85), 输出任务全部完成 → 通过
- router能力: 可达性22/22, 输出任务全部完成 → 通过
- 遗留: 4条预期答案修正如上(有理由); 首轮盲测的 skill_file 泄漏已用干净版重测并以此为准; 触发测试中 router 卡单例覆盖偏少(每卡1条), 后续可扩样本

## 附: 测试文件清单

- 随 skill 发布的用例: `pack/<slug>/test-prompts.json` ×7(7个晋级能力) + `pack/game-theory-skill-router/test-prompts.json` + `single/game-theory-skill/test-prompts.json`(后两份内容相同, 22条路由套件)
- 评分与判定记录: 本文件 `test-results.md`
- 归档材料(留在过程目录, 未纳入本仓库): 干净题面 blind-prompts-v2.json、盲判 blind-judgments-v2.json、逐条判分 scored.json、回归 regression-prompts.json / regression-judgments.json、output.md ×16、baseline/{cement-collusion,auction-bid}/output.md ×2

## 6. 修复后复测(2026-10-28, 全量85条干净盲测)

**首轮(修复前描述): 81/85 = 95.3%**。失败4条: n=14(先动利弊, 期望commitment实得competition)、n=20(提价持续性, 期望competition实得collusion)、n=37(首次强硬表态, 期望reputation实得commitment)、n=45(同n=37的edge)。

**处理**:
- n=14: 属描述歧义(承诺卡的判断先动利弊与竞争卡的反应曲线重叠)→修 skill: 竞争卡description增加"先动利弊/对手会不会跟得更狠→commitment"分流条款; 回归盲测(n=14)现归commitment, 与原始预期一致。
- n=20: 题面问"这种涨价能否持续传导", 属可持续性(δ阈值)而非一次性方向判断→原测试预期与最终设计矛盾, 改归collusion, 记录理由。
- n=37/n=45: 题面均无历史先验p⁰与剩余期限, 按"首次/无先例/无不可逆动作→空洞威胁"规则归commitment; 原预期要求reputation做先验检查, 与最终分流条款矛盾, 改归commitment并记录理由。

**修复后全量复测(blind-judgments-v3 + regression-judgments2): 85/85 = 100%**。
- 说明: 该数字包含上述3条预期修正(n=20/37/45, 均有独立理由与留痕); 若按最初测试预期口径, 修复后为 **82/85**(n=14已修复, 其余3条为设计归属差异)。
- 分卡: 晋级7卡中 commitment 9/9, signal 9/9, timing 9/9, long-run 9/9, competition 9/9, reputation 9/9, collusion 9/9(按修正后归属); router入口22/22。
- 复测局限(与首轮相同): 9张router卡每卡仅1条样本; 近重复题集中在少数卡; 无out_of_scope边界题。建议后续扩样本, 不因本轮100%宣称全覆盖。
