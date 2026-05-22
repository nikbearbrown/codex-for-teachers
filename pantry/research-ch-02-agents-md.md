# Research: Chapter 2 — AGENTS.md: Your Coding Constitution
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** AGENTS.md is the file Codex reads at the start of every session. It is the difference between a Codex that knows your project and a Codex that guesses.

**Research date:** 2026-05-21

---

## 1. Primary Sources

### Foundational papers and texts

- **OpenAI. "Custom instructions with AGENTS.md – Codex" (developers.openai.com/codex/guides/agents-md).** Canonical. Documents the 2026 hierarchical discovery: `~/.codex/AGENTS.md` global → project root → subdirectories. Codex reads `AGENTS.override.md` first if present, then `AGENTS.md`, then fallback names. Concatenates files from root down, joined with blank lines. **32 KiB combined size limit** (`project_doc_max_bytes`). Fallback filenames: AGENTS.override.md → AGENTS.md → TEAM_GUIDE.md → .agents.md.
- **OpenAI Codex repo. github.com/openai/codex/blob/main/AGENTS.md.** OpenAI's own AGENTS.md, used as a worked example by the broader community. Useful as "what production looks like" reference.
- **OpenAI. "How OpenAI Engineers use Codex" (forum.openai.com, Dec 2025).** TIKTOC quotes: "Keep AGENTS.md short and human-readable. Bloated files cause Codex to ignore your actual instructions." And: "Files closer to your current working directory take precedence."
- **Knuth, Donald E. "Literate Programming." *The Computer Journal* 27, no. 2 (1984): 97–111.** AGENTS.md as literate programming for AI collaboration.
- **Anthropic. CLAUDE.md documentation.** Comparable: auto-loaded project context file. Useful for cross-tool framing; not the book's tool.

### Key empirical cases

- **Teacher's first AGENTS.md (TIKTOC).** Five entries; class website project; checked into git. Author produces.
- **OpenAI's own AGENTS.md.** Open repo. Show production scale.
- **The "Codex makes the same mistake twice" pattern.** Recurring; the fix is adding to AGENTS.md.
- **The "AGENTS.md grew to 600 lines and Codex stopped following it" pattern.** The 32 KiB limit is real but the *effective* limit (where Codex still reliably follows) is much smaller. The 200-line guideline (consistent with cross-series CLAUDE.md / CLI.md recommendations) is the operational ceiling.

---

## 2. The Core Concept — State of the Field

### What is settled

- **AGENTS.md is loaded automatically.** OpenAI-documented.
- **Hierarchical discovery is the spec.** Global → project root → subdirectories. 32 KiB combined limit. Fallback names supported.
- **Bloated AGENTS.md degrades Codex.** Documented in OpenAI's own guidance.

### What is disputed

- **The right size.** 32 KiB is the technical limit; practitioner consensus is keep under 200 lines for effective instruction-following.
- **Whether to use AGENTS.override.md.** Useful for temporarily overriding project AGENTS.md for a specific task; risks confusion. The book's primary reader is individual teacher; brief sidebar mention.
- **Whether to use fallback names (TEAM_GUIDE.md, .agents.md).** Most teachers will use AGENTS.md directly. The fallbacks exist for legacy or different-team-naming purposes.

### What has changed recently (last 5 years)

- The 32 KiB limit and fallback-name hierarchy are 2025–2026 specifications. Earlier Codex was simpler.
- Subdirectory AGENTS.md (loaded when Codex works in that directory) is a 2025–2026 feature. Useful for the simulation build (Ch 10): a `simulation/AGENTS.md` can specify simulation-only rules without polluting the project-root AGENTS.md.
- Codex Skills (developers.openai.com/codex/skills) is the on-demand complement to AGENTS.md. Brief mention; not the book's focus.

---

## 3. Application Domain Examples

(Domain coverage map: Ch 2 sits in class website project.)

A class website AGENTS.md, five entries (worked example):

1. **Stack and build:** "Static HTML/CSS/JS; no build step. Files in `src/`; deployed via `npm run deploy` (rsync to school server)."
2. **Code style:** "Vanilla CSS (no Tailwind). Plain JS, ES modules. Semantic HTML5; no div-soup."
3. **Test/verification:** "After HTML changes, run `npm run lint-html`. After CSS, manual mobile check."
4. **Architectural decisions:** "Each page self-contained. Shared components as template literals at build time. No JS framework."
5. **Environment quirks:** "School server uses old mod_rewrite; all paths end in .html explicitly; no trailing slashes."

