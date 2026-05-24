# Vibe Coding Review

A project-governance Skill for Codex and Claude Code that keeps AI-assisted coding sessions aligned with the user's intent, active phase, and explicit non-goals.

## Why This Exists

AI coding agents are strong at implementation, but long sessions often drift:

- the original plan gets forgotten
- new features appear without approval
- vague ideas become oversized builds
- implementation continues after a phase should have stopped
- review happens only after the project has already expanded

I created this Skill after running multi-step projects with Claude Code and Codex where the agent would start with a reasonable plan, then later lose track of that plan or add features that were never approved. The result was not a lack of code, but too much ungoverned code.

The useful pattern was clear: the project needed a lightweight supervisor workflow. Before coding, the agent should clarify the idea. Before implementation, it should produce a phase plan. During implementation, it should stay inside the active phase. When scope changes, it should stop and create a new phase instead of expanding silently.

Vibe Coding Review packages that workflow into a reusable Skill.

## What It Does

- Turns vague project ideas into clearer build directions
- Requires project anchors before implementation
- Reviews Claude Code or Codex plans before coding
- Supervises active development phases
- Detects scope drift and unapproved feature expansion
- Structures targeted Codex review handoffs
- Supports project closeout before publishing, deployment, or presentation

## Lifecycle Modes

1. Initial Setup / Anchor Creation
2. Brainstorming Ask
3. Plan Review
4. Phase Supervisor
5. Diff Review
6. Scope Change / Phase 2 Plan
7. Project Closeout

## Required Project Anchors

Governed projects should keep these files:

```text
docs/
  PROJECT_BRIEF.md
  phases/
    ACTIVE_PHASE.md
```

`PROJECT_BRIEF.md` captures durable project intent, boundaries, and non-goals.

`ACTIVE_PHASE.md` captures the current phase contract: objective, allowed scope, review gates, out-of-scope items, and handoff format.

For larger projects, optional phase files can be added under `docs/phases/`.

## Quick Install

### Codex

Copy this folder to:

```text
~/.codex/skills/vibe-coding-review/
```

### Claude Code

Copy this folder to:

```text
~/.claude/skills/vibe-coding-review/
```

Restart the app or open a new session if the Skill does not appear immediately.

## Usage

Explicit invocation:

```text
Use $vibe-coding-review to brainstorm this project idea before planning.
```

Plan review:

```text
Use $vibe-coding-review.

Here is Claude Code's plan. Review whether it fits PROJECT_BRIEF.md and ACTIVE_PHASE.md before I approve implementation.
```

Scope change:

```text
Use $vibe-coding-review.

The active phase only allows README edits, but I now want to add a CLI and GitHub publishing. Tell me whether this fits the current phase.
```

## Recommended Workflow

1. Start with Brainstorming Ask.
2. Create or review project anchors.
3. Produce a file-level phase plan.
4. Send the plan to Codex for review when required.
5. Implement only the approved active phase.
6. Run Diff Review.
7. Close out the phase before expanding scope.

## What This Skill Is Not

- Not a code-generation framework
- Not a universal architecture guide
- Not a replacement for tests
- Not an automation runner
- Not a GitHub publishing workflow
- Not permission to expand scope without a new phase

## Repository Structure

```text
SKILL.md
agents/
  openai.yaml
references/
  codex-review-gates.md
  handoff-examples.md
  lifecycle-mode-details.md
  project-anchor-templates.md
```

## Design Principles

- Low freedom for lifecycle gates and output contracts
- High freedom for brainstorming questions
- Explicit non-goals before implementation
- New feature requests become new phase plans
- Codex review prompts should be targeted, not vague

## Status

This is an initial public Skill release. It is intentionally small and procedural: the goal is to prevent AI-assisted project drift, not to replace engineering judgment.

