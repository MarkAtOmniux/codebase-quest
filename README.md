# codebase-quest

[![skills.sh](https://skills.sh/b/MarkAtOmniux/codebase-quest)](https://skills.sh/MarkAtOmniux/codebase-quest)

A skill for Cursor, Claude Code, Antigravity, and other coding agents. It turns an unfamiliar part of a codebase into a short scored tutorial. You implement the change by hand. The agent researches the code, writes a quest, and coaches one lesson at a time.

## Install

Requires [Node.js 22.20](https://nodejs.org) or later.

```bash
npx skills add MarkAtOmniux/codebase-quest -g -a cursor claude-code antigravity antigravity-cli
```

`-g` installs it for every project on your machine. That is the right default, because you use the skill inside whatever codebase you are learning. Omit `-g` to install it into the current repo only. Omit `-a` to pick agents from a list. Agent names are separated by spaces.

A new session picks the skill up. Then ask for a quest:

```text
Walk me through adding a budget cap to the meta marketing flow.
I will write the code. Quest me through it.
```

## What you get

The agent writes `.quests/<slug>.md` in the repo you are learning. That file is the save game: the scoreboard, each lesson, and your points. Recon lessons come first and ask you to trace the code. Build lessons ask you to change it yourself. You can see every lesson and its points up front. The agent coaches the current lesson, and opens the next one when the checks pass.

You can commit `.quests/` or leave it untracked.

## Update

```bash
npx skills update codebase-quest
```

## License

[MIT](LICENSE)
