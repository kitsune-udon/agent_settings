# Agent instruction templates

This repository maintains global defaults and a repository execution policy for Codex. Deploy them at their respective scopes rather than concatenating both templates into one instruction file. Independent review remains required for every change unit in a repository that adopts the execution policy, including small changes and documentation changes.

## Files

| Source | Deployment destination | Purpose |
| --- | --- | --- |
| [AGENTS.user.md](AGENTS.user.md) | `~/.codex/AGENTS.md` | Reusable communication, engineering, safety, and validation defaults. |
| [AGENTS.project.md](AGENTS.project.md) | `<repository>/AGENTS.md` | Repository instructions that require the execution policy. |
| [Execution policy](.agent/agent-execution-policy.md) | `<repository>/.agent/agent-execution-policy.md` | Detailed delegation, independent review, validation, acceptance, and runtime Goal procedures. |

The repository template summarizes the execution policy's entry conditions; the linked policy remains mandatory, and its detailed requirements and exceptions apply in full. The policy preserves independent review for every change unit while making selection, pending review, records, and recovery procedures explicit.

Keep agent execution instructions in `.agent/` to distinguish them from product documentation.

## Global defaults

Install `AGENTS.user.md` as `AGENTS.md` in your Codex home directory, which defaults to `~/.codex`. If `CODEX_HOME` is configured, use that directory instead. Compare and merge any existing global instructions before replacing them.

Keep personal language and communication preferences and cross-project engineering defaults here. More specific repository, directory, and task instructions can override these defaults within governing runtime instructions.

## Initial repository adoption

Adopt the execution policy in repositories where its required independent reviews are intended and supported by the runtime. This is a choice of deployment scope, not an exemption for particular changes within an adopting repository. If review later becomes unavailable, the policy's hold requirements still apply.

Before adoption, verify that the runtime and governing instructions allow you to:

- Assign a sub-agent that does not implement the change unit to its required reviews, with sufficient capacity available.
- Give that reviewer access to the relevant files, diff, acceptance criteria, and validation evidence.
- Receive its review result and address findings before the applicable implementation or acceptance gate.

Check actual tool, permission, and lifecycle restrictions rather than assuming that sub-agent support alone is sufficient. If capability is uncertain, use an authorized read-only review trial when needed. Do not adopt the policy on the assumption that self-review can replace an unavailable independent reviewer.

Copy the repository template to the repository root as `AGENTS.md` and distribute `.agent/agent-execution-policy.md` at the referenced path. Merge with existing repository instructions rather than replacing them blindly. If the policy path changes, update the link in `AGENTS.md` and verify that it resolves.

Use the repository template and execution policy from the same source commit. Record that commit in an existing setup or maintenance record so a later update can distinguish the distributed baseline from local additions. This README provides source-repository guidance and examples; it is not a required deployment artifact.

Replace the template's generic Repository context section with verified repository information as available:

- Setup requirements and the actual test, lint, type-check, and build commands.
- Relevant directory boundaries and existing architectural conventions.
- Generated files and the process used to update them.
- Domain invariants, compatibility constraints, migrations, and known failure modes that matter when making changes.

Avoid copying global defaults into each repository. Put narrower instructions in the relevant subdirectory's `AGENTS.md` when needed; preserve the adopted execution policy's review requirements.

## Updating deployed instructions

1. Identify the deployed source commit and the intended replacement commit. If provenance is unknown, compare the deployed files directly and establish a baseline before updating.
2. Compare both `AGENTS.project.md` and `.agent/agent-execution-policy.md` from that replacement commit with the deployed pair. Preserve and reconcile repository-specific additions rather than overwriting them. Update the pair together; if one file has no upstream change, verify that it still matches the chosen baseline.
3. Inspect the final diff, confirm the mandatory policy link resolves, and check plan review, result review, selected change unit rejection or deferral review, and review-unavailable hold requirements. Check that nested or override instructions do not unintentionally narrow those requirements. Updating instructions in an adopting repository is itself subject to its existing review policy.
4. Start a new session and perform the instruction discovery checks below. Compare and merge global defaults separately when updating them; repository policy updates do not require replacing global instructions.

## Task record example

Use the execution policy's minimum record requirements in an existing issue, PR, or task or review artifact. The following is a template, not evidence that any review or validation has happened:

```text
Change unit: objective and selection for planning or implementation
Acceptance criteria: required outcome and preservation requirements
Reviewed source: commit or source identifier plus relevant uncommitted diff
Plan review: reviewer, judgment, evidence reference, and finding dispositions
Validation: scope, commands or checks, execution status, results, and evidence
Result review: reviewer and judgment, or pending with missing evidence
Open findings: affected requirement, disposition, and remaining work
Partial work: retained changes and any unfinished agents, commands, or resources
Decision: pending required review, accepted, or reviewed rejection or deferral
```

Distinguish performed and passed, performed and failed, not performed, and not available. Record a stable reference to the reviewed diff or preserve it in the existing artifact when no commit identifies the full state. Keep secrets and sensitive data out of records. A pending review report identifies unmet conditions and does not finalize acceptance, rejection, or deferral; ending the turn does not complete the task or imply automatic background execution.

## Instruction discovery and verification

These source filenames are not standard automatic instruction filenames. Codex discovers global `AGENTS.override.md` or `AGENTS.md`, then project instructions along the path from the project root to the current working directory. It includes at most one instruction file per directory, checking `AGENTS.override.md`, `AGENTS.md`, then configured fallback names. Registering both source names as fallbacks does not concatenate them. An override replaces the regular file at the same scope, so ensure it preserves required policy references and requirements. See the [official instruction discovery documentation](https://learn.chatgpt.com/docs/agent-configuration/agents-md).

The linked execution policy is read because the repository template explicitly requires it; the policy document is not a second automatically discovered instruction file. Keep the mandatory reference in the active repository instructions.

After initial deployment or an update, verify the setup against actual files and runtime configuration:

- Confirm the intended Codex home, repository root, working directory, and deployed instruction files. Inspect same-scope overrides and configured fallback names that could select a different file.
- Resolve the policy link from the repository root and inspect the deployed document. Confirm it belongs to the intended template and policy pair and that nested instructions preserve the adopted review requirements.
- Start a new session in the target repository. Ask it to identify the absolute paths it actually read and summarize plan review, result review, selected change unit rejection or deferral review, and review-unavailable holds. Compare the answer with the deployed files and configuration rather than treating self-report as sufficient proof of automatic loading.
- Where the runtime provides an instruction-source display or discovery log, use it as additional evidence and reconcile discrepancies before treating adoption as verified. If loading cannot be independently confirmed, report that limitation.

Keep deployed-file checks, session self-report, available discovery evidence, and any read-only reviewer trial distinct in the setup record. Do not report an unperformed runtime check as passed.
