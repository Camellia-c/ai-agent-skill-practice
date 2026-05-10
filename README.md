# AI Agent Prompt Cases

这是一个围绕 Prompt 构建、Prompt 评测、Prompt 优化与 AI Agent 工具使用设计的练习项目。

本项目的重点不是收集“万能提示词”，而是练习如何把用户的普通需求，转化成更标准、清晰、可执行、可复用、可评估的 Prompt，并通过案例验证 Prompt 的效果。

项目覆盖以下能力：

- 用户需求分析
- Prompt 结构化设计
- Prompt 质量评分
- Prompt 类型分类
- 评分方式选择
- 模型输出评测
- Prompt 对比分析
- Prompt 优化改进
- Agent 工具使用判断
- Agent Workflow 设计

---

## 1. 项目目标

本项目主要训练以下能力：

1. 理解用户原始需求，识别需求中缺失的信息。
2. 按照角色、目标、背景、输入、步骤、输出格式、质量标准、边界条件等要素设计 Prompt。
3. 建立 Prompt 评分标准，从多个维度判断 Prompt 好坏。
4. 理解不同评分方式，包括人工评分、大模型评分、规则评分和混合评分。
5. 根据任务类型选择合适的评分方式。
6. 区分不同类型 Prompt，例如学习型、总结型、评测型、对比型、优化型、Agent Prompt 等。
7. 对比两个 Prompt 的质量，说明谁更好以及为什么。
8. 将低质量 Prompt 优化成更清晰、可执行、可复用的 Prompt。
9. 设计 Agent 工具使用规则，判断用户问题是否需要调用工具。
10. 设计完整 Agent Workflow Prompt，覆盖任务理解、计划、工具判断、执行、观察、状态更新和终止判断。

---

## 2. 项目结构

项目目录如下：

    ai-agent-prompt-cases/
    ├── README.md
    ├── notes/
    │   ├── prompt_design_principles.md
    │   └── prompt_scoring_rubric.md
    ├── prompts/
    │   ├── 01_learning_assistant_prompt.md
    │   ├── 02_summary_prompt.md
    │   ├── 03_eval_prompt.md
    │   ├── 04_tool_use_agent_prompt.md
    │   └── 05_agent_workflow_prompt.md
    └── cases/
        ├── case_01_tool_use_learning.md
        ├── case_02_agent_loop_summary.md
        ├── case_03_model_answer_eval.md
        ├── case_04_agent_tool_rule.md
        ├── case_05_prompt_comparison.md
        ├── case_06_prompt_optimization.md
        └── case_07_agent_workflow.md

---

## 3. Notes：方法论文件

### 3.1 prompt_design_principles.md

记录 Prompt 构建的基本原则。

核心内容包括：

- 明确角色
- 明确任务目标
- 给出背景信息
- 规定执行步骤
- 规定输出格式
- 给出质量标准
- 设置信息不足时的处理方式

这个文件解决的问题是：

> 一个 Prompt 应该包含哪些基本要素？

---

### 3.2 prompt_scoring_rubric.md

记录 Prompt 评分标准与评分方式分类。

核心内容包括：

1. Prompt 评分维度  
   例如目标清晰度、角色设定、背景完整性、输入明确性、执行步骤、输出格式、质量标准、边界控制、可复用性、可评估性。

2. 5 分制评分等级  
   用于判断 Prompt 从 1 分到 5 分分别代表什么质量水平。

3. 评分方式分类  
   包括人工评分、大模型评分、规则/程序评分、混合评分。

4. 评分方式选择  
   根据任务是否客观、是否需要语义理解、是否需要大规模自动化处理，选择不同评分方式。

5. Prompt 类型分类  
   包括学习型 Prompt、总结型 Prompt、评测型 Prompt、对比型 Prompt、优化型 Prompt、Agent Prompt、安全/Guardrails 型 Prompt、格式控制型 Prompt。

这个文件解决的问题是：

> 怎么判断一个 Prompt 好不好？谁来评？用什么方式评？不同类型 Prompt 应该重点看什么？

---

## 4. Prompts：可复用 Prompt 模板

### 4.1 01_learning_assistant_prompt.md

学习助手 Prompt。

用途：

- 学习 AI 概念
- 生成结构化学习笔记
- 输出面试表达版本

适合主题：

