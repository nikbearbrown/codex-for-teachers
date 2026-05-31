# Chapter 7 — Building the Grading Tool: Full Build Arc


## TL;DR

- This chapter gives a working overview of Building the Grading Tool: Full Build Arc, focusing on the ideas a reader needs before moving to the next chapter.
- The chapter moves through Learning outcomes, Opening, The scope, narrowed before we begin, The grading tool's AGENTS.md, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

> The grading tool is the Act Two build. Every prior concept — AGENTS.md, Ask Mode → Code Mode gate, specifications, handoff conditions, supervisory capacities, generate-evaluate-select — applied to a build that matters.

---

## Learning outcomes

1. **(Apply)** Build a grading tool through the complete conducting sequence: Ask Mode plan → Code Mode execution → handoff conditions → verification.
2. **(Apply)** Use generate-evaluate-select on the step requiring the most pedagogical judgment.
3. **(Analyze)** Identify which steps in the build required which supervisory capacities.

---

## Opening

You have everything you need.

You have an AGENTS.md for your project. You have practiced the Ask Mode → Code Mode gate on the class website. You have written specifications, not requests. You have built handoff conditions that catch silent failures. You have named the five supervisory capacities and labeled them in a build sequence. You have used generate-evaluate-select on a step where pedagogical judgment mattered.

Now you use all of it, in one build, on a tool that — if it goes wrong — affects your students' work.

The grading tool is Act Two's central build. It is also where the conducting discipline stops being theoretical. The class website's worst-case failure was a broken link. The grading tool's worst-case failure can be a misleading flag on a student's submission that you act on in your grade book. The stakes are real. The discipline is what handles the stakes.

---

## The scope, narrowed before we begin

The grading tool this chapter builds is *not* an automatic grader.

The book's stance, developed fully in the next chapter, is that AI grading of student work is appropriate only as a **first-draft pattern-flagger** that surfaces things for the teacher to look at — never as a producer of final grades or of feedback the teacher does not read. Chapter 8 explains why. Chapter 7 designs around it.

The tool will:

- Read student submissions from a directory you specify.
- Check each submission for the presence of required sections (configured per assignment).
- Count code metrics — functions, docstrings, lines of code excluding comments and blank lines — using AST analysis where possible.
- Flag patterns across the cohort: common missing sections, common misconceptions visible in the code, code-style outliers.
- Produce a **per-student flagging report** that lists what the tool noticed, with verbatim excerpts when relevant.
- Produce a **cohort pattern report** that summarizes what was common across the class.

The tool will not:

- Generate a numeric or letter grade.
- Produce feedback the teacher does not read before it is delivered.
- Modify the student's submission file in any way.
- Touch your grade book.

These are the things AGENTS.md will name as **never** rules. They are the operational form of the narrowing principle. We write them into the build before the build begins.

---

## The grading tool's AGENTS.md

Before any specification, write an AGENTS.md for the grading project. Five sections, the same format as Chapter 2.

```markdown
# AGENTS.md — Mr. Brown's AP CS Grading Tool

## Stack and build
- Python 3.11. No package manager beyond pip; no virtualenv per assignment.
- Single script per workflow phase: survey.py, check_sections.py, analyze_code.py,
  report.py. No build step.
- Output goes to ./reports/, never overwriting; each run timestamps a subdirectory.

## Code style
- Black formatting, type hints where they help, no enforcement.
- AST-based code analysis preferred over regex when the structure matters.

## Test and verification
- Each script has a `--dry-run` flag that prints what it would do without doing it.
- After any change to the analysis logic, run on the test submission set in
  ./tests/sample_submissions/ and compare output to ./tests/expected_output/.
- Final verification before running on real submissions: dry-run on real
  submissions, manual spot-check of 3 outputs.

## Architectural decisions
- Submissions are READ-ONLY. The tool never modifies a submission file.
- The grade book CSV (path: ~/teaching/grade-book.csv) is NEVER touched by
  this tool — read or write. Mention this in every spec.
- Per-student outputs are flagging reports, NOT final feedback. The teacher
  writes individual feedback after reading the flags.
- No numeric or letter grades in any output. EVER.

## Environment quirks and lessons learned
- Submissions arrive in mixed formats (.py, .ipynb, .zip). Convert all to .py
  before analysis. Keep originals.
- Some students submit with non-ASCII identifiers. Don't normalize; preserve.
- 2026-03-04: Codex tried to read student names from filenames and include
  them in the flagging report. Reverted. Anonymize at the script level —
  reports reference submission IDs, not names.
```

Notice the *never* rules. The grade book is named explicitly, with its path. Codex will respect the rule because the rule is concrete. Vague rules ("don't touch sensitive files") get ignored; specific ones ("never read or write `~/teaching/grade-book.csv`") get followed.

