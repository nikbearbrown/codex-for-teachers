# Chapter 10 — The Three-File System: Intent, Constitution, State

> Before Codex enters Code Mode on the simulation, three files define everything. The Intent Layer is human, always.

---

## Learning outcomes

1. **(Understand)** Explain what each of the three files protects and why all three must be populated before Code Mode begins.
2. **(Apply)** Write the Intent Layer of a PROJECT.md for an interactive simulation.
3. **(Apply)** Write a DESIGN.md specifying the simulation's visual and interaction vocabulary completely enough that Codex cannot improvise.

---

## Opening

You open Codex. You type: *"Build me an interactive sorting algorithm simulator."*

Codex builds something.

It works. It opens in a browser. There is a bar chart. There are buttons. The user can step through a sort. The colors are mid-range blues and grays. The interaction is drag-and-drop with mouse-hover-to-explain. The pedagogical scaffolding consists of two short paragraphs above the chart, written in a chipper, slightly generic voice.

It is fine.

It is also not yours. The colors are not your colors. The interaction model is not what you wanted (drag-and-drop on a phone is hard; you wanted single-tap stepping). The voice is not your classroom's voice. The pedagogical decisions about *what to show* and *what to hide* and *when to pause* are decisions Codex made by sampling from training-data patterns, not decisions you made because they are right for your students learning *this* concept *this* week.

The simulation works. It is generic. And it is generic because you did not draw the line before Codex started.

This chapter is the line. Three files. Three concerns separated. Each file protects against a different way the build can go generic.

![Three-file system as three concentric circles or nested](images/12-three-file-system-fig-01.png)
*Figure 12.1 — Three-file system as three concentric circles or nested*

---

## A note on attribution

This chapter teaches the **Brutalist three-file system** — AGENTS.md plus DESIGN.md plus PROJECT.md, with specific size and discipline conventions. The system is one operational choice within a broader 2025–2026 ecosystem of AI-readable project-specification files. Other entries in the ecosystem include the DESIGN.md catalogs at designmd.app, the awesome-design-md collection, and the SKILL.md / CLAUDE.md / AGENTS.md genre that grew across the same period.[^1]

The Brutalist three-file system is documented at brutalist.art. **brutalist.art is the author's own design system.** That is not a third-party reference; it is the same author who wrote this book teaching their own framework. The book recommends the system because it has held up in practice across multiple projects in the series; you should know who is recommending what.

If you prefer a different three-file (or two-file, or four-file) approach from the broader ecosystem, the *principles* of this chapter still apply. The names of the files are less important than the *concerns the files separate*: technical decisions you do not want Codex to revisit; visual and interaction decisions Codex must not improvise; intent that is irreducibly yours.

---

## The three files

### AGENTS.md — Technical Constitution

You have an AGENTS.md already (Chapter 2). For the simulation project, the AGENTS.md is the same kind of artifact, extended for simulation-specific technical decisions:

- The stack (vanilla HTML/CSS/JS; no framework; deployable as a single page).
- The file structure (`index.html`, `simulation.css`, `simulation.js`; no others at the top level).
- The naming conventions (kebab-case for IDs; camelCase for JS functions; CSS variables in the `--simulation-*` namespace).
- The never-touch list (anything outside the `simulation/` directory; the class website's shared CSS; the grading tool's reports directory).
- The verification step (opens in Chromium without console errors; works on the mobile breakpoint; passes the lint check).

The AGENTS.md for the simulation is project-scoped — `simulation/AGENTS.md` — so the rules apply only when Codex is working in the simulation directory. Codex's subdirectory AGENTS.md discovery (Chapter 2) handles this automatically.

### DESIGN.md — Visual Constitution

The DESIGN.md is the file that prevents Codex from improvising aesthetics. The opening of the chapter — where Codex built a generic simulation with mid-range blues and chipper paragraphs — happened because there was no DESIGN.md. The model sampled the most-probable visual choices from its training data.

A useful DESIGN.md is *brutally specific*. Six color variables, named, with hex values. No others. The typography is two faces — say, one monospace, one sans — with sizes specified. The interaction vocabulary lists what the system *does* and explicitly names what the system *does not do*.

