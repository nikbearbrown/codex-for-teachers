# codex-for-teachers-a-practitioners-guide
## Full TOC Draft — All Phase Outputs Compiled

**Working title:** Codex for Teachers: A Practitioner's Guide
**Series:** Practitioner Guides for the AI Classroom · Bear Brown & Company
**Author:** Humanitarians AI · bear@bearbrown.co · Bear Brown, LLC
**Practitioner voice:** Seth Brown
**Document:** Full TOC Draft — compiled from all phase outputs
**Version:** 1.0
**Status:** Pre-production — simulation domain to be confirmed (see OQ-1)

---

## Document structure

1. Book Concept and Thesis
2. Learner Profile
3. Book Type and Deployment Specification
4. Field Positioning
5. Three-Act Learning Arc
6. Prerequisite Map
7. Build Arc and Terminal Deliverables
8. Chapter-by-Chapter TOC
9. Chapter Anatomy Template
10. Case Study Strategy
11. Hard Topics, Contested Claims, Aging Risk
12. Market Positioning
13. Feature List
14. Out of Scope
15. Adoption Risk Register
16. Open Questions

---

# PART 1 — BOOK CONCEPT AND THESIS

## Book concept summary

> This book teaches **K-12 CS teachers to conduct Codex through
> real classroom builds** — a class website, a grading tool, an
> interactive simulation — **and then to teach that same discipline
> to their students**, using the conducting framework they just
> practiced on their own work. It fills the gap left by generic
> AI-tools-for-teachers resources (which teach teachers to use
> ChatGPT as a faster lesson-plan generator) and developer-facing
> Codex courses (which target engineers, not educators). It succeeds
> when **the teacher can sit next to a student who is mid-build and
> say exactly where the line is, because they have drawn it
> themselves**.

**One-sentence logline:**
The teacher who builds with Codex and the teacher who teaches
students to build with Codex are the same person practicing the
same discipline — you cannot teach the line until you have drawn
it yourself.

## Central thesis

"This book argues that the teacher-as-builder and the teacher-as-
instructor are the same discipline applied twice — that a K-12 CS
teacher who conducts Codex through their own classroom builds using
explicit handoff conditions, AGENTS.md, Ask Mode / Code Mode gates,
and Best-of-N verification is practicing exactly the discipline they
are trying to instill in their students, and this matters because
a teacher who has never drawn the line cannot teach it."

## Thesis test

- ACT ONE: The teacher builds their first class website page using
  the conducting discipline, then designs a classroom activity
  using the same concept. Building and teaching in the same
  chapter. ✓
- ACT TWO: The teacher builds a grading tool — higher stakes,
  every supervisory capacity exercised, AGENTS.md and Best-of-N
  introduced — and designs classroom activities at each step. ✓
- ACT THREE: The teacher builds an interactive classroom simulation
  and deploys it in their actual classroom. The discipline is
  demonstrated, not described. ✓

**Thesis test: PASS**

---

# PART 2 — LEARNER PROFILE

## Primary reader

A K-12 CS teacher, 2026. Ten-plus years in the classroom. Three
to four years teaching CS. Has tried ChatGPT for lesson plans.
Watches students use AI in ways that make them uneasy. Tired and
committed simultaneously. Has 30 minutes on Monday night.

**CSTA 2025 data portrait:** 74% of CS teachers have 10+ years
of classroom experience. Only 26% have taught CS for 10+ years.
96% participated in professional development in the past year.
Almost half did fewer than 11 hours of PD.

## Prior knowledge assumed

- ChatGPT or basic AI prompting
- Google Classroom or similar LMS
- Some coding experience
- Comfortable running a terminal command if given exact syntax

## Prior knowledge NOT assumed

- Codex CLI or ChatGPT's Codex interface
- AGENTS.md
- Ask Mode vs. Code Mode distinction
- Best-of-N
- The five supervisory capacities by name
- The conducting framework
- Software Design Documents or minimum viable specs

## Prior misconceptions

1. "Codex is just a better version of ChatGPT's chat interface" —
   it is an agentic system that plans multi-step tasks, executes
   shell commands, reads and writes files autonomously; the
   autonomy requires a different discipline
2. "I need to be a developer to use Codex" — the teacher-as-
   builder pattern requires specification writing and verification,
   not deep coding ability
3. "AI for teachers means faster lesson plans" — this book teaches
   AI for teachers as a build discipline, not content generation
4. "My students know more than me, so I can't teach this" — the
   teacher who has built with Codex knows something the technically
   fluent student does not: what the discipline costs when skipped

## Motivation type

**Primary:** Professional — the teacher needs tools that work
on Tuesday.
**Secondary:** Intellectual — the teacher who has watched the
homework/quiz gap wants the repair kit.

## Prerequisite map

| Prerequisite | Safe to assume? | If not: where addressed |
|---|---|---|
| Basic AI prompting | Yes | — |
| Terminal basics | Probably | Ch 1 first session walkthrough |
| Codex CLI / interface | No | Ch 1 installation |
| AGENTS.md concept | No | Ch 2 (full chapter) |
| Ask Mode vs. Code Mode | No | Ch 3 (full chapter) |
| Best-of-N | No | Ch 5 (introduced) |
| Five supervisory capacities | No | Ch 5 (full chapter) |
| Students book concepts | No | Referenced; not required |

---

# PART 3 — BOOK TYPE AND DEPLOYMENT SPECIFICATION

## Book type

**PRIMARY TYPE:** Practitioner handbook with course-textbook
bones. The teacher reads it cover to cover once, then consults
it chapter by chapter during builds and classroom activity design.

## Deployment specification

**Primary adoption context:**
Self-directed K-12 CS teacher finding it through professional
development, CSTA community, or recommendation.

**Secondary adoption context:**
University teacher training programs and CS education PD providers
who need a practitioner text with real builds.

**Companion relationship:**
`codex-for-students-a-practitioners-guide` ($1 Kindle) is the
student companion. The teachers book references it explicitly.
Chapter 13 maps the students book to classroom activities.

**What the book is NOT designed for:**
Generic AI ethics PD; teachers who want to ban AI use; developer
audiences; university CS education research seminars.

---

# PART 4 — FIELD POSITIONING

## The positioning statement — consolidated

- AI-for-teachers resources teach teachers to use ChatGPT as a
  content generator. This book teaches teachers to conduct Codex
  through real builds.
- Developer-facing Codex courses (Vanderbilt/Coursera) target
  engineers. This book targets educators.
- No practitioner handbook yet exists for the K-12 CS teacher who
  is both builder and instructor in the Codex ecosystem.

## Positioning statements by comparable

**vs. ChatGPT-for-teachers resources:**
"Unlike AI-for-teachers programs, which teach educators to generate
content with ChatGPT, this book teaches K-12 CS teachers to conduct
Codex through real classroom builds — using the Ask Mode / Code Mode
gate and the conducting discipline that prevents the most common
AI-assisted development failures."

**vs. the students book:**
"This book is the teacher's half of a two-book pair. The students
book teaches the conducting discipline to students. This book teaches
the same discipline to the teachers who assign it — and adds the
classroom activity design that makes the students book teachable."

## Research validation

The CSTA 2025 CS Teacher Landscape report: experienced educators,
early in CS journey, wanting more than 11 hours of PD per year.

The OpenAI internal use doc provides the teacher-as-builder
validation: "Teachers are now building tools with Codex they
always wanted but could never afford." The Ask Mode → Code Mode
discipline is described explicitly: "For large changes, start by
prompting Codex for an implementation plan using Ask Mode."

---

# PART 5 — THREE-ACT LEARNING ARC

## The arc statement

This book takes the K-12 CS teacher from **their first Codex
session** to **deploying an interactive classroom simulation they
built themselves** — first by establishing the conducting discipline
on a low-stakes class website, then by practicing it on a grading
tool that immediately saves time, then by applying it at full
complexity to build something their students learn from directly.

## The interleaved structure

Every chapter covers one conducting concept and applies it in both
directions simultaneously: the teacher's own build, then a
classroom activity using the same concept. The teacher who reads
a chapter on handoff conditions and immediately applies it in both
directions never has to translate the concept.

## The pebble-in-the-pond opening

Chapter 1 gives the teacher their first Codex session in Ask Mode
— they interrogate a project folder before touching anything.
The pebble: one web page built with explicit handoff conditions
in Chapter 3. Everything that follows expands the pond.

