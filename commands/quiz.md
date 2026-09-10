---
description: Practice a topic with questions grounded in your connected coursework and saved notes.
argument-hint: "[course or topic] [optional number of questions]"
disable-model-invocation: true
---

Read and apply the study skill at `${CLAUDE_PLUGIN_ROOT}/skills/study/SKILL.md`.

Run a Roost practice session for: $ARGUMENTS

Resolve the course or topic, retrieve relevant course notes, and search and fetch selected assignments or readings when needed. If no source can be read, explain the gap; offer a general-knowledge practice session explicitly labelled as such instead of claiming it uses the student's materials.

Briefly identify the sources and any limits. Default to five questions, one at a time, unless the student requests another format. Wait for the answer before giving feedback. Explain corrections using retrieved evidence, and adapt subsequent questions to gaps in understanding. End with a short recap and suggested review topics, without claiming a score or progress was saved to Roost.