For a sorting-algorithm simulation:

```markdown
# DESIGN.md — Sorting Algorithm Simulator

## Color system (six variables, no others)
--background:  #f5f5f0   /* warm white, near-paper */
--ink:         #1a1a1a   /* near-black, body text */
--accent:      #c97a3a   /* terracotta, the element being compared */
--target:      #3a7ac9   /* blue, the element being placed */
--rule:        #999999   /* medium gray, axis lines and dividers */
--highlight:   #f0d843   /* amber, the sorted region */

## Typography (two faces, no others)
Monospace: SF Mono, Menlo, monospace — for numeric values, code, identifiers.
Sans:      Inter, system-ui — for labels and prose. 16px minimum.

No serif. No display face. No script.

## Interaction vocabulary
ALLOWED:
- Single click on a step-forward button: advance one comparison.
- Long-press on the step-back button: step backward.
- Keyboard arrow keys: fine control (left = back, right = forward).
- "Reset" button: return array to initial state.

NEVER:
- Drag-and-drop. (Hard on touch devices; we use single-tap stepping.)
- Hover-only states. (Hover doesn't exist on touch; never make information
  reachable only by hovering.)
- Hidden controls. (Every interactive element is visible at all times.)
- Auto-advance. (The student controls the pace.)

## Accessibility
- Keyboard-navigable.
- Each interactive element has an aria-label.
- Minimum 16px text; minimum 44px tap target on touch.
- Color is not the only signal of state (use shape/position too).
- Works at 200% browser zoom.
```

Sixty lines. Six colors. Two typefaces. Four allowed interactions. Five forbidden interactions. The file fits on a single screen. **The constraint is the point.** A DESIGN.md that tries to specify everything Codex *might* do produces a file Codex ignores. A DESIGN.md that specifies the small number of decisions you actually care about — *and explicitly forbids the most-probable improvisations* — gets followed.

### PROJECT.md — Project State (with Intent Layer human, always)

PROJECT.md has two layers.

**Layer 1: Intent (Human Layer — never overwritten by Codex).** What the simulation is. What the student should understand after using it. What questions it answers. What questions it refuses to answer. The tone.

**Layer 2: Technical State (Codex layer).** What is built. What is pending. The generation log. Open technical questions.

Layer 1 is the irreducibly human part. You write it. Codex reads it but does not modify it. If Codex proposes changes to Layer 1, you reject; the proposal goes to Layer 2 as a question for you to decide.

For the sorting-algorithm simulation:

```markdown
# PROJECT.md — Sorting Algorithm Simulator

## Layer 1: Intent (Human Layer — never overwritten by Codex)

What this simulation is:
An interactive bubble-sort visualization that shows, comparison by comparison,
why bubble sort runs in O(n²) on average and why it sometimes "looks fast"
on small or already-sorted arrays.

What the student should understand after using it:
That comparison-based sorts trade simplicity for efficiency. That small changes
in the input (one early-swap vs. many) can have cascading effects on the
number of operations. That "already sorted" and "reverse sorted" are
opposite-extreme inputs and their counts differ dramatically.

What questions it answers:
- "How does bubble sort actually move through an array?"
- "Why is it slow?"
- "What happens when the input is already sorted?"
- "How does the number of operations change with array size?"

What questions it refuses to answer:
- "Which sort is best?" (Too context-dependent; out of scope for this sim.)
- "Why is quicksort faster?" (Different simulation; not in this scope.)
- "What's the worst-case input?" (Adjacent topic; if students ask, point
  them at the next class period's planned discussion.)

The tone:
Matter-of-fact. Slightly playful. No jargon ("comparison" is fine; "complexity
class" is not, in the body — it goes in a footnote). No condescension.
Students learn by stepping, not by reading paragraphs. Text on the simulation
should be short labels and prompts; long explanation belongs in the surrounding
lesson, not in the sim.

## Layer 2: Technical State (Codex Layer)

What is built:
- HTML scaffold with the structural elements.
- CSS variables defined per DESIGN.md.

What is pending:
- The JavaScript simulation logic for bubble sort.
- The step controls (forward/back buttons; keyboard handling).
- The visual highlighting of compared/swapped/sorted elements.
- The array-size selector.
- The "reset" button behavior.

Generation log:
[will populate during build]

Open technical questions:
- How to handle very-large arrays without performance degradation (probably
  a max-size cap; ask before adding it).
- Whether to support custom inputs (out of scope for v1; capture in queue).
```

