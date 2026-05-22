# Research: Chapter 11 — Building the Simulation: Conducting at Full Complexity
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** The three files are in place, the plan is approved. The build begins.

**Research date:** 2026-05-21

---

## 1. Primary Sources

### Foundational papers and texts

**TIKTOC names Schön here — also at Ch 7 and Ch 14. Triple-booking. Recommendation: keep Schön at Ch 7, swap Ch 11 to Wanda Orlikowski, Ch 14 to bell hooks.**

Sources for Ch 11 (independent of Wayback choice):

- **Deming, W. Edwards. *Out of the Crisis*. MIT Press, 1986.** PDCA at command granularity. (Already Ch 4 Wayback; reference.)
- **Spear & Bowen 1999.** Andon-cord; stop on abnormality.
- **Beyer et al. 2016.** SRE iterative discipline. Open access sre.google.
- **OpenAI engineer-voice posts** (Dec 2025). TIKTOC quotes: "Give it a mock and you say, build this web UI, it will get it pretty good. But if you iterate two or three times, often it gets it almost perfect."

### Key empirical cases

- **Seth's simulation build (TIKTOC).** Real prompts, real Codex outputs. Author + Seth produce.
- **Screenshot-and-iterate pattern.** Define target, screenshot, compare, iterate. Anchor case.
- **Best-of-N (technique, per Ch 6) on visual states.** Generate three approaches; evaluate against DESIGN.md.
- **Scope-creep moment.** "While I'm here" suggestions → log in PROJECT.md Layer 2, don't execute.

---

## 2. The Core Concept — State of the Field

### What is settled

- **Iterative builds with verification beat single-shot.**
- **Per-step approval reduces compounding error.**
- **Three-file system protects against drift.**

### What is disputed

- **Per-step gate speed cost.** Anthropic RCT: engagement patterns match or beat single-shot total time.
- **Autopilot for simulation builds.** Book argues against pure autopilot.
- **State-reset verification.** Manual before classroom deploy.

### What has changed recently (last 5 years)

- 2026 Codex app's parallel-task UI changes how scope creep is captured (use task queue, not main session).
- Screenshot-and-iterate is a 2025–2026 pattern; Codex can take screenshots via app/MCP.

---

## 3. Application Domain Examples

(Domain coverage map: Ch 11 sits in simulation.)

For sorting-algorithm simulation, Phase 1:
- **Step 1: HTML scaffold.** Spec: file structure, semantic elements, no styling. Handoff: validates; matches DESIGN.md interaction vocabulary.
- **Step 2: CSS with six variables.** Spec: which selectors use which variables. Handoff: visual matches DESIGN.md description.
- **Step 3: JS bubble-sort logic.** Spec: function signatures, data structure, step interface. Handoff: correct output on three test inputs.
- **Step 4: Step controls + keyboard.** Spec: exact key mappings. Handoff: works on three test paths.
- **Step 5: Mobile responsiveness.** Spec: breakpoint, expected layout. Handoff: Chrome devtools mobile renders correctly.

One rejection: Step 3 first version uses `setTimeout` for animation; doesn't match Step 4 step controls. Revert; respecify with explicit step-by-step (no auto-advance); re-run.

One scope-creep: Codex suggests insertion-sort viz "while I'm here." Logged to PROJECT.md Layer 2 + task queue (Ch 9). Not executed.

---

## 4. The Book's Thesis Connection

Ch 11 is framework in motion at full complexity. Teacher has all tools.

Contribution:
1. Framework in motion.
2. Three-file system in action.
3. Simulation works by end.

Student-supplied capacity: every step, decision about whether output serves pedagogical purpose.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: Donald Schön (1930–1997).** Triple-booked. **Recommend swap.**

Candidates:
- **Wanda Orlikowski** (born 1953, USA, MIT Sloan). Technology-in-practice. **Strongest alternate.** Woman, American, ongoing scholar.
- **Donald Schön** — keep at Ch 7 only.
- **Adele Goldberg** (born 1945, USA). Smalltalk.
- **Frances Allen** (1932–2020, USA). Compiler optimization.

Recommendation: **swap to Orlikowski.** Cross-series consistent with gh-copilot teachers Ch 11 and Claude Code teachers Ch 11 recommendations.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Full framework + Ch 10 (three files).

### Common misconceptions to disarm
- **"With three files, build runs itself."** Per-step gate remains.
- **"Skip explain on familiar commands."** No.
- **"Scope creep is fine."** Log; don't execute.

### Effective instructional sequences
- **Seth's full transcript annotated.** Every step capacity-labeled.
- **Three pivotal moments.** Handoff failure, scope creep, screenshot iteration.
- **Screenshot-iterate demo.**

### Known failure modes
- **Transcript dump.** Narrative + transcript.
- **Simulation as exhibition.** Pedagogical tool.
- **Over-claiming framework universality.**

### What separates understanding from memorization
A reader who *understands* Ch 11 has built Phase 1 of their own simulation with documented specifications and handoff conditions. A reader who memorized Ch 11 describes steps without producing working phase.

---

## 7. Representation and Display Research

TIKTOC specifies one figure:

- **`<!-- → [DIAGRAM: The simulation build loop.] -->`** Three files populated → Ask Mode plan → review/approve → Code Mode spec → execute → handoff check → pass/revert. Supervisory capacity at each human step. Editorial style.

---

## 8. Open Questions and Research Gaps

- **Seth's specific simulation (OQ-1).** Most acute here.
- **Schön over-booking.** Swap to Orlikowski.
- **Screenshot-and-iterate tooling status.** Verify 2026.

---

## 9. Sourcing Notes

- **Schön 1983** — Basic Books. (For Ch 7 only.)
- **Orlikowski 2000.** "Using Technology and Constituting Structures." *Organization Science* 11, no. 4: 404–428. Open access AOM.
- **Deming 1986** — MIT Press.
- **Spear & Bowen 1999** — HBR.
- **Beyer et al. 2016** — open access sre.google.
- **OpenAI engineer-voice** — forum.openai.com Dec 2025.
