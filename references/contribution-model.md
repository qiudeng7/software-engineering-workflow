# Contribution model

Read this reference when deciding which artifacts a repository needs or when reviewing an existing collaboration system.

## Artifact boundaries

### README

Explain the project's purpose, supported use cases, fastest valid setup path, and links to contributor documentation. Do not store active task status here.

### CONTRIBUTING

Document prerequisites, local setup, repository-specific validation commands, branch and commit conventions, review expectations, and how contributors access task discussions. Use executable commands where stable. Avoid copying architecture prose.

### Architecture documentation

Provide a coarse code map, module responsibilities, allowed and forbidden dependency directions, important invariants, key execution paths, and the tests that protect them. Explain where to begin a kind of change. Do not manually maintain a complete call graph or narrate every file.

### AGENTS.md

Use as a short route map for coding agents: where canonical project, contribution, architecture, and task information lives; what to read before work; and what evidence or handoff is required at the end. Repository instructions may add non-obvious operational constraints, but should not become a second copy of `CONTRIBUTING.md`.

### Issue

Treat an issue as a task package that a contributor unfamiliar with previous chats can resume. Acceptance criteria should describe observable behavior, not only implementation steps. Use one primary status system and make blockers explicit.

### Handoff comment

Add a structured comment at meaningful interruption or transfer points. Summarize recoverable state rather than conversation history. A statement such as “mostly complete” is not recoverable; name the commit, passing checks, skipped checks, and next action.

### Pull request

Treat the pull request as delivery evidence. Map acceptance criteria to checks or observations and distinguish code integration from deployment and runtime verification. Partial work should reference an issue without closing it.

### ADR or design proposal

Record decisions with durable cross-module consequences, including context, constraints, choice, alternatives, tradeoffs, reevaluation conditions, and implementation tracking. Keep superseded records and link replacements. Routine implementation detail belongs in the pull request.

## Knowledge promotion

Promote information according to its lifetime:

- temporary investigation stays with the task;
- durable design rationale becomes an ADR or accepted proposal;
- stable usage and operational guidance enters maintained documentation;
- enforceable behavioral constraints become tests or automated checks.

Only promote evidence-backed, reusable findings. Do not preserve every agent output or chat transcript.

## Platform access

Repository clones contain files and Git history, not hosted issue and pull-request discussions. Document the supported access path, such as GitHub CLI:

```bash
gh issue view 123 --repo OWNER/REPO --comments
gh pr view 456 --repo OWNER/REPO --comments
```

Before using platform APIs, confirm authentication and repository identity. Reading existing state does not authorize posting comments or changing remote state.

## Review questions

- Does every kind of project knowledge have one obvious primary location?
- Can a newcomer find the correct module and its invariants without reading the whole codebase?
- Does a task state outcomes, scope, evidence, dependencies, and unresolved decisions?
- Can interrupted work be resumed from exact repository and task state?
- Does the pull request prove each completed acceptance criterion and disclose gaps?
- Are design acceptance, code integration, deployment, and runtime availability represented as separate states?
- Is the process lighter for small changes and stronger only when risk warrants it?