---

## Phase 1 — Survey

The first build step is the smallest possible thing: a script that lists the submissions and confirms the file inventory matches what you expect.

**Ask Mode interrogation:** *"Given the AGENTS.md, propose a survey.py that lists all student submissions in a directory I specify, handles the .py / .ipynb / .zip format mixing per the AGENTS.md, and prints a table of submissions found with format and basic file size. Read-only."*

Codex returns a plan. You read it. You notice that it proposes converting .ipynb files in place. You correct: *"Don't convert. List the formats. Conversion is a separate step."* You approve.

**Code Mode:** Codex generates `survey.py`. You run it on `./tests/sample_submissions/`. Output:

```
SUBMISSIONS FOUND: 5
  001.py          (1.2K)
  002.ipynb       (4.7K)
  003.zip         (8.1K)  contains: project/main.py, project/utils.py
  004.py          (2.3K)
  005.py          (1.8K)
```

**Handoff condition:** The script lists every file in the directory; reports format and size; does not modify any file; exits 0. All pass. Commit.

**Capacity exercised:** TO (tool orchestration — choosing survey before any deeper analysis), IJ (reading the output for plausibility — does this match your expected file inventory?).

---

## Phase 2 — Section-presence check

For an assignment that requires specific sections (`Methodology`, `Results`, `Discussion`), check each submission for their presence.

**Specification:**

> **Operation:** Implement `check_sections.py` that takes a submission file and a configuration listing required sections, and reports which are present and which are missing.
>
> **Invariants:** Does not modify the submission. Does not touch any file outside the reports directory. Submission file reads as-is.
>
> **Context:** AGENTS.md sections on code style and architectural decisions. The section-detection logic should use the markdown heading conventions in `tests/sample_submissions/001.py` (which has the format right) as the reference.
>
> **Output format:** A per-submission report in `./reports/YYYY-MM-DD/sections/{submission_id}.md` containing: submission ID, sections found, sections missing, brief excerpt of each section's first 50 characters as evidence.
>
> **Negative constraint:** Do not match section headers fuzzy; match exact (case-insensitive) or report missing. Do not infer that a section is "implicitly present"; either the heading is there or it isn't.

**Ask Mode plan:** Codex proposes. You review. The plan is clean except that Codex assumes sections will be in markdown comment headers (`# Methodology`). You confirm that's correct for your assignment format and approve.

**Code Mode:** Codex generates `check_sections.py`. Run on test submissions.

**Handoff conditions:**
- Output report exists for each test submission.
- Sections-found list matches what you'd find manually on the test set.
- No file outside `./reports/` modified.
- Excerpts are present and accurate.

You verify by spot-checking three of the five test outputs against the source submissions. Two match exactly. One has a missing-section flag that surprises you — submission 003 (the zip one) shows `Results` as missing. You look at the submission. The student put `Results` as a code comment (`# Results`) on a line that also contained code, and the parser missed it because it expected the section header on its own line.

This is a *plausibility audit catch*. The output looks fine; the count of sections-found is exactly what you'd expect; only the manual spot-check surfaces the failure. The fix is in the specification, not the code: tighten the section-header detection rule, or relax it. You decide to tighten (the rubric requires section headers on their own line; the student's submission was non-compliant; flagging it as missing is correct behavior). Update AGENTS.md to record the decision. Continue.

