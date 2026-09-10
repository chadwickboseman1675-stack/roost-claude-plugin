---
description: Read a connected assignment and explain its requirements or review a saved draft.
argument-hint: "[course and assignment] [optional question]"
disable-model-invocation: true
---

Read and apply the study skill at `${CLAUDE_PLUGIN_ROOT}/skills/study/SKILL.md`.

Help with this Roost assignment: $ARGUMENTS

Resolve the class and assignment using Roost, asking the student to choose only if multiple matches remain. Fetch the selected assignment through the saved Roost school connection before explaining its contents. Retrieve saved notes when they are relevant to the request.

State what the readable source asks, list its explicit deliverables or constraints, and explain the requested part with citations. If the student requested draft feedback and a draft is available in retrieved notes or the conversation, compare it with the verified requirements. Separate confirmed requirements from suggestions. Report source gaps or ambiguous extraction instead of reconstructing unseen instructions. Follow Roost's returned recovery guidance when reading fails.
