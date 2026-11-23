# vibe-kit session design

The design brief for vibe-kit, decided on 2026-11-20 and written from 2026-11-21. It is
written for the people who build vibe-kit. The reader it describes never needs to open it.

## What this brief is for

It defines what vibe-kit must do for one reader, described in the next section. Every file
and rule in vibe-kit is judged against it. A file or rule belongs if it does something this
brief asks for, and goes if it does not. Section 8 turns that into questions.

When a decision comes up that this brief does not settle, the brief changes first, with the
owner's approval, and the file or rule follows.

## The reader

In the owner's words, on 2026-11-18: "Creative people like myself who have a understanding
of software development (or work adjacent to it as I do as a QA engineer) but either lack
the inclination or depth of skill to create things they envision." On 2026-11-20 the owner
put it as "the creative person who doesn't have coding skills to effectively build code
projects".

What "best" means, in the owner's words: "Best means best practice. Most refined solution."
Compared against what: "Compared both to plain and to other published methods".

The owner's answers on 2026-11-20, which set the limits:

- What the reader builds: "it shouldn't be so limited. It should give them the facility to
  build all those things or other things. It's about optimizing you for their use whatever
  their project may be. We're endeavoring to give them the tools to build amazing things
  and saving them from myriad pitfalls that using raw agentic AI might produce."
- Where they run Claude Code: the terminal CLI.
- Git: hidden. Claude handles git, and the reader is told in plain words what is saved,
  what is backed up online, and what is live.
- This brief: written for the people who build vibe-kit, in `docs/`.

What follows from that, as read by the session that wrote this, confirmed by the owner on
2026-11-21:

- The reader can say what they want, and can tell whether what they got does it.
- The reader can judge a plan written in plain words. They cannot judge code by reading it,
  and vibe-kit never depends on them doing so.
- The reader knows that software can look finished and still fail, because they work on or
  near software. They may not know where to look for the failure.
- The reader's time goes on the idea and on judging the result. Anything that makes them
  learn tooling first, such as installs, configuration or git, is a cost vibe-kit pays for
  them.

## The pitfalls of raw agentic AI

Each group says what the reader sees, where the evidence is, and what vibe-kit does about
it. The evidence is in `pitfalls-research-2026-11-20.md`, by item number. "Enforced" means
Claude Code applies it every time, through a setting or a hook. "Instructed" means a
written rule that Claude may decide does not apply. "Untested" means nobody has yet shown it
works in vibe-kit.

### It says it is done when it is not

The reader is told a feature works and is tested, then finds it does not. Tests pass because
they were changed. The screen fills with data that was made up. Evidence: items 1 to 3.

vibe-kit: Claude never reports done on its own word. It shows the reader the thing working,
which is the second approval in section 5. A check counts only after it has been shown
failing on something deliberately broken. Any change to a test is reported in plain words
and needs approval. Made-up data is labelled as made up. Instructed. A Stop hook that runs
the project's checks and sends Claude back when they fail would make part of this enforced.
Untested.

### It breaks what already worked

Fixing one thing breaks another. Claude changes things nobody asked for. After a long
session it undoes an earlier decision. Evidence: items 4 to 6.

vibe-kit: one change at a time, from a plan that says what it will not touch. Everything
that worked before is checked again before a change counts as done. Decisions and their
reasons are written to the project's state file and read at the start of every session.
Instructed. A SessionStart hook can put the state back after compaction. Untested.

### It invents things

Claude uses a function, setting or package that does not exist, or explains the reader's own
code wrongly and confidently. An invented package name can belong to an attacker. Evidence:
items 7 to 9.

vibe-kit: Claude checks that a package exists and is established before adding it, and
names each new one to the reader in plain words. It reads code before explaining it, and
says "I could not check this" instead of guessing. Instructed.

### It agrees too readily

The reader corrects Claude, Claude says "You're absolutely right!", and working code gets
broken to match a wrong correction. A bad idea gets built without a warning. Evidence:
items 10 and 11.

