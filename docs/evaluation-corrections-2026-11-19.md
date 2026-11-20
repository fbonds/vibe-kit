# Corrections to the evaluation of 2026-11-18

Checked 2026-11-19 against the source pages saved in `sources-2026-11-18/`, not against the
live sites. `evaluation-2026-11-18.md` is a dated record and is not rewritten. Each item
below gives its line there, what it says, and what the saved pages show.

## Line 17: the count of methods

It says "eight published methods" and lists nine sources. The count holds only if
Anthropic's documentation is counted apart from the eight, as the handoff counts it. Lines
32 and 141 say "nine".

## Lines 51 to 55: dated facts

It says "The others treat their files as current." Anthropic's memory page, `mem.txt:564`,
says that when Claude writes a memory file with YAML frontmatter, Claude Code records the
write time in a `modified` field, and "The timestamp shows how current the fact is, both to
you and to Claude when it reads the memory back." The evaluation cites that page and does
not mention this.

What holds: Anthropic dates a memory file by when it was written. No saved source dates
each fact and pairs it with the command that re-checks it.

## Lines 57 to 59: replaced decisions

It says Spec Kit's "immutable" constitution "stops change rather than recording it". The
same page, `sdd.txt:391-401`, has an amendment process that requires "Explicit
documentation of the rationale for change", and says "The constitution shows its own
evolution with dated amendments." Cline's `progress.md` has a heading "Evolution of project
decisions", `cline.txt:102`.

What holds: no saved source keeps a reversed decision in place with a line naming what
replaced it. Spec Kit's dated amendments are the nearest, and the difference is one of
degree.

## Lines 61 to 63: what adopting each one needs

Spec Kit needs uv as well as Python 3.11, `speckit.txt:73`. BMAD needs uv as well as Node
and Python, `bmad.txt:18`. Kiro is not only an IDE. Its specs run in the IDE, CLI, Web and
Mobile, `kiro.txt:86`. The point stands: each needs more than copying files.

## Line 87: where the examples are

It lists "a lockfile guard, a third-party notices file" among the examples the template
asks the owner to replace. Both are in project-kit's `README.md`, lines 65 to 69 at
`23edcce`, and not in `template/`. The template's examples are linked or installed
binaries, symlinks, registries, dashboards and caches. The gap stands.
