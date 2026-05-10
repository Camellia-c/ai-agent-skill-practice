# AI Agent Skill Practice

## 项目简介

这是一个 AI Agent Skill 实战项目。

项目目标不是单纯练习 Prompt，而是把高频 AI 学习、AI 评测和 Agent 任务执行场景，沉淀成可复用的 Skill。

在这个项目中，Skill 被理解为一种可复用的任务能力包。它通常包含：

- 适用场景；
- 用户目标；
- 输入格式；
- 执行流程；
- 标准输出结构；
- 输出要求；
- 示例输入输出；
- 质量检查清单。

通过这些结构，模型可以在处理同类任务时更加稳定、清晰、可复用，也更方便进行评测和优化。

---

## 项目结构

```text
ai-agent-skill-practice/
├── README.md
├── skills/
│   ├── ai_learning_note_skill.md
│   ├── prompt_evaluation_skill.md
│   ├── ai_answer_evaluation_skill.md
│   └── agent_task_execution_skill.md
│
├── cases/
│   ├── skill_case_01_ai_learning_note.md
│   ├── skill_case_02_prompt_evaluation.md
│   ├── skill_case_03_answer_evaluation.md
│   ├── skill_case_04_agent_task_execution.md
│   └── skill_case_05_codex_excel_renewal_analysis.md
│
└── .agents/
    └── skills/
        └── codex-excel-renewal-analysis/
            ├── SKILL.md
            ├── scripts/
            │   └── calculate_renewal_risk.py
            └── references/
                └── sample_student_data_schema.md
Skill 列表
Skill	文件	作用
AI 学习资料整理 Skill	skills/ai_learning_note_skill.md	将 AI / 大模型相关资料整理成学习笔记和面试表达
Prompt 质量评测 Skill	skills/prompt_evaluation_skill.md	对比和评估 Prompt 的质量，判断哪个更适合用户需求
AI 回答质量评测 Skill	skills/ai_answer_evaluation_skill.md	从相关性、准确性、完整性、清晰度、安全性、可操作性等维度评估模型回答
Agent 任务执行 Skill	skills/agent_task_execution_skill.md	模拟 Agent 的任务理解、工具判断、执行计划、状态更新和终止判断
Codex Excel 续费风险分析 Skill	.agents/skills/codex-excel-renewal-analysis/SKILL.md	调用 Python 脚本处理 Excel，计算学生续费风险并生成分析报告
Case 列表
Case	对应 Skill	场景
Case 01	AI 学习资料整理 Skill	将 RAG 整理成适合 AI 评测岗位学习者使用的学习笔记
Case 02	Prompt 质量评测 Skill	对比两个 RAG 学习 Prompt 的优劣
Case 03	AI 回答质量评测 Skill	评估一个关于 Agent 工具调用的模型回答
Case 04	Agent 任务执行 Skill	判断“查询 OpenAI API 当前价格”是否需要工具
Case 05	Codex Excel 续费风险分析 Skill	根据学生学习数据 Excel 计算续费风险分，并生成结果表和 Markdown 报告
核心理解：Prompt 和 Skill 的区别

Prompt 更偏一次性指令。

例如：

帮我解释一下 RAG。

Skill 更像一套可复用的任务能力包。

例如：

当用户提供 AI 学习资料时，按照固定流程整理成：
核心结论、关键概念、流程机制、岗位关联、常见风险、面试问法和 1 分钟表达。

因此，Skill 的重点不是只解决一次问题，而是让同一类任务可以被稳定复用。

标准输出结构和质量检查清单

在 Skill 设计中，两个模块很重要：

1. 标准输出结构

标准输出结构负责规定：

最终结果应该包含哪些模块。

它可以让同类任务每次都有稳定、清晰、可对比的输出格式，减少模型自由发挥导致的跑偏。

2. 质量检查清单

质量检查清单负责检查：

这些模块的内容是否真的合格。

标准输出结构只能保证“该有的模块都有”，但不能保证内容写得好。质量检查清单用于检查输出是否真实、完整、具体，是否避免编造，是否真正满足用户目标。

一句话总结：

标准输出结构管“输出长什么样”。
质量检查清单管“输出质量合不合格”。
Codex Excel 续费风险分析 Skill

本项目中包含一个更复杂的 Codex Skill 案例：

.agents/skills/codex-excel-renewal-analysis/

这个 Skill 用于模拟一个真实业务场景：

班主任或运营人员需要根据学生学习数据，识别高续费风险学生，并安排优先跟进。

输入字段

输入 Excel 需要包含：

字段	含义
student_name	学生姓名
attendance_rate	到课率
homework_rate	作业完成率
interaction_score	课中互动分
parent_reply_rate	家长回复率
renewal_intent	续费意向
complaint_count	投诉次数
last_contact_days	距离上次沟通天数
执行流程

该 Skill 会调用 Python 脚本完成：

读取 Excel；
校验必填字段；
清洗数值；
计算续费风险分；
划分 High / Medium / Low 风险等级；
生成跟进建议；
导出新的 Excel 结果表；
生成 Markdown 分析报告。
脚本路径
.agents/skills/codex-excel-renewal-analysis/scripts/calculate_renewal_risk.py
示例命令
python .agents/skills/codex-excel-renewal-analysis/scripts/calculate_renewal_risk.py sample_student_data.xlsx renewal_risk_result.xlsx renewal_risk_report.md
预期输出
文件	作用
renewal_risk_result.xlsx	包含风险分、风险等级和跟进建议的 Excel 结果表
renewal_risk_report.md	风险概览和高风险学生摘要
和 AI 评测岗位的关系

这个项目对应 AI 评测岗位中的多个核心能力：

拆解用户需求；
设计可复用任务流程；
设计评测维度；
判断模型回答质量；
识别跑题、遗漏、幻觉和误导；
设计标准输出结构；
设计质量检查清单；
将业务任务转化为可执行流程；
使用脚本处理结构化数据；
将自动化结果转化为业务可理解的报告。
项目收获

通过这个项目，我理解到：

Skill 不是简单的 Prompt 模板；
Skill 是一类重复任务的执行规范；
好的 Skill 需要清楚定义适用场景、输入、流程、输出和质量标准；
AI 评测不只是判断“好不好”，而是定位问题、解释原因、给出优化方向；
Agent 任务执行不是直接回答，而是理解任务、判断信息、判断工具、执行步骤、观察结果、更新状态并判断是否结束。
面试表达

我做过一个 AI Agent Skill 实战项目，主要是把高频 AI 评测任务沉淀成可复用的 Skill。

项目里包括 AI 学习资料整理、Prompt 质量评测、AI 回答质量评测、Agent 任务执行流程，以及一个 Codex Excel 自动计算案例。

前几个 Skill 偏评测流程标准化，后面的 Codex Excel 案例偏自动化执行。它会读取学生学习数据 Excel，校验字段，计算续费风险分，划分高、中、低风险等级，并输出新的 Excel 结果表和 Markdown 分析报告。

这个项目让我理解到，Prompt 更偏一次性指令，而 Skill 更像可复用的任务能力包。对于 AI 评测岗位来说，这种结构化能力很重要，因为评测工作本身就需要稳定标准、可复现流程和清晰的质量判断维度。

后续优化方向

后续可以继续优化：

增加更多 Skill 案例；
为 Codex Excel Skill 增加样例 Excel 文件；
增加自动化测试脚本；
增加中英文双语说明；
将 Skill 与真实 Tool Calling 项目结合，形成 Agent 工作流。