- RAG
- Tool Use / Function Calling
- Agent Loop
- Memory
- Guardrails
- Evaluation

训练能力：

> 把“我想学习某个概念”转化成结构化学习任务。

---

### 4.2 02_summary_prompt.md

资料总结 Prompt。

用途：

- 整理文章资料
- 整理技术笔记
- 整理论文或文档内容
- 转成学习笔记和面试表达

训练能力：

> 把零散资料整理成结构化内容，并避免照抄和编造。

---

### 4.3 03_eval_prompt.md

模型回答评测 Prompt。

用途：

- 评估模型回答是否相关
- 判断回答是否准确
- 判断是否完整
- 判断是否清晰
- 判断是否存在误导或编造
- 给出修改建议和更好的回答版本

训练能力：

> 根据明确维度评估模型输出质量。

---

### 4.4 04_tool_use_agent_prompt.md

Agent 工具使用规则 Prompt。

用途：

- 判断用户问题是否需要调用工具
- 判断应该使用什么工具
- 说明工具使用顺序
- 输出执行方案

覆盖工具类型：

- 搜索工具
- 文件读取工具
- 计算工具
- 代码执行工具
- API / 数据库工具
- 邮件 / 日历工具

训练能力：

> 让 Agent 判断什么时候直接回答，什么时候必须调用外部工具。

---

### 4.5 05_agent_workflow_prompt.md

完整 Agent Workflow Prompt。

用途：

- 指导 Agent 执行多步骤任务
- 覆盖任务理解、计划制定、工具判断、工具调用、观察结果、状态更新、终止判断和最终输出

训练能力：

> 设计一个更完整的 Agent 执行流程，而不是只做单点工具判断。

---

## 5. Cases：实际案例

### Case 01：Tool Use / Function Calling 学习案例

文件：

cases/case_01_tool_use_learning.md

内容：

使用学习助手 Prompt 学习 Tool Use / Function Calling。

案例流程：

原始需求 → 问题分析 → 优化后的 Prompt → 模型输出 → 复盘

训练重点：

> 把“我想学习 Tool Use”转化成适合 AI 评测岗位学习者的结构化学习任务。

---

### Case 02：Agent Loop 资料总结案例

文件：

cases/case_02_agent_loop_summary.md

内容：

使用资料总结 Prompt 整理 Agent Loop 学习笔记。

训练重点：

> 把一段 Agent Loop 资料整理成核心结论、关键概念、流程机制、和 AI Agent / AI 评测的关系、面试问法和口头表达版本。

---

### Case 03：模型回答评测案例

文件：

cases/case_03_model_answer_eval.md

内容：

评估一个错误模型回答。

用户问题：

AI Agent 为什么需要工具调用？

模型回答：

因为 Agent 很聪明，所以它可以直接完成所有任务。工具调用就是让它变得更智能。

训练重点：

> 从相关性、准确性、完整性、清晰度、安全性等维度评估模型回答质量，并给出更好的回答版本。

---

### Case 04：Agent 工具使用判断案例

文件：

cases/case_04_agent_tool_rule.md

内容：

使用 Agent 工具使用规则 Prompt 判断不同问题是否需要工具。

测试案例包括：

1. 稳定概念解释类：什么是 RAG？
2. 最新信息查询类：OpenAI API 现在最新价格是多少？
3. 文件分析类：帮我总结上传的 AI Agent 论文。

训练重点：

> 判断不同任务是否需要搜索、文件读取或直接回答。

---

### Case 05：Prompt 对比评测案例

文件：

cases/case_05_prompt_comparison.md

内容：

对比两个 Prompt。

Prompt A：

帮我解释一下 RAG。

Prompt B：

你是一个 AI 学习助手，面向 AI 评测岗位学习者解释 RAG，并规定输出结构和质量要求。

训练重点：

> 不靠感觉判断哪个 Prompt 更好，而是从目标清晰度、角色设定、背景完整性、输出格式、质量标准、边界控制、可复用性等维度进行对比。

---

### Case 06：Prompt 优化改进案例

文件：

cases/case_06_prompt_optimization.md

内容：

将低质量 Prompt：

帮我总结这篇文章。

优化成一个面向 AI 评测岗位学习者的资料总结 Prompt。

训练重点：

> 先分析原 Prompt 缺什么，再按评分标准补齐角色、目标、背景、步骤、格式、质量标准和边界条件。