**Capacity exercised:** PA (catching the wrong note in the test output), PF (revisiting the frame on what "missing" means in this rubric), IJ (deciding the student's non-compliant header should be flagged).

---

## Phase 3 — Function-count and docstring detection

For Python submissions: count functions, flag missing docstrings.

This is the step where AST analysis matters. Regex for docstrings produces false positives (matching string literals that aren't docstrings) and false negatives (missing triple-single-quoted docstrings). Python's `ast` module reads the parsed structure directly and produces correct counts.

**Specification:**

> **Operation:** Implement `analyze_code.py` that takes a Python submission and reports: number of functions defined, number with docstrings, list of functions missing docstrings (by name and line number).
>
> **Invariants:** Read-only on the submission. Uses the `ast` module from the standard library; no external dependencies.
>
> **Context:** AGENTS.md sections on AST-preferred analysis and code style. For docstrings, accept either triple-double-quoted or triple-single-quoted strings as valid; both are PEP 257-compliant.
>
> **Output format:** `./reports/YYYY-MM-DD/code/{submission_id}.md` containing: function count, docstring coverage percentage, list of missing-docstring functions with line numbers and brief signatures.
>
> **Negative constraint:** Do not flag docstrings as missing based on quote style. Do not count nested helper functions inside `if __name__ == "__main__"` as missing docstrings (they conventionally don't need them in student work). Do not modify the submission.

**Ask Mode plan, Code Mode execution, handoff verification:** as before. The output for test submissions looks plausible. You spot-check.

**Capacity exercised:** PF (deciding to use AST not regex — frame shift), TO (choosing the standard library over an external dependency), PA on the verification.

---

## Phase 4 — First-draft feedback generation (with generate-evaluate-select)

This is the step where the technique from Chapter 6 earns its place.

The tool reads the per-submission flagging reports from Phases 2 and 3 and generates a first-draft feedback paragraph that the teacher reads, revises, and decides whether to deliver.

**Specification:** as in the Chapter 6 worked example. Operation: generate a first-draft feedback paragraph. Invariants: no numeric or letter grade; references at least two specific flagged items. Context: AGENTS.md's never rules; the per-student flagging reports from Phases 2–3. Output format: plain markdown to `./reports/YYYY-MM-DD/feedback/{submission_id}_draft.md`. Negative constraint: do not address student by name; do not assume the student has read the rubric; do not produce anything that reads as a final assessment.

You run the specification through generate-evaluate-select. Three responses. You compare. You select. You revise. You note the selection reasoning. **You also recognize, if all three responses share a problematic framing, that the problem is in your specification, not in the responses.**

**Handoff condition for this phase:** Every submission has a draft in `./reports/YYYY-MM-DD/feedback/`. No draft is labeled "final" or contains a grade. Each draft references at least two flagged items from the per-submission report. The teacher (you) has reviewed each draft and marked it: USE, REVISE, REWRITE.

**Capacity exercised:** PA (does this feedback fit *this* student?), IJ (the revision is where meaning is supplied), TO (the choice to use generate-evaluate-select rather than single-shot), EI (the final framing must be consistent with the never rules in AGENTS.md).

---

## Phase 5 — Output and review queue

The final phase aggregates: a cohort pattern report, plus a teacher review queue ordering the feedback drafts by your priority.

**Specification:** `report.py` reads all per-submission outputs from Phases 2–4 and produces (a) a cohort pattern report listing common missing sections, common code-style flags, common docstring patterns, with counts; (b) a teacher review queue listing each submission with its flag count and your assigned priority for the feedback review pass.

**Handoff condition:** Cohort report contains at least three identified patterns with counts. Review queue lists every submission. No submission is missing a feedback draft. No feedback draft is marked final by the script. The output is in `./reports/YYYY-MM-DD/SUMMARY.md` and the file is readable.

**Capacity exercised:** EI (this is the integration step — do all the prior phases produce a coherent whole that serves the actual task?), PF (does the cohort pattern report tell you something useful about the cohort, or is it just data?).

---

## What the build produces

By the end of the five phases, on a class of 30 students, you have:

- 30 per-student section-check reports.
- 30 per-student code-analysis reports.
- 30 first-draft feedback paragraphs, each marked USE/REVISE/REWRITE.
- One cohort pattern report.
- One teacher review queue.

Your job after the tool runs: read each first-draft feedback, write the actual feedback you will deliver (using the draft as a starting point or rewriting where needed), use the cohort report to plan the next class period's lesson around the common patterns you saw.

The tool saves you time on the survey, the section check, and the code analysis. It generates the starting material for feedback. **It does not write the feedback you deliver.** That distinction is the entire point of the narrowing scope, and it is what makes the tool defensible to use.

---

## The CLI.md grows

Open AGENTS.md. Add a lessons-learned entry:

```markdown
- 2026-03-19: The first run of analyze_code.py false-flagged docstrings as missing
  for triple-single-quoted strings (Python is fine; my regex was wrong). Fixed by
  switching to ast.get_docstring(). The AGENTS.md now specifies AST-preferred;
  if a future task seems to want regex for code analysis, push back.
- 2026-03-19: First batch of feedback drafts trended deficit-heavy. Used
  generate-evaluate-select with three candidates; the hybrid framing won.
  Future feedback prompts should include "include at least one specific strength
  before listing improvements" in the spec.
```

AGENTS.md is now a record of how the build matured. By the time you reach Act Three, it will be the most useful teaching artifact you have.

---

## Common misconceptions

**"Building the full tool is overkill."** Building the full tool is the point. Building only Phase 1 would not exercise the supervisory capacities the way the grading-tool stakes require. The full build is what makes the discipline real.

**"I'll skip the framework on the easy phases."** The easy phases (Phases 1 and 2 in this build) are exactly where the dangerous middle hides. The phase you skim is the phase that ships with a silent failure.

**"AI generates the tool; I review."** No. You wrote the specifications. You decided the scope. You revised the framing decisions. You wrote the AGENTS.md. The tool is yours; Codex built parts of it under your direction. The distinction matters because, when you teach this in Chapter 13, the lesson is *teacher-as-builder* — and that is only true if the teacher built.

**"My grading tool needs to do more than flag patterns; I want it to grade."** The narrowing principle in the next chapter is the argument for why this is the wrong design — even if it is the design pressure. The next chapter is the discipline that catches the design pressure before it produces a tool that disadvantages your most vulnerable students.

---

## Exercises

1. **(Apply)** Build Phase 1 (survey) of your grading tool using the complete sequence — AGENTS.md, Ask Mode plan, specification, Code Mode, handoff conditions. Run on your real submission directory in `--dry-run` first. Document each handoff condition's pass/fail.

2. **(Analyze)** For each phase you've built, label the supervisory capacity required at the riskiest step. Compare your labels to the worked example in this chapter. Where do they diverge? What does that tell you?

3. **(Evaluate)** At the end of your Phase 1 build: what would you change in the AGENTS.md? What would you change in the Ask Mode plan if you could rerun it?

---

## Classroom activity

Have students build a simpler version of the same tool — a *rubric self-checker* — that takes a single student submission and checks for the presence of required sections. Constraints:
- Same five-phase discipline (Ask Mode plan, specification, Code Mode, handoff conditions, verification).
- AGENTS.md for the student tool project.
- A handoff condition that explicitly catches a "looks fine but wrong" case.

Peer review: students exchange tools (not code). They run a peer's tool on their own submission. They report on whether the tool's handoff conditions caught the things they would expect a teacher to catch.

This activity maps to Chapter 7 of the students book — *Building the Grading Tool: Full Build Arc.* Your build experience is the example.

---

## Links

- OpenAI Codex documentation: [developers.openai.com/codex](https://developers.openai.com/codex)
- OpenAI engineer-voice retrospective: [forum.openai.com/public/blogs/how-openai-engineers-use-codex-to-tackle-big-projects-with-rigor-2025-12-04](https://forum.openai.com/public/blogs/how-openai-engineers-use-codex-to-tackle-big-projects-with-rigor-2025-12-04)

---

## What would change my mind

The chapter's strong claim is that **the conducting discipline scales** — that the same techniques (gate, specifications, handoff conditions, capacities, generate-evaluate-select) that worked at the class-website scale in Act One also work at the grading-tool scale in Act Two, just with higher stakes. If a controlled comparison of build quality between conducted and unconducted grading-tool builds found no measurable difference in tool quality or in teacher satisfaction with the tool, the chapter's "do the full discipline at the higher stakes" prescription weakens. The discipline would still help on the riskier steps; the case for applying it across all five phases would be in question.

---

## Still puzzling

- **Where is the right scope ceiling?** The grading tool in this chapter is intentionally scoped narrowly (flagging, not grading). The teacher who wants to build something more ambitious will push against the narrowing principle. Where the right ceiling sits — and whether it is the same ceiling for all subject areas — is a live practitioner question.

- **The build's reusability across teachers.** A grading tool built for one teacher's AP CS class is not portable to another teacher's class without revision. Whether teacher-built tools become shareable artifacts (with each teacher's AGENTS.md fork) is an open ecosystem question.

- **Python vs. other build languages.** This chapter uses Python because AST analysis is unusually clean in Python. The same tool in JavaScript or in pure bash has different shape. Whether the chapter's language choice is incidental or load-bearing is an open question for teachers in other curricula.

---

##  AI Wayback Machine
 **Donald Schön** (1930–1997) — philosopher of practice whose *The Reflective Practitioner* (1983) introduced the concept of **reflection-in-action**: the practitioner who thinks about what they are doing *while* they are doing it, adjusting in real time rather than only after the fact.[^1] Schön observed that experts in many fields — architects, therapists, urban planners — work by *reframing problems* during practice in response to what the situation reveals. The supervisory capacity labels in your build log are Schön's reflection-in-action made operational: by naming what you are doing as you do it (PA, PF, TO, IJ, EI), you make the reflection visible, durable, and teachable. Schön's book argued that this reflective practice is what distinguishes expert work from competent work. The conducting framework is built on Schön's claim. *(Author's note: Schön appears once here, on the chapter where reflection-in-action lands most directly. The book's final chapter — Ch 14 — originally also used Schön; the pantry research recommended swapping that one to bell hooks to avoid the over-use. See Ch 14.)*

---

## Bridge

The grading tool is built. Chapter 8 is about the hardest moment: when the tool produces output that passes every handoff condition you wrote and is still pedagogically wrong — and when that wrongness disadvantages specifically the students who are most vulnerable.

---

[^1]: Schön, D. A. *The Reflective Practitioner: How Professionals Think in Action*. Basic Books, 1983.
