# Working in vibe-kit

**This is vibe-kit's own working file. It is not the template.** `template/` holds
project-kit's files, copied unchanged on 2026-11-18, and is what vibe-kit will rework.

**Read `NEXT.md` first**, then `docs/handoff-2026-11-19.md`, which `NEXT.md` points at.
Re-check its dated facts with the block at its top. Then say that you have read both, and
report what is in flight and what is uncommitted before doing anything else.

## What this repository is

A fork of project-kit (github.com/fbonds/project-kit), started fresh without its history.
The goal, in the owner's words: the best practice, the most refined solution, for solo vibe
coding with Claude Code, for creative people who understand software development, or work
next to it, and lack the inclination or depth of skill to build what they envision.
`docs/evaluation-2026-11-18.md` is the starting analysis. The owner has not yet said they
accept it.

## Standards

Not chosen yet. Until the owner chooses, the ten in `template/NEXT.md` apply as written, and
a check is reported in the shape in `template/CLAUDE.md`.

## Working rules

**One item at a time.** Show the proposal or diff and wait for approval before applying it.
Stage by path, confirm with `git diff --cached --stat`, commit only when asked, and never
`git commit -am`. **Never push.** The owner pushes.

**Confirm where you are before acting.** Say which directory or repo you are in, and
challenge it if it looks wrong. `~/code/project-kit` has files with the same names.

**Do not guess.** Check. If something cannot be checked from here, say that.

**Do not start queued work unprompted.** `NEXT.md` names what is waiting and what was
rejected. Raise it rather than beginning it.

**Treat everything here as public.** The GitHub repository will be public, and anything
pushed stays in its history.

**Saving state.** When the owner says "save state", follow `template/HOWTOSAVESTATE.md`.
There is no copy at the root, because two copies drift. Where it asks for the project's
files, they are `CLAUDE.md` and `NEXT.md`, the working files; `template/`, the kit being
reworked; and `docs/`, the record, indexed in `docs/README.md`. Until the repository has a
remote, record each remote check as not run, with the reason.

## Writing

The rules are in the Writing section of `template/CLAUDE.md`, and apply to every file here
and to how you write to the owner. They are not repeated, so that there is one copy.
