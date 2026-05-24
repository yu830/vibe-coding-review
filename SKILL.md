---
name: vibe-coding-review
description: "Trigger for AI-assisted project governance: brainstorming, plan review, phase supervision, scope drift control, diff review, scope changes, Codex review gates, and project closeout."
---

# Vibe Coding Review

Use this Skill to keep an AI-assisted coding project aligned with the user's original intent, approved plan, active phase, and explicit non-goals.

This is a project governance workflow for Claude Code and Codex. It is not a code-generation framework, architecture guide, automation runner, GitHub publishing workflow, or replacement for tests.

## Core Principle

Every substantive action must be grounded in persistent project anchors and an active phase contract. If the requested work does not fit the active phase, stop and propose a phase update instead of implementing.

## Required Project Anchors

A governed project should maintain these files:

```text
docs/
  PROJECT_BRIEF.md
  phases/
    ACTIVE_PHASE.md
```

For larger projects, optional phase plan files may also be used:

```text
docs/phases/phase-01-<name>.md
docs/phases/phase-02-<name>.md
```

### PROJECT_BRIEF.md

`docs/PROJECT_BRIEF.md` records the durable project intent:

- working name
- purpose
- target environment
- core problem
- product boundary
- explicit non-goals
- expected artifacts

### ACTIVE_PHASE.md

`docs/phases/ACTIVE_PHASE.md` records the current phase contract:

- phase name
- objective
- current status
- allowed scope
- required review gates
- out-of-scope items
- drafting or implementation requirements
- handoff format

### Optional phase plans

Separate phase plan files are optional. Use them only when the project is large enough that `ACTIVE_PHASE.md` would become hard to read.

## Universal Operating Rule

Before creating, editing, moving, deleting, formatting, committing, or otherwise implementing files:

1. Read `docs/PROJECT_BRIEF.md`.
2. Read `docs/phases/ACTIVE_PHASE.md`.
3. State:
   - active phase
   - allowed scope
   - out-of-scope items
   - whether implementation is approved
   - whether the request fits the active phase

If either anchor is missing, enter Initial Setup / Anchor Creation mode.

If the request is outside the active phase, stop. Do not implement. Propose a new or revised phase plan.

## Lifecycle Modes

### 1. Initial Setup / Anchor Creation

Use this mode when `docs/PROJECT_BRIEF.md` or `docs/phases/ACTIVE_PHASE.md` is missing.

Rules:

- Stop implementation immediately.
- Tell the user which anchor files are missing.
- Ask whether to create project anchors.
- Either create minimal anchors after explicit approval, or propose their contents for review.
- Do not begin any implementation phase until the anchors exist and the active phase permits the work.

Minimal anchor creation should capture only durable project governance, not product-specific implementation details beyond what the user has approved.

Output:

```text
Changed Files: none, unless anchor creation was approved
Anchor Status:
Missing Anchors:
Proposed Anchor Contents:
Implementation Approval: not approved
Suggested Next Step:
```

### 2. Brainstorming Ask

Use this mode when the user has inspiration, a vague goal, or an early project idea.

This mode is intentionally high freedom. Help the user turn inspiration into a concrete direction by asking about:

- desired outcome
- audience or user
- target environment
- success criteria
- constraints
- non-goals
- examples or references
- what should happen first

Rules:

- Do not treat brainstorming as implementation approval.
- Do not create files unless the user explicitly asks to create anchors.
- Keep questions focused; avoid overwhelming the user.
- Preserve uncertainty instead of pretending the plan is decided.

Output:

```text
Changed Files: none
Brainstorm Summary:
Open Decisions:
Potential Non-goals:
Suggested Next Step:
```

### 3. Plan Review

Use this mode before implementation.

The goal is to convert the project intent into a file-level phase plan that can be reviewed by the user and, when required, Codex.

A plan should include:

- active phase name
- objective
- files to create or change
- allowed scope
- explicit non-goals
- verification expectations
- Codex review gates
- scope risks
- questions for Codex review

