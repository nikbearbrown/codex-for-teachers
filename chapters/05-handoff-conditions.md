# Chapter 4 — Handoff Conditions: The Gate Between Steps

> Not "looks good." A specific, testable condition that must be true before the next step begins. This is what separates conducting from approving.

---

## Learning outcomes

1. **(Understand)** Define a handoff condition and explain why "looks good" fails as one.
2. **(Apply)** Write handoff conditions for three steps in the class website build.
3. **(Analyze)** Identify the dangerous middle in a build step — where Codex's output requires specific verification not in the obvious checklist.

---

## Opening

Last week you added a page to your class website. Codex did exactly what you specified. The page rendered. You approved the build. You moved on.

This week you go to add the *next* page. You run Codex. You notice, in the file diff, that one of the links on last week's page is now broken — a relative path that was correct when you first wrote it, but that pointed to a directory you reorganized two days ago and forgot to update.

The page rendered. The link broke later. You did not catch it because "rendered" was your criterion. *Rendered* is not enough.

This chapter is about the criterion that would have caught it.

![Handoff condition gate](images/05-handoff-conditions-fig-01.png)
*Figure 5.1 — Handoff condition gate*

---

## What a handoff condition is

A **handoff condition** is the specific, testable, binary condition that must be true before the next build step begins.

Three properties.

**Specific.** Not "looks good" — looks good is a feeling. *"Every link on the new page returns HTTP 200"* is specific. *"The page validates as HTML5"* is specific. *"The mobile breakpoint renders without horizontal scroll"* is specific. Each names something that can be checked.

**Testable.** Someone could run a check — automated or manual — and produce an answer. "The lint command exits 0" is testable. "The new section reads well" is not testable in the same way; it requires interpretive judgment, which is fine but is a different kind of condition (interpretive handoffs are valid but should be labeled as such).

**Binary.** Pass or fail. Yes or no. "Mostly works" is not a handoff condition. If the condition cannot be made binary, it is two conditions; split it.

Together: a handoff condition is the operational answer to "how do I know this step is done?" Without one, the answer collapses to "Codex says it's done" or "it looks right to me" — both of which produce silent failures.

---

## Why "looks good" fails

"Looks good" is the default. It is also wrong, for two reasons.

The first reason is empirical. The Anthropic 2026 RCT on coding skill formation identified three low-scoring AI-interaction patterns. The third was *Iterative AI Debugging* — fixing surface errors without catching deeper ones. "Looks good" is the moment that Iterative Debugging starts: you accept the output, ship the result, encounter the deeper error two days later, and start fixing forward. The fix-forward pattern is what the data shows produces the largest decline in conceptual understanding.[^1]

The second reason is structural. "Looks good" is a feeling produced by *fluency* — the output is well-formatted, well-named, syntactically valid. Codex is excellent at fluency. The feeling that fluent output produces is precisely the feeling that bypasses the supervisory work. The chapter's central warning: *fluency is the trap, not the signal.* Specific, testable, binary conditions are the antidote.

This is the **Frictional principle** applied to per-step verification. The friction of writing a real condition is what produces the cognitive event that catches the silent failure. Without the friction, the silent failure ships.

---

## Worked example: handoff conditions for the class website

The class website build (Chapter 3) added a syllabus page. Three steps; three handoff conditions.

**Step 1: Create `src/syllabus.html`.**

- *Weak condition:* "Page renders." (Looks good. Default fail mode.)
- *Strong condition:* "The file `src/syllabus.html` exists. Opening it in Chrome produces the expected layout. The page renders correctly at the mobile breakpoint (Chrome devtools, iPhone preset). `npm run lint-html` exits 0 with no warnings."

**Step 2: Update `src/index.html` nav to link to syllabus.**

- *Weak:* "Nav looks right."
- *Strong:* "The nav in `src/index.html` contains a link to `syllabus.html`, positioned between `units.html` and `office-hours.html`. Clicking the link from a browser navigates correctly. The nav on `src/units.html` and `src/office-hours.html` is unchanged (verified by `git diff`)."

**Step 3: Deploy.**

- *Weak:* "`npm run deploy` exits 0."
- *Strong:* "The live URL at the class website serves the new page. The new page is reachable from the nav on the live site. HEAD request to the new page returns HTTP 200. HEAD requests to the three previously-existing pages still return HTTP 200."

The strong conditions are not heroic; they are concrete. Each takes thirty seconds to verify. Each one would have caught the broken-link failure in the chapter opening.

| Item | Meaning |
| --- | --- |
| Strong vs. weak handoff conditions. Five examples for website context. Left: weak. Right: strong. No color. | Use the chapter example as the concrete test case. |

