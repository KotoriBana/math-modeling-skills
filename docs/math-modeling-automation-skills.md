# 数学建模自动化 Skills 调研

调研日期：2026-05-16

目标：整理网上可用于数学建模竞赛、数学建模自动化、论文生成、数据处理和建模流程管理的 AI Skills / Agent 工作流项目。

## 总体结论

网上确实已有一批可用项目，但它们的定位不同：

- 原生 Codex / Claude Skill：适合直接作为 AI Agent 的技能包使用。
- 自动化流水线：适合端到端跑题目解析、建模、求解、论文生成。
- 方法论 Skill：适合作为建模知识、模型选择、质量检查的参考材料。
- Trae / 其他工具 Skill：需要迁移或改写，但里面的流程设计值得借鉴。

如果目标是“在 Codex 里尽快用起来”，优先看 `handsomeZR-netizen/mathmodel-skill` 和 `deafenken/auto-MM`。

## 推荐清单

| 推荐级别 | 项目 | 类型 | 适合场景 | 备注 |
|---|---|---|---|---|
| A | [handsomeZR-netizen/mathmodel-skill](https://github.com/handsomeZR-netizen/mathmodel-skill) | Codex / Claude 双入口 Skill | CUMCM、MCM/ICM、电工杯流程管理 | 最适合先试用 |
| A | [deafenken/auto-MM](https://github.com/deafenken/auto-MM) | 端到端自动化 Skill 套件 | 题目 PDF 到论文包 | 自动化强，强调匿名和引用校验 |
| A- | [RealSeaberry/AutoMCM-Pro](https://github.com/RealSeaberry/AutoMCM-Pro) | Claude Code 自动化系统 | AP/MANUAL 双模式、GitOps、自验证 | 功能强但可能需要适配 Codex |
| B+ | [XiaoMaColtAI/math-modeling-skill](https://github.com/XiaoMaColtAI/math-modeling-skill) | 中文数模 Skill | 建模分析、代码实现、论文撰写 | 算法资源库较全 |
| B | [yushui2022/liuhuan-mathmodel-skills](https://github.com/yushui2022/liuhuan-mathmodel-skills) | Trae Skills 流水线 | 论文自动化、数据清洗、微单元生成 | 可借鉴或迁移 |
| B- | [majiayu000/claude-skill-registry mathematical-modeling](https://github.com/majiayu000/claude-skill-registry/blob/main/skills/other/other/mathematical-modeling/SKILL.md) | 通用数学建模知识 Skill | 建模方法论、模型评估 | 非竞赛自动化 |

## 1. handsomeZR-netizen/mathmodel-skill

链接：[https://github.com/handsomeZR-netizen/mathmodel-skill](https://github.com/handsomeZR-netizen/mathmodel-skill)

特点：

- 面向 CUMCM、MCM/ICM、电工杯。
- 支持 Claude Code 的 `SKILL.md` 和 Codex CLI 的 `AGENTS.md`。
- 采用 10 阶段工程化流程。
- 使用 `decision_log.json` 持久化状态，可跨工具接力。
- 提供 fast、standard、championship 等模式。
- 内置多层反馈、跨阶段一致性检查、模型目录、论文结构和评分参考。

适合：

- 希望在 Codex 和 Claude Code 之间切换。
- 希望流程由 AI 引导，但关键决策仍由人确认。
- 希望做选题、建模、求解、写作和终局评审的完整管理。

注意：

- 项目说明里明确它“不替选题、不替建模、不保证拿奖”。
- 更像高质量流程辅助，而不是无人值守全自动提交器。

## 2. deafenken/auto-MM

链接：[https://github.com/deafenken/auto-MM](https://github.com/deafenken/auto-MM)

特点：

- 包含 5 个 staged skills：`auto-mm`、`auto-mm-triage`、`auto-mm-modeling`、`auto-mm-solving`、`auto-mm-writing`。
- 支持 MCM/ICM、CUMCM 和其他数模类比赛。
- 流程覆盖：题目读取、选题评分、模型形式化、求解、验证、敏感性分析、LaTeX 写作、匿名扫描、打包 `submit.zip`。
- 强调 resume-safe，即中断后可继续。
- 强调匿名规则、真实引用、验证和时间预算。

适合：

- 想从题目 PDF 自动推进到论文包。
- 想做正式比赛前的端到端演练。
- 想借鉴分阶段 agent 架构。

注意：

- 它会打包提交文件，但不会自动提交。
- CUMCM 模板可能需要用户自行提供当年官方模板。

## 3. RealSeaberry/AutoMCM-Pro

链接：[https://github.com/RealSeaberry/AutoMCM-Pro](https://github.com/RealSeaberry/AutoMCM-Pro)

特点：

- 提供 `/auto-mcm`、`/cumcm-master`、`/mcm-master` 三个 Skill。
- 覆盖题目解读、文献调研、数据预处理、模型构建、自验证、敏感性分析、LaTeX 论文和 PDF 编译。
- 有 AP 模式和 MANUAL 模式。
- 使用 `state/pipeline.json` 做 GitOps 风格状态机。
- 要求所有求解代码配套验证脚本。
- 支持多 Agent 并行、质量门禁、论文版本快照。

适合：

- 想实验高度自动化的数学建模流水线。
- 想做自动验证、阶段回滚、并行子问题求解。
- 想借鉴 GitOps 管理建模流程。

注意：

- 更偏 Claude Code 生态。
- 自动化程度高，实际使用时更需要人工审查模型假设和结果。

## 4. XiaoMaColtAI/math-modeling-skill

链接：[https://github.com/XiaoMaColtAI/math-modeling-skill](https://github.com/XiaoMaColtAI/math-modeling-skill)

特点：

- 中文数学建模 Skill。
- 三阶段协作：建模分析、代码实现、论文撰写。
- 提供 7 大类 60+ 算法资源：优化、预测、评价、图论、统计分析、综合算法、机器学习。
- 集成 docx、pdf、xlsx、paper_search 等子技能思路。
- 面向 CUMCM、MCM/ICM、研究生数模等。

适合：

- 希望快速获得中文数模建模工作流。
- 希望有模型和算法选择参考。
- 希望借鉴建模手、编程手、论文手的角色分工。

注意：

- 自动化流水线能力弱于 `auto-MM` 和 `AutoMCM-Pro`。
- 更像结构化助手包和知识库。

## 5. yushui2022/liuhuan-mathmodel-skills

链接：[https://github.com/yushui2022/liuhuan-mathmodel-skills](https://github.com/yushui2022/liuhuan-mathmodel-skills)

特点：

- Trae Skills 项目，不是原生 Codex Skill。
- 包含多个有用模块：
  - `paper-workflow-orchestrator`
  - `modeling-paper-rubric-and-model-selector`
  - `data-cleaning-and-visualization`
  - `authoritative-data-harvester`
  - `paper-micro-unit-generator`
- 目标是赛题解析、数据整理、写作生成、合并成稿。
- 输出结构包括 `problem_files/`、`crawled_data/`、`paper_output/`。

适合：

- 想借鉴论文自动化流水线。
- 想拆分“数据获取、清洗、生成、合并、QA”这些技能。
- 想迁移到 Codex Skill 格式。

注意：

- 需要适配路径、脚本和工具环境。
- 一键生成论文的质量仍需人工审校。

## 6. claude-skill-registry mathematical-modeling

链接：[https://github.com/majiayu000/claude-skill-registry/blob/main/skills/other/other/mathematical-modeling/SKILL.md](https://github.com/majiayu000/claude-skill-registry/blob/main/skills/other/other/mathematical-modeling/SKILL.md)

特点：

- 通用数学建模 Skill。
- 覆盖建模循环、Polya 方法、常见模型、量纲分析、优化、概率模型、统计建模、模型批判。
- 强调假设、验证、解释和敏感性分析。

适合：

- 做方法论补充。
- 给自动化系统增加模型选择和模型批判能力。
- 教学、训练或作为参考 Skill。

注意：

- 不是比赛自动化系统。
- 不包含完整数据处理和论文生成流水线。

## 其他参考

- [Anthropic skills](https://github.com/anthropics/skills)：可参考官方 Skills 结构和写法。
- [vadimcomanescu/codex-skills](https://github.com/vadimcomanescu/codex-skills)：Codex skills 目录型仓库，可参考组织方式。

## 建议使用路线

### 路线 A：想在 Codex 里尽快试用

1. 先试 `handsomeZR-netizen/mathmodel-skill`。
2. 如果想要更自动化的端到端流程，再试 `deafenken/auto-MM`。
3. 把自己的常用模型、模板、数据处理脚本整理成项目内 `skills/` 或 `AGENTS.md`。

### 路线 B：想做自己的数模自动化系统

1. 参考 `auto-MM` 的五阶段拆分。
2. 参考 `AutoMCM-Pro` 的状态机、自验证和质量门禁。
3. 参考 `XiaoMaColtAI/math-modeling-skill` 的算法资源库和角色分工。
4. 参考 `liuhuan-mathmodel-skills` 的数据清洗、微单元生成和论文合并模块。

### 路线 C：想备赛而不是全自动

1. 用 `mathematical-modeling` 类 Skill 做模型选择和假设检查。
2. 用 `modeling-paper-rubric-and-model-selector` 类 Skill 做评分点对齐。
3. 用数据清洗/可视化模块做 EDA 和图表。
4. 论文正文由人审校和重写，AI 只做框架、草稿和检查。

## 风险和注意事项

- 自动生成的论文不能直接当成最终提交，需要人工审查事实、模型、代码和结论。
- 比赛规则可能限制 AI 使用，必须阅读当年赛事说明。
- 需要特别检查匿名规则、引用真实性、数据来源合法性。
- 数值结果必须可复现，最好有独立验证脚本。
- 高级模型不一定比简单模型更适合数模比赛，贴题、可解释、可验证更重要。