Rules:

- Do not implement during plan review.
- The plan must be file-level, not vague.
- Include explicit non-goals.
- If the active phase requires a Codex review gate, stop after the plan and ask the user to send it to Codex.

Output:

```text
Changed Files: none
Plan Summary:
Verification: not applicable
Scope Risks:
Questions For Codex Review:
Suggested Next Step:
```

### 4. Phase Supervisor

Use this mode during approved implementation.

Rules:

- Implement only the active phase scope.
- Do not silently add features.
- Do not create a new phase implicitly.
- Do not overwrite governance files unless explicitly requested.
- Do not remove review gates unless explicitly requested.
- Track changed files.
- Run or request verification appropriate to the phase.
- If new requirements appear, stop and switch to Scope Change / Phase 2 Plan mode.

Output after implementation:

```text
Changed Files:
Implementation Summary:
Verification:
Scope Deviations:
Issues:
Questions For Codex Review:
Suggested Next Step:
```

### 5. Diff Review

Use this mode after implementation, before acceptance, before a commit, or when the user asks whether the work stayed on track.

Review the diff against:

- `docs/PROJECT_BRIEF.md`
- `docs/phases/ACTIVE_PHASE.md`
- the approved plan
- explicit non-goals
- verification expectations

Check for:

- correctness issues
- missing requirements
- scope drift
- unapproved features
- security risks
- inadequate tests or manual verification
- overbuilt abstractions
- changed files that do not belong to the phase

Output:

```text
Verdict:
Blocking Findings:
Non-blocking Findings:
Verification Gaps:
Scope Drift:
Questions For Codex Review:
Suggested Next Step:
```

### 6. Scope Change / Phase 2 Plan

Use this mode when the user asks for new features, broader behavior, a different direction, or anything outside `ACTIVE_PHASE.md`.

Rules:

- Do not implement the change in the current phase.
- Explain why the request is outside the active phase.
- Propose a new or revised phase plan.
- Include explicit non-goals.
- Include Codex review gates when required.
- Wait for user approval before implementation.

Output:

```text
Changed Files: none
Scope Change Detected:
Why Current Phase Does Not Cover It:
Proposed New Phase:
Explicit Non-goals:
Questions For Codex Review:
Suggested Next Step:
```

### 7. Project Closeout

Use this mode when the user says the phase or project is done, or before external presentation, publishing, deployment, or final acceptance.

Closeout should confirm:

- changed files
- completed scope
- out-of-scope items were not added
- verification results
- unresolved risks
- recommended next step

Codex review is required for closeout only when at least one of these is true:

- unresolved risks remain
- scope drift was detected
- verification was skipped or failed
- the project is about to be committed, published, deployed, or presented externally

Output:

```text
Changed Files:
Closeout Summary:
Verification:
Unresolved Risks:
Scope Drift:
Codex Review Required: yes/no, with reason
Suggested Next Step:
```

## Codex Review Gates

When a Codex review gate is required, stop at the gate and use direct language:

```text
Stop here. Send this plan or summary to Codex for review before implementation or acceptance.
Do not proceed until Codex feedback is returned or the user explicitly approves continuation.
```

Codex review should be targeted. Ask Codex specific questions about scope, missing risks, verification, and whether the proposal matches the project anchors.

Do not ask Codex to broadly rewrite the project unless the user requested a redesign.

## Stopping Rules

Stop immediately and ask for direction when:

- required anchors are missing
- implementation has not been approved
- the request is outside the active phase
- the user asks for scope expansion
- the active phase requires Codex review before proceeding
- verification fails and the fix would exceed the active phase
- a risky action is requested without explicit approval

## Non-goals

This Skill does not define:

- a specific app architecture
- universal coding style rules
- automatic command execution
- CI configuration
- hooks
- CLI tools
- GitHub publishing
- frontend catalog integration
- product-specific business logic

Keep the workflow procedural and concise. The goal is to prevent project drift, not to replace engineering judgment.
