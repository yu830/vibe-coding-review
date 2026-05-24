# Project Anchor Templates

Use these templates when Initial Setup / Anchor Creation mode is approved by the user.

## Minimal `docs/PROJECT_BRIEF.md`

```md
# Project Brief

## Working Name

<project name>

## Purpose

<what this project is meant to accomplish>

## Target Environment

- <environment or tool>

## Core Problem

<problem this project solves>

## Product Boundary

This project should define:

- <included capability>

This project should not define:

- <explicit non-goal>

## Expected Artifacts

- <artifact>
```

## Minimal `docs/phases/ACTIVE_PHASE.md`

```md
# Active Phase

## Phase Name

Phase 1 - <phase name>

## Objective

<what this phase should accomplish>

## Current Status

<current status>

## Allowed Scope

The agent may:

- <allowed action>

## Required Review Gates

Before implementation:

1. Produce a concise file-level plan.
2. Stop for user approval or required Codex review.

After implementation:

1. Report changed files, verification, issues, and scope deviations.
2. Stop for required review if risks remain.

## Out Of Scope

The agent must not:

- <forbidden action>

## Handoff Format

When the agent finishes a planning or implementation step, it must report:

1. Changed Files, or "none"
2. Plan Summary or Implementation Summary
3. Verification, if applicable
4. Scope Risks or Scope Deviations
5. Questions For Review
6. Suggested Next Step
```

## Optional phase plan file

Use only for larger projects.

```md
# Phase <number> - <name>

## Objective

<phase objective>

## Files Expected To Change

- `<path>` - <reason>

## Allowed Scope

- <allowed work>

## Explicit Non-goals

- <excluded work>

## Verification

- <test, build, manual check, or review expectation>

## Review Gates

- <Codex or user review requirement>

## Completion Criteria

- <how the phase is accepted>
```
