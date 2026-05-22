# Research: Chapter 9 — The Task Queue: Keeping the Build Clean
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** The task queue captures tangential ideas and parallel work without breaking the main build's focus.

**Research date:** 2026-05-21

---

## 1. Primary Sources

### Foundational papers and texts

- **OpenAI. Codex app documentation (openai.com/index/introducing-the-codex-app/, chatgpt.com/codex/, developers.openai.com/codex).** Canonical for the task queue. As of 2026, Codex queues parallel tasks in separate cloud containers; the Codex app is built around managing multiple parallel agents. Available on Free (rate-limited), Go, Plus, Pro, Business, Enterprise, Edu.
- **OpenAI. "How OpenAI Engineers use Codex" (forum.openai.com, Dec 2025).** TIKTOC quotes: "Fire off tasks to capture tangential ideas, partial work, or incidental fixes. There's no pressure to generate a full PR in one go." And: "I was in meetings all day and still merged 4 PRs because Codex was working in the background."
- **Simon, Herbert A. "The Architecture of Complexity." *Proceedings of the American Philosophical Society* 106, no. 6 (1962): 467–482.** Nearly decomposable systems. The task queue is Simon's decomposition.
- **Simon, Herbert A. *The Sciences of the Artificial*, 3rd ed. MIT Press, 1996.** Decomposition.
- **Beyer, Betsy et al. *Site Reliability Engineering*. O'Reilly, 2016.** Runbook + work-queue patterns. Open access sre.google.

### Key empirical cases

- **Teacher's "noticed a related improvement" moment (TIKTOC opening).** Mid-Code-Mode. Pursue now → break focus. Task queue is answer.
- **Pattern-analysis task queue item.** Reads submissions, identifies misconceptions, returns structured report — without interrupting main grading session.
- **The "meetings all day, 4 PRs" pattern.** TIKTOC quotes OpenAI's flagship case. Teacher version: "teaching class, Codex analyzing submissions in background."

---

## 2. The Core Concept — State of the Field

### What is settled

- **The task queue exists as a Codex feature.** OpenAI-documented. Confirmed for 2026 Codex app.
- **Parallel cloud-container execution.** Confirmed.
- **Plan availability.** Plus and above. Rate limits vary; Pro has 5× the Plus rate.

### What is disputed

- **When to use task queue vs. /clear vs. fresh session.** Practitioner consensus evolving. Recommendation: task queue for clear input/output with isolated context need; fresh session for major topic switch.
- **Whether to use task queue for high-stakes work.** Each task queue return still requires supervisory evaluation; the task queue doesn't reduce supervisory work, it relocates it.

### What has changed recently (last 5 years)

- The Codex app's multi-agent UI (2025–2026) made parallel-task management mainstream.
- Earlier Codex CLI required manual parallel sessions; the app provides UI.
- 2026 Codex Skills + Automations interact with task queue (Skills can be invoked from tasks).

---

## 3. Application Domain Examples

(Domain coverage map: Ch 9 sits in grading tool — task queue during grading-tool build.)

- **Pattern-analysis task queue item.** Specification: read all submissions under `submissions/<assignment>/`; identify top 5 common misconceptions with examples; return structured report. Main grading session continues.
- **Research task queue item.** "What are common approaches to teaching late-submission policy in CS classrooms?" Ask Mode-style. Returns when ready; main build proceeds.
- **Draft-generation task queue item.** "Generate three first-draft feedback templates for missing-docstring flags." Returns three drafts; teacher selects in next Code Mode session.

---

## 4. The Book's Thesis Connection

Ch 9 closes Act Two. Teacher has grading tool with AGENTS.md, Ask/Code gate, specifications, handoff conditions, Best-of-N technique (Ch 6), task queue. Experienced dangerous middle (Ch 8). Gate 2.