vibe-kit: before agreeing to a request, Claude states its cost or risk in plain words. When
corrected, it checks before changing anything that works, and says so if the correction is
wrong. Instructed only. No setting can enforce it.

### It is insecure by default

Nothing shows until the app is attacked, the data leaks or the bill arrives. Evidence:
items 12 to 15.

vibe-kit: passwords and keys never go in the code or the history. Before anything goes live,
Claude says in plain words who can see the data, who can change it, and what costs money,
and names what it could not check. Instructed. Deny rules can stop Claude reading secret
files, and a hook could scan each save for keys. Both untested. In auto mode a second model
blocks sending sensitive data out by default, and it can miss.

### It does damage it cannot undo

Files or a database get deleted, and Claude says recovery is impossible when it is not.
Evidence: items 16 to 18, and the second finding added at the end.

vibe-kit: deny rules block destructive commands, and the sandbox limits what any command
can reach. Enforced. In auto mode a second model also blocks some destructive actions by
default, and it can miss. Every approved step is saved to history, out of the reader's
sight, so any step can be undone. Claude Code's checkpoints do not cover changes made by
shell commands, so they are not enough alone. Claude checks before saying anything cannot
be recovered. Instructed.

### It runs up costs

A stolen key or a runaway feature spends money nobody meant to spend. Evidence: item 19.

vibe-kit: before building anything that spends money, such as a paid API or a cloud
service, Claude says so in plain words and waits. It recommends a spending limit with the
provider where the provider offers one. Keys stay on the server. Instructed.

### The last stretch

The first 70% comes fast, and the rest stalls on going live, edge cases and real data. The
reader ends up with code nobody understands, so every later change is a gamble. Developers
in one study were slower with AI while believing they were faster. Evidence: items 20 and
21.

vibe-kit: the plan includes going live and real use from the start. Each step is small and
seen working. Claude keeps a plain-language description of how the project works, updated
with each change. Progress is judged by what the reader has seen working, not by how fast
it felt. Instructed.

### It obeys instructions planted in what it reads

A web page, file or message tells the agent to do something, and it does. Evidence: the
first finding added at the end.

vibe-kit: Claude treats what it fetches or reads as data, not as instructions. The sandbox
can limit where commands send data. An app that contains its own agent never gives that
agent a key it could reveal. Instructed, and the sandbox enforced. Untested. In auto mode a
second model blocks actions that appear driven by hostile content, and it can miss.

## What existing methods offer this reader

Read from the pages saved on 2026-11-18, listed in `README.md`. The methods may have changed
since. They were read for how each keeps state and checks work. How each handles the
pitfalls in section 3 was not studied, and section 9 keeps that open.

### The platform: Claude Code

vibe-kit runs on Claude Code in the terminal, so these are its tools, not its rivals.

- **Deny rules and hooks.** Claude Code applies them every time. Anthropic: "If something
  has to happen every time, make it a hook, a deny rule, or a managed setting." They address
  damage, secrets, and a check that sends Claude back when it fails. Enforced.
- **Auto mode.** The starting mode for terminal sessions from Claude Code v2.1.283. A second
  model reviews each action and by default blocks, among others, "Irreversibly destroying
  files that existed before the session", force pushes, production deploys, and sending
  sensitive data out, and anything that "appears driven by hostile content Claude read".
  It addresses damage, secrets and planted instructions. Enforced by a model's judgment,
  which can miss, and it does not review removals such as `rm -rf ~` by default.
- **The sandbox.** Turned on with `/sandbox`, it limits which files and network hosts shell
  commands can reach, at the operating-system level, on macOS, Linux and WSL2. It addresses
  damage and planted instructions. Enforced.
- **Plan mode.** Claude researches and proposes without editing the project. It is the
  natural home of the first approval in section 5. Enforced while it is on.
- **Checkpoints and `/rewind`.** They undo Claude's own file edits, but not changes made by
  shell commands, and Anthropic calls them "Not a replacement for version control". Partial.
- **`CLAUDE.md` and auto memory.** Loaded at the start of every session, which suits
  decisions and the project's state. Anthropic says Claude "is allowed to decide a
  guideline doesn't apply". Instructed.