For the simulation (Act Three), a `simulation/AGENTS.md` extends:
6. **Simulation-specific naming:** "Kebab-case for IDs. CSS variables in `--simulation-*` namespace. JS in `simulation.js` (single file)."

---

## 4. The Book's Thesis Connection

Ch 2 is where the discipline becomes durable. AGENTS.md persists across sessions; the gate (Ch 3, Ch 4) is per-prompt.

The chapter's contribution:
1. **Artifact is discipline made visible.**
2. **Automatic injection is the feature** — unlike CLI.md (gh-copilot CLI book), Codex auto-loads. Discipline is upstream (write well) not per-invocation.
3. **Eventually becomes teaching artifact** (Ch 13). Three-tier AGENTS.md spans website + grading tool + simulation.

Student-supplied capacity: teacher knows project conventions, exclusions, prior mistakes.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: Donald Knuth (born 1938).** Strong fit. Cross-series consistent.

Candidates:
- **Knuth** — named. Diversity: white male American.
- **Margaret Hamilton** (born 1936, USA, software engineer). Apollo flight-software documentation. **Strongest diverse alternate.** Same cross-series recommendation as in other books.
- **Ward Cunningham** (born 1949, USA, programmer). Wiki inventor.

Recommendation: **consider Hamilton swap.** Cross-series consistency would unify the recommendation.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Ch 1 first session.

### Common misconceptions to disarm
- **"AGENTS.md is for Codex."** Written by humans; read by both. Writing is for the teacher.
- **"More is better."** No. Under 200 lines effective; 32 KiB technical limit.
- **"Wait until project is bigger."** Start at minute one.
- **"Subdirectory AGENTS.md is power-user."** Useful at Ch 10 (simulation); brief introduction here.

### Effective instructional sequences
- **Write AGENTS.md, then use it, in one session.** Apply-level exercise.
- **OpenAI's own AGENTS.md as worked example.** Production scale contrast.
- **Lessons-learned by example.** Three entries: date, mistake, fix.
- **The 200-line ceiling.** Concrete; not aspirational.

### Known failure modes
- **AGENTS.md as homework.** Frame as upstream investment.
- **Over-documented file.** Brevity wins.
- **Never-updated file.** End-of-session two-minute review.

### What separates understanding from memorization
A reader who *understands* Ch 2 has written an AGENTS.md, used it across two sessions, observed one specific behavior change, and added one lesson-learned entry. A reader who memorized Ch 2 recites the five-element format without tailored content.

---

## 7. Representation and Display Research

TIKTOC specifies two figures:

- **`<!-- → [DIAGRAM: AGENTS.md in the session context.] -->`** Top: session start → AGENTS.md loaded (hierarchical, 32 KiB max). Middle: every prompt operates with AGENTS.md in context. Bottom contrast: without (guesses) vs. with (knows). Editorial style.
- **`<!-- → [TABLE: AGENTS.md include/exclude.] -->`** Worked content:

  | Include | Exclude |
  |---|---|
  | Bash commands Codex can't guess | What Codex can figure out from code |
  | Code style deviations | Standard conventions |
  | Test runners | Constantly changing state |
  | Architectural decisions | Personal notes |
  | Environment quirks | Secrets, credentials |

No additional displays required.

---

## 8. Open Questions and Research Gaps

- **AGENTS.override.md positioning.** TIKTOC excludes from main content (Out of Scope). Brief sidebar mention only.
- **Codex Skills.** Brief mention; not the book's focus.
- **Subdirectory AGENTS.md.** Introduce here; apply in Ch 10 for simulation-specific rules.
- **Hamilton swap.** Cross-series decision.

---

## 9. Sourcing Notes

- **OpenAI Codex AGENTS.md docs** — developers.openai.com/codex/guides/agents-md. URL stable; verify at press.
- **OpenAI Codex repo** — github.com/openai/codex/blob/main/AGENTS.md.
- **Knuth 1984** — open access *Computer Journal*.
- **OpenAI engineer-voice quotes** — forum.openai.com Dec 2025.
- **Hamilton sources** if swapping: NASA Apollo archive; McMillan 2015 *Wired*.
