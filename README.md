<h1 align="center">博弈论 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把朱·弗登博格与让·梯若尔《博弈论》里的均衡分析工具，蒸馏成 16 张可单独触发、也可组合调用的能力卡。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 行业龙头连续发涨价函、签了限产保价协议，说不清这轮默契定价还能撑几个季度，也判断不了价格战会从哪一环先破
- 同一轮成本冲击或需求下滑，分不清行业是产量竞争还是价格竞争，推不出价格会落到哪个位置、这轮涨价该跟还是该抢份额
- 公司突然回购、增发、降价、扩产，读不出这是有成本的可信信号还是零成本表态，也推不出市场会怎么解读这条公告
- 管理层"死磕到底""绝不降价"的表态，评不出它还能约束行为多久，也分不清哪些话无论真实打算如何都会说、因而是零信息
- 补贴大战、亏损扩张、夕阳行业出清，判断不了谁先退、还要熬多久，也不知道这场竞赛把多少租金白白耗散掉了
- 招拍挂 / 定增询价该报多少、并购谈判的份额与时限怎么估、供应商为什么年年被要求降价，缺少一套能反推对手结构的算法

## 蒸馏了什么

16 张能力卡，按"先建模、再判竞争与可信性、最后看交易与信息结构"的顺序组织。其中 7 张晋级为可独立触发的 skill，9 张留在路由入口内按需加载（去向逐张见 [INDEX.md](./INDEX.md)）：

- **建模地基**：`industry-game-modeling-foundations`（行业博弈建模与预测基础：数有效参与人、按时序 × 信息两维选均衡概念、输出区间而非点位）
- **竞争与合谋**：`competition-pattern-comparative-statics`（竞争格局判别与比较静态）、`collusion-price-war`（合谋可持续性与价格战：δ 阈值、惩罚深度、期限结构）、`monitoring-cooperation-discipline`（监督结构与合作纪律：背离是否可归因）
- **可信性与信号**：`commitment-deterrence-credibility`（承诺与威慑可信性：子博弈完美检验）、`signal-reading-pbe`（信号解读与 PBE 四件套：类型 / 策略 / 信念 / 反应）、`reputation-tough-talk`（声誉与强硬表态：先验阈值与几何衰减）
- **时机与关系资产**：`timing-war-attrition-preemption`（消耗战、抢先与退出：L/F/B 三曲线分类）、`long-run-relationship-assets`（品牌、平台与长期关系资产：关系租金 vs 欺骗利得）
- **交易与机制**：`auctions-bidding`（拍卖与竞价）、`bargaining-durable-pricing`（议价份额与科斯猜想）、`mechanism-reverse-engineering`（机制反推与筛选定价）、`truthful-mechanisms-collective-action`（说真话机制与集体行动）
- **均衡与信息结构**：`multiple-equilibria-consensus`（多重均衡与共识稳定性）、`information-structure-common-knowledge`（信息结构敏感性与共同知识）、`markov-state-variables`（马尔可夫状态变量）

这 16 张卡背后是 338 条通过三重验证的候选单元（framework 148 / principle 190），每张卡都带原书例题（A1 段）与边界（B 段），判断有出处、不越界。

## 两种打包模式：single 与 pack

同一套 16 张能力卡，按两种粒度各编译了一次。两者内容完全相同，区别只在"agent 能看到几个入口"。

| | single（单一入口） | pack（compact pack，多入口） |
|---|---|---|
| 可发现入口 | **1 个**：`game-theory-skill` | **8 个**：1 个来源路由入口 + 7 个已晋级独立 skill |
| 16 张能力卡放在哪 | 全部在入口的 `references/capabilities/` 里，由入口按路由表按需加载 1–2 张 | 7 张卡各自独立成 skill；其余 9 张仍在 router 的 `references/` 里 |
| 触发方式 | 只有入口的 description 参与匹配，进入后靠路由表分流 | 7 个高频能力可被 description 直接命中，少一跳 |
| 升级维护 | 替换 1 个目录 | 替换 8 个目录 |

pack 里被晋级为独立 skill 的 7 张卡：