## Act One — Establish (Chapters 0–4)

**Transition condition:** The teacher has built one deployable web
page using AGENTS.md, specification prompts, and explicit handoff
conditions. They have designed one classroom activity using each
concept. They are ready for a build that costs something if it
goes wrong.

## Act Two — Build (Chapters 5–9)

**The build:** A grading tool. Highest stakes, every supervisory
capacity exercised.
**Act Two crisis:** Chapter 8 — the dangerous middle. Codex
produces grading feedback that passes every handoff condition
and is still pedagogically wrong.
**Transition condition:** The teacher has experienced a dangerous
middle moment on a build that mattered.

## Bridge chapter

Seth's voice. The moment builds stopped being about productivity
and started being about what's possible in the classroom.

## Act Three — Apply (Chapters 10–14)

**The build:** An interactive classroom simulation.
**Terminal deliverable:** Simulation deployed in the teacher's
actual classroom, with a post-build document and a classroom
activity where students use it as the starting point for their
own build.

---

# PART 6 — PREREQUISITE MAP

## Prerequisite chain by chapter

| Chapter | Prerequisites | Load-bearing? |
|---|---|---|
| Ch 0 (Introduction) | None | No |
| Ch 1 (First Codex Session) | None | Yes — establishes agentic loop |
| Ch 2 (AGENTS.md) | Ch 1 | Yes — governs all subsequent builds |
| Ch 3 (Specifications + Ask/Code gate) | Ch 1–2 | Yes — workflow used throughout |
| Ch 4 (Handoff Conditions) | Ch 3 | Yes — gate between all build steps |
| Ch 5 (Five Capacities) | Ch 1–4 | Yes — labels used in all subsequent chapters |
| Ch 6 (Best-of-N) | Ch 5 | No — additive verification tool |
| Ch 7 (Grading Tool Build) | Ch 2–6 | Yes — applies all prior concepts |
| Ch 8 (Dangerous Middle) | Ch 3–7 | No — crisis chapter |
| Ch 9 (Task Queue) | Ch 5–6 | No — context management |
| Bridge | Ch 5–9 | No — motivational transition |
| Ch 10 (Three-File System) | Ch 2, Ch 3 | Yes — governs simulation build |
| Ch 11 (Simulation Build) | Ch 10, Ch 5 | Yes — full build arc |
| Ch 12 (Deploying in Class) | Ch 11 | No — deployment and revision |
| Ch 13 (Teaching the Discipline) | All prior | No — synthesis |
| Ch 14 (Post-Build Document) | All prior | No — terminal deliverable |

---

# PART 7 — BUILD ARC AND TERMINAL DELIVERABLES

## The three build tiers

| Tier | Chapters | Teacher builds | Classroom activity | Terminal artifact |
|---|---|---|---|---|
| Foundations | 1–4 | Class website (one page) | Observation and specification exercises | One deployable web page |
| Core | 5–9 | Grading tool | Rubric and feedback tool activities | Working grading tool with Best-of-N verification |
| Application | 10–14 | Interactive simulation | Simulation-based learning activities | Simulation deployed in class |

## Terminal deliverable specification

**The interactive classroom simulation, deployed:**

Required components:
1. Three governing files complete before build begins:
   AGENTS.md (technical constitution), DESIGN.md (visual
   constitution), PROJECT.md (intent layer + technical state)
2. Ask Mode plan reviewed and approved before Code Mode begins
3. Build execution log (specification per step, handoff
   condition evaluation, supervisory capacity label)
4. Student-facing verification pass
5. Revision build based on classroom observation
6. Post-build document (five sections)

**Post-build document — five sections:**
1. What I built (one paragraph, plain language)
2. What I delegated to Codex and why
3. What I kept for myself and why
4. What I learned that I didn't know before the build
5. What I would do differently

---

# PART 8 — CHAPTER-BY-CHAPTER TOC

---

## ACT ONE — ESTABLISH
*Chapters 0–4: The conducting discipline on a class website*

---

### Chapter 0 — Introduction: The Line

**One-line:** There is a line between what Codex executes and
what only you can do. This book teaches you to draw it — by
building real things, then teaching students to draw it
themselves.

**Learning outcomes:**
1. (Understand) Explain the difference between prompting Codex
   and conducting a build with Codex.
2. (Understand) Describe what the interleaved structure means
   for how to read this book.
3. (Remember) Identify the three builds that form the book's arc.

**Opening:** Seth, eighteen months after the students book.
Describing the first time he built something real with Codex and
understood why the discipline matters from the inside. The
teacher meets him here — not as a student to manage, but as
someone who has done what the teacher is about to do.

<!-- → [DIAGRAM: The book's arc as three build tiers on a
timeline. Tier 1: class website (Act One). Tier 2: grading tool
(Act Two). Tier 3: interactive simulation (Act Three). Each tier
labeled with the conducting concept it introduces. Editorial
style. No color.] -->

**Core content:**
- What Seth learned that the students book couldn't teach him
- The two tracks in every chapter: your build, your classroom
- How to use the students book alongside this one
- What the teacher will have built and taught by Chapter 14
- Dictation shortcut: Mac OS System Settings → Accessibility
  → Dictation; Windows: Win+H. The teacher who has 30 minutes
  on Monday night benefits from speaking prompts rather than
  typing them.

**Assessable exercises:**
1. (Remember) Name the three builds in this book's arc and the
   conducting concept each one introduces.
2. (Understand) What is the difference between a teacher who
   uses Codex to generate lesson plans and a teacher who
   conducts Codex through a classroom build?
3. (Understand) Read Chapter 0 of the students book. Name one
   concept Seth learns that you will teach using your own build
   experience.

**Wayback Machine:** 🕰️ **John Dewey** (1859–1952) — philosopher
of education who argued that the teacher learns by teaching —
that making the discipline explicit for students deepens the
teacher's own understanding. His concept of "reflective
practice" is the interleaved structure in theoretical form.

**Bridge:** The reader knows the arc. Chapter 1 puts them in
the terminal for the first time.

---

### Chapter 1 — Your First Codex Session: This Is Not ChatGPT

**One-line:** Codex plans multi-step tasks, executes shell
commands, reads and writes files, and iterates autonomously.
That autonomy is the feature — and the reason you need a
discipline before you start.

**Learning outcomes:**
1. (Understand) Explain the agentic loop and how it differs
   from a chat conversation.
2. (Apply) Set up Codex and run a first Ask Mode session in
   a project directory.
3. (Understand) Explain why Ask Mode interrogation must precede
   Code Mode execution.

**Opening:** The teacher opens Codex for the first time. They
type a request. Codex starts reading files, proposing changes,
running commands. Something about this feels different from
ChatGPT. This chapter names why.

<!-- → [DIAGRAM: The agentic loop — Gather context → Plan →
Execute → Verify → Repeat. Ask Mode: gather and plan only.
Code Mode: execute and verify. Human interruption point at
every phase. Editorial style. No color.] -->

**Core content:**
- The agentic loop: how Codex plans and executes autonomously
- Ask Mode vs. Code Mode: the fundamental distinction.
  Ask Mode: Codex reads, questions, and plans — no execution.
  Code Mode: Codex executes. Nothing goes to Code Mode without
  an Ask Mode plan reviewed and approved.
- From OpenAI: "If you're just showing it to someone for the
  first time, start with Ask Mode. Don't start by using Code
  Mode. Just start by asking questions about the codebase."
- Questions before execution: spend the first session in Ask
  Mode only. Ask Codex what it sees. Ask it to describe the
  project. Ask what would need to change to support a feature.
  Do not ask it to build anything yet.
- Setting up Codex: ChatGPT Plus/Pro subscription, Codex CLI
  (`npm install -g @openai/codex`), AGENTS.md initialization
- Permission modes: on-request (default), never, on-failure;
  sandbox policy: workspace-write restricts writes to the
  project directory

**Teacher build:** The teacher runs their first Ask Mode
session in a folder they will use for the class website. They
ask five questions about what Codex sees. They make no changes.

**Classroom activity:** Students run their first Codex session
in Ask Mode on a provided starter project, ask three questions
about the codebase, and document what Codex told them —
without making any changes.

**Assessable exercises:**
1. (Apply) Set up Codex. Run an Ask Mode session in a project
   folder. Ask Codex to describe what it sees. What did it
   notice that you didn't tell it?
