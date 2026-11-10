# Format sample

This file shows the quest shape. It is not an active quest. Do not score it or coach it. Live quests are written into the learner's repo at `.quests/<slug>.md`.

```markdown
---
title: Add a campaign budget cap to the meta marketing flow
slug: meta-marketing-budget-cap
status: draft
current: 1
earned: 0
total: 14
---

# Scoreboard

| # | Lesson | Kind | Points | Status |
|---|--------|------|--------|--------|
| 1 | Find where a campaign is created | recon | 2 | current |
| 2 | Predict a missing budget | recon | 2 | locked |
| 3 | Add the budget field | build | 6 | locked |
| 4 | Cover it with tests | build | 4 | locked |

## Lesson 1 — Find where a campaign is created

Kind: recon
Points: 2

### Checks

- [ ] Name the function that creates a campaign (1)
- [ ] Name the file that owns the marketing validation rules (1)

### Guidance

Start from the campaign create request. Follow it to the function that persists the campaign, then to the module that rejects an invalid campaign. A good answer names both, with the file path for the validation rules.

### Verify

The answer matches the code. Say what matched and what is still open.

## Lesson 2 — Predict a missing budget

Kind: recon
Points: 2

### Checks

- [ ] Say what the create path does today when budget is absent (1)
- [ ] Point at the test that locks that behavior in (1)

### Guidance

Read the create path and its tests. Predict the current behavior before changing it. Quote the assertion that would fail if that behavior changed.

### Verify

The prediction matches the code and the named test asserts it.

## Lesson 3 — Add the budget field

Kind: build
Points: 6

### Checks

- [ ] Add the budget cap to the create request in the same shape as the nearest existing field (2)
- [ ] Reject a cap below the existing minimum in the validation module (2)
- [ ] Pass the cap through to the persist call (2)

### Guidance

Copy the nearest existing field on the create request. Validate the cap beside the other marketing rules. Thread the value through the persist call the same way the neighboring field is threaded. The human writes the code.

### Verify

The diff contains those three edits and the human can explain each one. Run the existing campaign tests. A failure stays on this lesson.

## Lesson 4 — Cover it with tests

Kind: build
Points: 4

### Checks

- [ ] Add a test that a valid cap is stored (2)
- [ ] Add a test that a cap below the minimum is rejected (2)

### Guidance

Extend the campaign create test file. One test asserts the stored cap. One asserts the rejection. Match the arrange-act-assert style already in that file. The human writes the tests.

### Verify

The new tests pass, and the previous campaign tests still pass.

## Facilitator notes

- Entry point: the campaign create request handler.
- Invariant: a campaign is stored only after the marketing validation rules pass.
- Files the human will touch: the create request type, the marketing validation module, the persist call, the campaign create tests.
- Nearest existing pattern: the existing optional field on the create request, validated in the same module and asserted in the create tests.
- How to verify: the project's campaign test command, plus the diff for each check.
```
