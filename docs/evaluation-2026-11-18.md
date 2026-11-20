# Evaluation of project-kit, 2026-11-18

This is the evaluation vibe-kit starts from. It judges project-kit as it stood at commit
`23edcce` on GitHub, read on 2026-11-18, against the owner's goal: the best practice, the
most refined solution, for solo vibe coding with Claude Code. It is a dated record. A later
change of view gets a new file, and this one is not rewritten.

## The reader

The kit is judged for one reader: a creative person who understands software development,
or works next to it, for example as a QA engineer, and who lacks the inclination or the
depth of skill to build what they imagine without help. That reader can describe what they
want and can tell whether it works. They may not read a diff with confidence.

## What it was compared against

Plain Claude Code with no instruction files, and eight published methods. Every source was
opened on 2026-11-18, and the quotes below were taken from the page text saved that day.

- Anthropic's Claude Code documentation: best practices, memory, permission modes and the
  hooks guide, at code.claude.com/docs/en/.
- Cline Memory Bank, docs.cline.bot/prompting/cline-memory-bank.
- GitHub Spec Kit, github.com/github/spec-kit, its README and `spec-driven.md`.
- Kiro specs, steering and hooks, kiro.dev/docs/.
- AGENTS.md, agents.md.
- BMAD Method, github.com/bmad-code-org/BMAD-METHOD and docs.bmad-method.org.
- Agent OS, buildermethods.com/agent-os. Its full setup instructions sit behind an email
  form and were not read.
- Harper Reed, "My LLM codegen workflow atm", harper.blog, 2025-02-16.
- Simon Willison, "Designing agentic loops", simonwillison.net, 2025-09-30.

None of the nine offers measured evidence that it works. The only numbers are adoption
figures.

## What project-kit does that the others do not

**Every check reports what it did not check.** The report shape in `template/CLAUDE.md`
has a line for what was broken to show the check can fail, the path used, the artifact
looked at, and what was not checked. Anthropic's page asks for "*evidence*: the command it
ran and its output, or the screenshot", which matches the first line only. Spec Kit
requires unit tests to be "confirmed to FAIL (Red phase)" before implementation. Only
project-kit applies the same demand to every check, including build guards, release checks
and checks on published documents, and only project-kit asks for a list of what went
unchecked. For a QA-minded reader this is the strongest part of the kit, because it is how
that reader already thinks about a test.

**Committed, pushed and released are three questions.** No other source separates them.
For a reader who cannot inspect a deploy by hand, this is how they learn that a fix is
still on their laptop.

**Facts are dated and come with the commands that re-check them.** The others treat their
files as current. Cline says to "update memory bank" when asked. Anthropic's
`/doctor prompt-audit` finds references "to files or commands that don't exist", which
catches a broken pointer and not a stale fact. Only project-kit says the state file
records what was true when checked and tells the session to re-check before acting.

**Decisions are replaced, not rewritten.** The Decided section keeps a reversed decision
with a line saying what replaced it. Spec Kit calls its constitution "immutable", which
stops change rather than recording it.

**It costs nothing to adopt.** Three Markdown files, 3,691 words, 380 lines, and an
optional settings file. Spec Kit needs Python 3.11 and a CLI. BMAD needs Node and Python.
Kiro is an IDE.

## Gaps, most important first

**1. It covers keeping state and checking work. It does not cover building.** Nothing in
the kit takes an idea to a specification, a plan and a list of tasks, and nothing says how
tests should be written or run. Spec Kit, Kiro, BMAD, Agent OS and Harper Reed's workflow
all begin there, and that is where this reader needs the most help. The reader can say what
they want. The kit gives the agent no method for turning that into something built in
steps the reader can judge.

**2. Almost all of it is prose that Claude may decide does not apply.** Anthropic's
best-practices page says "`CLAUDE.md` is for guidelines, and Claude is allowed to decide a
guideline doesn't apply", and "If something has to happen every time, make it a hook, a
deny rule, or a managed setting." It also says a chat instruction like
"don't push" "can get lost when the conversation compacts". The kit's optional settings
file has six deny rules and one SessionStart hook. Both daily habits, "Read CLAUDE.md and
comply" and "save state", depend on the owner remembering to type them. Claude Code has
hooks for compaction (`PreCompact`, `PostCompact`), for the end of a turn (`Stop`, which can
send Claude back to work by exiting with code 2) and for the end of a session
(`SessionEnd`). The kit uses none of them. Whether each can carry part of the habits is not
yet tested.

**3. The examples come from one project's release engineering.** Linked binaries, a
lockfile guard, a third-party notices file, symlinks and registries. The template asks the
owner to replace them, but this reader may not recognise the failure in any of them on day
one. The Traps questions are all about publishing: dashboards, listings, registries,
caches. None asks about the failures a new builder meets first, such as a feature that
works only with the developer's data, or a fix that passes its own test and breaks
something else.

**4. Rule 10 asks for something the README says the reader will not need to do.** Rule 10
says to show the diff and wait for approval. The README says "You can audit your agent
without reading a line of code." For a reader who does not read diffs with confidence, an
approval of a diff is a formality. What this reader can judge is the proposal before the
work and the behaviour after it.

**5. There is no measured evidence.** The README's Results are the owner's account of
runs in private repositories. The test harness that would measure the kit is queued in
github.com/fbonds/project-kit-harness and not built. None of the nine has evidence either,
so measured results would be the clearest way for a kit to show it is better rather than
say so.

**6. The state file has no size limit.** project-kit's own `NEXT.md` was 4,758 words on
2026-11-18, more than the three template files together. Anthropic loads only "The first
200 lines of `MEMORY.md`, or the first 25KB, whichever comes first", and its
best-practices page says "Only write down what Claude can't find by reading the repo." Much
of a large `NEXT.md` is history the git log already holds.

**7. It does not use what Claude Code already provides.** Plan mode "tells Claude to
research and propose changes without making them", which is rule 4 enforced by the tool
rather than by prose. Checkpoints and `/rewind` make a wrong attempt cheap to undo.
Sandboxing limits what a command can reach. Auto memory exists, and the kit treats it only
as something that goes stale. Willison argues that approving every command "dramatically
reduces their effectiveness" and that the answer is a sandbox. The kit takes no position on
any of these.

## The path

In this order, because each step tells the next one what to build.

1. **Measure.** Build the harness, or adopt project-kit's queued design for it, so that
   every later change can be shown to help rather than assumed to. Write the expected
   results down before the first run.
2. **Add a light build loop.** Idea, short specification, plan, tasks, each task with the
   check that will show it done. Keep it to files a reader can follow, and reuse
   Claude Code's plan mode for the approval step.
3. **Move the rules that must always hold into the harness.** Deny rules, and hooks where a
   test shows they work. Keep in prose only what Claude may reasonably judge.
4. **Rewrite the examples and Traps questions for this reader.** Keep project-kit's
   examples as one worked case, and add questions about the failures a new builder meets.
5. **Change what the owner approves.** Approve the proposal and the observed behaviour.
   Make the diff available, not required.
6. **Set a size budget for the state file**, and say what moves out of it when it is
   exceeded.

## What this evaluation cannot establish

It is one reviewer's reading of the files and of nine sources, with no runs of anything. It
cannot show that any gap above costs a user anything, or that any step on the path would
help. The reviewer was a Claude session working for the kit's author, so it is not
independent. The comparison covers what each source says, not how well it works in use.
The Agent OS setup and the Kiro memory page were not read.
