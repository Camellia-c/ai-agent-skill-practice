---
name: codex-excel-renewal-analysis
description: Analyze a student renewal-risk Excel file, calculate renewal risk scores, classify students into high/medium/low risk groups, and generate an output Excel file plus a Markdown summary.
---

# Codex Excel 续费风险分析 Skill

## 1. When to use this skill

Use this skill when the user provides or describes an Excel file containing student learning and parent communication data, and wants to:

- calculate renewal risk scores;
- classify students into high, medium, and low risk groups;
- generate follow-up priorities;
- export a new Excel result file;
- create a short analysis report.

Typical trigger phrases:

- "帮我分析这份学生续费风险 Excel"
- "根据到课率、作业完成率、互动分计算风险"
- "把学生按高/中/低风险分类"
- "生成一份 Excel 分析结果"
- "设计一个能调用 Excel 计算的 Codex Skill"

## 2. Expected input

The input Excel should include these columns:

| Column | Meaning |
|---|---|
| student_name | Student name |
| attendance_rate | Attendance rate, 0-100 |
| homework_rate | Homework completion rate, 0-100 |
| interaction_score | In-class interaction score, 0-100 |
| parent_reply_rate | Parent reply rate, 0-100 |
| renewal_intent | Renewal intent: high / medium / low / unknown |
| complaint_count | Number of complaints |
| last_contact_days | Days since last contact |

If columns are missing, stop and report which columns are missing.

## 3. Risk scoring logic

Calculate `risk_score` from 0 to 100. Higher score means higher renewal risk.

Default scoring logic:

1. Low attendance increases risk.
2. Low homework completion increases risk.
3. Low interaction score increases risk.
4. Low parent reply rate increases risk.
5. Low renewal intent increases risk.
6. More complaints increase risk.
7. Longer time since last contact increases risk.

Formula:

```text
risk_score =
  (100 - attendance_rate) * 0.20
+ (100 - homework_rate) * 0.20
+ (100 - interaction_score) * 0.15
+ (100 - parent_reply_rate) * 0.15
+ renewal_intent_risk * 0.15
+ complaint_risk * 0.10
+ contact_risk * 0.05

Mapping rules:

renewal_intent:
  high    -> 10
  medium  -> 40
  low     -> 80
  unknown -> 60

complaint_risk:
  complaint_count >= 3 -> 100
  complaint_count == 2 -> 70
  complaint_count == 1 -> 40
  complaint_count == 0 -> 0

contact_risk:
  last_contact_days >= 14 -> 100
  last_contact_days >= 7  -> 60
  last_contact_days < 7   -> 20
4. Risk level rules

Classify students by risk_score:

Risk score	Risk level
>= 70	High
>= 40 and < 70	Medium
< 40	Low
5. Follow-up priority rules

Generate a follow_up_action field:

High risk: call parent within 24 hours and provide a personalized learning review.
Medium risk: send private message within 48 hours and reinforce course value.
Low risk: maintain regular follow-up and encourage continued learning.
6. Execution steps
Validate the Excel file and required columns.
Clean numeric fields and handle invalid values.
Calculate risk_score.
Classify risk_level.
Generate follow_up_action.
Export a new Excel file.
Generate a Markdown summary report.
Clearly report output file paths.
7. Script

Use:

python .agents/skills/codex-excel-renewal-analysis/scripts/calculate_renewal_risk.py input.xlsx output.xlsx report.md

Example:

python .agents/skills/codex-excel-renewal-analysis/scripts/calculate_renewal_risk.py sample_student_data.xlsx renewal_risk_result.xlsx renewal_risk_report.md
8. Quality checklist

Before finishing, check:

Required columns are validated.
Risk score formula is applied consistently.
Risk levels are correctly classified.
High-risk students are clearly visible.
Output Excel is generated.
Markdown summary is generated.
No missing or invalid data is silently ignored.
The final response explains what files were created.