The Intent Layer is what makes the build *yours*. The Technical State is the working surface Codex updates as the build proceeds.

The phase gate: **Code Mode does not begin until both layers of PROJECT.md are populated.** This is not a suggestion. The simulation that opened this chapter — the generic one — happened because there was no PROJECT.md to start from. Codex filled in defaults for everything the Intent Layer would have specified.

---

## The 45-minute scope test

A useful forcing function: **if writing all three files takes more than 45 minutes, the simulation is too large for a first build.**

This is the test the chapter's worked example was designed to pass. Bubble sort on a small array, with the specific intent of teaching O(n²) operationally — small enough to scope in 45 minutes. Quicksort with three-way partitioning, with the intent of teaching every sorting concept on the course list — too large; scope back.

The 45-minute test is not about whether you *can* write a longer set of files. It is about whether the *first* simulation should be ambitious enough to need a longer set. For a first build, the answer is no. Make it small. Make it complete. Ship it. Then build the next one larger.

| Item | Meaning |
| --- | --- |
| Three-file system | file name, what it contains, who writes it, when it changes. Three rows. No color. |

---

## Common misconceptions

**"Three files is too much for a small simulation."** The 45-minute test forces appropriate scope. If three files genuinely feel like overhead for the build you have in mind, the build is small enough that the constraint will land lightly. Write them anyway; they protect against the failure mode that opened the chapter.

**"DESIGN.md is for designers."** No. Anyone building anything with visual output makes design decisions. The choice is whether you make them *explicitly* or whether Codex makes them by sampling from the most-probable patterns in its training data. The chapter argues for explicit. Six colors is not designer expertise; it is the constraint that prevents generic.

**"Codex can figure out the Intent Layer from context."** No. The Intent Layer is what makes the simulation *yours*. Codex's "context" is its training distribution; the Intent Layer is what you know about your students that is not in that distribution.

**"I'll iterate on the files as I build."** No. Iteration during generation is forward correction (Chapter 4 warned against this). Write the files first; refine them only if the build surfaces a genuinely new question that the files did not anticipate. *Most* "I'll refine later" turns into *never refine* turns into *the simulation drifted because the files were never tight*.

**"The Intent Layer can be vague; I'll fill in details during the build."** No. Vague Intent → vague output. The Intent Layer's specificity is what produces a simulation that teaches *this* concept rather than *some adjacent concept*.

---

## Exercises

1. **(Apply)** Write all three files for your simulation project before opening Code Mode. If it takes more than 45 minutes, the scope is too large — shrink it. Document the scope shrink.

2. **(Analyze)** Review a provided PROJECT.md with a weak Intent Layer (you can use a deliberately-vague Codex draft for this). Identify what's missing and rewrite the Intent Layer to be specific enough that a peer reading it could tell what the simulation is supposed to teach.

3. **(Evaluate)** What decisions in your simulation are pedagogical (Intent Layer) vs. technical (AGENTS.md)? List three of each. Which were ambiguous? Which file did you put the ambiguous ones in, and why?

---

## Classroom activity

Have students write the Intent Layer of a PROJECT.md for a simulation they want to build. Constraint: under 200 words. Class exercise: read each other's Intent Layers *without* seeing the simulation concept. Can you tell what the simulation is trying to teach? If not, the Intent Layer needs work before any Codex prompt should run.

This activity maps to Chapter 10 of the students book and to the Brutalist three-file system more broadly. Use your own Intent Layer for the sorting-algorithm simulation as the worked example.

---

## Links