---

### Case 07：Agent Workflow 综合案例

文件：

cases/case_07_agent_workflow.md

内容：

使用完整 Agent Workflow Prompt 处理综合任务。

用户问题：

帮我判断：如果我要写一篇关于 AI Agent 工具调用的学习笔记，是否需要搜索资料？应该怎么执行？

训练重点：

> 让 Agent 完成任务理解、信息判断、执行计划、工具判断、模拟执行、状态更新、终止判断和最终输出。

---

## 6. Prompt 构建方法总结

一个较好的 Prompt 通常需要包含：

| 要素 | 说明 |
|---|---|
| 角色 | 告诉模型它现在是谁 |
| 任务目标 | 明确要完成什么 |
| 背景信息 | 说明面向谁、使用场景是什么 |
| 输入内容 | 提供模型需要处理的材料 |
| 执行步骤 | 规定先做什么、后做什么 |
| 输出格式 | 控制回答结构和呈现方式 |
| 质量标准 | 说明什么样的回答算好 |
| 边界条件 | 说明信息不足时不能编造，需要指出缺失信息 |
| 可复用性 | 让 Prompt 可以替换变量后重复使用 |
| 可评估性 | 让输出结果可以被检查和优化 |

---

## 7. Prompt 评分方式总结

本项目将评分方式分为四类：

| 评分方式 | 适合场景 | 特点 |
|---|---|---|
| 人工评分 | 主观性强、业务语境复杂、高风险内容 | 灵活，但成本高 |
| 大模型评分 | 批量评估、初筛、Prompt 对比 | 快速，但可能不稳定 |
| 规则/程序评分 | 格式、字段、关键词、标准答案 | 稳定，但不擅长开放语义 |
| 混合评分 | RAG、Agent、客服质检、上线验收 | 兼顾效率和质量 |

选择原则：

- 有标准答案或明确格式：优先规则评分。
- 需要判断语义质量：可以使用大模型评分。
- 主观性强或风险高：需要人工复核。
- 复杂业务、大规模评测：使用混合评分。

---

## 8. Agent Prompt 设计总结

Agent Prompt 不只是普通 Prompt 加上“你是一个 Agent”。

一个完整的 Agent Prompt 通常需要包含：

1. Agent 角色
2. 任务目标
3. 可用工具
4. 工具使用规则
5. 执行流程
6. 工具结果观察方式
7. 状态更新方式
8. 继续 / 终止判断
9. 错误处理规则
10. 最终输出格式

本项目中的 Agent Prompt 覆盖了两个层级：

| 文件 | 重点 |
|---|---|
| 04_tool_use_agent_prompt.md | 判断是否需要工具，以及使用什么工具 |
| 05_agent_workflow_prompt.md | 设计完整 Agent 任务执行流程 |

---

## 9. 项目复盘

通过这个项目，我理解了 Prompt 不只是简单提问，而是把用户的模糊需求转化为模型可以稳定执行的任务说明。

在普通问答场景中，Prompt 需要明确任务目标、输出结构和质量要求。

在 AI 评测场景中，还需要建立评分维度、评分方式和优化流程。

在 AI Agent 场景中，Prompt 还需要进一步规定工具使用规则、执行顺序、状态更新、终止条件和错误处理方式。

这个项目目前完成了从 Prompt 构建到 Agent Workflow 的基础闭环：

Prompt 构建原则  
↓  
Prompt 评分标准  
↓  
Prompt 类型分类  
↓  
Prompt 模板设计  
↓  
模型输出评测  
↓  
Prompt 对比  
↓  
Prompt 优化  
↓  
Agent 工具判断  
↓  
Agent Workflow 设计

---

## 10. 后续可扩展方向

后续可以继续扩展：

1. 增加真实模型输出对比，例如同一问题下 Prompt A 和 Prompt B 的实际回答差异。
2. 增加 RAG 问答评测案例。
3. 增加 Agent 工具调用失败案例。
4. 增加 Agent 执行轨迹日志分析。
5. 增加规则评分脚本，例如检查 JSON 格式、字段完整性和关键词覆盖。
6. 增加多轮对话 Prompt 评测案例。
7. 增加 Guardrails / Safety Prompt 案例。
8. 将案例整理成作品集说明，用于 AI 评测岗位面试表达。

