# Chapter 1 — Your First Codex Session: This Is Not ChatGPT

> Codex plans multi-step tasks, executes shell commands, reads and writes files, and iterates autonomously. That autonomy is the feature — and the reason you need a discipline before you start.

---

## Learning outcomes

By the end of this chapter, you will be able to:

1. **(Understand)** Explain the agentic loop and how it differs from a chat conversation.
2. **(Apply)** Set up Codex and run a first Ask Mode session in a project directory.
3. **(Understand)** Explain why Ask Mode interrogation must precede Code Mode execution.

---

## Opening

You open Codex for the first time. You type something simple — something you have typed into ChatGPT a hundred times.

*"Add a syllabus page to my class website."*

ChatGPT, in this scenario, would respond with HTML. You would copy the HTML, paste it into a file somewhere, save it, look at it, decide if you liked it.

Codex does not respond with HTML.

Codex starts reading your project directory. It opens files. It notices the file structure. It proposes a multi-step plan: it will create `src/syllabus.html`, modify the navigation in `src/index.html` to link to it, copy a header block from one of your existing pages so the styling matches, and run the lint check you mentioned in your AGENTS.md last week. It tells you which files it will touch. Then it asks whether to proceed.

You realize, in the small pause between Codex's plan and your decision, that something has changed.

ChatGPT is a chat interface. Codex is *something else*. Codex acts on your filesystem. Codex chains operations. Codex iterates. If you say yes, Codex executes. If you say nothing, Codex waits.

You are now in a relationship with software that does what software has rarely done before in your work — it *takes initiative*. The chapter you are reading is about the discipline that initiative requires.

<!-- → [DIAGRAM: The agentic loop — Gather context → Plan → Execute → Verify → Repeat. Ask Mode: gather and plan only. Code Mode: execute and verify. Human interruption point at every phase. Editorial style. No color.] -->

---

## The agentic loop

What you just experienced is called the **agentic loop**. Most agentic coding systems share it:

1. **Gather context.** The system reads files, notices conventions, builds a mental model of what is there.
2. **Plan.** The system proposes a sequence of operations that will produce the requested change.
3. **Execute.** The system runs the operations — writes files, runs commands, edits in place.
4. **Verify.** The system checks whether the result matches what was requested.
5. **Repeat.** If something didn't work, the system adjusts and tries again.

Each phase has a human interruption point. You can stop the system mid-gather, refuse the plan, halt during execution, override verification. The discipline this book teaches is largely about *which* interruption points to use, *when*, and *why*.

The two modes that matter most are the ones at the top of the loop.

**Ask Mode** is the read-and-plan mode. Codex looks at your project. Codex answers your questions about it. Codex proposes a plan if you ask for one. Codex does not write anything in Ask Mode. You can stay in Ask Mode forever and nothing on your filesystem will change.

**Code Mode** is the execute mode. Codex acts. Files are written. Commands are run. Changes happen.

The most important rule in this book — the rule everything else depends on — is:

> **Nothing goes from Ask Mode to Code Mode without a reviewed plan.**

This is the **phase gate**. It is the operational version of the principle that runs through the entire book: that the cognitive work which produces good outcomes is the work of *deciding what to build*, not the work of building it. Codex is excellent at the building. The deciding is yours. The phase gate is where the deciding happens.[^1]

---

## Setting up Codex

This section gets you to a working first session. The exact commands evolve quickly; the conceptual steps do not.

### Account and plan

Codex is included with most ChatGPT plans as of 2026. The book's working assumption is **ChatGPT Plus** ($20/month) — sufficient for everything in Acts One and Two and most of Act Three. If your school district has institutional **ChatGPT Edu** access, that works identically. If you are on the free tier, you have rate-limited Codex access; expect to hit limits during longer sessions. Pro ($100/month) gives roughly 5× the Plus rate limits, which becomes useful when the simulation build in Act Three is iterating on visual states.[^2]

### Installation

You have two surfaces:

1. **The Codex app** (the visual surface most teachers will use). Download from the OpenAI account page or the app store on macOS or Windows. The app is built around managing one or more parallel agents at once, which becomes useful by Chapter 9.

2. **The Codex CLI** (the terminal surface). Installed via `npm install -g @openai/codex`. The CLI is more flexible and more script-friendly. If you are comfortable in a terminal, the CLI is faster for many operations.

This book uses both. The chapters describe operations in tool-agnostic language — "ask Codex to read the codebase," not "click the read button in the Codex app." Where the surface matters, the chapter says which surface.

### First-time configuration

Create a project directory. Anywhere you want, but make a habit of putting your classroom builds together — `~/teaching/class-website/`, `~/teaching/grading-tool/`, `~/teaching/simulations/`. Codex's behavior depends on the project root.

Permission modes: Codex's default is **on-request** — Codex asks before each file write or shell command. Two alternatives: **never** (Codex never asks; useful in trusted automated pipelines, not useful for teacher builds) and **on-failure** (Codex asks only when something errors). For Acts One and Two, leave the default as on-request. You want to be asked.