- Brutalist Design System: [brutalist.art](https://brutalist.art) (author's own)
- Broader DESIGN.md ecosystem: [designmd.app](https://designmd.app), [getdesign.md](https://getdesign.md), [github.com/VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md)
- Codex Skills (the SKILL.md genre): [developers.openai.com/codex/skills](https://developers.openai.com/codex/skills)

---

## What would change my mind

The chapter's strong claim is that **three concerns separated into three files produces materially better simulation builds than a single-file or no-file approach**. If a controlled comparison — same simulation brief, with and without the three-file system — produced equivalent visual fidelity, equivalent pedagogical specificity, and equivalent classroom outcomes, the chapter's prescription becomes optional rather than load-bearing.

A two-file system (combining AGENTS.md and DESIGN.md, or combining DESIGN.md and PROJECT.md) might also work. The book's choice is three because the three concerns are clearly separable in practice. Whether two are clearly separable enough is an open practitioner question.

---

## Still puzzling

- **The 200-line size limit per file.** AGENTS.md has documented Codex behavior degrading past ~200 lines. DESIGN.md and PROJECT.md have not been similarly characterized. The book extends the limit by analogy; whether it holds is empirically untested.

- **brutalist.art as authority.** The chapter cites the author's own design system. Reader trust depends on transparency: the system has held up across multiple projects in this series, but it is not third-party-validated. Other approaches in the broader ecosystem (designmd.app's 454-design-system catalog, for example) are also defensible.

- **Mies van der Rohe vs. Eileen Gray.** The Wayback Machine figure is "less is more" Mies. The pantry research recommended swapping to Eileen Gray, whose total-design approach to E-1027 maps onto the three-file system more precisely (and improves the book's overall diversity spread). Either is defensible. The Mies attribution is also famously aphoristic and hard to source precisely; Gray's documented work would be a cleaner citation. *I have kept Mies here for consistency with the TIKTOC; if the author swaps, Gray is the recommended substitute.*

---

## AI Wayback Machine

🕰️ **Mies van der Rohe** (1886–1969) — German-American architect of the Bauhaus and the International Style, associated with the principle *"less is more."* The phrase summarizes the structural-frame concept that runs through his work: the building's structure defines what is built without determining every detail. The Barcelona Pavilion (1929) and the Seagram Building (1958) are the canonical examples. Mies argued that the architect's discipline is in *what is removed* — that an excess of decoration, materials, or competing systems weakens the structural argument. The three-file system is this principle as digital architecture: AGENTS.md is the structural frame; DESIGN.md is the constraint that prevents decoration drift; PROJECT.md's Intent Layer is the program brief. Within the constraints, execution is delegated. Outside the constraints, nothing happens. *(For a more precisely-documented total-design parallel, Eileen Gray's E-1027 villa — where every interior element from furniture to lighting was designed as part of one coherent intent — maps even more cleanly onto the three-file system; see "Still puzzling" above.)*

---

## Bridge

Three files complete. Ask Mode plan approved. Chapter 11 begins the simulation build — every step a specification, every output a handoff condition, every supervisory decision labeled.

---

[^1]: For the broader ecosystem, see designmd.app's library of 454 design systems for AI agents; VoltAgent's awesome-design-md collection on GitHub; the DEV Community discussion *"AGENTS.md, SKILL.md, DESIGN.md: How AI Instructions Split into Three Layers."* The Brutalist three-file system is one entrant in this conversation; the conversation itself is broader than any single system.

## Prompts

Use these prompts with Claude to generate interactive D3 v7 versions of the
figures in this chapter. Each produces a standalone HTML file you can open
in a browser and modify freely.

**Prerequisites:** Load `brutalist/CLAUDE.md` and `brutalist/DESIGN.md` into
your Claude project context before using these prompts. They define the stack,
naming conventions, color system, and typography the figures use.

---

### Figure 12.1 — Three-file system as three concentric circles or nested

Create a standalone D3 v7 HTML file for Figure Three-file system as three concentric circles or nested. Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: Three-file system as three concentric circles or nested boxes. Outer: AGENTS.md (technical constitution). Middle: DESIGN.md (visual constitution). Inner: PROJECT.md (project state — Intent Layer is human, always). Editorial style. No color.. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/12-three-file-system-fig-01.html`
