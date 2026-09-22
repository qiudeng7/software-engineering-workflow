---
name: general-collaboration-skills
description: Establish or improve a repository contribution system for human and AI collaborators. Use when defining contribution rules, repository knowledge ownership, issue and pull-request templates, ADR policy, resumable handoffs, or evidence-based delivery. Do not trigger for ordinary feature implementation that merely follows an existing workflow.
---

# General Collaboration Skills

Build the smallest repository-native collaboration system that lets a contributor with no prior chat history discover the task, constraints, current state, and proof of completion.

## Preserve scope and authority

First determine whether the user asked for an audit, a proposal, or implementation.

- Keep audits and proposals read-only.
- Before editing, inspect repository instructions, existing documentation, templates, Git state, and automation. Preserve useful conventions rather than replacing them with generic templates.
- Do not create issues, comments, branches, commits, pull requests, rulesets, or other remote state unless the request authorizes that action.
- Do not silently turn a contribution-policy task into product-code refactoring.

## Establish one source for each kind of truth

Use this ownership model unless the repository already has an equally clear one:

| Question | Primary record |
|---|---|
| What is the project and how is it used? | `README.md` |
| How is it developed, tested, and submitted? | `CONTRIBUTING.md` |
| Where is code and what boundaries matter? | Architecture or module documentation |
| Why was a durable design choice made? | ADR or accepted design proposal |
| What should this task deliver and where is it now? | Issue and its handoff comments |
| What changed and what proves it? | Pull request, commits, and CI |
| What does this revision actually do? | Code, configuration, and tests |

Link to the primary record instead of maintaining parallel summaries. Code describes current behavior; accepted requirements and decisions describe intended behavior. When they conflict, expose and resolve the discrepancy rather than rewriting the requirement to match a defect.

For detailed artifact boundaries and scaling rules, read [references/contribution-model.md](references/contribution-model.md).

## Design the minimum viable workflow

Prefer this baseline, adapting names and locations to the repository:

1. A useful `README.md`, `CONTRIBUTING.md`, and architecture/navigation document.
2. A task issue template and pull-request template.
3. A short `AGENTS.md` only when AI contributors need an entrypoint. Route to canonical documents; do not duplicate them.
4. An ADR directory only after a durable cross-cutting decision needs one.
5. Structured handoffs only for unfinished or transferred work.

The files under [assets/templates](assets/templates) are starting points, not mandatory replacements. Inspect the project first, remove irrelevant sections, fill project-specific commands and boundaries, and never leave placeholders presented as facts.

## Make work recoverable

A task package should define the observable goal, in-scope and out-of-scope work, verifiable acceptance criteria, relevant context, dependencies, and unresolved decisions. Preserve implementation freedom unless a constraint genuinely requires a particular design.

When work is interrupted or transferred, record:

- exact branch, commit, pull request, and location of uncommitted work;
- completed work tied to files or commits;
- commands actually run, results, environment, and unverified checks;
- confirmed findings and evidence;
- rejected approaches with the conditions that made them unsuitable;
- remaining work, blockers, decision owner, and one concrete next action.

Keep handoffs in the task's primary record when platform access and authorization exist. If access is unavailable, create a clearly dated read-only snapshot and reconcile it back to the primary record when access returns. Never imply that cloning Git also retrieves issue or pull-request discussions.

## Require evidence at delivery

Pull requests should connect changes to acceptance criteria and state:

- whether they fully deliver or partially advance the task;
- the important implementation choices;
- evidence for each completed criterion;
- checks not run and why;
- documentation or decision records changed;
- compatibility risks, limitations, follow-up work, and rollback considerations when relevant.

Use automatic issue-closing syntax only when merging the pull request truly completes the task. A merge, build, deployment command, or health response proves only its own stage; do not claim later runtime or production outcomes without testing them.

## Keep formal process proportional

- Typo or small obvious correction: direct pull request and proportionate checks; an issue is optional.
- Ordinary feature, defect, or cross-session task: issue, pull request, tests, and a handoff if unfinished.
- Durable API, compatibility, security, persistence, or architecture choice: add explicit design discussion and a decision record.

Record a decision as accepted separately from recording its implementation as delivered. Do not infer historical rationale from current code; label missing history as unknown and record new decisions as new.

## Validate the system

Check syntax and repository-specific commands, then perform an empty-context review: from only the repository and one task, can a new contributor identify the goal, constraints, modification area, latest state, and next verification? Fix the exact missing entrypoint or evidence. Do not answer every failure by adding more generic documentation.

Report what changed, what was verified, and what remains unverified. Keep facts, constraints, hypotheses, and recommendations visibly distinct.
