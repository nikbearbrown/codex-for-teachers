# Chapter 13 — Teaching the Discipline: What Your Students Are Reading

> Your students have the Codex students book. This chapter maps what they're learning to what you now know how to teach.

---

## Learning outcomes

1. **(Apply)** Map each chapter of the students book to a classroom activity using the teacher's built tools as context.
2. **(Apply)** Design an assessment requiring students to document their supervisory capacity use during a build.
3. **(Analyze)** Distinguish the teacher's role in a conducted student build from the role in a traditional coding class.

---

## Opening

You sit down to read Chapter 5 of *Codex for Students* — the five supervisory capacities, from Seth's perspective.

You recognize what he is describing.

You did not recognize it twelve weeks ago. Twelve weeks ago, the five capacities would have read as abstract framework: plausibility auditing was a phrase; problem formulation was a concept. You would have grasped them intellectually. You would not have been able to *teach* them, because you did not have an inside view of what they felt like when they fired.

Now you do. You have the moment from Chapter 5 of this book — the moment you almost shipped the grading-tool feedback that was technically accurate and pedagogically wrong. You have the scope-creep moment from Chapter 11 — Codex offering the size selector, you logging it and declining. You have the screenshot-iterate moment from the mobile-responsiveness build. You have lived twelve weeks of supervisory work and you can now read the students book and recognize, in your own practice, what Seth is naming.

This chapter is the bridge between what you have lived and what you can now teach.

---

## The students book chapter map

The mapping is direct. Each chapter of the students book corresponds to a build experience you have had in this book and to a classroom activity you can design around that experience.

<!-- → [TABLE: Students book chapter map — chapter number, what students learn, corresponding teacher build experience, suggested classroom activity. 14 rows. No color.] -->

| Student Ch | Students learn | Teacher build experience | Suggested classroom activity |
|---|---|---|---|
| 0 | Seth's observation: homework/quiz gap | The Introduction (Ch 0 of this book): you meet Seth as co-practitioner | Discuss in class: when have you seen a peer "use AI" in a way that made you uneasy? |
| 1 | The neurobiological mechanism | The website's first specification (Ch 3); the cost of a vague prompt | Reader audit: list three recent AI uses; classify each as borrowed vs. built capability |
| 2 | What students vs. Codex are good at | The grading-tool labor split (Ch 7) | Classify ten tasks as Codex-work, human-work, or dangerous middle |
| 3 | The teacher-student AI gap | Your own AP CS reality; the Anthropic 48.9% finding | Validation discussion — students name the gap they've felt |
| 4 | Conducting: prompting → conducting | Ask Mode / Code Mode gate from Chs 1–3 | Apply the gate to a peer-supplied prompt; document the difference |
| 5 | The five supervisory capacities | Your grading-tool moment (Ch 5 of this book) | Label a build transcript by capacity |
| 6 | AGENTS.md (or the equivalent in the students book) | Your three-tier AGENTS.md (Chs 2, 7, 10) | Write an AGENTS.md for a student project |
| 7 | Problem formulation | The Ch 7 grading-tool problem-frame work | One-sentence test on a peer's project |
| 8 | Specifications as prompts | Your specifications across builds | Rewrite a weak prompt as a five-element spec |
| 9 | Handoff conditions and the dangerous middle | Your Ch 4 and Ch 8 experiences | Write handoff conditions for a five-step task; identify one dangerous-middle case |
| 10 | The Brutalist three-file system for creative builds | Your three files from Ch 10 | DESIGN.md for a student creative project |
| 11 | Planning the first build | Your simulation architecture (Ch 10) | Plan a student-scale shell or web build |
| 12 | Running the build | Your Ch 11 simulation execution | Execute a build with a build log |
| 13 | Verification | The three-check verification from Ch 12 of this book | Run the three checks on a peer's build |
| 14 | The first full build | Your post-build document (Ch 14 of this book) | Complete the student's own first full build + write a post-build document |

The table is the chapter. Everything else in this chapter is how you *use* the table.

---

## Using your built artifacts as teaching material

You have three tangible artifacts from this book. Each is a teaching artifact.

**Your AGENTS.md, three tiers deep.** Show it to your students. *"Here is the AGENTS.md I started with for the class website. Here is what I added when I built the grading tool. Here is the simulation's subdirectory AGENTS.md. Notice how the lessons-learned section grew."* The students see what a maintained AGENTS.md looks like, from a real project, with real lessons. The students book describes AGENTS.md from the student angle; your AGENTS.md is the example.

A note on what to share: most of AGENTS.md is fine to share verbatim. The lessons-learned section may contain context — student names, sensitive details, school-specific information — that should be redacted before sharing. The conducting practice extends to this: read your AGENTS.md as a publishable document and redact what should not be public.

