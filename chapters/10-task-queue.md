# Chapter 9 — The Task Queue: Keeping the Build Clean


## TL;DR

- This chapter gives a working overview of The Task Queue: Keeping the Build Clean, focusing on the ideas a reader needs before moving to the next chapter.
- The chapter moves through Learning outcomes, Opening, What the task queue is, When to use the task queue, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

> The task queue captures tangential ideas and parallel work without breaking the main build's focus. It is the lightweight backlog that prevents context from accumulating into noise.

---

## Learning outcomes

1. **(Understand)** Explain what the Codex task queue is and how it differs from a main build session.
2. **(Apply)** Use the task queue to capture three tangential ideas during the grading tool build without interrupting the main session.
3. **(Apply)** Define a specialized task queue item for pattern analysis across student submissions.

---

## Opening

You are mid-Code-Mode on the grading tool's Phase 4 — first-draft feedback generation. The build is focused. The handoff conditions for this step are explicit. The session context is clean.

Codex finishes generating a feedback draft for the current submission. While you are reading it, you notice three things you want to do *eventually*:

1. The cohort pattern report from Phase 5 should probably also include "average length of submission" as a metric.
2. You should investigate whether you can add a hook that runs `analyze_code.py` automatically when a new submission file appears in the directory.
3. There is a small bug in the section-presence check that flags submissions with the section header capitalized differently from your test set.

None of these are part of the current step. All three are real and worth doing. If you pursue any one of them right now, you break the focus of the current build session and the context fills with three half-finished tangents.

The task queue is the answer.

![Main build session vs](images/10-task-queue-fig-01.png)
*Figure 10.1 — Main build session vs*

---

## What the task queue is

The Codex app (and, increasingly, the CLI) supports firing off **parallel tasks** that run in separate cloud containers with their own isolated contexts. The main session continues; the parallel tasks work independently; their results return when ready.[^1]

This is different from generate-evaluate-select (Chapter 6), which runs multiple *responses to the same task*. The task queue runs *different tasks in parallel*. The two are complementary and serve different supervisory purposes — generate-evaluate-select is for the moment of judgment on a single decision; the task queue is for keeping the main build focused while incidental work happens in the background.

The OpenAI engineers describe the productive use bluntly: *"Fire off tasks to capture tangential ideas, partial work, or incidental fixes. There's no pressure to generate a full PR in one go."*[^2] The mental model is: the main session is the focused work; the task queue is the place where the work that should not interrupt the focused work happens anyway.

---

## When to use the task queue

Three patterns work well.

**Pattern 1: capture-and-defer.** A tangential idea appears during the main build. You file it as a task queue item — *"Investigate adding average-submission-length to the cohort report; return a brief findings document with a recommended yes/no"* — and return to the main work. The task runs in the background. When you next have attention to spare, you read the findings and decide whether to act.

**Pattern 2: research-without-context-bloat.** You need to investigate how to handle a specific case (file format conversion, an edge case in section detection) but you do not want the research to pollute the main session's context. Fire off the research as a task queue item. The investigation runs in an isolated context. The summary returns to the main session; the file-reads and dead-ends do not.

**Pattern 3: parallel work that does not require supervision per step.** Pattern analysis across many submissions. Generating draft documentation for files you have just written. Running test-coverage analysis. These are tasks where the input is well-defined and the output is a summary you will evaluate when it returns. Firing them off lets you continue the main build while they work.

The pattern that does **not** work well: high-stakes work that *should* require supervision per step. The task queue is not a way to delegate the conducting discipline. When a task queue item returns, it still requires the same supervisory evaluation as any Code Mode output. The task queue saves you the *context* of the parallel work; it does not save you the *supervision* of the work's output.

---

## When NOT to use the task queue

Two failure modes worth naming.

**Fire-and-forget.** The task queue makes it easy to fire off many tasks. It also makes it easy to *not evaluate the returns*. Every task queue item that returns is a Codex output you must evaluate against your specifications and handoff conditions. If you fire off ten items and only evaluate three, the unevaluated seven are silent failures-in-waiting. The discipline is: *fire only what you will return to evaluate.*

**The task queue as supervisor-substitute.** The temptation is to use the task queue to *run the parts of the build you don't want to think about*. This is the dangerous middle's invitation. If you would not have shipped the work without supervision, do not fire it into the queue and ship its return without supervision. The task queue is for work that you *will* supervise, just not synchronously.

