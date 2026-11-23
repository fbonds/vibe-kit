# Working in vibe-kit

**This is the working file for building vibe-kit.** The kit itself is in `kit/`, and its
`CLAUDE.md` is for the kit's reader, not for this repository.

**Read `NEXT.md` first**, then `docs/handoff-2026-11-19.md`, which `NEXT.md` points at.
Re-check its dated facts with the block at its top. Then say that you have read both, and
report what is in flight and what is uncommitted before doing anything else.

## What this repository is

A fork of project-kit (github.com/fbonds/project-kit), started fresh without its history.
The goal, in the owner's words: the best practice, the most refined solution, for solo vibe
coding with Claude Code, for creative people who understand software development, or work
next to it, and lack the inclination or depth of skill to build what they envision.
`docs/session-design-2026-11-20.md` is the design brief every file in `kit/` is judged
against.

## Standards

Carried over from project-kit, where each was earned by a failure, except 10. They apply
until the owner chooses otherwise.

1. No check counts as verified until it has been shown failing on deliberately broken
   input, and the report says what was broken.
2. Never verify through a path that can resolve to a development copy: a link, a symlink, a
   cache, a running server. Name the path, resolve it, and prove it is the one you meant.
3. Check claims against the thing itself, the file or the fetched page, not a description of
   it. That includes `NEXT.md`.
4. Proposal before code, for anything with a surface. Wait for approval.
5. Stage by path, confirm with `git diff --cached --stat`, and never use `git commit -am`,
   `git add -A` or `git add .`.
6. Describe contents and order, not counts and pagination, which go stale silently.
7. Say what was not checked, and where each fact came from. An omission reads as a
   verified negative.
8. Never point at the conversation. A later session reads files, not chat.
9. Check stored memories against the repo. They load first and can outrank a correct file.
10. One item at a time: show the proposal or diff and wait for approval. Commit only when
    asked. **Never push.** The owner pushes.

Report a check in this shape. If it was never shown failing, say so on that line, and the
result does not count as verified.

    Result: what the output showed.
    Shown failing: what was broken, and what the check then reported.
    Path: the path used, resolved.
    Artifact: the thing checked, and where it came from.
    Not checked: each thing, named.

## Working rules

**Confirm where you are before acting.** Say which directory or repo you are in, and
challenge it if it looks wrong. `~/code/project-kit` has files with the same names.

**Do not guess.** Check. If something cannot be checked from here, say that.

**Do not start queued work unprompted.** `NEXT.md` names what is waiting and what was
rejected. Raise it rather than beginning it.

**Treat everything here as public.** The GitHub repository is public, and anything pushed
stays in its history.

## Saving state

When the owner says "save state":

1. **Check the outside world now.** Run the block at the top of `NEXT.md`. Record each fact
   with its date and how it was checked, and record any check that could not run.
2. **Write it into `NEXT.md`.** External facts with dates. Decisions with their reasons,
   what was ruled out, and anything the owner said not to do, under Decided: a changed
   decision is a new entry, and the old one gets one line saying what replaced it.
   Uncommitted, unpushed and unreleased as three separate questions, with unpushed given as
   the command that answers it plus a dated snapshot. Anything that exists only in the
   conversation, written out in full; a long one goes in its own file in `docs/`, indexed
   in `docs/README.md`. Approved wording, verbatim. New traps.
3. **Check stored memories** for this project against the repo. Correct or delete what has
   drifted, and name in the report which were checked.
4. **Stage by path and report.** Commit only when asked, and never push. Say what was
   written and where, what was verified and when, and what could not be verified.

The files: `CLAUDE.md` and `NEXT.md` are the working files, `kit/` is the kit, and `docs/`
is the record.

## Writing

These apply to every file here and to how you write to the owner. They are the patterns
that read as machine-written.

- No "not X, it's Y" reframes. State what it is.
- No rule-of-three cadence, three parallel items or three adjectives on everything.
- No trailing participial clauses that tack a conclusion onto a fact.
- No "that said" or "with that said" pivots. Use "but".
- No "here's the thing" or "the thing is" lead-ins.
- No rhetorical questions as transitions.
- No bolded mini-header on every bullet where prose works.
- No "not only... but also". Use "and".
- No summary sentence restating what was just read.
- No unprompted "think of it like" analogies.
- No "X is where Y matters" constructions.
- No emoji or checkmark decoration in headers or lists.
- Prefer short declaratives over clause-heavy sentences.
- No em dashes, anywhere: chat, files, commit messages.
- Say what a thing does rather than performing it.
- No preamble, and no restating the request before answering it.