**Your grading-tool flagging report.** Show it to your students. *"Here is the report the tool produces. Here is what I do with it — I read each draft, write the actual feedback by hand, deliver what I wrote. The tool is the first-draft pattern-flagger. The feedback is mine."* The students see, concretely, what the narrowing principle (Chapter 8) looks like in operation.

**Your simulation, plus the build log.** Show the simulation. Then show the build log — the actual specifications, the actual handoff conditions, the actual revision when Phase 3's end-signal failure was caught. Students see what *conducting* looks like across a full build, from someone they know.

These three artifacts are what *you* have that the students book does not. The students book teaches the discipline. Your artifacts show the discipline operating in a teacher's real practice.

---

## Assessment design for the discipline

The traditional CS-class assessment is on the *code*. The student writes code; the teacher grades the code; the grade is on the output.

The conducting discipline requires a different assessment. The student writes code *with Codex*; the relevant capacity is not the code (Codex did a lot of it) but the *supervisory work the student did*. The assessment has to be on the supervisory work.

The instrument: the **build log**, peer-reviewed.

A build log captures, for each significant step in the student's build:

- The specification prompt (or a summary).
- The Ask Mode plan review (was anything corrected?).
- The handoff condition (was it specific, testable, binary?).
- Whether the handoff condition passed or failed; if failed, what was the revert and respecification.
- The supervisory capacity exercised at the step (PA, PF, TO, IJ, EI; one or two per step).
- Anything generate-evaluate-select was used for; the selection reasoning.

The build log is not the code. It is the *meta-artifact* describing how the code was built. Peer review is on the build log, not on the code. The peer evaluates whether the log is honest, whether the capacity labels are right, whether the dangerous-middle moments were named.

A rubric for the build log might score:

- **Completeness:** Are the major build steps documented? (Yes/Partial/No)
- **Honesty:** Does the log name failures and reverts, or does it present only success? (A log with no failures is suspect.)
- **Capacity labeling:** Are PA/PF/TO/IJ/EI used appropriately? (Mislabels are a learning moment, not necessarily a deduction.)
- **Plausibility-audit cases:** Are at least one or two named where PA caught what a handoff condition would not have?
- **Dangerous-middle awareness:** Did the student name any cases where output passed conditions but felt wrong?

The grade is on the supervisory work. The grade reflects whether the student exercised the conducting discipline, not whether Codex produced the right code.

---

## The teacher's role during a student build

Once you assess on the build log, the teacher's role during student work changes.

Traditional CS-class teacher role: walk around, watch students debug, help fix the code that is not compiling.

Conducting-class teacher role: walk around, watch students *conduct*, ask supervisory-capacity questions:

- *"What was your handoff condition for this step? Did it pass?"*
- *"What did the Ask Mode plan say? Did you correct anything before approving?"*
- *"What does this output do that the specification did not ask for?"*
- *"Did you generate-evaluate-select on this? Why or why not?"*
- *"Why did you decide to use Codex here rather than write this part by hand?"*

These are not gotcha questions. They are the questions the student should be able to answer because they have done the supervisory work. If the student cannot answer, the conducting discipline was not exercised, and the gap is now visible — to you and to them.

This is the role-shift the Geoffrey Challen insight captures:

> *"The challenge now isn't turning specifications into code — Codex is really good at that. The challenge is getting your idea out of your own brain and into a specification so the coding agent can do the rest. Teaching specification writing IS CS education."*[^1]

You are no longer the code-debugging teacher. You are the specification-coaching teacher. The student's specifications, handoff conditions, capacity labels — these are the work you are teaching.

---

## Common misconceptions

**"Teaching the discipline is just assigning the students book."** No. The discipline is built through practice; the students book is the conceptual map. Your teaching is the practice scaffolding. The two together are the curriculum.

**"My AGENTS.md is too personal to share."** Some of it. Most of it is not. With redaction (sensitive paths, credentials, student-name references), most AGENTS.md is shareable.

**"Build logs are too much work to grade."** Peer review reduces teacher load. A rubric that focuses on five clear criteria (above) makes the peer review tractable. The grading load is comparable to grading code; the pedagogical signal is much higher.

**"Students won't see my framework as authority."** They will if you have lived it. The AGENTS.md spanning three build tiers, the grading tool flagging reports, the deployed simulation are not borrowed authority; they are demonstrated practice. *(The teacher who has not built anything cannot teach this without borrowing all the examples from the students book. Your builds are what your authority rests on.)*

