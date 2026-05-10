# Sample Student Data Schema

This file describes the expected Excel input format for the Codex Excel Renewal Analysis Skill.

## Required columns

| Column | Type | Description | Example |
|---|---|---|---|
| student_name | text | Student name | 小明 |
| attendance_rate | number | Attendance rate from 0 to 100 | 85 |
| homework_rate | number | Homework completion rate from 0 to 100 | 76 |
| interaction_score | number | In-class interaction score from 0 to 100 | 90 |
| parent_reply_rate | number | Parent reply rate from 0 to 100 | 60 |
| renewal_intent | text | Renewal intent: high / medium / low / unknown | medium |
| complaint_count | number | Number of complaints | 1 |
| last_contact_days | number | Days since last contact | 8 |

## Output columns

The output Excel will include all original columns plus:

| Column | Description |
|---|---|
| risk_score | Calculated renewal risk score |
| risk_level | High / Medium / Low |
| follow_up_action | Suggested follow-up action |

## Notes

- All percentage fields should use 0-100.
- Invalid or missing numeric values are treated as 0 by default.
- Missing required columns will stop execution.
- The result is for prioritization, not a final business conclusion.
