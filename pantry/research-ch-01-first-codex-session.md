# Research: Chapter 1 — Your First Codex Session: This Is Not ChatGPT
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** Codex plans multi-step tasks, executes shell commands, reads and writes files, and iterates autonomously. That autonomy is the feature — and the reason you need a discipline before you start.

**Research date:** 2026-05-21

---

## 1. Primary Sources

### Foundational papers and texts

- **OpenAI. "Introducing the Codex app" (openai.com/index/introducing-the-codex-app/) and "Using Codex with your ChatGPT plan" (help.openai.com).** Canonical references for the 2026 Codex app surface. macOS Aug 2025; Windows March 2026. Available on Free, Go (rate-limited), Plus, Pro ($100/mo, 5×–10× through May 2026), Business, Enterprise, Edu.
- **OpenAI. "Introducing Codex" (openai.com/index/introducing-codex/).** Originating product announcement.
- **OpenAI. "Custom instructions with AGENTS.md" (developers.openai.com/codex/guides/agents-md).** Documentation for Ch 2 but reference here.
- **OpenAI. "How OpenAI Engineers use Codex to Tackle Big Projects with Rigor" (forum.openai.com, Dec 4, 2025).** TIKTOC's Ask-Mode-first quote: "Start with Ask Mode. Don't start by using Code Mode."
- **Kay, Alan. "A Personal Computer for Children of All Ages." Xerox PARC, 1972.** Computer as medium for exploration. Ask Mode interrogation is Kay's stance applied.

### Key empirical cases

- **Teacher's first Codex session (TIKTOC opening).** Opens Codex; types request; Codex starts reading files, proposing changes, running commands. Feels different from ChatGPT. Author should preserve specifics.
- **The "questions before execution" pattern.** TIKTOC's Ch 1 operationalization. Spend first session in Ask Mode only. Concrete walkthrough.
- **The "permission denied / sandbox-write" first-session friction.** Codex's 2026 permission modes (on-request default, never, on-failure) and sandbox policies (workspace-write) need walking through for first users.

---

## 2. The Core Concept — State of the Field

### What is settled

- **Codex is agentic, not chat.** OpenAI-documented; the Codex app is built around this.
- **Ask Mode / Code Mode distinction is real and current** as of May 2026. May be renamed or reframed in future versions; the conceptual gate (plan before execution) is tool-agnostic.
- **The context window is the primary resource.** Established in LLM literature; Codex-specific guidance from OpenAI emphasizes this.

### What is disputed

- **Whether Ask Mode should be default for all first sessions** vs. only for non-trivial. TIKTOC implies Ask-Mode-first; OpenAI agrees for "large changes." Reasonable.
- **Plus vs. Pro for teacher use.** Plus ($20/mo) provides Codex access with rate limits; Pro ($100/mo) provides 5–10× capacity. Most K-12 teachers will use Plus or institutional Edu access.

### What has changed recently (last 5 years)

- The Codex app (2025–2026) replaced earlier Codex CLI-only experience. Multi-agent parallel execution, scheduled Automations, Skills now part of the app.
- Permission modes and sandbox policies are 2025+ additions. Earlier Codex was more permissive by default.
- Codex was made available on Free tier (rate-limited) and Go plans in late 2025 / early 2026, broadening access.

---

## 3. Application Domain Examples

(Domain coverage map: Ch 1 sits in class website foundation.)

- **First session: Ask Mode on class website folder.** Teacher asks "what do you see in this folder?" Codex describes structure, identifies framework, notices conventions. Teacher reads; makes no changes.
- **First session: Ask Mode plan for adding a page.** Teacher asks Codex to propose a plan. Reads plan. Doesn't approve. Notes assumptions Codex made (which CSS to import, which nav location, etc.).
- **First session: ask about a quirk.** Teacher asks "why does this CSS file have these specific media queries?" Codex explains. Teacher learns; Codex calibrates what the teacher knows.

---

## 4. The Book's Thesis Connection

Ch 1 puts hands on Codex with the discipline in place. Must:
1. Get teacher through setup + first session.
2. Establish Ask-Mode-first as habit from minute one.
3. Foreshadow what comes (AGENTS.md Ch 2, specifications Ch 3, handoff conditions Ch 4).

Student-supplied capacity: teacher's judgment about which generated suggestions match their actual project.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: Alan Kay (born 1940).** Strong fit. Cross-series consistent with Claude Code teachers Ch 1.

Candidates:
- **Alan Kay** (born 1940, USA, computer scientist). Named. Diversity: white male American.
- **Adele Goldberg** (born 1945, USA, computer scientist). Co-developer of Smalltalk with Kay. **Strongest diverse alternate.** Woman, American.
- **Seymour Papert** — TIKTOC's Bridge candidate; avoid double-booking.

Recommendation: keep Kay.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Reader can run a terminal command if given exact syntax. ChatGPT or basic AI familiarity.

### Common misconceptions to disarm
- **"Codex is like ChatGPT."** No. Agentic.
- **"I'll skip Ask Mode."** Anthropic RCT data: engagement patterns beat delegation. OpenAI's own guidance: Ask Mode for large changes.
- **"My school IT won't allow Codex."** Real problem; reference appendix on access (OQ-3).

### Effective instructional sequences
- **Setup walkthrough, exact commands.** `npm install -g @openai/codex` or the Codex app download. Plus the ChatGPT plan reality.
- **First session: Ask Mode only.** Concrete.
- **Plan-mode demonstration.** Teacher reviews a proposed plan; doesn't approve.

### Known failure modes
- **Setup-as-gatekeeper.** Over-resource help.
- **First-session demo that fails.** Test commands against current Codex app before press.
- **Plus-vs-Pro confusion.** Be clear about which features are on which plan.

### What separates understanding from memorization
A reader who *understands* Ch 1 has run their first Ask Mode session, identified one assumption Codex made, and explained why Ask Mode precedes Code Mode. A reader who memorized Ch 1 can recite "Ask before Code" without applying.

---

## 7. Representation and Display Research

TIKTOC specifies one figure:
- **`<!-- → [DIAGRAM: The agentic loop.] -->`** Gather context → Plan → Execute → Verify → Repeat. Ask Mode: gather + plan only. Code Mode: execute + verify. Human interruption point at every phase. Editorial style.

---

## 8. Open Questions and Research Gaps

- **Codex app vs. CLI feature parity.** As of 2026, Codex app is the primary UI; CLI still exists. Teachers may use either. The chapter should be tool-agnostic where possible.
- **Permission-mode defaults.** Verify current defaults at press; they evolve.
- **Plan availability for Best-of-N and task queue.** TIKTOC OQ-6. Critical for Ch 6 and Ch 9.

---

## 9. Sourcing Notes

- **OpenAI Codex app docs** — openai.com/index/introducing-the-codex-app/, chatgpt.com/codex/, help.openai.com.
- **OpenAI Codex pricing** — developers.openai.com/codex/pricing.
- **Kay 1972** — Xerox PARC TR.
- **OpenAI engineer-voice quotes** — forum.openai.com Dec 2025.
