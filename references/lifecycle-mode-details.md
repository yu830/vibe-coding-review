# Lifecycle Mode Details

This reference expands the core modes in `SKILL.md`. The core rules remain authoritative.

## Initial Setup / Anchor Creation

Trigger when `docs/PROJECT_BRIEF.md` or `docs/phases/ACTIVE_PHASE.md` is missing.

Allowed:

- identify missing anchors
- ask whether to create them
- propose minimal contents
- create anchors after explicit approval

Forbidden:

- starting implementation without anchors
- guessing durable project intent
- creating broad phase plans without user confirmation

## Brainstorming Ask

Trigger when the user has a vague idea, inspiration, or early goal.

Useful questions:

- What inspired this?
- What should exist when this is done?
- Who will use it?
- What should this not become?
- What would make Phase 1 successful?
- What review or approval gates do you want?

## Plan Review

Trigger before implementation.

A good plan is file-level and contains:

- files to create/change
- purpose of each file
- explicit non-goals
- verification expectations
- Codex questions
- stopping point

## Phase Supervisor

Trigger during approved implementation.

The agent should continuously compare work against:

- project brief
- active phase
- approved plan
- non-goals

If drift appears, stop and report it.

## Diff Review

Trigger after implementation or before acceptance.

Review order:

1. List changed files.
2. Match each change to approved scope.
3. Identify unapproved files or behavior.
4. Check verification evidence.
5. Separate blocking issues from suggestions.

## Scope Change / Phase 2 Plan

Trigger when the user asks for something outside the active phase.

The response should make the boundary explicit and propose a new phase instead of implementing immediately.

## Project Closeout

Trigger when the phase or project is ready to end.

Codex review is risk-triggered, not automatic. Require it when risks remain, drift was detected, verification failed or was skipped, or external publication/deployment is about to happen.