---

## When a condition fails: revert, do not correct forward

This is the chapter's contrarian operational rule.

When a Codex output fails a handoff condition, the temptation is to fix it forward — describe what went wrong in a follow-up prompt and ask Codex to correct. This works sometimes. It produces a slow accumulation of failed attempts in your session context, each of which Codex must reason through to produce the next output. By the third or fourth correction, Codex is operating against a context that contains more failed attempts than successful pattern, and the corrections get worse.

OpenAI's own guidance puts it plainly: *"If you've corrected Codex more than twice on the same issue, the context is cluttered. Start fresh with a more specific prompt."*[^2]

The discipline is:

1. **First correction:** OK, write a follow-up prompt that names what failed and asks for a fix.
2. **Second correction (on the same step):** Codex is struggling with the spec. Revisit the specification. Probably it was under-specified.
3. **After two failed corrections:** Stop. Use `/clear` (the CLI) or start a fresh session. Write a better specification from scratch. The previous failed attempts are no longer helping Codex; they are confusing it.

The cost of starting fresh feels high. It is almost always lower than the cost of continuing with a cluttered context.

The same discipline applies even more strongly to the dangerous middle (Chapter 8), where forward correction can mask the real problem entirely. For now, internalize the rule: **two failed corrections → fresh start with a better spec.**

---

## What handoff conditions cannot do

Handoff conditions catch the failures that can be made specific, testable, and binary. They do not catch failures that resist that treatment.

The most important class of failures they cannot catch is the **dangerous middle**: outputs that pass every condition you wrote and are still wrong, because the condition you needed to write was one you did not know to write. Chapter 8 owns the dangerous middle. Chapter 4's job is to make you good enough at handoff conditions that the dangerous middle is what is *left* when you finish.

A useful frame: a build step has three possible outcomes. (a) Output fails a handoff condition you wrote. Easy — revert, respecify. (b) Output passes all conditions and is correct. Easy — proceed. (c) Output passes all conditions and is *not* correct. This is the dangerous middle. The handoff conditions cannot detect (c) by construction; only **plausibility auditing** (Chapter 5) can, and only sometimes.

The book's strategy is to use handoff conditions to make (a) cheap to handle, leaving your attention free for (c). This is the Humans + AI division of labor in operation: the testable verification is the machine's; the irreducibly human verification is yours.

---

## The STOP block

A useful idiom: include explicit conditions in your specification under which Codex must pause and ask before continuing. The OpenAI engineers call these STOP blocks; the term is informal but the practice is real.

For the syllabus build:

> *"STOP and confirm before: (a) modifying any file outside `src/`, (b) introducing any new dependency, (c) modifying the navigation in any page other than `src/index.html`, (d) adding any CSS that is not already in `src/styles.css`."*

The STOP block is a handoff condition that fires *during* Code Mode rather than at the end of a step. It catches the scope creep that the negative constraint in your specification was supposed to prevent, providing a second layer of defense when the negative constraint slips. Codex respects STOP blocks reliably when they are explicit and concrete.

The STOP block becomes essential by Chapter 7 (the grading tool build), where a single mis-scoped operation can affect student work. For the website build, the STOP block is practice.

---

## Common misconceptions

**"'Looks good' is a condition."** No. Feeling, not criterion. The whole chapter is the disarming.

**"Forward correction is fine."** Sometimes. The risk grows with each correction. Two is the practitioner threshold; OpenAI agrees. Going past two without restarting is the move that produces the worst session-context bloat.

**"All build steps need handoff conditions."** In proportion to consequence. A typo fix in a CSS comment does not need a three-element handoff condition. A change to your deployment script does. Calibrate by what failing silently would cost you.

**"Handoff conditions slow me down."** They take thirty seconds to write. They save hours when they catch a silent failure. The math is favorable except for the most trivial changes.

**"My handoff condition was 'the tests pass.' That should be enough."** Tests pass when the code matches the tests. If the tests encode the same misunderstanding as the code, both pass and both are wrong. The dangerous middle (Chapter 8) lives precisely in this gap.

---

## Exercises

1. **(Apply)** Write handoff conditions for the next three steps in your class website build. Each must be specific, testable, and binary.

2. **(Analyze)** Identify one "dangerous middle" step in your website build — a step where the obvious handoff conditions would pass but a deeper failure could still occur. Write a handoff condition (or a STOP block) that would catch it.

3. **(Create)** Design a classroom exercise that teaches handoff conditions using a non-coding build — a recipe, a lesson plan, a rubric. The exercise should make students experience the difference between "looks good" and a binary condition by having a peer evaluate their work against both kinds of criteria.

