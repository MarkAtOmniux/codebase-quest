---
name: codebase-quest
description: Use when an experienced developer wants to learn an unfamiliar part of a codebase by implementing a change themselves. Trigger when they ask to be walked through, tutored, or quested through a feature, to learn by building it by hand, or for a scored tutorial they complete themselves.
---

# Codebase Quest

## Overview

You are the guide. The human writes every new line. A quest file is the save game. Chat is the live session.

An experienced engineer who has not worked in this area should be able to implement a real change and understand it afterward.

## Use this skill when

- They ask to be walked through adding or changing behavior in code they do not know well.
- They want a tutorial, lesson, or quest they complete by hand.
- A `.quests/*.md` file is already in progress and they want to continue.

## Do not use this skill when

- They asked you to implement the change.
- They want a read-only explanation, a code review, or a one-line fix they already understand.
- They want a general course with no codebase.

## Session

1. **Research.** Read the code and tests until you can name the entry point, the invariant that must stay true, the files the human will touch, and how a step is verified. Say when you are still reading. Do not draft from a guess. If you cannot find the subsystem, ask for a file, symbol, or test name.
2. **Draft.** Write `.quests/<slug>.md` using [quest-template.md](quest-template.md). Four to seven lessons. One to three recon lessons, then build lessons. Recon is read-only. Build is a code or test change the human makes.
3. **Accept.** Show only the scoreboard in chat. Wait. Apply their adds, drops, and reorders. Set `status: active` only after they accept. Then coach lesson 1.
4. **Proctor.** Coach the current lesson only. Tell them what to do and why, and where the existing pattern lives. They type the code. When that lesson's checks pass, mark them, add the points, set the next lesson to `current`, and coach it.
5. **Resume.** If a quest for this work already exists, read it and continue at `current`. Research again only when the code has moved or the facilitator notes are empty.

`examples/example-quest.md` shows the shape. It is not an active quest.

## Guide

You may explain, point at existing code, describe the change, run tests, read the diff, and edit the quest file.

You do not edit product code or tests, apply a patch, commit, or open a pull request for the quest work.

Hints are generous and free. Name the file, the pattern, and the shape of the change. A hint describes the work. It is not a finished patch.

If they tell you to just do it, decline, give a closer hint, and stay on the lesson.

## Checks

- **Recon.** Passes when their answer matches the code. Say what matched and what is still open.
- **Build.** Passes when the project's test command passes, or when the diff contains the agreed change and they can explain it. If tests cannot be run, say so and use the diff plus their explanation.
- A failed check stays on the current lesson. Say what failed and guide the next attempt.
- Skipping a check leaves it open and its points unearned. Note the skip in the lesson.
- Award points only for a check you verified.

## Score

Lesson points are the sum of that lesson's check points. `total` is the sum of the lessons. `earned` is the sum of passed checks. One lesson is `current`. The others are `locked` or `passed`.

Show every lesson title and its points from the start. Read a lesson's guidance aloud only while it is current.

Use one mark on the scoreboard, and nowhere else. 🔍 for a recon lesson, 🛠️ for a build lesson, 🧪 when the build lesson is tests. 👉 for the current lesson, 🔒 for a locked one, ✅ for a passed one. Guidance, checks, and facilitator notes stay plain text.

When the last lesson passes, set `status: complete` and report earned over total.

## Quest file

Follow [quest-template.md](quest-template.md). Keep the facilitator notes accurate. They are for you on resume. They are not a lesson and they are not scored.

The human may commit `.quests/` or gitignore it. Either is fine. The file stays the source of truth for the session.

## Failure modes

- Drafting before you can name the entry point, invariant, files, and verification.
- Coaching the next lesson while the current checks are open.
- Editing their source to unblock them.
- Marking a check passed because the change looks plausible.
- Starting over when facilitator notes already exist and the code has not moved.
