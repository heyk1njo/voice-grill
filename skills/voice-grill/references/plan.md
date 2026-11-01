# Plan

Use this after the summary is agreed, when producing something other than an article (an implementation, research, a sequence of steps, a decision). The goal is a plan that can be carried through to the end even if the user steps away, with all judgment calls and permissions gathered up front.

## Write the plan

Write `plan.md` in the same folder as the notes.

```markdown
# Plan: <topic>

## Goal
<What it is for, and for whom> (Q1, Q4)

## Done when
- <A state that counts as finished, in a form that can be checked>

## How to verify
- <tests, lint, running it for real, reading side by side, …>

## Steps
- [ ] 1. <step> (done when: <what marks it finished>)
- [ ] 2. …

## Operations that need permission
- commit: yes / no (and in what units)
- push, publish, send: yes / no
- delete, overwrite: <target and extent>
- operations that cost money, deploying to production: yes / no

## Assumptions
- <What goes ahead undecided, and the assumption made>

## Out of scope
- <What is left out>
```

- Cut steps small enough that each one can be judged finished on its own.
- Look up what can be looked up before planning. Leave no guesses in the steps.
- If the repository has its own rules (AGENTS.md, CLAUDE.md, README, existing skills), read them and reflect them in the plan.

## Get agreement

Show the key points of the plan (goal, done-when, step headings) in 5–7 lines, and open a single agreement round.

- Up to 5 questions, in the same format as the interview (numbered, with recommendations). Ask here, up front, about every judgment call and permission that could otherwise stop execution midway.
  - e.g. "**Q21** May I commit? If so, I'll split commits into logical units → Recommended: commit, but don't push"
- Phrase it so that "yes" or "yes to all" accepts the whole plan and the recommendations.
- Once agreed, set the notes' status to "plan agreed" and move on to [run.md](run.md).

## Changing the plan

- If the plan stops fitting during execution, update `plan.md` and leave one line on why.
- Don't act on a change that widens done-when, out of scope, or the permissions until the user confirms it.
