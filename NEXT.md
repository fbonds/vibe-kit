# Where we are

**This is vibe-kit's own working state. It is not the template in `template/`.**

> **Read this before acting on anything below.** Every fact in this file is dated and may
> be stale. It records what was true when it was checked, not what is true now. Re-check
> first:
>
> ```sh
> git ls-remote --heads --tags origin       # what GitHub actually has
> git fetch -q origin && git rev-list --left-right --count origin/main...main   # left = behind, right = unpushed
> git status -sb
> ```

Updated 2026-11-20 00:48 UTC. Working state for vibe-kit, a fork of project-kit
(github.com/fbonds/project-kit) aimed at being the best practice for solo vibe coding with
Claude Code. **Read `docs/handoff-2026-11-19.md` next.** It holds everything from the
session that started this repository: the owner's goal and its definition in their words,
the decisions, what was rejected, and the lessons so far. Then report what is in flight and
what is uncommitted, and wait for the owner.

## Standards

Not chosen yet. `template/` holds project-kit's files unchanged, and `template/NEXT.md` has
its ten standards. Until the owner decides otherwise, work by the owner's global
instructions and by the working rules in the handoff: one item at a time, proposal or diff
before applying, stage by path, commit only when asked, never push.

## Traps

The six from the first session are in the handoff, under "Lessons from this session". Move
them here when this file's structure is settled.

- **macOS writes `.DS_Store` into folders opened in Finder.** One appeared at the root of
  this repository on 2026-11-19. `.gitignore` excludes it since 2026-11-19. Stage by path
  anyway.
- **The "none of the others" trap recurred after it was recorded.** On 2026-11-19 two such
  claims in the evaluation failed against the pages it cites: `mem.txt:564` dates memory
  files, and `sdd.txt:391-401` records dated amendments. Grepping for a quote confirms the
  quote exists. It does not find the passage that contradicts the claim. Search the cited
  page for the opposite claim too.
- **A URL taken from a saved docs page can be a link to another page.** Taking the first
  `code.claude.com/docs/en/*.md` link in each saved Anthropic page gave the wrong URL for
  all four, on 2026-11-19. Each page's first heading identified it, and fetching the live
  URL confirmed it.

## Decided, do not redo

**vibe-kit starts fresh from project-kit's `template/`** (2026-11-18, owner's decision).
No history, no root working files and no `docs/` from project-kit. The owner creates the
public GitHub repository and pushes.

**The evaluation lives here, as vibe-kit's starting document** (2026-11-18, owner's
decision on the session's recommendation). project-kit's README presents that kit as
complete, and a critique in its `docs/` would sit against that.

**A benchmark article and the five-item proposal based on it were dropped** (2026-11-18,
owner's decision). The owner said not to do any of it and to forget the article. Do not
raise it again unless the owner does.

**The evaluation's gaps are accepted, as corrected, and its path is reordered**
(2026-11-19, owner's decisions on the session's recommendations). The owner accepted the
seven gaps in `docs/evaluation-2026-11-18.md` with the corrections in
`docs/evaluation-corrections-2026-11-19.md`, with gap 4 ranked above gap 3: it affects the
approval in every session, and gap 3 affects examples read once. The path runs in this
order, numbered as in the evaluation: 5, approve the proposal and the observed behaviour,
with the diff available and not required; 6, a size budget for the state file; 2, a light
build loop; 1, measurement, extended to test building as well as keeping state; 3, rules
that must always hold moved into deny rules and tested hooks; 4, examples and Traps
questions rewritten for the reader. Reason: 5 and 6 are small and need no measurement, and
the harness designed in project-kit-harness tests keeping state, not building. Path work
starts after the first commit and push, so that `git diff` shows what vibe-kit changed in
project-kit's files.

**`docs/sources-2026-11-18/` stays out of the public repository, and the rest of `docs/` is
published** (2026-11-19, owner's decision on the session's recommendation). A search of the
saved pages for license notices on 2026-11-19 found an MIT license only on the six Spec Kit
and BMAD pages. The other 18 carry a copyright notice or none. The folder is ignored, and
`docs/README.md` lists each page's URL in its place. The handoff is published with its two
absolute home paths shortened to `~/code/project-kit`. The owner's name and email are
already public in project-kit's commit history, and the owner did not ask to switch
commits to GitHub's noreply address.

## In flight

Nothing. The first commit, `daacda6`, was pushed by the owner on 2026-11-20. At 00:48 UTC
`git ls-remote` showed GitHub `main` at `daacda6`, `gh repo view` showed the repository as
public, and the GitHub API listed `docs/` without `sources-2026-11-18/`. The first commit
holds:

- `.gitignore`: excludes `.DS_Store` and `docs/sources-2026-11-18/`.
- `template/`: project-kit's four template files at `23edcce`, copied unchanged.
- `docs/evaluation-2026-11-18.md`: the evaluation of project-kit. The owner accepted its
  gaps, as corrected, and reordered its path on 2026-11-19. See Decided.
- `docs/evaluation-corrections-2026-11-19.md`: five errors found in the evaluation on
  2026-11-19 by checking it against the saved pages.
- `docs/handoff-2026-11-19.md`: the first session's handoff.
- `docs/README.md`: the index of `docs/`, with the URL of each saved source page.
- `CLAUDE.md`: vibe-kit's working file, approved and written on 2026-11-19. The owner opens
  each session with "Read CLAUDE.md and comply".
- This file.

Ignored, and kept only on the owner's disk: `docs/sources-2026-11-18/`, the 24 source pages
the evaluation quotes, in 47 files. Each page has a `.raw` and a `.txt`, except `pm`, which
has only a `.txt`. On 2026-11-19 `git status --ignored` listed those 47 files and
`.DS_Store` as ignored, and nothing else.

## Queued, unscheduled, and not to be started unprompted

These are the next steps, in order. Raise them one at a time. Do not begin any without the
owner's approval.

1. Path step 5, the first in the order under Decided: change what the owner approves to the
   proposal and the observed behaviour.
2. In project-kit, with the owner's approval and from a session there: delete the vibe-kit
   entry under In flight in its `NEXT.md`, which says to do so once this file exists. Its
   three commits are pushed: on 2026-11-20 at 00:45 UTC its `origin/main` was `83b8a27`,
   0 behind and 0 ahead after a fetch.

## Committed, pushed, released: three separate questions

As of 2026-11-20 00:48 UTC. Re-check with the block at the top of this file.

**Uncommitted.** Nothing, apart from this update.

**Unpushed.** Nothing. GitHub `main` was `daacda6`, 0 behind and 0 ahead, at 00:48 UTC.
This snapshot goes stale with the next commit. The `rev-list` line at the top answers it.

**Unreleased.** Nothing released.

## Open, not blocking

- A license. project-kit is MIT-0. vibe-kit has none yet.
- Whether vibe-kit keeps project-kit's layout of a README, `template/` and `docs/`.
