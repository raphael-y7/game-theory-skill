# Stage 4 压力测试摘要

> 本文件汇总《博弈论》（弗登博格、梯若尔）skill 包在 cangjie-skill 流水线阶段 4 的测试资产与结果。原始材料见 `evals/`（8 份触发用例 + `test-results.md`）与各 skill 目录下的 `test-prompts.json`。数据来源：`evals/test-results.md`、`evals/test-prompts__*.json`、`审计过程/PIPELINE_STATE.md`。

## 测试范围

- **能力单元**：16 个（7 个晋级独立入口 + 9 张 router 能力卡），编译为两种形态——`single/` 1 个入口（16 张卡全部在入口的 `references/capabilities/` 内）、`pack/` 8 个入口（1 个来源路由入口 + 7 个晋级独立 skill）。
- **test-prompts 文件**：17 份。`evals/` 下 8 份（`test-prompts__<slug>.json`，按能力一份）+ 9 份随 skill 放置的副本（`pack/<slug>/test-prompts.json` ×8、`single/game-theory-skill/test-prompts.json` ×1，与 `evals/` 同名文件逐字节一致）。
- **用例总数**：85 条（去重后），覆盖三类：
  - `should_trigger`（应触发）51 条——7 个晋级能力各 5 条 + 入口路由 16 条，取自投资者真实口吻的问题；
  - `should_not_trigger`（诱饵，零容忍）25 条——7 个晋级能力各 3 条 + 入口路由 4 条（含跨 skill 近邻负例与无关场景）；
  - `edge_case`（边界）9 条——7 个晋级能力各 1 条 + 入口路由 2 条（前提缺失、泛化场景等）。
- **关于 `output_case`**：用例 JSON 中**没有** `output_case` 这个 type，`type` 取值仅上述三种。输出评测不走 test-prompts，而以"16 个能力各 1 个代表任务"的形式单独执行，产物为 `evals/outputs/<slug>/output.md` 16 份（**这 16 份输出留在归档目录 `审计过程/evals/outputs/`，未纳入本仓库**），结果记录在 `evals/test-results.md` 第 3 节。

## 结构检查

- **JSON 可解析性**：17 份 test-prompts JSON（`evals/` 8 + 随 skill 副本 9）逐份解析，0 失败；每份均含 `skill` / `version` / `test_cases` 字段，`type` 取值仅 `should_trigger` / `should_not_trigger` / `edge_case` 三种，无未知取值；单份用例数 9 条（7 个晋级能力）或 22 条（入口路由）。
- **frontmatter**：9 个 `SKILL.md`（`pack/` 8 个 + `single/` 1 个）全部以 `---` 开头，`name` 与 `description` 齐备，`description` 为块标量（`|`），0 异常。
- **六段完整性**：55 张 RIA++ 能力卡（`bundle/cards/` 16 + `single/game-theory-skill/references/capabilities/` 16 + `pack/game-theory-skill-router/references/capabilities/` 16 + `pack/` 7 个晋级 skill 的 `SKILL.md`）逐份检查 `R` / `I` / `A1` / `A2` / `E` / `B` 六个段标题，全部齐备，0 缺段。`single/game-theory-skill/SKILL.md` 与 `pack/game-theory-skill-router/SKILL.md` 是路由入口卡而非能力卡，不采用六段结构（检查中按预期排除，非缺陷）。
- **candidates 资产**：`candidates/` 15 份文本（framework 148 / principle 189 / cases 94 / counter-examples 64 / glossary 40 = 535 条候选，按 `PIPELINE_STATE.md` 口径；实测 `principle.md` 含 191 个 id，含阶段 1.5 补漏的 p-190、p-191），另有 framework-C1–C5、principle-C1–C5 十份分块提取过程稿。无图片、无 PDF。

## 结果

- skills: 9（`single/` 1 个入口 + `pack/` 8 个入口；能力卡 16 张）
- test_json: 17（`evals/` 8 + 随 skill 副本 9）
- 通过情况（取自 `evals/test-results.md`，测试条件为干净 sub-agent 盲测：未参与蒸馏、未见预期答案）：