---

## A worked example: pattern analysis as a task queue item

The grading tool's pattern analysis (Phase 5 in Chapter 7) is a natural task queue candidate. The job: read all per-submission flagging reports, identify common patterns across the cohort, return a structured report.

The specification, filed as a task queue item:

> **Operation:** Analyze the per-submission flagging reports in `./reports/2026-03-19/sections/` and `./reports/2026-03-19/code/`. Identify the top 5 common missing sections, top 5 common code-style flags, and top 3 patterns that appear in 25%+ of submissions. Return a structured report.
>
> **Invariants:** Read-only. Does not modify any file in `./reports/`. Does not touch the grade book or any submission file.
>
> **Context:** The flagging report formats are documented in AGENTS.md. The cohort is approximately 30 submissions.
>
> **Output format:** A markdown report saved to `./reports/2026-03-19/patterns/cohort_summary.md`. Sections: "Top common missing sections (with counts)", "Top common code flags (with counts)", "Patterns in 25%+ of submissions (with example excerpts)". Brief — under 500 words total.
>
> **Negative constraint:** Do not generate per-student feedback. Do not name students. Do not score the cohort. Do not propose grading changes.

You fire this off. The main session continues with feedback-draft review on the current submission. Twenty minutes later, the pattern analysis returns. You open the file. You read it.

This is the supervisory moment for the task queue return. You evaluate against the specification's invariants. Did it stay read-only? (Check that no submission files have new modification timestamps.) Did the output land in the expected location? Are the patterns named with counts? Is anything in the report that the negative constraint prohibited?

If yes, you incorporate the cohort pattern report into your next-class planning. If no, you treat it like any other failed handoff condition: revert, respecify, re-fire.

**The lesson:** the task queue is the conducting discipline applied to *parallel* work. The supervisory work does not disappear; it shifts from synchronous (during main session) to asynchronous (when the task returns). The shift is what keeps the main build clean.

**The limit:** asynchronous supervision is harder than synchronous. You can forget to evaluate returns. The discipline requires building the habit of *reading every return*, and treating returns you have not read as if you had not fired the task at all.

---

## Closing Act Two: Gate 2

You have a working grading tool. You have AGENTS.md with the project's never-rules. You have used the Ask Mode → Code Mode gate. You have written specifications and handoff conditions. You have named the five supervisory capacities and labeled them in build logs. You have used generate-evaluate-select on the step that needed pedagogical judgment. You have experienced the dangerous middle in Chapter 8 and rebuilt your tool around the narrowing principle. You have used the task queue to keep the main build focused.

You are at Gate 2. The framework is complete. Act Three begins with a different question: not *can I build a tool that saves me time*, but *can I build a tool that opens classroom experiences my students could not have otherwise*.

The Bridge chapter is that question, in Seth's voice.

---

## Common misconceptions

**"Task queue is for power users."** The Codex app is built around it. As of 2026, parallel tasks in separate cloud containers are a first-class affordance. K-12 teachers can use it on Plus and above. The friction is in the *discipline* (evaluating returns), not in the tool.

**"More parallel tasks = better."** Each return needs supervision. The right number is *as many as you will actually evaluate*. For most builds, three concurrent items is plenty.

**"Task queue replaces supervision."** It relocates it. The supervisory work happens when the return arrives, not when the task fires.

**"Task queue and generate-evaluate-select are the same thing."** No. Different tools for different supervisory purposes. Generate-evaluate-select is multiple responses to *one task* for a single judgment. The task queue is multiple *different tasks* in parallel for separation of concerns.

**"The grading tool's pattern analysis should be a main-session step."** It can be. The task-queue approach is the optimization: pattern analysis is well-specified, does not require step-by-step supervision, and benefits from running while you do other work. If your build is short enough that synchronous is fine, synchronous is fine.

---

## Exercises

1. **(Apply)** During your next grading-tool build session, fire off three task-queue items for tangential ideas (capture the *what* and *why* of each in a sentence). Return to each before the session ends. Document which returns you evaluated and which you would have forgotten to evaluate if not for this exercise.

