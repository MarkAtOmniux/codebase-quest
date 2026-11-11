# Codebase Quest 🎯

Learn the part of a codebase you have never touched, by building the change yourself.

You already know how to write software. You have not worked in this corner of the system. Codebase Quest turns that area into a short tutorial. The agent reads the code, writes a quest, and coaches you one lesson at a time. You type every line. A small score marks the checks you pass.

It works with Cursor, Claude Code, Antigravity, and any agent that loads [Agent Skills](https://agentskills.io).

## Who it's for

Experienced developers about to change a subsystem they did not write.

- You are adding a feature in a flow you have not owned.
- You want the real path, the rules, and the tests in your head before the change lands.
- You want a coach in the editor while you do the work.

It fits a change you can finish in a sitting or two. A new field on an existing flow. A branch in a complicated path. A behavior you need to extend while keeping the current rules intact.

## What it looks like

You open the repo and ask:

> Walk me through adding a budget cap to the meta marketing flow. I will write the code.

The agent reads the implementation and the tests before it teaches anything. Then it shows a scoreboard and waits until you accept the plan.

| Lesson | What you do | Points |
| --- | --- | --- |
| 🔍 Find where a campaign is created | Trace the code and name the function | 2 |
| 🔍 Predict a missing budget | Say what happens today, and which test locks it in | 2 |
| 🛠️ Add the budget field | Write the change, following the existing pattern | 6 |
| 🧪 Cover it with tests | Write the tests and get them passing | 4 |

The first lessons are 🔍 recon. You read, predict, and point at the code. Later lessons are 🛠️ build lessons, and a test lesson is marked 🧪. The agent tells you what to change and why, and shows you the pattern already in the repo. You write the code. It runs the tests, reads your diff, and checks the lesson off when the work holds.

You can see every lesson and its points from the start. Coaching stays on the current lesson until those checks pass. Ask for a hint and you get the file, the pattern, and the shape of the change.

Close the laptop whenever you want. The quest lives at `.quests/<slug>.md` in the repo you are learning, with your score and the lesson you were on. Come back tomorrow and pick up there. Commit that file, or leave it untracked.

## Install

You need [Node.js 22.20](https://nodejs.org) or later.

**Cursor**, for every project:

```bash
npx skills add MarkAtOmniux/codebase-quest -g -a cursor -y
```

**Cursor, Claude Code, and Antigravity** together:

```bash
npx skills add MarkAtOmniux/codebase-quest -g -a cursor claude-code antigravity antigravity-cli -y
```

`-g` installs the skill for every project on your machine. Drop it if you want the skill in the current repo only. Drop `-a` to pick agents from a list. Names are separated by spaces.

Start a new chat in the codebase you want to learn, and ask to be walked through the change.

Update it later with:

```bash
npx skills update codebase-quest
```

## License

[MIT](LICENSE)