| 项目 | 规模 | 结果 |
|---|---|---|
| 触发盲测（全量） | 85 条 = 7 个晋级能力 63 条（35 should_trigger + 21 should_not_trigger + 7 edge_case）+ 入口路由 22 条 | 首轮 **81/85 = 95.3%**；分卡 commitment 9/9、signal 9/9、timing 9/9、long-run 9/9、competition 8/9、reputation 8/9、collusion 7/9 |
| 路由可达（入口 → 16 能力卡） | 上述 85 条中的 22 条 | **22/22 通过**（16 条 route-U01..U16 全部到预期卡；4 条无关场景全 none；2 条泛化场景由入口或 industry-game-modeling-foundations 承接） |
| 实际输出评测 | 16 个能力各 1 个代表任务 | **16/16 完成**，全部通过"按 E 段执行且输出契约要素齐备"的核对；数值抽查与书中定理一致（δ*=0.75、二价报价=估值、MS 门槛 1/4、声誉阈值几何衰减） |
| 基线对比（without_skill） | 2 例（水泥合谋、破产资产二价投标） | 定性 + 检查项计数：基线在标准公式上与本包一致，本包增量为结构化流程与边界（11 项检查项） |

- **失败项与修复如实记录**：首轮 4 处失败全部为近邻歧义（n=3 collusion vs monitoring、n=5 collusion vs competition、n=20 competition vs collusion、n=37 commitment vs reputation），处理方式是**改 skill 的 description 补近邻分流条款**（4 张卡），回归盲测 4/4 与更新后描述一致。另有一批预期答案修正，`test-results.md` 两处记录口径不同：第 1 节列 n=3 / n=5 / n=20 / n=37 四条，第 6 节列 n=20 / n=37 / n=45 三条，均附独立理由与留痕，本文件不合并两个数字。
- **修复后复测**：85 条干净盲测按最终设计归属 **85/85**；若按最初测试预期口径则为 **82/85**。两数并列记录，不以后者掩盖前者。
- **限制（不得省略）**：9 张 router 卡每卡仅 1 条样本；近重复题集中在少数卡；无 out_of_scope 边界题；未做多宿主/多模型重复；基线对比为定性+检查项计数，不宣称统计显著。**本包不宣称"100% 即全覆盖"。**

## 可接入 darwin-skill 的后续动作

1. **作为回归样本直接接入**：85 条用例已按能力分文件、带 `type` 与 `expected_behavior`，可直接作为 darwin-skill 的回归集。建议按 `type` 分层评估——诱饵（`should_not_trigger`）单独统计为零容忍指标，不与正向触发混算。
2. **用随 skill 的副本复跑**：`pack/<slug>/test-prompts.json` 与 `evals/test-prompts__<slug>.json` 内容一致，盲测时只给 `prompt`，不提供 `type` / `expected_behavior` / `notes`；入口侧用 `single/game-theory-skill/test-prompts.json`（22 条路由套件）。
3. **已修缺陷作为回归锚点**：4 条近邻歧义（collusion/monitoring、collusion/competition、competition/collusion、commitment/reputation）应固化为必跑用例，防止后续改 description 时回退；阶段 4 回炉的 16 张卡补丁（如 reputation 的"末端瓦解窗口"读法、collusion 的"识别溢价性质"步骤）同理。
4. **补样本量**：9 张 router 卡每卡仅 1 条，建议扩到每卡 3–5 条，并补 out_of_scope 边界题，这是当前最明显的覆盖缺口。
5. **输出评测与触发评测分开统计**：16 份 `output.md` 的"输出契约要素齐备"核对与 test-prompts 的触发判定是两类能力，接入 darwin-skill 后应分列，不合并成单一通过率。
6. **登记未收敛的归属竞争**：n=20（提价能否持续）在"竞争方向判断"与"合谋可持续性"之间天然摇摆，n=37（首次强硬放话）在 commitment 与 reputation 之间亦然；接入时应把两类 prompt 同表对照，收集分流证据，而不是靠单轮通过率判定已收敛。
