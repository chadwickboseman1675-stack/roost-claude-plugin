---
description: Find upcoming saved assignments and turn them into a practical study plan.
argument-hint: "[date range] [optional course]"
disable-model-invocation: true
---

Read and apply the study skill at `${CLAUDE_PLUGIN_ROOT}/skills/study/SKILL.md`.

Find the student's upcoming work in Roost for: $ARGUMENTS

Use the conversation's date and timezone context. If no period is specified, use the next seven calendar days and state the date range. Ask for timezone clarification only if it is needed to choose the range correctly. Search unfinished saved work, follow all result pages, and preserve the requested course and date filters. If the user asks for a general plan, also identify unfinished undated items separately rather than assigning them invented due dates.

Show the assignment, course, verified deadline, status, and returned link. Fetch only the assignments whose contents are needed to recommend concrete steps. Give a short prioritized plan based on known deadlines and retrieved requirements, marking time estimates and assumptions. Explain missing or partial coverage. State that the plan is a proposal in this conversation and has not been saved to Roost.
