# Research: Chapter 12 — Deploying in Class: From Build to Lesson
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** The simulation works in Code Mode. Now it has to work with 30 students who have never seen it.

**Research date:** 2026-05-21

---

## 1. Primary Sources

### Foundational papers and texts

- **Montessori, Maria. *The Montessori Method*. Frederick A. Stokes, 1912.** Self-correcting educational materials. Control of error. The "first 30 seconds" test applied to educational design.
- **Montessori, Maria. *The Absorbent Mind*. Henry Holt, 1949.** Prepared environments.
- **Norman, Donald A. *The Design of Everyday Things*, rev. ed. Basic Books, 2013.** Affordances and feedback. The simulation's user-facing surface.
- **OpenAI. ChatGPT Artifacts documentation.** Fastest path to shareable URL.
- **GitHub Pages documentation.** Free hosting alternative.
- **Beyer et al. *SRE book*. O'Reilly, 2016.** Production deployment discipline. Open access sre.google.

### Key empirical cases

- **Teacher's "student clicks something unexpected" (TIKTOC opening).** First classroom; simulation breaks. The chapter trains for this.
- **First-30-seconds test.** Student knows nothing; knows what to do without instructions.
- **Cross-class usability test.** Student from another group tries; builder observes.

---

## 2. The Core Concept — State of the Field

### What is settled

- **Classroom deployment differs from solo.** 30 students, multiple OS.
- **Graceful failure is requirement.** Silent failure in front of 30 students is worst-case.
- **Classroom observation reveals what no pre-deploy test catches.**

### What is disputed

- **Test on every machine or representative sample.** Three is practical.
- **Demonstrate failure modes to students.** Book argues yes — showing how it was fixed from feedback is itself a lesson in conducting.
- **ChatGPT Artifacts vs. GitHub Pages.** Either works.

### What has changed recently (last 5 years)

- ChatGPT Artifacts (2024+) enables sharing without setup.
- 2024–2026 Chromebook/BYOD push pronounces cross-platform variance.
- Student-AI interaction expectations have matured.

---

## 3. Application Domain Examples

(Domain coverage map: Ch 12 sits in simulation deployment.)

- **First-30-seconds failure.** Screen with no obvious start. Fix: "click here to start" affordance.
- **Unexpected-click failure.** Student clicks visually-styled-but-not-interactive element. Fix: remove styling or make interactive.
- **Mobile/Chromebook failure.** Touch events don't fire. Fix: explicit touch-event handling.

---

## 4. The Book's Thesis Connection

Ch 12 closes build-to-deploy loop. Deployment is new application of framework.

Contribution:
1. Names deployment work.
2. Student-facing verification protocol.
3. Classroom observation as conducting.

Student-supplied capacity: classroom observation. Only teacher.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: Maria Montessori (1870–1952).** Cross-series consistent.

Recommendation: keep Montessori. Substantive + diversity fit both strong.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Ch 11 (simulation built).

### Common misconceptions
- **"Works on my machine = works in class."** No.
- **"Pre-deploy is overkill."** < 15 min, saves a failed class.
- **"Failures are embarrassing."** Teaching opportunities.
- **"I'll fix during class."** No.

### Effective sequences
- **Three-check verification protocol.**
- **Graceful failure examples.** "Click here to retry" vs. silent break.
- **Revision-build cycle.**
- **Show students the fix** as meta-lesson.

### Known failure modes
- **Deployment-engineering chapter.** Classroom-specific.
- **Over-engineering verification.** Three checks.
- **"Perfect simulation" trap.** Most need revision.

### What separates understanding from memorization
A reader who *understands* Ch 12 has deployed simulation, run three-check verification, identified issue, conducted revision. A reader who memorized Ch 12 recites three checks without applying.

---

## 7. Representation and Display Research

TIKTOC specifies one figure:

- **`<!-- → [DIAGRAM: Student-facing verification pass — three checks.] -->`** Vertical:
  - Check 1: student who knows nothing knows what to do in 30 seconds?
  - Check 2: failure states informative or just broken?
  - Check 3: progression from easy to hard?
  - Binary pass/fail; revision-build path on fail.
  - Editorial style.

---

## 8. Open Questions and Research Gaps

- **Chromebook-specific guidance.** Sidebar.
- **Touch-event handling for tablets/phones.** Brief.
- **District-IT (OQ-3).** Reference appendix.
- **"Show the fix" lesson.** Pedagogically strong; sidebar.

---

## 9. Sourcing Notes

- **Montessori 1912 / 1949** — Frederick A. Stokes / Henry Holt.
- **Norman 2013** — rev. ed.
- **ChatGPT Artifacts docs** — openai.com / help.openai.com.
- **GitHub Pages docs** — pages.github.com.
- **Beyer et al. 2016** — open access sre.google.
