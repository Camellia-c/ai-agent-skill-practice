# Skill Case 05：Codex Excel 续费风险分析

## 1. 使用的 Skill

`.agents/skills/codex-excel-renewal-analysis/SKILL.md`

## 2. 案例目标

设计一个具有一定复杂度的 Codex Skill，用于读取学生学习数据 Excel，计算续费风险分，划分风险等级，并输出新的 Excel 结果表和 Markdown 分析报告。

## 3. 业务场景

班主任或运营人员需要从班级数据中识别高风险学生，优先跟进可能不续费的家庭。

原始 Excel 中包含：

- 到课率；
- 作业完成率；
- 课中互动分；
- 家长回复率；
- 续费意向；
- 投诉次数；
- 距离上次沟通天数。

这些字段可以帮助判断学生和家长的参与度、满意度和续费风险。

## 4. 输入字段

| 字段 | 含义 |
|---|---|
| student_name | 学生姓名 |
| attendance_rate | 到课率 |
| homework_rate | 作业完成率 |
| interaction_score | 课中互动分 |
| parent_reply_rate | 家长回复率 |
| renewal_intent | 续费意向 |
| complaint_count | 投诉次数 |
| last_contact_days | 距离上次沟通天数 |

## 5. 执行逻辑

Skill 会调用 Python 脚本执行以下步骤：

1. 读取 Excel；
2. 校验必填字段；
3. 清洗数值；
4. 按权重计算续费风险分；
5. 根据分数划分 High / Medium / Low 风险等级；
6. 生成跟进建议；
7. 导出新的 Excel；
8. 生成 Markdown 分析报告。

## 6. 风险分计算逻辑

风险分越高，续费风险越高。

主要影响因素包括：

- 到课率越低，风险越高；
- 作业完成率越低，风险越高；
- 互动分越低，风险越高；
- 家长回复率越低，风险越高；
- 续费意向越低，风险越高；
- 投诉次数越多，风险越高；
- 距离上次沟通时间越久，风险越高。

## 7. 输出结果

该 Skill 预期生成两个文件：

| 文件 | 作用 |
|---|---|
| renewal_risk_result.xlsx | 学生续费风险计算结果 |
| renewal_risk_report.md | 风险概览和高风险学生摘要 |

## 8. 示例命令

```bash
python .agents/skills/codex-excel-renewal-analysis/scripts/calculate_renewal_risk.py sample_student_data.xlsx renewal_risk_result.xlsx renewal_risk_report.md
9. 项目价值

这个案例体现了 Skill 不只是 Prompt 模板，也可以把：

业务规则；
标准流程；
Excel 数据处理；
Python 脚本；
输出报告；

组合成一个可复用的自动化工作流。

对于 AI 评测岗位来说，这个案例可以体现：

能把业务任务抽象成可执行流程；
能设计输入、处理、输出标准；
能识别数据质量和字段校验问题；
能将自动化结果转化为业务可理解的报告；
能理解 Agent / Codex Skill 中“说明 + 脚本 + 案例”的组合方式。
10. 质量检查点
是否有清晰业务场景；
是否定义了输入字段；
是否有明确计算逻辑；
是否能输出 Excel 和 Markdown 报告；
是否有字段缺失校验；
是否能说明该 Skill 的业务价值；
是否适合作为作品集展示。