---

## Gate 1

You have built one deployable web page using AGENTS.md, the Ask Mode → Code Mode gate, specification prompts, and explicit handoff conditions. You have designed at least one classroom activity using each concept. You are ready for a build where the consequences of a missed handoff condition reach further than your own laptop. Act Two begins.

---

## Classroom activity

Have students add handoff conditions to a provided build sequence (a small multi-step task — adding a page with a working nav link and verified mobile rendering works well). Have them deliberately test each other's conditions by introducing the specific errors the conditions are meant to catch. Did the condition catch it?

This activity maps to Chapter 9 of the students book — *Handoff Conditions and the Dangerous Middle*. The students learn the same gate from their angle. Your build experience this chapter is the example.

---

## Links

- OpenAI Codex best practices: [developers.openai.com/codex/learn/best-practices](https://developers.openai.com/codex/learn/best-practices)

---

## What would change my mind

The chapter's strong claim is that **explicit, binary handoff conditions catch silent failures that "looks good" does not**, and that the cost of writing them is less than the cost of missing the failures. If a controlled comparison — same build tasks, with and without explicit handoff conditions — showed no measurable reduction in silent-failure rate, or showed a reduction so small that the time cost of writing the conditions exceeded the time saved, the chapter's prescription weakens. The discipline would still help; the urgency would drop.

---

## Still puzzling

- **What is the right number of handoff conditions per step?** The chapter's examples use 2–4 conditions per step. Practitioners disagree on the optimum. Too few miss failure modes; too many become checkbox theater. The right granularity is undocumented.

- **Can handoff conditions be auto-generated by Codex itself?** If you write a clean specification, Codex can in fact propose handoff conditions for it. The discipline question: does auto-generated handoff verification produce the same supervisory benefit, or does writing them yourself matter? Practitioner intuition is that writing them yourself is irreplaceable because the act of writing forces you to think about what could fail. Empirically untested.

- **The "looks good" failure across other AI surfaces.** This chapter is framed for Codex. The same pattern appears in writing assistants, image generators, slide creators. Whether the handoff-condition discipline transfers cleanly to non-code domains is open.

---

## AI Wayback Machine

🕰️ **W. Edwards Deming** (1900–1993) — statistician whose **Plan-Do-Check-Act** cycle became the foundation of modern quality management. Deming argued that quality is built into a process through verification at every step — not inspected in at the end.[^3] His warning, *"A bad system will beat a good person every time,"* is the operational argument for the handoff condition: a build system without per-step verification will produce silent failures regardless of how careful the individual builder is. Deming's PDCA cycle is the handoff condition principle applied to manufacturing, and the manufacturing line is the conceptual ancestor of the agentic build loop. *Plan* is Ask Mode. *Do* is Code Mode. *Check* is the handoff condition. *Act* is the revert-and-respecify response when the check fails.

---

## Bridge

Act Two begins. Chapter 5 names the five things you do that Codex cannot — the supervisory capacities that the conducting discipline keeps yours, no matter how much Codex improves.

---

[^1]: Anthropic, "How AI assistance impacts the formation of coding skills" (anthropic.com/research/AI-assistance-coding-skills, 2026); arXiv:2601.20245. The three low-scoring patterns are AI Delegation, Progressive AI Reliance, and Iterative AI Debugging.
[^2]: OpenAI engineers, "How OpenAI Engineers use Codex to Tackle Big Projects with Rigor" (forum.openai.com, December 4, 2025).
[^3]: Deming, W. E. *Out of the Crisis*. MIT Press, 1986. The 2018 MIT Press reprint is the standard recent edition. "A bad system will beat a good person every time" is widely attributed to Deming from his consulting practice; see also *The New Economics for Industry, Government, Education* (MIT Press, 2nd ed. 2000).

## Prompts

Use these prompts with Claude to generate interactive D3 v7 versions of the
figures in this chapter. Each produces a standalone HTML file you can open
in a browser and modify freely.

**Prerequisites:** Load `brutalist/CLAUDE.md` and `brutalist/DESIGN.md` into
your Claude project context before using these prompts. They define the stack,
naming conventions, color system, and typography the figures use.

---

### Figure 5.1 — Handoff condition gate

Create a standalone D3 v7 HTML file for Figure Handoff condition gate. Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: Handoff condition gate. Build step N → [Handoff condition: specific, testable, binary] → Pass → Build step N+1. Fail path: revert to step N, respecify, rerun. Editorial style.. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/05-handoff-conditions-fig-01.html`
