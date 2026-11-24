# vibe-kit

You have an idea for some software. You can tell whether it works when you see it. You
don't want to learn to write the code. vibe-kit sets up Claude Code, Anthropic's coding
assistant, to build it with you that way, and to keep you clear of the mistakes AI coding
is known for.

## What it does

- **You approve a plan before anything is built**, written in plain words: what you will
  be able to do when it is done, what will not change, and anything that costs money or
  cannot be undone.
- **You see it working before it counts as done.** Claude shows you, says what it checked
  and what it could not check, and you decide.
- **It talks to you in plain words.** No code, no diffs, no git terms, unless you ask.
- **Your work is saved after every step**, and Claude asks before backing it up online or
  putting it live.
- **It keeps notes** on what works, what is left and what was decided, so the next session
  picks up where you stopped.
- **Some mistakes are blocked outright**: commands that destroy history, and reading files
  where passwords are kept.

## What you need

Claude Code, installed and working in your terminal. Anthropic's instructions are at
https://code.claude.com/docs.

## Set it up

1. Open your terminal in the folder for your project. For something new, make an empty
   folder first.
2. Start Claude Code by typing `claude`.
3. Paste this, all of it:

```
Set up vibe-kit in this folder. Copy these three files from GitHub exactly as they are, without changing them: https://raw.githubusercontent.com/fbonds/vibe-kit/main/kit/CLAUDE.md to CLAUDE.md, https://raw.githubusercontent.com/fbonds/vibe-kit/main/kit/.claude/settings.json to .claude/settings.json, and https://raw.githubusercontent.com/fbonds/vibe-kit/main/kit/PROGRESS.md to PROGRESS.md. If any of them already exists, ask me before replacing it. If this folder is not a git project yet, make it one. Talk to me in plain words, without git terms. When it is done, tell me it is ready, that I should close Claude Code and start it again here, and that when it starts again it will ask whether I trust this folder: explain why in a sentence, and tell me to say yes.
```

4. When Claude says it is ready, type `/exit`, then `claude` again.
5. Claude Code will ask whether you trust this folder, and warn that it "configures hooks
   that can run commands". That is vibe-kit: at the start of each session it reads your
   progress notes. Choose **Yes, I trust this folder**.
6. Say hi. Claude will ask what you want to build, or offer to carry on where you left
   off.

## For people building vibe-kit

The design is in `docs/session-design-2026-11-20.md`, and the kit's files are in `kit/`.
`docs/README.md` lists the rest. MIT-0 licensed: see `LICENSE`.
