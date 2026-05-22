# Research: Chapter 7 — Building the Grading Tool: Full Build Arc
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** The grading tool is the Act Two build. Every prior concept — AGENTS.md, Ask Mode / Code Mode gate, specifications, handoff conditions, supervisory capacities, Best-of-N — applied to a build that matters.

**Research date:** 2026-05-21

---

## 1. Primary Sources

### Foundational papers and texts

**TIKTOC names Schön here. Schön is also at Ch 11 and Ch 14. Triple-booking. Recommendation: keep Schön at Ch 7 (most directly about reflection-in-action during build), swap Ch 11 to Wanda Orlikowski, Ch 14 to bell hooks. See terminal summary.**

- **Schön, Donald A. *The Reflective Practitioner*. Basic Books, 1983.** Reflection-in-action.
- **Beyer, Betsy et al. *Site Reliability Engineering*. O'Reilly, 2016.** Runbook practice; iterative discipline. Open access at sre.google.
- **Anthropic Education Report (2025).** 48.9% automation-heavy grading finding. Useful context.
- **OpenAI engineer-voice posts (Dec 2025).** Build-discipline lineage.

### Key empirical cases

- **Teacher's complete grading-tool build (TIKTOC).** Built step by step with full conducting sequence. Author + Seth + teacher contributor must produce. TIKTOC adoption risk #4 calls for contributor with K-12 classroom Codex experience.
- **AGENTS.md update across the build.** Lessons-learned grows. Show before/after.
- **The narrowing principle in practice.** Codex flags patterns; teacher writes feedback. Cross-references Ch 8.

---

## 2. The Core Concept — State of the Field

### What is settled

- **Iterative AI builds with verification beat single-shot.** Established.
- **AGENTS.md shapes generated output.** Vendor-confirmed.
- **Scope verification catches most grading dangerous-middle errors.** SRE / DevOps practice.

### What is disputed

- **From-scratch vs. extending a template.** Book takes from-scratch position; defensible.
- **Python vs. bash for grading tools.** Mixed (likely Python for AST work; bash for orchestration).
- **Whether to share grading tool as teaching artifact.** TIKTOC implies yes (Ch 13). Strong position.

### What has changed recently (last 5 years)

- 2025–2026 LLM grading accuracy improvements (Ch 8) make pattern-detection more capable.
- Codex's plan mode / Ask Mode formalizes per-step approval.

---

## 3. Application Domain Examples

(Domain coverage map: Ch 7 sits in grading tool — Act Two build.)

The full grading-tool build:

- **Phase 1: survey.** Spec names directory, file patterns, exclusions. Handoff: file list matches teacher expectation.
- **Phase 2: section-presence check.** Spec names regex patterns, case-sensitivity, conventions. Handoff: count of missing sections.
- **Phase 3: function-count + docstring detection.** Spec names AST tools (Python `ast`), docstring conventions. Handoff: counts match teacher sample review.
- **Phase 4: first-draft feedback generation.** Spec names tone, rubric mapping, explicit "first draft" labeling. Best-of-N (technique) on this step.
- **Phase 5: output + review queue.** Spec names file layout. Handoff: every submission has draft; none marked final.

CAVEAT: phases 4 onward must apply Ch 8's narrowing principle. The chapter is the build; Ch 8 is the rethink.

---

## 4. The Book's Thesis Connection

Ch 7 is where framework becomes deployed tool. Every prior concept applied at higher stakes.

Contribution:
1. **Discipline at full complexity.**
2. **AGENTS.md as living artifact.**
3. **Working tool by end of Ch 7.**

Student-supplied capacity: every grading judgment — missing section criteria, feedback tone, "good enough" thresholds.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: Donald Schön (1930–1997).** Strong fit BUT triple-booked across Ch 7, 11, 14.

Recommendation: **keep Schön at Ch 7.** Ch 11 → Orlikowski. Ch 14 → bell hooks. See terminal summary.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Act One framework + Ch 5 (capacities) + Ch 6 (Best-of-N technique).

### Common misconceptions to disarm
- **"Full tool is overkill."** Full tool is the point.
- **"Skip framework on easy phases."** Easy phases hide dangerous middle.
- **"AI generates; I review."** No. *Teacher writes specifications*; specification is the work.

### Effective instructional sequences
- **Walk through five phases.**
- **Show AGENTS.md update at each phase.**
- **Classroom activity** (TIKTOC): simpler student version (rubric self-checker).

### Known failure modes
- **Code-walkthrough chapter.** Discipline is content.
- **Over-engineering.** Student-scale.
- **Skipping AGENTS.md updates.** Visibility matters.

### What separates understanding from memorization
A reader who *understands* Ch 7 has built their own grading tool through five phases with AGENTS.md updates. A reader who memorized Ch 7 describes phases without producing tool.

---

## 7. Representation and Display Research

TIKTOC does not specify figures. Optional:
- **Grading-tool architecture diagram.** Five phases horizontal with AGENTS.md growing across.
- **AGENTS.md before-and-after.** Two columns.

---

## 8. Open Questions and Research Gaps

- **K-12 contributor (TIKTOC adoption risk #4).** Critical. Don't draft without classroom experience.
- **Python vs. bash boundary.** Decide before drafting.
- **Open-source release of grading tool.** Strong adoption play.
- **Schön over-booking.** Recommend swap at Ch 11 and Ch 14.

---

## 9. Sourcing Notes

- **Schön 1983** — Basic Books.
- **Beyer et al. 2016** — open access sre.google.
- **Anthropic Education Report 2025** — anthropic.com.
- **OpenAI engineer-voice posts** — forum.openai.com Dec 2025.
