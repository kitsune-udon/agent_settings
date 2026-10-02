# Repository instructions

These instructions apply throughout this repository, subject to governing runtime instructions and the user's authorization. They supplement global defaults without granting permission for external actions.

## Execution policy

- MUST read and follow [the execution policy](.agent/agent-execution-policy.md) before starting work. Resolve this path relative to this repository's root. This document MUST be distributed with these instructions.
- The policy applies to every change unit in this repository, including small changes and documentation changes. A change unit is a coherent set of changes sharing an objective and validation approach, evaluated and decided on together.
- Nested instructions may supplement local procedures and conventions, but MUST NOT narrow the adopted independent review requirements without an explicit user instruction to change them, subject to governing runtime instructions.
- MUST obtain plan review and result review from a sub-agent that does not implement the change unit. Follow the policy's prerequisites, bounded speculation conditions, validation requirements, and acceptance criteria; task decomposition adds no recursive review layer.
- Rejection or deferral of a candidate selected as a change unit for planning or implementation MUST receive sub-agent review under the policy. Initial screening and mandatory user or runtime stops retain the policy's distinct rules.
- If required review is unavailable, follow the policy's hold requirements and report the limitation as `pending required review`. This is an unresolved work state, not acceptance or a finalized rejection or deferral. MUST NOT substitute self-review for required independent review.
- Tasks and local subgoals do not themselves require a runtime Goal. Create and manage runtime Goals only as authorized by governing instructions and the policy.

## Repository context

Inspect relevant implementation, tests, interfaces, and existing documentation before changing code. Use repository-defined setup, validation commands, and conventions. If required information is unavailable, report the material gap rather than inventing commands or constraints.