- `collusion-price-war` — 合谋可持续性与价格战分析
- `signal-reading-pbe` — 信号解读与动态不完全信息分析
- `commitment-deterrence-credibility` — 承诺与威慑可信性分析
- `competition-pattern-comparative-statics` — 竞争格局判别与比较静态分析
- `timing-war-attrition-preemption` — 时机竞争：消耗战、抢先与退出分析
- `long-run-relationship-assets` — 品牌、平台与长期关系资产评估
- `reputation-tough-talk` — 声誉与强硬表态分析

未晋级的 9 张卡（`industry-game-modeling-foundations`、`monitoring-cooperation-discipline`、`auctions-bidding`、`bargaining-durable-pricing`、`mechanism-reverse-engineering`、`truthful-mechanisms-collective-action`、`multiple-equilibria-consensus`、`information-structure-common-knowledge`、`markov-state-variables`）留在 router 的 `references/` 里，经路由入口访问，能力一张不少。

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"这轮提价能不能撑 / 这公告是不是信号 / 这表态算不算数 / 这仗谁先退 / 这牌子的溢价真不真" | pack | 这几类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：涨价函发了三轮，这轮默契定价还能撑多久

**用户问题**

"华东两家水泥龙头连续发了三轮涨价函，但产能利用率只有七成，这轮提价能撑几个季度？"

**skill 如何判断**

- 先过 `industry-game-modeling-foundations` 建模边界：这是重复互动（每期同构、历史只影响信念），归重复博弈，不是承诺 / 资本积累模型
- 进 `collusion-price-war` 步骤 2 期限检查：有没有公开确定的到期日？没有 → 按无限期框架处理
- 步骤 3 识别溢价性质：先用竞争格局卡的对称古诺 / 伯特兰基准核算，看观察到的价格是不是静态寡头加价就能解释——不能区分就不假定为合谋
- 步骤 4–5 算地板线与阈值：δ* =（max g − v）/（max g − 惩罚后每期利润），惩罚点用静态均衡 e 还是最小最大 v̲ 必须二选一并注明
- 步骤 6 估现实 δ：资金成本 + 关系存续概率 + 调价间隔三源合成，给区间不给点；年度口径与季度调价之间要先做换算
- 步骤 8 比较判停：δ 区间与 δ* 无交集 → 判"不可持续"；骑线 → 判"条件性可持续"并列出翻转因素

**最终回答示例**

> 结论是条件性可持续，不是"能撑住"。三件事要分开看。第一，涨价函本身是零成本的，它不构成承诺——真正支撑价格的是"背离之后会被打回竞争"这个威胁，所以判断落在 δ 上，而不是函件频率上。第二，你的产能利用率只有七成，意味着背离的当期利得 max g 很大（多出来的产能随时可以低价填满），δ* 会被推高；同时行业资金成本和调价间隔决定了现实 δ 大概在哪个区间。两个区间一比：如果现实 δ 明显低于 δ*，那这轮提价的正确预期是"撑不过下一轮需求淡季"；如果骑线，就要把翻转因素写下来——谁先背离、需求冲击多大、有没有临近的确定终点（长协到期、新增产能投放）。
>
> 还有两条必须自己补。一是惩罚后每期利润用 e（静态均衡）还是 v̲（最小最大）——差 0.05–0.10 就足以改变骑线判定，你不选一个并写进预案，同一组数据会得出相反结论。二是如果这个行业只能看到市场价、看不到各家出货明细，那价格战可能根本不是有人背叛，而是需求噪声触发的纪律机制（Green-Porter 型）：观察到价格战不等于观察到背叛。这种情况下该转 `monitoring-cooperation-discipline` 先查信息结构能不能归因，而不是继续算 δ。

### 示例 2：管理层说"绝不降价"，这话能约束多久

**用户问题**

"董事长在业绩会上说'我们绝不参与价格战，死磕到底'。这算不算数？"

**skill 如何判断**

- 进 `reputation-tough-talk` 步骤 1 廉价磋商过滤：假如他实际打算降价，他还会说同样的话吗？会 → 这句话本身零信息
- 步骤 2 查承诺类型支撑：市场先验里有没有"不计成本死磕"的类型正概率？为零 → 声誉机制失效，流程终止
- 步骤 3 查行动可观察性：对手 / 投资者能不能看到他的实际行为？看不到（比如根本没有进入者来试探）→ 类型永远无法暴露，定理不适用
- 步骤 4 算阈值：两期版 p̄ = b/(b+1)，第 k 期阈值 [b/(b+1)]^k，几何衰减；比较 p⁰ 与阈值，倒算出末端瓦解窗口
- 步骤 5 结构检查：让步是否可逆（可逆才有多市场声誉放大）、信息是否关联（透明度的灵活性代价）

