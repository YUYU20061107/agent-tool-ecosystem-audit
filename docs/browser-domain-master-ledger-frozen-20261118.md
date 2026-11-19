# 浏览器域裁决后主账冻结件（2026-11-18）

- **性质**：浏览器域试点（四模型 × 10 家族 × 4 条件 × 3 臂，设计格子替换制）经 J1–J8 全部裁决后的**单一冻结主账正本**，补 C1 签署前置缺口 2（见 `files/c1-gap-check-20261118.md`）。自本件冻结起，浏览器域试点数字以本件为准；裁决前口径留痕于下列源文件，不再单独引用。
- **冻结方**：Muse，2026-11-18。拼合与回写，**未新跑任何评测、未调用任何模型 API**。

## 一、主账终局数（裁决后口径）

**主账**＝stock＋native 两臂，n=80/模型；错误＝实质错误（substantive_error），分母维持 ITT 设计格子 80 不缩减。

| 模型 | 裁决前错误 | J1 剔除（A_infra） | **裁决后错误** | **裁决后错误率** |
|---|---|---|---|---|
| M1 Flash（deepseek:deepseek-flash） | 62/80 | 0 | **62/80** | **0.775** |
| M2 Qwen（ollama:qwen3:8b） | 77/80 | 2（均在 native 臂） | **75/80** | **0.9375** |
| M3 Pro（deepseek:deepseek-v4-pro） | 67/80 | 2（均在 native 臂） | **65/80** | **0.8125** |
| M4 GLM（glm:glm-5.3-flash） | 65/80 | 0（其 4 条 infra 全在 mcp 敏感性臂） | **65/80** | **0.8125** |

与 C1 §1.3 所引四数（0.775／0.9375／0.8125／0.8125）**逐一吻合**。

**按臂（主账，n=40/臂）**：

| 模型 | stock | native（裁决前 → 裁决后） |
|---|---|---|
| M1 Flash | 31/40 | 31/40（无 infra，不变） |
| M2 Qwen | 39/40 | 38/40 → **36/40** |
| M3 Pro | 35/40 | 32/40 → **30/40** |
| M4 GLM | 33/40 | 32/40（无 infra，不变） |

**按条件（主账，n=20/条件）**：

| 条件 | M1 | M2（前 → 后） | M3（前 → 后） | M4 |
|---|---|---|---|---|
| clean | 8/20 | 18/20 → **17/20** | 10/20 | 8/20 |
| F2 | 20/20 | 20/20 → **19/20** | 20/20 | 20/20 |
| F3 | 16/20 | 19/20 | 17/20 → **16/20** | 17/20 |
| F4 | 18/20 | 20/20 | 20/20 → **19/20** | 20/20 |

受 J1 影响的四个格子：M2 native-clean 9→8、M2 native-F2 10→9、M3 native-F3 8→7、M3 native-F4 10→9；其余格子不变。

**MCP 敏感性账（n=40，不并主账）**：M1 35/40＝0.875（不变）；M2 38/40＝0.95（不变）；M3 36/40＝0.90（不变）；M4 36/40 → **32/40＝0.80**（J1 剔除其 4 条 infra）。

**全量 120 格（裁决后）**：M1 97/120；M2 115/120；M3 103/120；M4 97/120。

## 二、分母与 A_infra 处理口径

- **分母**：维持每模型 80 个设计格子（ITT），J1 不缩分母——剔除只动错误分子。此与 J1 裁决登记的新口径（75/80、65/80）一致。
- **A_infra 登记（8 条）**：计入行中 8 条 infra_error 在台账与判分中原均记 substantive_error=true；经 J1 裁决（鱼鱼 2026-11-16）全部剔除出实质错误、单列 A_infra，正文引用时加脚注。明细：

| 轨迹 | 臂 | 死因 |
|---|---|---|
| TRAJ-PILOT-M2-FAM08-F2-native-R1 | 主账 native | ollama unreachable 超时 |
| TRAJ-PILOT-M2-FAM09-clean-native-R1 | 主账 native | ollama unreachable 超时 |
| TRAJ-PILOT-M3-FAM05-F4-native-R1 | 主账 native | deepseek helper timeout |
| TRAJ-PILOT-M3-FAM10-F3-native | 主账 native | deepseek helper timeout |
| TRAJ-PILOT-M4-FAM02-F2-mcp-R1 | 敏感性 mcp | glm helper unparseable output |
| TRAJ-PILOT-M4-FAM04-clean-mcp-R1 | 敏感性 mcp | glm helper unparseable output |
| TRAJ-PILOT-M4-FAM05-F3-mcp-R1 | 敏感性 mcp | glm helper unparseable output |
| TRAJ-PILOT-M4-FAM05-F4-mcp-R1 | 敏感性 mcp | glm helper unparseable output |

