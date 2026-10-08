# Agent instructions

Self-contained, equivalent templates: [English](AGENTS.project.md) / [Japanese](AGENTS.project.ja.md). Choose one. This README is setup guidance and need not be deployed.

## Installation

- Install the chosen template as `<repository>/AGENTS.md`; the source filenames are not standard automatic instruction filenames. Use global `AGENTS.md` in the Codex home directory only when the entire policy is intended across repositories. Avoid duplicating both scopes; repository instructions can supply local commands and conventions.
- Merge existing instructions, preserving local additions and unrelated work. Confirm applicable files fit the effective loading limit and required independent reviews are permitted and available. Review conditions, gates, and records are defined in the template.
- Editing source files does not update installed instructions. Deployment outside this repository is a separate action.

See the [official AGENTS.md documentation](https://learn.chatgpt.com/docs/agent-configuration/agents-md) for discovery and configuration. Account for overrides and configured fallback names; a same-directory override may replace the installed file.

## Migration and updates

1. Compare the installed version with the chosen source; preserve local additions and a rollback reference. Former `AGENTS.user.md` and `.agent/agent-execution-policy.md`, including Japanese equivalents, are consolidated; no separate policy is needed.
2. Update the intended `AGENTS.md` and obsolete policy-reading directives. Remove legacy files only when no retained instruction or consumer needs them; preserve unrelated `.agent/` files.
3. Keep source language versions equivalent. Inspect the diff and affected review, independence, acceptance, and hold rules. Review changes under the template's applicability and gate rules.
4. Reuse valid loading and discovery evidence; repeat only checks affected by configuration, scope, capacity, or missing evidence. Routine content updates need no full setup rehearsal.

For initial deployment or scope migration, check target paths, applicable files and configuration, and loading capacity. Use a new session for runtime discovery checks and available source displays or logs to corroborate its report; self-report alone does not prove complete loading. Report unavailable checks and uncertainty. Source inspection does not verify runtime deployment.