**最终回答示例**

> 先分两层。第一层是话本身：这句话对任何真实打算都成立——他就算准备降价，也会说"死磕到底"，所以言辞的信息量为零，不能作为判断依据。能约束行为的是声誉机制：市场是否给了"不计成本的强硬类型"一个正概率 p⁰，以及他还剩多少期要打。
>
> 第二层才算得出来：设 b 为对手退让时他得到的收益，威慑维持到倒数第 k 期的条件是 p⁰ > [b/(b+1)]^k，阈值按几何速率递减。注意方向——k 是从终点倒数的剩余期数，p⁰ 只够撑到倒数若干期，越靠后的末期越容易瓦解，前面的期数都可信。所以这个公式给的是**末端瓦解窗口的长度**，不是"总共可信几期"；把它读成后者是这张卡在压力测试里被抓出来并回炉修正过的方向性错误。
>
> 两个常见错觉要提前排掉：一是"集团体量大、多个市场一起强硬所以更可信"——让步不可逆的多市场竞争里，人数会被约去，每个市场的均衡和一对一完全相同，除非让步可逆（对手能重新进入）。二是"表态越频繁越可信"——约束力只取决于 p⁰ 与剩余期限，不取决于喊话次数。如果 p⁰ 你根本估不出来，正确做法是输出"先验—期限条件表"（p⁰ 落在哪个区间对应哪种结局），而不是硬给一个单点判断。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（跨域）、能回答书中未明说的新问题（预测力）、不是常识（独特性）
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表
6. **触发与输出测试**——为每张卡设计触发盲测题（含诱饵题：该触发时要触发，不该触发时要沉默）与输出评测场景，未通过的卡回炉重做，回炉后再做回归验证

本书的几处特殊处理也影响蒸馏结果：原书是研究生水平的理论教科书，几乎没有直接的股票市场案例，"博弈概念 → 投资场景"的映射由能力卡自行构建并自设参数；定理证明与技术性小节（1.3、3.3、5.5–5.6 部分、7.6 附录、12.1、13.3）不作独立能力，只作各卡的依据引用；序贯均衡与颤抖手的技术定义并入"可信性检验"的参考层，不单独成卡。

## 测试与验证

测试材料随 skill 一起发布：各 skill 目录下的 `test-prompts.json` 共 9 份、107 条用例（其中 `single/` 与 `pack/` 路由入口的 22 条路由用例为同一份，去重后 85 条），外加仓库根目录的逐项评分记录 [test-results.md](./test-results.md)。

- **触发用例 63 条**（7 张晋级卡 × 9 条）：should_trigger 35 条、should_not_trigger 21 条、edge_case 7 条
- **路由可达用例 22 条**（`game-theory-skill-router`）：should_trigger 16 条（route-U01…U16，逐条对应一张能力卡）、should_not_trigger 4 条、edge_case 2 条
- **触发盲测结果**：干净 sub-agent 盲测首轮 81 / 85 通过（95.3%），4 条失败全部是近邻歧义而非能力缺失；按"修 skill、不修测试"补齐三对近邻分流条款后，回归与全量复测 85 / 85 与更新后的描述一致（若按最初测试预期口径则为 82 / 85，两个数并列记录，不以后者掩盖前者）
- **路由可达结果**：22 / 22 通过，16 条 route 题全部落到预期能力卡，4 条无关场景全部返回 none
- **输出评测**：16 张卡各 1 个代表任务，16 / 16 完成；数值类结论抽查与书中定理一致（如 δ* = 0.75、二价报价 = 估值、MS 门槛 1/4、声誉阈值几何衰减）
- **回炉修复**：16 张卡全部打补丁，其中 `reputation-tough-talk` 有一处方向性错误（把几何衰减倒算的临界期数读成"可维持 4 期"，已改为"末端瓦解窗口"读法）