Sandbox policy: **workspace-write** restricts writes to the current project directory. Leave this on. It is the safety net.

---

## Your first session — questions only

The instinct, the first time you sit down with Codex, is to ask it to build something.

Resist.

Your first session should produce no changes to your filesystem. Open the Codex app or run `codex` in your project directory. You are in Ask Mode by default. Now ask questions.

Suggested opening questions (literally type these):

- *"What do you see in this folder?"*
- *"What language and framework is this project using?"*
- *"What conventions do you notice in the existing files?"*
- *"If I asked you to add a new page, where would it go and what would you need to know?"*
- *"What are you uncertain about regarding this project?"*

Read the answers carefully.

Two things happen in this session. The first is that you calibrate Codex. You see what it gets right (probably the file structure, the framework, the obvious conventions) and what it gets wrong (probably the specific conventions you care about that aren't visible in the code yet, or the constraints from your school's deployment setup that Codex can't see). The gap between what Codex sees and what you know is precisely the gap your AGENTS.md will close in Chapter 2.

The second thing that happens is that you build the habit of **questions before execution**. Senior OpenAI engineers describe this as their standard practice when they open a new codebase. In the December 2025 engineering retrospective they put it bluntly: *"If you're just showing it to someone for the first time, start with Ask Mode. Don't start by using Code Mode. Just start by asking questions about the codebase."*[^3]

You will violate this habit later. Everyone does. When that happens, the dangerous middle (Chapter 8) is what catches you. For now, build the habit.

---

## Worked example: the first Ask Mode session

Here is a concrete first session for a teacher whose class website project lives in `~/teaching/class-website/`. The directory contains a handful of HTML files, a CSS file, and a `package.json` left over from a previous attempt to set up a static-site generator.

**Teacher (Ask Mode):** *What do you see in this folder?*

**Codex:** *I see a vanilla HTML/CSS class website. Files: `src/index.html`, `src/units.html`, `src/syllabus.html`, `src/styles.css`. There's also a `package.json` referencing eleventy as a dependency, but I don't see eleventy config or templates. Either the project was migrated away from eleventy, or the static-site-generator setup was never completed. Which is it?*

The teacher pauses. The teacher had forgotten about the eleventy attempt. Codex has surfaced a real ambiguity in the project that the teacher would have run into the moment they asked Codex to build something. Already, in question one, Codex has earned its place.

**Teacher:** *Migrated away. Plain HTML/CSS, no build step.*

**Codex:** *Understood. In that case, the `package.json` is leftover. Want me to flag it for deletion later, or leave it alone?*

**Teacher:** *Leave it for now. Tell me what conventions you see.*

**Codex:** *Two-space indentation in HTML. Single-quoted attributes consistently. CSS uses class names in kebab-case (`unit-card`, `nav-link`). No CSS variables yet. The pages share a header and navigation block, but the block is copy-pasted — not templated. Any change to nav will need to be made in three places. Is that intentional or an artifact?*

**Teacher:** *Artifact. We'll fix it eventually but not this week.*

**Codex:** *Noted. One more thing I'd want to know before I touched anything: what is your verification step? When you change a page, how do you know it didn't break?*

**Teacher:** *I open it in the browser and check on my phone.*

**Codex:** *OK. I'll match that. I won't add automated tests or a build step unless you ask.*

That is the first session. No files were modified. No commands were run. The teacher learned three things about how Codex reads the project, and Codex learned one thing about how the teacher works. This calibration will pay back in every subsequent session.

**The lesson:** the first session is for calibration, not construction. The cognitive work of describing what you are looking at is what makes Codex useful when it starts doing things.

**The limit:** Ask Mode does not catch every assumption Codex is making. There are conventions and constraints Codex cannot see — your school server's mod_rewrite oddities, your district's network restrictions, the fact that you cannot install build tools on the school-issued laptop you grade from. Those go into AGENTS.md (Chapter 2). The first session reveals what is visible in the code. AGENTS.md captures what is not.

---

## Common misconceptions

**"Codex is like ChatGPT, just for code."** No. ChatGPT replies; Codex acts. ChatGPT's worst failure is a wrong answer. Codex's worst failure is a wrong answer *and* an unintended change to your project. The discipline this book teaches exists because the two failure modes have very different costs.

**"I'll skip Ask Mode for simple changes."** This is the most common pattern that leads new Codex users into the dangerous middle. The "simple change" is the change where you are most likely to skip the review step — and the change where Codex is most likely to assume a convention you have not communicated. Senior OpenAI engineers prescribe Ask-Mode-first specifically because *they* have learned not to skip it on simple changes. Treat the gate as default, not exception.

**"Installation problems mean this book isn't for me."** Installation is real friction; not every district allows it; not every laptop is configured for it. If installation is blocking you, three options: (a) use ChatGPT Edu access if your district provides it (it includes Codex); (b) use the Codex app on a personal device for the build chapters, then deploy to school; (c) read the conducting framework chapters (4, 5, 9) which are tool-agnostic and apply to any agentic coding tool you can run.

**"My school IT won't let me run shell commands."** Verify. The Codex app's default sandbox restricts writes to the project directory and does not require system-level privileges. Many districts allow it once they understand what it actually does. If you need a single page to send to your IT department, see the back matter.

---

## Exercises

1. **(Apply)** Set up Codex (Plus, Edu, or Pro). Open a project folder you will use for the class website build (Chapters 3–4). Run an Ask Mode session. Ask Codex five questions about what it sees. Make no changes. Document what Codex noticed that you didn't tell it — at least three specific things.

2. **(Analyze)** Still in Ask Mode, ask Codex to propose a plan for adding a new page to your class website. Read the plan carefully. Do not approve it. List two assumptions Codex made in the plan that you would need to correct before you would let it execute.

3. **(Evaluate)** What is the single most important thing to do before switching from Ask Mode to Code Mode, and why? Answer in one paragraph. (You will return to this in Chapter 3, where Ask Mode → Code Mode becomes the spine of every build.)

---

## Classroom activity

Have your students run their first Codex session on a starter project you provide (or any small open-source project — a single-file HTML/CSS landing page works). Constraints:

- **Ask Mode only.** No file modifications permitted in this session.
- **Three questions.** Each student asks at least three codebase questions and documents Codex's responses verbatim.
- **One ambiguity surfaced.** Students must identify at least one thing Codex noticed that they wouldn't have told it explicitly. This is the *calibration moment* — the point at which Codex's reading of the project goes beyond what the student would have specified.

Class discussion: what did Codex see that you didn't? What did Codex *miss* that you would have caught? The gap between the two is where the conducting discipline lives.

This activity maps to Chapter 1 of the students book, which introduces the agentic loop from the student's perspective. If your students have read it, the activity will land harder.

---

## Links

- OpenAI Codex documentation: [platform.openai.com/docs](https://platform.openai.com/docs)
- Codex pricing and plan availability: [developers.openai.com/codex/pricing](https://developers.openai.com/codex/pricing)
- Codex CLI repository: [github.com/openai/codex](https://github.com/openai/codex)

---

## What would change my mind

The chapter's strong claim is that **Ask-Mode-first reduces build errors materially** for non-trivial work. If a controlled study compared teachers who used Ask-Mode-first to teachers who went straight to Code Mode on matched build tasks — and the Ask-Mode group did not produce measurably fewer broken handoffs or unintended file modifications — the "questions before execution" rule loses its empirical foundation. It would still be sound practice (defense in depth is a virtue), but it would no longer be necessary in the strong sense. The book would still recommend the gate; the urgency would drop.

---

## Still puzzling

- **When does Ask Mode itself become a friction tax?** For a one-line change to fix an obvious typo, the Ask Mode interrogation step is almost certainly overhead. Where is the threshold? Practitioners disagree. The book's working answer (Chapter 3) is: any change you would not bet a full hour on getting right in one shot.

- **Should Codex have more aggressive defaults for first-time users?** Currently the default is on-request approval. Some practitioners argue that for new users the default should be on-request with a plan-mode-required-first switch. OpenAI has not adopted this. The book's discipline does not depend on the default — but it would be easier to teach if the tool enforced more of the gate by default.

- **Is the agentic loop the right abstraction long-term?** As of 2026 the loop is the standard frame. Whether 2028 systems will still be productively described this way — or whether they will be sufficiently different to require new vocabulary — is open.

---

## AI Wayback Machine

🕰️ **Alan Kay** (born 1940) — computer scientist who designed the Dynabook concept: a personal computer as an instrument for learning, not just a tool for executing pre-specified tasks. Kay argued, in his 1972 Xerox PARC paper *A Personal Computer for Children of All Ages*, that the computer should be *a medium for exploration, not just execution*.[^4] The Ask Mode discipline is Kay's argument restated for agentic systems: spend time in the exploration register before you spend time in the execution register. The cognitive value happens upstream of the execution.

---

## Bridge

You have been in a Codex session. You have seen what Codex sees and noticed what it does not. Chapter 2 gives you the file that makes every subsequent session smarter — AGENTS.md, the persistent context Codex reads at the start of every session. The first session was calibration. The second session, with a good AGENTS.md, is acceleration.

---

[^1]: The phase-gate principle runs through the entire book. Chapter 4 (handoff conditions) is the phase gate at command granularity. The Frictional/Phase-Gates/Humans+AI themes (97-fundamental-themes) develop it more fully.
[^2]: OpenAI, Codex pricing. [verify — confirm exact rate-limit multipliers and plan inclusions at press; figures evolve.]
[^3]: OpenAI engineers, "How OpenAI Engineers use Codex to Tackle Big Projects with Rigor" (forum.openai.com, December 4, 2025).
[^4]: Kay, A. *A Personal Computer for Children of All Ages*. Xerox PARC, August 1972. Available as Xerox PARC Technical Report; republished in multiple histories of personal computing.