2. **(Apply)** Define a task queue item for pattern analysis across student submissions in your grading workflow. Specify: input directory, output location, output format, handoff condition, and what the negative constraint protects against.

3. **(Analyze)** Compare a session in which you pursued a tangential idea inline (interrupting the main build to chase it) vs. a session in which you fired it as a task queue item. What was different about the main build's context, focus, and output quality?

---

## Classroom activity

Have students use the task queue to fire off a research task (Ask Mode: *"what are common approaches to handling X in this kind of project?"*) while continuing their main build. They evaluate the return when it arrives. They document:

- The task they fired and why.
- The return they received.
- Whether the return was useful enough to incorporate into the main build, or whether evaluating it taught them something else (the discipline of evaluating returns is the point, not the tool's specific usefulness for this task).

This activity maps to the conducting framework's context-management chapters in the students book. Use your own task-queue experience as the teaching example.

---

## Links

- Codex app and parallel tasks: [openai.com/index/introducing-the-codex-app](https://openai.com/index/introducing-the-codex-app/)
- Codex pricing and plan availability: [developers.openai.com/codex/pricing](https://developers.openai.com/codex/pricing)

---

## What would change my mind

The chapter's claim is that **the task queue improves session focus and output quality** when it is used with discipline (evaluate every return). If a controlled comparison showed teachers who used the task queue produced no measurably better main-session output than teachers who did inline tangents — and showed equivalent total time spent — the task queue becomes a feature rather than a discipline. The book would still introduce it for its workflow benefits; it would not require a chapter.

I expect the difference to be real but modest. The chapter's argument is structural (separating concerns helps) and the data, when it exists, will likely confirm it.

---

## Still puzzling

- **Auto-memory across task-queue sessions.** Codex's auto-memory feature accumulates learnings across sessions without the teacher writing them down. Whether task-queue items should share or separate auto-memory from the main session is an active practitioner discussion. The book sidesteps the question; the practical answer for K-12 teachers is to keep them separate until you understand the implications.

- **Agent teams.** The 2026 Codex app supports coordinating multiple specialized agents on different tasks. This is beyond the book's scope but is the natural extension of the task queue. For teachers in 2027–2028, agent teams may become a regular pattern. The conducting discipline still applies; the surfaces multiply.

- **The forgotten-return problem.** Empirically, what fraction of task-queue items get evaluated vs. forgotten? Practitioner anecdotes suggest the forgotten share is uncomfortably high. Whether the discipline of evaluating returns can be reliably built in K-12 teacher workflows is an open question. If you cannot make yourself evaluate returns, do not fire tasks.

---

##  AI Wayback Machine
 **Herbert Simon** (1916–2001) — Nobel laureate (Economics, 1978) whose paper *The Architecture of Complexity* (1962) introduced the concept of **nearly decomposable systems**: complex systems can be productively analyzed and built when they decompose into subsystems with strong internal coupling and weak external coupling.[^3] Simon's argument: the brain can manage complexity precisely because it can break large problems into nearly independent subproblems, solve each in isolation, and integrate the results. The task queue is Simon's nearly decomposable system applied to AI-assisted builds. Each task-queue item is a subproblem with strong internal coupling (the task is self-contained) and weak external coupling (the result returns as a summary, not as a context-bloat). The main session integrates. *(The pantry research recommended Carl Hewitt's actor model — independent agents communicating through messages — as a substantively closer match to the task queue's literal architecture. Either Simon or Hewitt is defensible; the book uses Simon for series consistency with the student book.)*

---

## Bridge

You have the full conducting framework. The Bridge chapter that follows is Seth's voice — the moment his builds stopped being about productivity and started being about what he could make that didn't exist before. After the Bridge, Act Three asks: what is the build you want to make for *your students*?

---

[^1]: OpenAI, "Introducing the Codex app" (openai.com/index/introducing-the-codex-app/). The parallel-task UI is the Codex app's organizing affordance as of 2026.
[^2]: OpenAI engineers, "How OpenAI Engineers use Codex to Tackle Big Projects with Rigor" (forum.openai.com, December 4, 2025).
[^3]: Simon, H. A. "The Architecture of Complexity." *Proceedings of the American Philosophical Society* 106, no. 6 (1962): 467–482. Republished in Simon's *The Sciences of the Artificial* (MIT Press, 3rd ed. 1996).