Contribution:
1. **Context management as discipline.**
2. **Parallel work without breaking focus.**
3. **Each task queue return requires same supervisory evaluation.**
4. **Closes Gate 2.**

Student-supplied capacity: deciding *what* to delegate to task queue. Scoping is teacher's.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: Herbert Simon (1916–2001).** **DOUBLE-BOOKED with Ch 6** (Simon for satisficing/Best-of-N).

Candidates:
- **Herbert Simon** — named. Decomposition. Substantive fit excellent here.
- **Carl Hewitt** (born 1944, USA, computer scientist). Actor model — independent agents communicating through messages. Substantive fit very strong for task queue (closer than Simon's decomposition, actually). Same diversity profile.
- **Allen Newell** (1927–1992, USA, CS). Cognitive architecture with Simon. Same diversity profile.

Recommendation: **swap Ch 6 to Klein (RPD); keep Simon at Ch 9 (decomposition).** Resolves double-booking. Klein at Ch 6 is substantively stronger; Simon at Ch 9 is substantively perfect.

**Alternative:** keep Simon at Ch 6 (satisficing), swap Ch 9 to Hewitt (actor model). Actor model is more precisely about isolated agents-with-messages, which is the task queue's literal architecture.

Either way: don't double-book.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Ch 5 (capacities) + Ch 6 (Best-of-N technique). Teacher mid-grading-tool build.

### Common misconceptions to disarm
- **"Task queue is for power users."** No — the Codex app is built around it.
- **"More parallel tasks = better."** Each return needs supervision.
- **"Task queue replaces supervision."** No — relocates.
- **"Task queue and Best-of-N are the same."** No — Best-of-N is multiple responses to one task; task queue is multiple tasks in parallel.

### Effective instructional sequences
- **Build the pattern-analysis task queue item live.** Apply-level exercise.
- **Show before/after main session context.** Task queue keeps main session clean.
- **The Anthropic 48.9% finding revisited.** Task queue is the discipline that lets teachers do grading work without abandoning supervision.

### Known failure modes
- **Power-user lecture.** Keep teacher-accessible.
- **Over-specifying task queue prompts.** Brief, clear, well-scoped.
- **Task-queue-as-fire-and-forget.** Each return needs evaluation.

### What separates understanding from memorization
A reader who *understands* Ch 9 has fired off a pattern-analysis task queue item, evaluated the return against supervisory criteria, and decided whether to act on it. A reader who memorized Ch 9 describes the queue without using it.

---

## 7. Representation and Display Research

TIKTOC specifies one figure:

- **`<!-- → [DIAGRAM: Main build session vs. task queue.] -->`** Worked content:
  - Main session: focused Code Mode, one step at a time, full supervisory attention.
  - Task queue: background tasks captured and deferred; isolated contexts.
  - Arrows: tasks fire off; returns evaluated and integrated.
  - Editorial style.

---

## 8. Open Questions and Research Gaps

- **Plan availability for task queue.** TIKTOC OQ-6. Confirmed: Plus and above. Free tier rate-limited. Edu/Business/Enterprise have higher capacity.
- **Simon double-booking.** Recommend swap as in Section 5.
- **Gate 2 acceptance criteria.** TIKTOC names. Chapter must end with concrete checklist: grading tool + AGENTS.md + Ask/Code gate + handoff conditions + Best-of-N technique + task queue + experienced dangerous middle.
- **Codex Skills + Automations.** Newer 2026 features; brief mention.

---

## 9. Sourcing Notes

- **OpenAI Codex app docs** — openai.com/index/introducing-the-codex-app/, chatgpt.com/codex/, developers.openai.com/codex.
- **OpenAI engineer-voice posts** — forum.openai.com Dec 2025.
- **Simon 1962** — open access via APS.
- **Simon 1996** — MIT Press 3rd ed.
- **Beyer et al. 2016** — open access sre.google.
- **Hewitt sources** if swapping: actor model papers (1973+); Hewitt's MIT page.