**"This is just for AP CS students."** The discipline is. The specific tools (Codex, the Codex app) may evolve; the framework is tool-agnostic and applies wherever students are using agentic AI to produce work that should reflect their own thinking. The applicability is broader than AP CS.

---

## Exercises

1. **(Apply)** Design a build log template for your students. Include: specification prompt, Ask Mode plan review notes, handoff condition, capacity label, dangerous-middle catches. Test the template on your own most recent build to verify it captures what matters.

2. **(Apply)** Create a rubric for assessing the build log that is separate from the rubric for the code. The build-log rubric should produce a meaningful score independent of whether the final code works.

3. **(Evaluate)** What is the hardest supervisory capacity for your students to exercise? Design a classroom activity that isolates and practices that specific capacity. (For most teachers, the answer will be PA — plausibility auditing requires domain knowledge that students are still building.)

---

## Classroom activity

The teacher designs an end-of-term assessment requiring students to submit a build log alongside their code. The build log is the primary grading artifact. The code is verification that the discipline produced something working — but the grade reflects the *practice*, not the *artifact*.

Peer review: students exchange build logs (not code). Peers evaluate against the rubric. The teacher reads a sample, calibrates with peer scores, and applies the calibration across the class.

This activity is the one that makes the entire book operational. It is what your students will remember in five years.

---

## Links

- *Codex for Students*: the companion book.
- Geoffrey Challen, "A Day With Claude: Using and Teaching Coding Agents" (January 2026): [geoffreychallen.com/talks/2026-01-15-a-day-with-claude-using-and-teaching-coding-agents](https://www.geoffreychallen.com/talks/2026-01-15-a-day-with-claude-using-and-teaching-coding-agents) — the closest contemporary statement of "specification-writing IS CS education."
- Lee Shulman, "Those Who Understand: Knowledge Growth in Teaching" (1986) — the canonical reference for pedagogical content knowledge.

---

## What would change my mind

The chapter's strong claim is that **build-log-as-assessment** materially shifts what students learn, in a direction that aligns better with the actual cognitive work the conducting discipline requires. If a controlled comparison — same AP CS class, with and without build-log assessment — found no measurable difference in student conducting fluency or in transfer to unassisted work, the build-log instrument is no longer essential. The discipline could still be taught; the assessment would be back to the code.

I expect the difference to be real. The argument is that you cannot reliably assess the discipline by inspecting the code (Codex did most of the typing). The build log is the trace of the discipline. Assess the trace.

---

## Still puzzling

- **The CLAUDE.md redaction question.** Sharing your AGENTS.md with students is recommended; redaction is necessary. What exactly to redact varies by school, district, student. The chapter cannot specify; the practitioner has to judge.

- **Build-log scale.** A build log for a 30-step build is itself an artifact of meaningful size. Whether students will write thorough build logs or will satisfice into checklist theater is an open practitioner question. The peer-review structure is the proposed answer; whether it works at scale across an entire class is empirically untested.

- **Whether to grade build logs strictly or as formative.** Some teachers will grade strictly; some will use the logs as formative artifacts in conferences with students. Both are defensible. The chapter is agnostic; the book argues for whichever works in your classroom.

---

## AI Wayback Machine

🕰️ **Lee Shulman** (born 1938) — educational psychologist whose 1986 paper *Those Who Understand: Knowledge Growth in Teaching* introduced the concept of **pedagogical content knowledge (PCK)** — the specific knowledge a teacher needs that is *neither* pure subject knowledge *nor* pure pedagogy, but the integrated knowledge of *how to teach this particular subject to learners at this particular level*.[^2] Shulman's argument was that domain expertise and teaching expertise are different competencies, and that expert teaching requires a third competency — PCK — that is built only through the practice of teaching the specific subject. The teacher who has built three classroom tools with Codex has *PCK for AI-assisted classroom work* in a way the teacher who has only used Codex for lesson plans does not. The Mishra & Koehler extension to TPACK (2006) added *technology* to the framework: pedagogical content knowledge for technology-integrated teaching is a fourth competency, built through technology-integrated practice. This book has been Shulman applied to Codex: PCK + technology, built through three builds, applied to teaching.

---

## Bridge

The discipline is taught. Chapter 14 is what the book has been pointing at all along — the post-build document that records what you built, what you delegated, what you kept, what you learned, what you would do differently.

---

[^1]: Challen, G. *A Day With Claude: Using and Teaching Coding Agents*. Illinois CS faculty retreat presentation, January 15, 2026.
[^2]: Shulman, L. S. "Those Who Understand: Knowledge Growth in Teaching." *Educational Researcher* 15, no. 2 (1986): 4–14. Mishra and Koehler's TPACK extension: *Teachers College Record* 108, no. 6 (2006): 1017–1054.