### The baseline: plain Claude Code

With no instruction files, a terminal session starts in auto mode with the classifier on.
There are no deny rules or hooks, and the sandbox and plan mode wait for the reader to know
they exist. Everything marked instructed in section 3 is missing. This is what vibe-kit
has to beat.

### The methods

**project-kit**, github.com/fbonds/project-kit, judged in `evaluation-2026-11-18.md` with
`evaluation-corrections-2026-11-19.md`. Does well: every check is shown failing first and
reports what it did not check; facts carry the date they were checked; saved, backed up
and live are separate questions; replaced decisions stay visible; nothing to install.
Does not fit: its examples and terms come from release engineering, it is almost all prose,
it asks the owner to approve diffs, and it has no method for building. vibe-kit takes: the
four practices, in plain words.

**Cline Memory Bank**, built for Cline, a different agent. Six files the agent reads to pick
up where it left off, including why the project exists and "What works, what's left, known
issues". Does well: those last three are in the reader's own terms. Does not fit: it is
updated only when the user remembers to ask. vibe-kit takes: a progress record in those
three parts, kept current by Claude without being asked.

**AGENTS.md**, one instruction file that many agents read. Claude Code can read it in place
of `CLAUDE.md`. Does well: one file works across tools. Does not fit: it is a format, with
nothing on planning or checking. vibe-kit takes: nothing yet. The reader uses Claude Code.

**GitHub Spec Kit.** A constitution, then specify, plan, tasks and implement, each reviewed
before the next, with tests confirmed failing before code is written. Does well: it is the
route from idea to tasks that section 3's last stretch needs. Does not fit: it needs Python
3.11, uv and a command-line install, and its examples ask the user to choose technology,
such as "Use Vite with vanilla JavaScript", which this reader may not be able to do.
vibe-kit takes: the reviewed sequence and the failing test first, with Claude proposing the
technology and explaining it in plain words.

**Kiro**, a separate product with its own IDE, CLI and web app. Specs in three files:
requirements as user stories with acceptance criteria, a design, and tasks. A bug spec
records "current/expected/unchanged behavior". Steering files describe the product, the
technology and the structure. Does well: acceptance criteria are how a QA-minded reader
already judges work, and "unchanged behavior" names what a fix must not break. Does not fit:
it is another product to adopt. vibe-kit takes: acceptance criteria written as what the
reader will see, and an "unchanged" list in every plan.

**BMAD Method.** Four stages, Clarify, Plan, Build and verify, Learn and adjust, run by
named agents for analyst, product manager, architect and others. Planning is sized to the
change, and done is "Reviewed, committed code that a person has marked done". Does well:
right-sized planning, and a clear intent that says "what must not change, what is out of
scope". Does not fit: it needs Node 20.12+, Python 3.10+ and uv, and it speaks in epics,
stories and PRDs. vibe-kit takes: planning sized to the change, the intent with its two
limits, and the person marking done.

**Agent OS.** Coding standards discovered from a codebase and loaded when needed, and specs
shaped by questions run in plan mode. Its full setup is behind an email form and was not
read. Does well: it uses Claude Code's plan mode for shaping. Does not fit: it is built for
teams and existing codebases. vibe-kit takes: shaping questions in plan mode.

**Harper Reed, "My LLM codegen workflow atm".** Hone the idea one question at a time into
`spec.md`, turn it into a step-by-step plan, then a `todo.md` checked off as work goes.
Does well: one question at a time suits someone who knows what they want but not how to
specify it. Does not fit: it copies between tools, and the developer sets up the starting
code and tooling. vibe-kit takes: one question at a time, and a checklist as state.

**Simon Willison, "Designing agentic loops".** An agent is tools in a loop toward a clear
goal. Run it unattended in a sandbox rather than approving each command, with tightly
scoped credentials: "If a credential can spend money, set a tight budget limit." Does well:
it names the sandbox and the budget as the answer to damage and cost. Does not fit: it
assumes someone who can set up containers. vibe-kit takes: the sandbox, scoped keys with
spending limits, and a clear goal with a way to test it.