## 仓库结构

```text
game-theory-skill/
├── README.md               ← 你正在看的
├── README.en.md            ← English version
├── LICENSE                 ← MIT
├── BOOK_OVERVIEW.md        ← 阶段 0 产出：全书 Adler 分析
├── DIGEST.md               ← 阶段 5 产出：面向读者的整书精华长文
├── INDEX.md                ← 阶段 3 产出：skill 总览 + 依赖关系
├── verified.md             ← 通过三重验证的 338 个单元
├── coverage-audit.md      ← 阶段 1.5 产出：原书任务覆盖审计
├── needs-review.md        ← 阶段 1.5 产出：待核查事项与缺口
├── TEST_SUMMARY.md         ← 阶段 4 产出：压力测试摘要
├── CANGJIE_ADAPTATION.md   ← 仓颉适配说明
├── GITHUB_REPO.md          ← 仓库元数据
├── test-results.md         ← 测试结果记录
├── candidates/             ← 阶段 1 产出：原始候选池
│   ├── frameworks.md       ← 框架与方法候选
│   ├── principles.md       ← 原则 / 规则 / 计算候选
│   ├── cases.md            ← 书中案例候选
│   ├── counter-examples.md ← 反例与边界候选
│   └── glossary.md         ← 术语候选
├── rejected/               ← 阶段 1.5 产出：被淘汰的单元 + 原因
├── bundle/                 ← 编译事实源
│   ├── verified.yaml       ← 能力元数据、判据与去向
│   ├── cards/              ← 能力卡源文件（六段结构）
│   └── book/               ← overview.md + glossary.md
├── single/                 ← single 模式（1 个入口 + 全部能力卡）
│   └── game-theory-skill/SKILL.md  ← 入口：触发 + 路由表 + 加载规则
└── pack/                   ← pack 模式（1 个路由入口 + 7 个晋级 skill）
    └── */SKILL.md          ← 8 个 skill，每个附带 test-prompts.json
```

## 如何使用

先把仓库克隆下来：

```bash
git clone https://github.com/raphael-y7/game-theory-skill.git
```

### 装 single（推荐先试这个）

```bash
# macOS / Linux
cp -r game-theory-skill/single/game-theory-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\game-theory-skill\single\game-theory-skill "$env:USERPROFILE\.agents\skills\"
```

### 装 pack

只复制含 `SKILL.md` 的目录，不要把 `pack/` 下的两个 json 一起拷进 skills 目录：

```bash
# macOS / Linux
cd game-theory-skill/pack
cp -r game-theory-skill-router \
      collusion-price-war \
      signal-reading-pbe \
      commitment-deterrence-credibility \
      competition-pattern-comparative-statics \
      timing-war-attrition-preemption \
      long-run-relationship-assets \
      reputation-tough-talk ~/.agents/skills/
```

```powershell
# Windows
$pack = ".\game-theory-skill\pack"
$dest = "$env:USERPROFILE\.agents\skills"
@('game-theory-skill-router','collusion-price-war','signal-reading-pbe','commitment-deterrence-credibility','competition-pattern-comparative-statics','timing-war-attrition-preemption','long-run-relationship-assets','reputation-tough-talk') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` 是 DSH 的 skill 目录；用别的 agent 时换成它自己的 skills 目录即可（例如 Claude Code 是 `~/.claude/skills`）。

### 怎么确认装好了

装完问一句"这两家龙头连发涨价函，这轮提价能撑几个季度"，看 agent 是否直接进入 `collusion-price-war` 的 δ* 核算流程（先查期限、再辨溢价性质、算地板线与阈值、比较判停），而不是给你一段泛泛的行业景气分析。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

《博弈论》朱·弗登博格（Drew Fudenberg）、让·梯若尔（Jean Tirole）著

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（临界贴现因子 δ*、声誉阈值 [b/(b+1)]^k、交易破裂的 1/4 门槛、拍卖收入等价等）都是定理在特例下的计算结果与教学例题的归纳，其成立依赖"参与人完全理性、结构为共同知识"这一组假设，原书未提供统计回测背书，也不保证在现实市场中成立。使用时需按标的自行测试并声明所用口径。本仓库内容不构成投资建议。

## License

[MIT](./LICENSE)