- **其余裁决对本账的影响**：J2（M2 门检 2 格以主台账次为准）只动成本口径、不动错误数；J3（usage 差额维持现行口径）不动错误数；J6（steps_used=0 维持四分口径）不动错误数；J7（M2 披露名 `ollama:qwen3:8b`）为命名口径；J8（FAM06×native 结构性单元保留于主口径、共同能力范围口径另行剔除）确认主账保留该 4 格。J4/J5 属 M5 Native+V 单独集，不在本账范围。

## 三、每项数字的来源与推导链

1. **裁决前主账**（62／77／67／65 及按臂、按条件分格表）← `~/workspace/browser-domain-pilot/PILOT-FOUR-MODEL-SUMMARY.md`（2026-11-15 四模型终局汇总，设计格子替换制，台账＋判分逐条回算，脚本 `compute_four_model.py`）。
2. **逐格对账**（480 格全覆盖、缺失 0、工作表回算与已发布汇总逐格吻合；台账与判分 substantive_error 493/493 零不一致）← `~/workspace/browser-domain-pilot/reconciliation-prep-20261116/RECONCILIATION-PREP.md` §一–§三，及同目录 `reconciliation-worksheet.csv`（恰 480 行）。
3. **J1 裁决原文与新口径登记**（8 条剔除、M2 主账 75/80＝0.9375、M3 主账 65/80＝0.8125、M4 敏感性 32/40＝0.80、其余不变）← 同上 RECONCILIATION-PREP.md §五 J1（裁决：鱼鱼 2026-11-16）；J8 于 2026-11-17 确认后 J1–J8 全部裁决完毕（同文件 §五 J8）。
4. **本件独立复算（2026-11-18，Muse）**：以 `reconciliation-worksheet.csv` 480 行按 model×arm×condition 重计数 substantive_error，再按 A6 名单（即上表 8 条，逐条核对其 scored_outcome 均为 substantive_error）做 J1 扣减。结果：裁决前四数 62／77／67／65 与汇总及对账件**逐一吻合**；裁决后四数 62／75／65／65 与 J1 裁决登记数**逐一吻合**；按臂、按条件扣减位置与 8 条 infra 的家族/条件/臂归属**逐格对得上**（M2 扣 native 的 clean、F2 各一；M3 扣 native 的 F3、F4 各一；M4 扣 mcp 四条）。**四项终局数字复算全过，无对不上项。**

## 四、已知限度（照实登记，不硬凑）

- **错误构成四分表仍为裁决前口径**：四模型汇总中的主账错误构成（错值交付／缺失／未知／协议失败）按裁决前分子计（M2 77 条、M3 67 条）；本件未逐条重分 4 条主账 infra 在四分中的归类，裁决后构成细分**未重算**。引用构成表时须注「裁决前口径」；终局错误率不受此影响。
- **成本口径沿用源文件**：调用数以台账计入行为准、token 以 usage 为准；usage 无 traj_id 的结构性缺口（M3 +16 行、M4 −5 行不可归因；M2 本地模型无 usage 文件）见 RECONCILIATION-PREP 缺口 G1 与四模型汇总「未解项」，本件不另处理。
- **M2 门检双执行**：gate-prefix 次执行的轨迹工件已被覆盖、不可恢复（缺口 G2）；错误结局两次均为 substantive_error=true，不影响本账任何数字。
- **范围**：本件只覆盖 M1–M4 的 480 设计格子；M5 Native+V（40/40 补齐后终局）为单独集，准本为 `driver/runs/batch-m5-nativev-20261115/SUMMARY-M5-COMPLETED-20261116.md`，不并入本账。
- 本件数字均为**试点计数**，不作确证推断（与源汇总口径一致）。

—— 冻结：Muse，2026-11-18。源文件均未改动；本件为唯一新增件。
