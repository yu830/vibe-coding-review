# Codex Review Gates

Use targeted Codex review questions. Do not ask for an unfocused rewrite unless the user requests redesign.

## Plan review prompt

```text
Review this file-level plan against the project anchors and active phase.

Check:
1. Does the plan fit PROJECT_BRIEF.md?
2. Does it stay within ACTIVE_PHASE.md?
3. Are non-goals explicit enough?
4. Are any files or behaviors missing?
5. Are Codex review gates too weak or too heavy?
6. What should be changed before implementation?

Return blocking issues first, then optional suggestions.
```

## Implementation summary review prompt

```text
Review this implementation summary and changed-file list against the approved plan.

Check:
1. Did implementation stay within scope?
2. Are any changed files unexpected?
3. Is verification sufficient?
4. Are there unresolved risks?
5. Should any follow-up become a new phase instead of being added now?

Return blocking issues first, then optional suggestions.
```

## Diff review prompt

```text
Review this diff against PROJECT_BRIEF.md, ACTIVE_PHASE.md, and the approved phase plan.

Focus on:
1. scope drift
2. missing requirements
3. unapproved features
4. verification gaps
5. correctness or security risks
6. unnecessary complexity

Do not propose broad rewrites unless required to fix a blocking issue.
```

## Scope expansion review prompt

```text
Review this proposed new phase.

Check:
1. Is this truly outside the current phase?
2. Is the new phase objective clear?
3. Are allowed scope and non-goals explicit?
4. Are review gates appropriate?
5. Is anything too broad for one phase?
```

## Closeout review prompt

```text
Review this closeout summary before acceptance or external presentation.

Check:
1. Were all phase objectives completed?
2. Were any non-goals violated?
3. Are verification results adequate?
4. Do unresolved risks require another phase?
5. Is this safe to commit, publish, deploy, or present externally?
```
