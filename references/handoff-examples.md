# Handoff Examples

## Planning handoff

```text
Changed Files: none
Plan Summary:
- Create `skills/example/SKILL.md` for the approved workflow.
- Add one optional reference file for examples.
- Keep core lifecycle rules in `SKILL.md`.

Verification: not applicable
Scope Risks:
- The user may later want automation, but automation is out of scope for this phase.
Questions For Codex Review:
1. Does this plan stay within ACTIVE_PHASE.md?
2. Are the non-goals clear enough?
Suggested Next Step:
Send this plan to Codex for review before implementation.
```

## Implementation handoff

```text
Changed Files:
- `skills/example/SKILL.md`
- `skills/example/references/examples.md`

Implementation Summary:
- Added the approved Skill draft.
- Kept core workflow rules in `SKILL.md`.
- Added examples only as reference material.

Verification:
- Read files after creation for structure and scope.

Scope Deviations:
- None.

Issues:
- None known.

Questions For Codex Review:
1. Is the Skill concise enough?
2. Are stopping rules explicit enough?
Suggested Next Step:
Send the implementation summary to Codex for review.
```

## Scope change handoff

```text
Changed Files: none
Scope Change Detected:
The requested GitHub publishing workflow is outside the active phase.

Why Current Phase Does Not Cover It:
ACTIVE_PHASE.md excludes GitHub publishing and automation.

Proposed New Phase:
Phase 2 - Publishing Workflow Design

Explicit Non-goals:
- No implementation until the phase plan is reviewed.
- No automatic publishing without explicit user approval.

Questions For Codex Review:
1. Should publishing be its own phase?
2. What review gates are required before external publication?
Suggested Next Step:
Review and approve a Phase 2 plan before implementation.
```

## Closeout handoff

```text
Changed Files:
- `skills/example/SKILL.md`

Closeout Summary:
- Completed the approved Skill draft.
- No unrelated automation or publishing behavior was added.

Verification:
- Confirmed changed files match approved scope.

Unresolved Risks:
- None known.

Scope Drift:
- None detected.

Codex Review Required: no, because verification passed, no drift was detected, and the project is not being externally published yet.

Suggested Next Step:
Accept the phase or request Codex review voluntarily.
```