---

# AI Agent Skill Practice

## 项目简介

本项目用于练习 AI Agent / Codex Skill 的设计与实战。

项目目标不是单纯写 Prompt，而是把高频 AI 评测任务沉淀成可复用的 Skill，包括：

- AI 学习资料整理；
- Prompt 质量评测；
- AI 回答质量评测；
- Agent 任务执行流程；
- Codex Excel 自动计算场景。

通过这些案例，可以理解 Prompt 和 Skill 的区别：

- Prompt 更偏一次性指令；
- Skill 更像一套可复用的任务能力包；
- Skill 需要包含适用场景、输入格式、执行流程、输出结构和质量检查标准。

## 项目结构

```text
ai-agent-prompt-cases/
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
Skill 说明
Skill	文件	作用
AI 学习资料整理 Skill	skills/ai_learning_note_skill.md	将 AI 概念资料整理成学习笔记和面试表达
Prompt 质量评测 Skill	skills/prompt_evaluation_skill.md	对比和评估 Prompt 的质量
AI 回答质量评测 Skill	skills/ai_answer_evaluation_skill.md	评估模型回答的相关性、准确性、完整性、清晰度、安全性和可操作性
Agent 任务执行 Skill	skills/agent_task_execution_skill.md	模拟 Agent 的任务理解、工具判断、执行计划和状态更新
Codex Excel 续费风险分析 Skill	.agents/skills/codex-excel-renewal-analysis/SKILL.md	调用 Python 脚本处理 Excel，计算学生续费风险并生成报告
案例说明
Case	对应 Skill	场景
Case 01	AI 学习资料整理	将 RAG 整理成 AI 评测岗位学习笔记
Case 02	Prompt 质量评测	对比两个 RAG 学习 Prompt 的优劣
Case 03	AI 回答质量评测	评估一个关于工具调用的模型回答
Case 04	Agent 任务执行	判断 OpenAI API 价格查询任务是否需要工具
Case 05	Codex Excel 续费风险分析	根据学生数据 Excel 计算续费风险分并生成结果表
Codex Excel Skill 示例

Codex Excel 续费风险分析 Skill 用于模拟一个真实业务场景：

班主任或运营人员需要根据学生学习数据，识别高风险学生，并安排优先跟进。

输入 Excel 字段包括：

student_name
attendance_rate
homework_rate
interaction_score
parent_reply_rate
renewal_intent
complaint_count
last_contact_days

脚本会输出：

renewal_risk_result.xlsx
renewal_risk_report.md

运行方式示例：

python .agents/skills/codex-excel-renewal-analysis/scripts/calculate_renewal_risk.py sample_student_data.xlsx renewal_risk_result.xlsx renewal_risk_report.md
我对 Skill 的理解

Skill 不是简单的 Prompt 模板，而是把一类重复任务沉淀成可复用的执行规范。

一个完整 Skill 通常包括：

适用场景；
用户目标；
输入格式；
执行流程；
标准输出结构；
输出要求；
示例输入输出；
质量检查清单。

其中：

标准输出结构负责规定“输出长什么样”；
质量检查清单负责判断“输出质量合不合格”。

这能让任务执行从“凭感觉生成”变成“按流程、按标准、可复用、可检查”。

和 AI 评测岗位的关系

这个项目对应 AI 评测岗位中的几个核心能力：

能拆解用户需求；
能设计评测维度；
能判断模型回答质量；
能识别幻觉、遗漏、跑题和不安全输出；
能把任务流程标准化；
能设计可复用的评测模板；
能结合脚本完成数据处理和结果输出。
面试表达

我做过一个 AI Agent Skill 实战项目，主要是把高频 AI 评测任务沉淀成可复用的 Skill。

项目里包括 AI 学习资料整理、Prompt 质量评测、AI 回答质量评测、Agent 任务执行流程，以及一个 Codex Excel 自动计算案例。

其中 Codex Excel 案例会读取学生学习数据 Excel，计算续费风险分，划分高、中、低风险等级，并输出新的 Excel 结果表和 Markdown 分析报告。

这个项目让我理解到，Prompt 更偏一次性指令，而 Skill 更像一套可复用的任务能力包。对于 AI 评测岗位来说，这种结构化能力很重要，因为评测工作本身就需要稳定标准、可复现流程和清晰的质量判断维度。