2. (Analyze) Ask Codex to propose a plan (still in Ask Mode)
   for adding a new page to your class website. Read the plan.
   Do not approve it yet. What assumptions did it make that
   you need to correct?
3. (Evaluate) What is the single most important thing to do
   before switching from Ask Mode to Code Mode, and why?

**Links:** [platform.openai.com/docs](https://platform.openai.com/docs)

**Wayback Machine:** 🕰️ **Alan Kay** (born 1940) — computer
scientist who designed the Dynabook concept: a personal computer
as an instrument for learning, not just a tool for executing
pre-specified tasks. His argument that the computer should be
a medium for exploration, not just execution, is the Ask Mode
principle stated as a design philosophy.

**Bridge:** The reader has been in a Codex session. Chapter 2
gives them the file that makes every subsequent session smarter.

---

### Chapter 2 — AGENTS.md: Your Coding Constitution

**One-line:** AGENTS.md is the file Codex reads at the start of
every session. It is the difference between a Codex that knows
your project and a Codex that guesses.

**Learning outcomes:**
1. (Understand) Explain what AGENTS.md is, where it lives, and
   when Codex reads it.
2. (Apply) Write an AGENTS.md for a classroom build project.
3. (Analyze) Distinguish AGENTS.md content (always-on) from
   task-queue items (session-specific).

**Opening:** The teacher starts their second Codex session.
Codex has no memory of the first one. The teacher types the
same context they typed yesterday. This chapter ends that.

<!-- → [DIAGRAM: AGENTS.md in the session context — loaded at
session start, persists across the session. Without AGENTS.md:
Codex guesses. With AGENTS.md: Codex knows.] -->

**Core content:**
- What AGENTS.md is: a markdown file read at every session
  start — conventions, build commands, "never do X" rules
- File discovery: global (~/.codex/AGENTS.md) overrides
  first, then project root (./AGENTS.md), then subdirectories
  loaded on demand. From OpenAI: "Files closer to your current
  working directory take precedence."
- The five-element format: bash commands Codex can't guess,
  code style deviations, test runners, architectural decisions,
  environment quirks
- What NOT to include: anything Codex can figure out from
  code, standard conventions, anything that changes frequently
- Size discipline: keep it tight. From OpenAI: "Keep AGENTS.md
  short and human-readable. Bloated files cause Codex to ignore
  your actual instructions."
- AGENTS.md vs. task queue: persistent context vs. session
  work. AGENTS.md governs every session; task queue captures
  current-session work.
- Checking it works: if Codex makes the same mistake twice,
  add the fix to AGENTS.md

<!-- → [TABLE: AGENTS.md include/exclude — two columns. Include:
bash commands, code style deviations, test runners, architectural
decisions, quirks. Exclude: what Codex can figure out, standard
conventions, changing content. No color.] -->

**Teacher build:** The teacher writes their first AGENTS.md
for the class website project. Five entries. Checked into git.

**Classroom activity:** Students write an AGENTS.md for a
provided starter project. Class discussion: what did different
students include? What happened with and without it?

**Assessable exercises:**
1. (Apply) Write an AGENTS.md for your class website project.
2. (Analyze) Run Codex without your AGENTS.md, then with it,
   on the same task. Document three specific differences.
3. (Evaluate) After one week: which entries is Codex ignoring?
   Fix one.

**Wayback Machine:** 🕰️ **Donald Knuth** (born 1938) — inventor
of literate programming: writing the explanation of a program
alongside the code, so both the human and machine are served.
AGENTS.md is literate programming applied to AI collaboration.

**Bridge:** The reader has AGENTS.md. Chapter 3 teaches them
to use Ask Mode and Code Mode correctly — and why the gate
between them is the book's most important rule.

---

### Chapter 3 — From Prompts to Specifications: Ask Mode, Code Mode, and the First Build

**One-line:** Ask Mode is for planning. Code Mode is for
executing. Nothing goes to Code Mode without a reviewed plan.
The class website is the first build.

**Learning outcomes:**
1. (Apply) Use Ask Mode to generate an implementation plan
   and review it before switching to Code Mode.
2. (Apply) Write a five-element specification prompt for a
   Code Mode task.
3. (Analyze) Identify the difference between a prompt that
   delegates and a specification that conducts.

**Opening:** The pebble. The teacher builds their first page —
not the whole site, one page — using the Ask Mode → Code Mode
gate and a specification prompt. It works. They understand
exactly why.

<!-- → [DIAGRAM: The Ask Mode / Code Mode sequence. Ask Mode:
interrogate → plan → review → approve. Code Mode: specification
→ execute → verify. Gate between modes labeled: "plan reviewed
and approved." Editorial style.] -->

**Core content:**
- Ask Mode: Codex interrogates the codebase and proposes a
  plan. The teacher reviews. Corrections happen here, cheaply.
- Code Mode: Codex executes against the approved plan.
  One step at a time.
- The five elements of a specification prompt:
  1. The specific task (the one thing)
  2. The invariants (what must not change)
  3. The context (AGENTS.md sections governing this step)
  4. The output format (what done looks like)
  5. The negative constraint (what Codex must not do)
- Why Codex has no memory between sessions: every specification
  must contain the constraints that govern it
- Give Codex a way to verify its own work: test suites, linters,
  bash commands Codex can run. From OpenAI: "When Codex has
  some way to check its work — like run tests or screenshot
  the UI — it can iterate and get dramatically better results."

<!-- → [TABLE: Prompt vs. specification — two columns. Same
task described as a request (left) and a specification (right).
Five rows showing each element.] -->

**Teacher build:** The teacher builds the first page of their
class website. One page, one Ask Mode plan, one five-element
specification, review, Code Mode, verify.

**Classroom activity:** Students build their first page using
the Ask Mode → Code Mode gate. Peer review: did each student
review the Ask Mode plan before switching modes?

**Assessable exercises:**
1. (Apply) Use Ask Mode to plan the next page of your class
   website. Review the plan. Correct at least one thing before
   approving.
2. (Analyze) Compare your specification to a vague prompt on
   the same task. What did Codex do differently?
3. (Create) Design a classroom activity teaching the Ask Mode /
   Code Mode gate without using those terms.

**Wayback Machine:** 🕰️ **George Pólya** (1887–1985) —
mathematician whose *How to Solve It* (1945) formalized problem-
solving as a sequence: understand the problem, devise a plan,
carry out the plan, look back. The Ask Mode / Code Mode gate
is Pólya's sequence applied to AI-assisted development.

**Bridge:** The reader has built a page. Chapter 4 names the
gate between build steps: the handoff condition.

---

### Chapter 4 — Handoff Conditions: The Gate Between Steps

**One-line:** Not "looks good." A specific, testable condition
that must be true before the next step begins. This is what
separates conducting from approving.

**Learning outcomes:**
1. (Understand) Define a handoff condition and explain why
   "looks good" fails as one.
2. (Apply) Write handoff conditions for three steps in the
   class website build.
3. (Analyze) Identify the dangerous middle in a build step —
   where Codex's output requires specific verification not in
   the obvious checklist.

**Opening:** The teacher reviews Codex's output. It looks
correct. They approve it. Three days later: a broken link they
would have caught if they'd checked the one thing they forgot.

<!-- → [DIAGRAM: Handoff condition gate. Build step N →
[Handoff condition: specific, testable, binary] → Pass →
Step N+1. Fail: revert to step N, respecify, rerun.] -->

**Core content:**
- What a handoff condition is: specific, testable, binary
- Why "looks good" fails: it's a feeling, not a criterion
- The dangerous middle in a class website build
- Writing a handoff condition
- When output fails: revert to the previous state and respecify.
  Do not correct forward. Two failed corrections on the same
  step → start the task fresh with a better specification.
- From OpenAI: "If you've corrected Codex more than twice on
  the same issue, the context is cluttered. Start fresh with
  a more specific prompt."

<!-- → [TABLE: Strong vs. weak handoff conditions. Five examples.
Left: weak. Right: strong. No color.] -->

**Teacher build:** The teacher adds handoff conditions to every
step of the class website build. Finds one failure. Reverts.
Respecifies. Verifies again.

**Classroom activity:** Students add handoff conditions to a
provided build sequence. Test each other's conditions by
deliberately introducing the errors they're meant to catch.

**Assessable exercises:**
1. (Apply) Write handoff conditions for the next three steps
   in your class website build. Each must be specific and binary.
2. (Analyze) Identify one "dangerous middle" step in your
   build. Write the handoff condition that catches it.
3. (Create) Design a classroom exercise teaching handoff
   conditions using a non-coding build.

**Gate 1:** The teacher has built one deployable web page using
AGENTS.md, Ask Mode / Code Mode gate, specification prompts,
and explicit handoff conditions. They have designed one
classroom activity using each concept. Ready for Act Two.

**Wayback Machine:** 🕰️ **W. Edwards Deming** (1900–1993) —
statistician who argued that quality is built into a process
through explicit verification at every step, not inspected in
at the end. His Plan-Do-Check-Act cycle is the handoff condition
principle applied to manufacturing.

**Bridge:** Act Two begins. Chapter 5 names the five things
the teacher must never delegate.

---

## ACT TWO — BUILD
*Chapters 5–9: The grading tool*

---

### Chapter 5 — The Five Supervisory Capacities

**One-line:** These are the five things you do that Codex cannot.
Name them. Exercise them explicitly. Never delegate them.

**Learning outcomes:**
1. (Remember) Name and define the five supervisory capacities.
2. (Apply) Label the supervisory capacity required at each step
   of a provided grading tool build sequence.
3. (Analyze) Diagnose a build that went wrong by identifying
   which supervisory capacity was absent.

**Opening:** Seth mid-build on a grading tool. Something is
wrong with Codex's output. It seems fine, it produces feedback,
it's fast. He almost ships it. What capacity would have caught
this? Plausibility auditing.

<!-- → [DIAGRAM: Five supervisory capacities as a five-column
layout. Each: abbreviation, plain name, one-sentence definition,
example in grading context. No color.] -->

**Core content:**

**[PA] Plausibility Auditing:** Hearing the wrong note. In a
grading tool: "This feedback is technically accurate. But would
I say this to this student?" Claude produces fluent output;
the teacher catches what is pedagogically wrong.

**[PF] Problem Formulation:** Deciding what the build IS before
Codex sees it. Ask Mode interrogation is the tool. "Am I building
a tool that generates feedback, or one that flags patterns so
I can write the feedback myself?" Those are different builds.

**[TO] Tool Orchestration:** Choosing Ask Mode vs. Code Mode,
when to use Best-of-N, which task in what order. From OpenAI:
"For large changes, start with Ask Mode, then switch to Code
Mode" — the sequencing choice is the teacher's.

**[IJ] Interpretive Judgment:** Supplying meaning Codex cannot
supply. "This feedback is correct, but this student has been
struggling all semester. The tone needs to change."

**[EI] Executive Integration:** Holding the whole build toward
a single goal. "Three prompts ago we agreed the tool would never
generate a final grade. This output is generating grades. Stop."

<!-- → [TABLE: Five supervisory capacities — label, name, what
it catches, example failure when absent. Five rows.] -->

**Teacher build:** Complete grading tool build sequence analyzed
step by step, with each supervisory capacity labeled.

**Classroom activity:** Students analyze a provided Codex
transcript where one supervisory capacity is systematically
missing. Identify which one, trace consequences, propose
intervention. Cross-reference with students book Chapter 5.

**Assessable exercises:**
1. (Apply) Label the supervisory capacity at each step of your
   grading tool build plan.
2. (Analyze) A build transcript where plausibility auditing
   was absent. Identify the exact moment.
3. (Create) Design a classroom activity teaching the five
   capacities using a non-coding context.

**Wayback Machine:** 🕰️ **Norbert Wiener** (1894–1964) — founder
of cybernetics who formalized the feedback loop as the mechanism
by which a system maintains its goal in the face of disturbance.
The five supervisory capacities are the feedback mechanisms that
keep a Codex build aligned with the teacher's intent.

**Bridge:** Chapter 6 introduces Best-of-N — the verification
tool that makes supervisory judgment systematic.

---

### Chapter 6 — Best-of-N: The Verification Layer

**One-line:** When uncertain which Codex output is correct,
generate multiple responses and evaluate all of them. The
selection judgment is irreducibly human.

**Learning outcomes:**
1. (Understand) Explain what Best-of-N is and why the selection
   judgment cannot be delegated to Codex.
2. (Apply) Use Best-of-N on a grading tool task where two
   reasonable approaches exist.
3. (Analyze) Distinguish tasks where Best-of-N adds value from
   tasks where a single well-specified prompt is sufficient.

**Opening:** The teacher has two approaches to the grading
tool's feedback generation and isn't sure which is pedagogically
better. Instead of guessing, they generate both and evaluate.
Best-of-N makes the comparison explicit.

<!-- → [DIAGRAM: Best-of-N pattern. Specification → [N parallel
Codex responses]. Human evaluates all N. Selects one.
Optionally combines parts. The selection is the supervisory
judgment.] -->

**Core content:**
- What Best-of-N is: simultaneously generating multiple Codex
  responses for the same task to explore multiple solutions
  and pick the best one. From OpenAI: "For more complicated
  tasks, you can review several iterations and combine parts
  of different responses to get a stronger result."
- When to use Best-of-N: architecture decisions, pedagogical
  choices in the grading tool, any step where two reasonable
  approaches exist and the right choice requires domain judgment
- When NOT to use Best-of-N: mechanical, well-specified tasks
  where the specification fully determines the correct output
- Best-of-N as plausibility auditing at scale: it forces the
  teacher to compare outputs rather than accept the first
  plausible-seeming one
- Best-of-N and the grading tool: which feedback framing
  serves this student population best is a pedagogical judgment
  that no Codex output can make
- From OpenAI: "The Best-of-N feature lets you simultaneously
  generate multiple responses for a single task to quickly
  explore multiple solutions and pick the best one."

**Teacher build:** The teacher uses Best-of-N on the grading
tool's feedback generation step. Generates three responses.
Evaluates each against pedagogical criteria. Documents the
selection reasoning.

**Classroom activity:** Students use Best-of-N on a provided
build task. They document not just which response they chose
but why — the reasoning is the exercise.

**Assessable exercises:**
1. (Apply) Use Best-of-N on a grading tool task. Generate
   three responses. Document which you chose and why.
2. (Analyze) Review three provided Codex responses for the
   same task. Which would you choose for a classroom context?
   What supervisory capacity did you exercise to decide?
3. (Evaluate) Name two tasks in your current build where
   Best-of-N adds value and two where it doesn't. Explain
   the difference.

**Wayback Machine:** 🕰️ **Herbert Simon** (1916–2001) —
Nobel laureate who formalized satisficing: the decision-maker
who does not search for the optimal solution but for a solution
that is good enough given real cognitive constraints. Best-of-N
is satisficing made explicit: generate N candidates, apply
domain judgment, select the satisficing solution.

**Bridge:** The reader has verification tools. Chapter 7 builds
the grading tool using all prior concepts together.

---

### Chapter 7 — Building the Grading Tool: Full Build Arc

**One-line:** The grading tool is the Act Two build. Every
prior concept — AGENTS.md, Ask Mode / Code Mode gate,
specifications, handoff conditions, supervisory capacities,
Best-of-N — applied to a build that matters.

**Learning outcomes:**
1. (Apply) Build a grading tool through the complete conducting
   sequence: Ask Mode plan → Code Mode execution → handoff
   conditions → verification.
2. (Apply) Use Best-of-N on the step requiring the most
   pedagogical judgment.
3. (Analyze) Identify which steps in the build required which
   supervisory capacities.

**Opening:** The teacher has all the tools. Now they use them
on a build that, if it goes wrong, affects students. This is
the Act Two build.

**Core content:**
- The grading tool scope: a tool that processes student
  submissions against a rubric and produces first-draft feedback
  for teacher review. Not fully automated. Teacher stays
  in the loop.
- The Ask Mode plan for a grading tool: what Codex needs to
  know about the rubric, the submission format, the output
  format, and the explicit "do not generate a final grade" rule
- AGENTS.md for the grading tool: what conventions apply,
  what Codex must never do in this build
- Best-of-N on the feedback generation step: two approaches
  (structured feedback vs. narrative feedback), teacher
  selects based on pedagogical judgment
- Handoff conditions for a grading tool: "Every piece of
  feedback references a specific rubric criterion. No output
  contains a numeric grade. The feedback is in the second
  person." Binary. Testable.
- The task queue during the build: capturing ideas for future
  features without losing the main build's focus

**Teacher build:** The complete grading tool, built step by
step. Ask Mode plan → review → Code Mode → handoff conditions
at each step → Best-of-N on the feedback generation step →
verification pass.

**Classroom activity:** Students build a simpler version of
the same tool (a rubric self-checker) using the same sequence.

**Assessable exercises:**
1. (Apply) Build Phase 1 of your grading tool using the
   complete sequence. Document each handoff condition.
2. (Analyze) Which step required the most supervisory judgment?
   Which supervisory capacity did you exercise?
3. (Evaluate) At the end of Phase 1: what would you change in
   the AGENTS.md? The Ask Mode plan?

**Wayback Machine:** 🕰️ **Donald Schön** (1930–1997) — educator
who introduced "reflection-in-action": the practitioner who
thinks about what they are doing while doing it, adjusting in
real time. The supervisory capacity labels in the build log
are Schön's reflection-in-action made operational.

**Bridge:** The grading tool is built. Chapter 8 is about the
hardest moment: when it's right and wrong simultaneously.

---

### Chapter 8 — The Dangerous Middle: When Codex Is Right and Wrong Simultaneously

**One-line:** The hardest moment in a grading tool build:
Codex produces feedback that passes every handoff condition
you wrote and is still pedagogically wrong.

**Learning outcomes:**
1. (Analyze) Identify the dangerous middle in a grading tool
   build.
2. (Apply) Write handoff conditions that require domain
   knowledge, not just technical correctness.
3. (Evaluate) Assess when plausibility auditing must substitute
   for a handoff condition that cannot be automated.

**Opening:** Seth describes the moment in his own grading tool
build where the output was correct and wrong simultaneously.
The teacher reads it and recognizes something they've already
experienced.

**Core content:**
- The three documented failure modes (Anthropic RCT): AI
  Delegation, Progressive AI Reliance, Iterative AI Debugging
- The debugging gap: largest performance disparity on
  diagnostic questions — exactly the skill grading develops
- The handoff condition you cannot write: "Does this feedback
  match what I would say to this specific student?" —
  irreducibly human, requires plausibility auditing every time
- The narrowing principle: use Codex to flag patterns across
  submissions, not to generate individual student feedback.
  The interpretive judgment layer stays with the teacher.
- AI grading accuracy: ~50-55% with rubric, ~33% without.
  First draft only, never final word.
- ESL and AAVE bias: documented 15-20% score discrepancies.
  The equity handoff condition: does this feedback treat all
  students' language as equally valid?
- Best-of-N as a dangerous middle detector: when three Codex
  responses all produce the same pedagogically problematic
  framing, the problem is the specification, not the response.

<!-- → [DIAGRAM: The narrowing principle. Before: Codex generates
individual student feedback (dangerous). After: Codex flags
patterns → teacher writes individual feedback (safe).] -->

**Teacher build:** The teacher rebuilds their grading tool with
narrower scope: Codex flags patterns, teacher writes individual
feedback.

**Classroom activity:** Students audit a provided AI-generated
feedback set for pedagogical appropriateness. Identify three
instances that pass technical handoff conditions but fail
pedagogical judgment.

**Assessable exercises:**
1. (Analyze) Review five pieces of Codex-generated feedback.
   Identify which ones pass technical handoff conditions but
   fail pedagogical judgment.
2. (Apply) Redesign your grading tool's scope based on the
   narrowing principle.
3. (Evaluate) Write a policy for classroom AI grading use
   you could explain to a student who asks why.

**Wayback Machine:** 🕰️ **Alfred Binet** (1857–1911) —
psychologist who developed the first intelligence test and
immediately warned against misusing it. His insistence on the
human interpretation layer — that a number requires professional
judgment to be useful — is the grading tool's plausibility
auditing requirement stated as a founding principle.

**Bridge:** The reader has the full conducting discipline.
Chapter 9 addresses context management using the task queue.

---

### Chapter 9 — The Task Queue: Keeping the Build Clean

**One-line:** The task queue captures tangential ideas and
parallel work without breaking the main build's focus. It is
the lightweight backlog that prevents context from accumulating
into noise.

**Learning outcomes:**
1. (Understand) Explain what the Codex task queue is and how
   it differs from a main build session.
2. (Apply) Use the task queue to capture three tangential ideas
   during the grading tool build without interrupting the main
   session.
3. (Apply) Define a specialized task queue item for pattern
   analysis across student submissions.

**Opening:** The teacher's grading tool build is in Code Mode.
They notice a related improvement they want to make. If they
pursue it now, they will break the current build's focus. The
task queue is the answer.

<!-- → [DIAGRAM: Main build session vs. task queue. Main session:
focused Code Mode execution, one step at a time. Task queue:
background tasks captured and deferred. Arrows showing tasks
fired off and returned to later.] -->

**Core content:**
- What the Codex task queue is: a staging area for tasks that
  can run in the background or be returned to later. From
  OpenAI: "Fire off tasks to capture tangential ideas, partial
  work, or incidental fixes. There's no pressure to generate
  a full PR in one go."
- Task queue vs. main build: the main build runs in Code Mode
  with full supervisory attention. The task queue runs
  background tasks — Ask Mode research, pattern analysis,
  draft generation — that don't require immediate supervision.
- When to use the task queue: when a "while I'm here" idea
  appears during Code Mode; when research would break focus;
  when a parallel task can run independently
- Pattern analysis via task queue: fire off a task to analyze
  student submissions for common misconceptions, return when
  ready. The main build session stays clean.
- From OpenAI: "I was in meetings all day and still merged
  4 PRs because Codex was working in the background" —
  the teacher version: "I was teaching class and Codex was
  analyzing submissions in the task queue."
- The handoff condition for task queue returns: when a task
  queue item returns, it still requires the same supervisory
  evaluation as any Code Mode output.

**Teacher build:** The teacher adds a pattern analysis task
to the task queue during the grading tool build. It reads
all submissions, identifies common misconceptions, and returns
a structured report — without interrupting the main grading
session.

**Classroom activity:** Students use the task queue to fire
off a research task (Ask Mode: "what are common approaches
to this problem?") while continuing their main build.

**Assessable exercises:**
1. (Apply) During your grading tool build, fire off three
   task queue items for tangential ideas. Return to them after
   the main build step is complete.
2. (Apply) Define a task queue item for student submission
   pattern analysis. Specify: task type, input, output format,
   handoff condition.
3. (Analyze) Compare a session where you pursued a tangential
   idea inline vs. a task queue session. What was different?

**Gate 2:** The teacher has a working grading tool with
AGENTS.md, Ask Mode / Code Mode gate, specifications, handoff
conditions, Best-of-N verification, and task queue management.
They have experienced the dangerous middle. Ready for Act Three.

**Wayback Machine:** 🕰️ **Herbert Simon** (1916–2001) —
who formalized decomposition in complex systems: breaking a
large problem into nearly independent subsystems solved
separately and integrated. The task queue is Simon's
decomposition applied to AI-assisted builds: isolated tasks,
local solutions, integrated results.

**Bridge:** The reader has the full conducting discipline.
The Bridge chapter transitions from productivity to pedagogy.

---

### BRIDGE — From Tools That Save Time to Tools That Change What's Possible

**One-line:** Seth describes the moment his builds stopped being
about productivity and started being about what he could make
that didn't exist before.

**No learning outcomes. No exercises. No classroom activity.**

**Core content:**
- The productivity frame vs. the possibility frame
- The grading tool served the teacher. The simulation serves
  the student. That's a different design question.
- What an interactive simulation can do that a worksheet cannot
- Seth's first simulation: what he built, what surprised him,
  what students did with it
- Why the Brutalist three-file system matters now
- The teacher's Act Three question: what concept in your
  curriculum has no good interactive analog yet?

<!-- → [DIAGRAM: The shift from productivity to pedagogy.
Grading tool (serves teacher) → interactive simulation (serves
student). The design question changes when the beneficiary
changes.] -->

**Wayback Machine:** 🕰️ **Seymour Papert** (1928–2016) —
mathematician and educator who invented Logo and argued that
children learn most deeply when they build things for others
to use. His concept of "objects to think with" is the
simulation's pedagogical theory.

---

## ACT THREE — APPLY
*Chapters 10–14: The interactive classroom simulation*

---

### Chapter 10 — The Three-File System: Intent, Constitution, State

**One-line:** Before Codex enters Code Mode on the simulation,
three files define everything. The Intent Layer is human,
always.

**Learning outcomes:**
1. (Understand) Explain what each of the three files protects
   and why all three must be populated before Code Mode begins.
2. (Apply) Write the Intent Layer of a PROJECT.md for an
   interactive simulation.
3. (Apply) Write a DESIGN.md specifying the simulation's visual
   and interaction vocabulary completely enough that Codex
   cannot improvise.

**Opening:** The teacher opens Codex and types "build me an
interactive sorting algorithm simulator." Codex builds
something. It works. But the color scheme isn't the teacher's.
The interaction model isn't right. The pedagogical scaffolding
is missing. The teacher didn't draw the line before Codex
started.

<!-- → [DIAGRAM: Three-file system as three nested boxes.
Outer: AGENTS.md (technical constitution). Middle: DESIGN.md
(visual constitution). Inner: PROJECT.md (intent layer is
human, always). Editorial style.] -->

**Core content:**
- **AGENTS.md (Technical Constitution):** What Codex never
  improvises. Naming conventions, what it must never touch
  without instruction, verification checklist. Already exists
  from prior chapters — extended for the simulation build.
- **DESIGN.md (Visual Constitution):** Complete color system
  (six variables maximum), typography, spacing, interaction
  vocabulary, explicit list of what the system never does.
  Not a guideline. A boundary.
- **PROJECT.md (Project State):** Two layers.
  Layer 1 — Intent (human, never overwritten by Codex): what
  this simulation is, what the student should understand, the
  tone.
  Layer 2 — Technical State (Codex layer): what is built, what
  is pending, generation log.
- The phase gate: Code Mode does not begin until both layers
  of PROJECT.md are populated. This is not a suggestion.
- The Ask Mode plan for a simulation: before Code Mode, Ask
  Mode interrogates the three files and proposes a complete
  implementation plan. The teacher reviews the plan, corrects
  it, approves it. Then Code Mode begins.

<!-- → [TABLE: Three-file system — file name, what it contains,
who writes it, when it changes. Three rows.] -->

**Teacher build:** The teacher writes all three files for their
simulation. Three files, fully populated. Ask Mode plan
proposed and reviewed. Then Code Mode begins.

**Classroom activity:** Students write the Intent Layer of a
PROJECT.md for a simulation they want to build. Class exercise:
read each other's Intent Layers. Can you tell what the
simulation is trying to teach?

**Assessable exercises:**
1. (Apply) Write all three files for your simulation project
   before opening Code Mode. If it takes more than 45 minutes,
   the scope is too large.
2. (Analyze) Review a provided PROJECT.md with a weak Intent
   Layer. Identify what's missing and rewrite it.
3. (Evaluate) What decisions in your simulation are pedagogical
   (Intent Layer) vs. technical (AGENTS.md)?

**Links:** [brutalist.art](https://brutalist.art)

**Wayback Machine:** 🕰️ **Mies van der Rohe** (1886–1969) —
architect whose principle "less is more" and structural frame
concept defines what is built without determining every detail.
The three-file system is this as a digital architecture:
the constitution defines the boundary; within the boundary,
execution is delegated; outside, nothing happens without
explicit instruction.

**Bridge:** Three files complete, Ask Mode plan approved.
Chapter 11 begins the simulation build.

---

### Chapter 11 — Building the Simulation: Conducting at Full Complexity

**One-line:** The three files are in place, the plan is
approved. The build begins. Every step has a specification,
a handoff condition, and a labeled supervisory capacity.

**Learning outcomes:**
1. (Apply) Execute a simulation build sequence in Code Mode,
   completing Codex tasks and human tasks in dependency order.
2. (Apply) Apply each supervisory capacity at the steps
   requiring it, labeled explicitly.
3. (Analyze) Identify when the simulation build is going
   off-script and stop before the three-file system is violated.

**Opening:** Seth's simulation build — real build, real prompts,
real Codex outputs. The teacher reads it and recognizes the
framework in action.

<!-- → [DIAGRAM: The simulation build loop. Three files populated
→ Ask Mode plan → review and approve → Code Mode specification
→ execute → handoff condition check → pass/revert.
Supervisory capacity label at check step.] -->

**Core content:**
- Running the build: Ask Mode plan → review → Code Mode,
  applied to simulation development
- Context management: start each major build phase with a fresh
  Ask Mode interrogation of the three files to verify Codex
  is working from current state
- The scope creep moment in simulation builds: Codex suggests
  "while I'm here" improvements. Log in PROJECT.md Layer 2.
  Do not execute.
- Give Codex a way to verify its own work: define a target
  state for each simulation state. From OpenAI: "Give it a
  mock and you say, build this web UI, it will get it pretty
  good. But if you iterate two or three times, often it gets
  it almost perfect."
- Best-of-N on visual states: generate three visual approaches
  for the key interaction, evaluate against the DESIGN.md
  visual constitution, select. The selection is the human's
  pedagogical and aesthetic judgment.
- The task queue during a simulation build: fire off parallel
  tasks (research a pedagogical approach, generate alternative
  interaction models) without breaking the main build focus.

**Teacher build:** Phase 1 of the simulation build, documented
step by step. Every specification, every handoff condition,
every supervisory capacity labeled. One rejection and revision
in full.

**Classroom activity:** Students run Phase 1 of their own
simulation build using their three files. Required: a build
log. Peer review of build logs.

**Assessable exercises:**
1. (Apply) Execute Phase 1 of your simulation build. Document
   every specification and handoff condition evaluation.
2. (Analyze) At least one Codex output will require revision.
   Document the failure and the revision specification.
3. (Evaluate) At the end of Phase 1: what would you change in
   your three files?

**Wayback Machine:** 🕰️ **Donald Schön** (1930–1997) — educator
whose concept of "reflection-in-action" describes the
practitioner who thinks about what they are doing while doing
it. The supervisory capacity labels in the build log are
Schön's reflection-in-action made operational.

**Bridge:** The simulation works. Chapter 12 deploys it in
class.

---

### Chapter 12 — Deploying in Class: From Build to Lesson

**One-line:** The simulation works in Code Mode. Now it has to
work with 30 students who have never seen it.

**Learning outcomes:**
1. (Apply) Deploy a classroom simulation as a shareable artifact
   that students can access without setup.
2. (Analyze) Identify the gap between "works in Code Mode" and
   "works in classroom" and conduct a revision build.
3. (Apply) Design a classroom activity using the simulation as
   a learning tool, not a demonstration.

**Opening:** The teacher projects the simulation on the
classroom screen. A student clicks something unexpected. The
simulation breaks. This chapter prepares for that moment before
it happens.

<!-- → [DIAGRAM: Student-facing verification pass — three checks.
Check 1: does a student who knows nothing about the code know
what to do in 30 seconds? Check 2: are failure states
informative? Check 3: does the simulation progress from easy
to hard? Binary results. Revision build path if any check
fails.] -->

**Core content:**
- Deployment options: shareable URL via ChatGPT Artifacts,
  GitHub Pages, class website integration from Act One
- The student-facing verification pass: three checks
- First 30 seconds test: does a student know what to do
  without instructions?
- Conducting a revision build based on classroom observation:
  watch students, note what confuses them, use Ask Mode to
  interrogate the problem, Code Mode to fix it
- Best-of-N for revision builds: when uncertain which fix
  is pedagogically better, generate multiple approaches
  and evaluate
- The feedback loop as a teaching opportunity: showing
  students how the simulation was built from their feedback
  is itself a lesson in conducting

**Teacher build:** The teacher deploys, runs the student-facing
verification pass, identifies two gaps, conducts a revision
build, deploys again.

**Classroom activity:** Students deploy their simulations and
run a cross-class usability test. Builder observes. Documents
what breaks. Conducts a revision build.

**Assessable exercises:**
1. (Apply) Deploy your simulation. Give it to one person who
   knows nothing about the topic. Document what they did that
   you didn't expect.
2. (Analyze) Conduct a revision build. Document the Ask Mode
   interrogation, the Code Mode specification, and the handoff
   condition.
3. (Evaluate) What is the difference between a simulation that
   works and one that teaches?

**Wayback Machine:** 🕰️ **Maria Montessori** (1870–1952) —
educator who argued that educational materials must be self-
correcting: the student who uses the material discovers their
own errors without teacher intervention. Her concept of the
"control of error" is the first 30 seconds test applied to
educational design.

**Bridge:** The simulation is deployed. Chapter 13 maps what
students are learning to what the teacher now knows how to teach.

---

### Chapter 13 — Teaching the Discipline: What Your Students Are Reading

**One-line:** Your students have the Codex students book. This
chapter maps what they're learning to what you now know how to
teach — and how to design activities that make both books work
together.

**Learning outcomes:**
1. (Apply) Map each chapter of the students book to a classroom
   activity using the teacher's built tools as context.
2. (Apply) Design an assessment requiring students to document
   their supervisory capacity use during a build.
3. (Analyze) Distinguish the teacher's role in a conducted
   student build from the role in a traditional coding class.

**Opening:** The teacher reads Chapter 5 of the students book
— the five supervisory capacities — and recognizes what Seth
is describing from the inside.

<!-- → [TABLE: Students book chapter map — chapter number, what
students learn, corresponding teacher build experience,
suggested classroom activity. 14 rows. No color.] -->

**Core content:**
- The students book chapter map: what students are learning
  and when, mapped to this book's build tiers
- Using the teacher's grading tool as a teaching artifact:
  "Here's a tool I built with Codex. Here's the Ask Mode plan.
  Here's where I used Best-of-N and why."
- Using the teacher's simulation as a teaching artifact
- Assessment design for conducting: what does "the student
  exercised plausibility auditing" look like in a build log?
- The teacher's role during a student build: asking supervisory
  capacity questions, not fixing code. "What was your handoff
  condition? Did the Ask Mode plan flag this?"
- From OpenAI: "The challenge now isn't turning specifications
  into code — Codex is really good at that. The challenge is
  getting your idea out of your own brain and into a
  specification." Teaching specification writing IS CS education.

**Teacher build:** None — this chapter's output is a classroom
activity design and a build log assessment template.

**Classroom activity:** The teacher designs an activity
requiring students to submit a build log alongside their code.
The build log documents: every Ask Mode plan reviewed, every
specification, every handoff condition, every supervisory
capacity label. Peer review of build logs, not code.

**Assessable exercises:**
1. (Apply) Design a build log template capturing Ask Mode
   plans, specifications, handoff conditions, and supervisory
   capacity labels.
2. (Apply) Create a rubric for the build log separate from
   the rubric for the code.
3. (Evaluate) What is the hardest supervisory capacity for
   your students to exercise? Design an activity targeting it.

**Wayback Machine:** 🕰️ **Lee Shulman** (born 1938) — educator
who introduced "pedagogical content knowledge": the specific
knowledge needed not just to know a subject but to teach it.
His argument that subject knowledge and pedagogical knowledge
must be integrated is the argument for this book existing
separately from the students book.

**Bridge:** The discipline is taught. Chapter 14 is the record
of what the teacher built.

---

### Chapter 14 — Your Terminal Deliverable: The Post-Build Document

**One-line:** The simulation is deployed. The build is done.
This chapter is the record of what you built, what you learned,
and what you would do differently.

**Learning outcomes:**
1. (Create) Produce a post-build document for the interactive
   simulation using the five-section template.
2. (Evaluate) Assess your own build against the five
   supervisory capacities.
3. (Create) Design a second build based on what the first one
   taught you.

**Opening:** Not Seth's build. Yours. The simulation is running
in your classroom. Students are using it. This chapter asks
you to account for every decision.

<!-- → [DIAGRAM: The post-build document as the arc's terminal
artifact. Timeline: first session / first page / grading tool
/ simulation deployed / post-build document. Five milestones.
Editorial style.] -->

**Core content:**
- The post-build document: five sections
  1. What I built (one paragraph, plain language)
  2. What I delegated to Codex and why
  3. What I kept for myself and why
  4. What I learned that I didn't know before the build
  5. What I would do differently
- The post-build document as a teaching artifact: share it
  with students. Model the discipline.
- What comes next: the second simulation (built faster, better
  three files), the CSTA community, the Irreducibly Human
  series, OpenAI's documentation

**Terminal deliverable:** The teacher's post-build document
for the interactive simulation.

**Closing:**
"You built it. Your students learned from it. You know what
every decision cost you and what it gave you. That is what
conducting looks like when it's complete. The next build
starts here."

**Assessable exercises:**
1. (Create) Write your post-build document. Five sections.
   Honest.
2. (Evaluate) Which supervisory capacity was hardest to
   exercise consistently? Design a practice exercise targeting
   that capacity in your students.
3. (Create) Design the second simulation — what you would
   build with what the first one taught you. Start with the
   three files.

**Wayback Machine:** 🕰️ **Donald Schön** (1930–1997) —
educator who introduced "reflection-on-action": the practitioner
who, after an episode of practice, thinks carefully about what
they did and why, to improve future practice. The post-build
document is Schön's reflection-on-action made mandatory.

---

# PART 9 — CHAPTER ANATOMY TEMPLATE

All 14 chapters plus bridge follow this structure. The Cowork
enrichment pass processes items marked with comments.

1. **One-line descriptor** (capability build, not topic)
2. **Learning outcomes** (3–5, Bloom's level labeled)
3. **Chapter opening** (Seth narrative, teacher scenario,
   or failure case — problem before framework)
4. **Figure comments** — `<!-- → [DIAGRAM: ... ] -->` or
   `<!-- → [TABLE: ... ] -->` embedded at point of use
5. **Core content sections** (4–6): concept → teacher build
   application → classroom activity application
6. **Teacher build** (explicit build step for this chapter's
   concept)
7. **Classroom activity** (classroom-facing application of
   the same concept; cross-reference to students book chapter)
8. **Assessable exercises** (minimum 3; at least one requiring
   production)
9. **Links** (where applicable: platform.openai.com/docs,
   brutalist.art, irreducibly.xyz)
10. **AI Wayback Machine** — `## 🕰️ AI Wayback Machine` — one
    pre-2000 figure per chapter, connected to chapter's
    intellectual substance
11. **Bridge** (one sentence; raises what next chapter answers)

**Phase gates embedded:** Gate 1 at end of Chapter 4, Gate 2
at end of Chapter 9. Both state explicitly what must be true
before the next act begins.

**Enforcement:** A draft chapter missing items 4 (figures),
6 (teacher build), 7 (classroom activity), 10 (Wayback Machine),
or 11 (bridge) is an incomplete draft.

---

# PART 10 — CASE STUDY STRATEGY

## Domain coverage map

| Domain | Chapters | Primary use |
|---|---|---|
| Class website | 1–4 | Act One build arc |
| Grading / rubric tools | 5–9 | Act Two build arc |
| Interactive simulation | 10–14 | Act Three build arc |
| Student submission pattern analysis | 8, 9 | Dangerous middle; task queue |
| CS concept visualizer | 10–11 | Simulation worked example |
| Cross-class usability test | 12 | Student-facing verification |

## Case escalation

Act One cases: low stakes — the broken link, the wrong CSS.
Act Two cases: higher stakes — the grading tool that produces
technically correct and pedagogically wrong feedback.
Act Three cases: full complexity — Seth's real simulation build
session across four chapters.

## Sourcing requirement

CSTA 2025 data cited for reader profile claims. Anthropic
Education Report cited for teacher-as-builder validation.
OpenAI internal use doc quoted with attribution. Anthropic
RCT cited for grading chapter empirical foundation.

---

# PART 11 — HARD TOPICS, CONTESTED CLAIMS, AGING RISK

## Contested claims

| Claim | Status | Book's position |
|---|---|---|
| AI grading is accurate enough for classroom use | Disputed | 50-55% accuracy with rubric; first draft only |
| Ask Mode / Code Mode gate prevents all errors | Overstated | Gate reduces errors; supervisory layer still required |
| Best-of-N always improves output | Overstated | Adds value for judgment-intensive steps; overhead for mechanical steps |
| Codex task queue is available on all plans | To be confirmed | Check before production (OQ-6) |

## Hard chapters

**Chapter 8 (Dangerous Middle):** AI grading accuracy data must
be stated precisely. ESL and AAVE bias findings require specific,
careful statement. Do not draft without K-12 classroom experience.

**Chapter 7 (Full Grading Tool Build):** Requires a contributor
who has actually built and used a Codex-based grading workflow
in a classroom context.

## Aging risk

| Content type | Risk | Review cadence |
|---|---|---|
| Codex feature references (Ask Mode, Code Mode, Best-of-N, task queue) | High | Before each edition |
| AGENTS.md syntax and file discovery rules | High | Before each edition |
| AI grading accuracy percentages | Medium | On new major studies |
| Five supervisory capacities | Low | On major framework revision |
| Three-file system (Brutalist) | Medium | On major tool change |
| CSTA and Anthropic Education Report data | Medium | Before each edition |

---

# PART 12 — MARKET POSITIONING SUMMARY

## The gap this book fills

No practitioner handbook teaches the conducting discipline to
K-12 CS teachers in the Codex ecosystem. The Ask Mode / Code
Mode gate, AGENTS.md file discovery hierarchy, Best-of-N, and
task queue are Codex-native mechanisms. This book serves the
OpenAI-native teacher reader who assigns the Codex students
book.

## Market size estimate

Primary: ~50,000 K-12 CS teachers in the US (CSTA estimate),
skewed toward those using ChatGPT Plus/Pro or institutional
Codex access.
Secondary: University teacher training programs, PD providers.

---

# PART 13 — FEATURE LIST

| Feature | Priority | Production effort |
|---|---|---|
| 14-chapter + bridge architecture | ESSENTIAL | Low |
| Three-act learning arc | ESSENTIAL | Low |
| Interleaved structure (teacher build + classroom activity) | ESSENTIAL | Medium |
| Seth's practitioner voice | ESSENTIAL | Medium |
| Three build tiers (website, grading tool, simulation) | ESSENTIAL | High |
| Five supervisory capacities framework | ESSENTIAL | Low |
| AGENTS.md full chapter treatment | ESSENTIAL | Medium |
| Ask Mode / Code Mode gate | ESSENTIAL | Low |
| Best-of-N chapter treatment | ESSENTIAL | Medium |
| Assessable exercises (3+ per chapter) | ESSENTIAL | Medium |
| Terminal deliverable (post-build document) | ESSENTIAL | Low |
| Gate 1 and Gate 2 explicit conditions | ESSENTIAL | Low |
| AI Wayback Machine (15 figures) | IMPORTANT | Low |
| Figure comments for Cowork enrichment | IMPORTANT | Medium |
| Students book chapter map (Ch 13) | IMPORTANT | Low |
| Three-file system templates (Appendix B) | IMPORTANT | Low |
| Appendix A (Codex quick reference) | IMPORTANT | Low |

---

# PART 14 — OUT OF SCOPE

| Topic | Reason | Covered better in |
|---|---|---|
| Full Codex API and advanced orchestration | Developer scope | platform.openai.com/docs |
| AI grading as primary assessment | Research shows 50-55% accuracy; first-draft-only | Excluded by design |
| Multi-agent pipelines | Power user pattern | Advanced follow-on |
| Server-side deployment and databases | Too complex for classroom-scale builds | Advanced follow-on |
| Generic AI ethics / responsible use policy | Not this book's scope | codex-for-teachers companion |
| AGENTS.override.md and enterprise policy | IT/DevOps scope | platform.openai.com/docs |

---

# PART 15 — ADOPTION RISK REGISTER

| # | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| 1 | Terminal barrier for non-coding-native CS teachers | High | High | Ch 1 includes complete first-session walkthrough with exact commands |
| 2 | Aging risk: Codex feature specifics | High | Medium | Features in appendices; discipline in main text; live URLs |
| 3 | Grading tool chapter requires careful accuracy statement | Medium | High | ESL/AAVE bias data cited precisely; "first draft only" enforced |
| 4 | Ask Mode / Code Mode interface may change | Medium | Medium | Conceptual gate (plan before execution) is tool-agnostic; appendix updatable |
| 5 | Best-of-N availability on teacher-accessible plans | Medium | Medium | Confirm before production (OQ-6) |
| 6 | Codex task queue not available on all plans | Medium | Medium | Confirm before production; concept maps to session management if unavailable |
| 7 | Interleaved structure harder to write than sequential | Medium | Medium | Each chapter has explicit teacher build and classroom activity sections |

---

# PART 16 — OPEN QUESTIONS

| # | Question | Stakes | Decision deadline | Owner |
|---|---|---|---|---|
| 1 | What CS concept does the Act Three simulation teach? | Worked example quality | Before chapter drafting | Author + CS teacher advisory |
| 2 | Should the grading tool have a specific subject domain or be domain-agnostic? | Example specificity | Before Act Two drafting | Author |
| 3 | Does the book include a district-level deployment appendix for restricted technology environments? | Adoption barrier mitigation | Publisher proposal stage | Author + Publisher |
| 4 | Seth's practitioner voice scope: which chapters does Seth draft vs. review? | Production planning | Before manuscript schedule | Author + Seth |
| 5 | Should Appendix A (Codex quick reference) be on a web page rather than in the book? | Aging risk | Before production | Author |
| 6 | Confirm Best-of-N and task queue availability on ChatGPT Plus (not just Pro) before chapters referencing them are finalized. | Accessibility | Before Ch 6 and Ch 9 drafting | Author |
| 7 | Windows dictation shortcut (Win+H) confirmed? Verify before Chapter 0 is final. | Accessibility | Before manuscript | Author |

---

## Appendix A — Codex Quick Reference for Teachers

| Feature | What it does | When to use it |
|---|---|---|
| Ask Mode | Codex reads and plans without executing | Always before Code Mode. Problem interrogation, plan generation. |
| Code Mode | Codex executes. Writes files, runs commands. | After Ask Mode plan is reviewed and approved. |
| Best-of-N | Generates N parallel responses for the same task | When uncertain which approach is better. Selection is human work. |
| Task queue | Captures tasks for background or later execution | Tangential ideas, parallel work, deferred fixes during a main build. |
| AGENTS.md | Persistent context read at every session start | Always. Write it before the first build session. |
| Approval policy | on-request / never / on-failure | on-request for new work; never only in trusted automated pipelines. |

Full documentation: [platform.openai.com/docs](https://platform.openai.com/docs)

---

## Appendix B — Three-File Templates

**AGENTS.md template for teacher classroom builds:**
```
# [Project Name] — Technical Constitution

## File structure
[Describe the file structure Codex must maintain]

## Stack
[Name the framework, CSS approach, JavaScript constraints]

## Naming conventions
[Specific naming rules]

## What Codex must never touch without explicit instruction
[List protected files and directories]

## Verification
[The command or check that confirms a step is complete]
```

**DESIGN.md template for interactive simulations:**
```
# [Simulation Name] — Visual Constitution

## Color system
[Six variables maximum. List them. No others.]

## Typography
[Display, body, code fonts. No others.]

## Interaction vocabulary
[What interactions are allowed. What the system never does.]

## Accessibility
[Requirements that cannot be compromised]
```

**PROJECT.md template:**
```
# [Simulation Name] — Project State

## Layer 1: Intent (Human Layer — never overwritten by Codex)
What this simulation is:
What the student should understand after using it:
What questions it answers:
What questions it refuses to answer:
The tone:

## Layer 2: Technical State (Codex Layer)
What is built:
What is pending:
Generation log:
Open technical questions:
```

---

## Appendix C — Post-Build Document Template

Five sections. One document. Honest.

1. **What I built** (one paragraph, plain language)
2. **What I delegated to Codex and why**
3. **What I kept for myself and why**
4. **What I learned that I didn't know before the build**
5. **What I would do differently**

---

## Series Links

[brutalist.art](https://brutalist.art) ·
[frictional.xyz](https://frictional.xyz) ·
[irreducibly.xyz](https://irreducibly.xyz) ·
[nikbearbrown.com](https://nikbearbrown.com) ·
[platform.openai.com/docs](https://platform.openai.com/docs)

---

*Full TOC Draft v1.0 — compiled from all phase outputs*
*All phases complete: Vision (i1–i4), Learning Architecture
(l1–l4), Chapter Architecture (c1–c4), Scope & Market (m1–m4)*
*Blockers before production: OQ-1 (simulation domain),
OQ-6 (Best-of-N and task queue plan availability confirmation)*
