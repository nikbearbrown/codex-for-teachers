# Chapter 2 — AGENTS.md: Your Coding Constitution

> AGENTS.md is the file Codex reads at the start of every session. It is the difference between a Codex that knows your project and a Codex that guesses.

---

## Learning outcomes

By the end of this chapter, you will be able to:

1. **(Understand)** Explain what AGENTS.md is, where it lives, and when Codex reads it.
2. **(Apply)** Write an AGENTS.md for a classroom build project using the five-element format.
3. **(Analyze)** Distinguish AGENTS.md content (always-on rules) from task-queue items (session-specific work).

---

## Opening

You sit down for your second Codex session.

Yesterday you spent thirty minutes in Ask Mode calibrating Codex on your class website project. You learned the framework, the naming conventions, the deployment quirks, the fact that your school server's mod_rewrite is older than your students. You typed all of this out into Codex. By the end of the session, Codex understood the project.

Today, Codex remembers nothing.

You open the session. You start typing. Within two prompts you have explained the framework again. Within five you are repeating the mod_rewrite quirk. By the tenth prompt, you are typing yesterday's calibration session almost verbatim, and you realize you have just spent fifteen of your thirty Monday-night minutes telling Codex what you told Codex yesterday.

This chapter ends that.

<!-- → [DIAGRAM: AGENTS.md in the session context — loaded at session start, persists across the session. Without AGENTS.md: Codex guesses. With AGENTS.md: Codex knows.] -->

---

## What AGENTS.md is

AGENTS.md is a markdown file that Codex reads automatically at the start of every session. You write it once. You update it as you go. Codex loads it into context before any other prompt, and consults it as the project's coding constitution.[^1]

Three things make this powerful:

1. **It is automatic.** You do not paste AGENTS.md into your first prompt every session. Codex finds it, reads it, applies it. You can confirm it loaded with `/memory` in the CLI or by asking Codex what conventions it sees.

2. **It is hierarchical.** Codex looks for AGENTS.md in multiple locations and concatenates what it finds. Your personal preferences live in `~/.codex/AGENTS.md` (your home directory). Project-specific rules live in `AGENTS.md` at the project root. Subdirectory-specific rules — say, rules that apply only inside a `simulations/` folder — live in `simulations/AGENTS.md` and are loaded when Codex works in that subdirectory.[^2]

3. **It is short.** The technical limit is 32 KiB combined across all the AGENTS.md files Codex loads (the `project_doc_max_bytes` setting). The *operational* limit — the size beyond which Codex starts ignoring your actual instructions — is much smaller. Practitioner consensus is **under 200 lines.** Bloated AGENTS.md files cause Codex to skim. A focused 100-line AGENTS.md gets followed more reliably than a 500-line one that contains everything you could think of.

The OpenAI engineers who write Codex for a living put the size discipline bluntly: *"Keep AGENTS.md short and human-readable. Bloated files cause Codex to ignore your actual instructions."*[^3] Treat it as a serious constraint.

---

## The five-element format

A good AGENTS.md for a classroom build contains five elements. None of them are optional; none of them should bloat past what the project actually needs.

**1. Stack and build.** What language, what framework, what build process (or lack of one), what deployment target. Codex can usually infer most of this from the code, but writing it out catches the cases where it cannot — and gives you a place to record the *intentional absence* of standard tooling (no bundler, no TypeScript, no test framework).

**2. Code style deviations.** Standard conventions Codex can figure out; deviations from them it cannot. If your class website uses kebab-case CSS classes everywhere, you do not need to say that — Codex will see it in the existing code. If your project uses snake_case for one specific reason and you do not want Codex to "fix" it to camelCase later, you must say so.

**3. Test and verification.** What command runs the lint check? What command runs the tests? What is the manual verification step? If your verification is "I open it in the browser on my phone," write that down. Codex will not invent a test framework for you, but if you do not tell it your verification step, Codex will assume there isn't one and write code that is hard to verify.

**4. Architectural decisions.** The decisions you have made that you do not want Codex to revisit every session. "Each page is self-contained; no templating system." "No JavaScript framework; vanilla JS only." "Shared components are template literals inlined at build, not iframes." These are the decisions that, if Codex did not know them, would result in Codex helpfully proposing the "improvement" you have already considered and rejected.

**5. Environment quirks and lessons learned.** The things that have already bitten you. Your school server's old mod_rewrite. The fact that the laptop where you grade does not have Node installed. The pattern Codex made a mistake on once and you do not want it to make again. This section grows over time. Treat it as a running record.

---

## Worked example: an AGENTS.md for the class website

Here is a real AGENTS.md for a class website project. Under 200 lines. Five sections. Checked into git from session one.

```markdown
# AGENTS.md — Mr. Brown's AP Computer Science Class Website

## Stack and build

- Static HTML/CSS/JavaScript. No build step.
- Files live in `src/`; deployed via `npm run deploy` (rsync to school server).
- No bundler. No preprocessor. ES modules where JavaScript is needed.

## Code style

- Two-space indentation in HTML and CSS.
- Single-quoted attributes consistently.
- CSS class names in kebab-case.
- Semantic HTML5 elements (`<article>`, `<section>`, `<nav>`); no div-soup.
- No CSS variables yet (this may change; ask before introducing).

## Test and verification

- After any HTML change, run `npm run lint-html` (broken-link + a11y check).
- After any CSS change, manual visual check on mobile breakpoint
  (Chrome devtools, iPhone preset).
- No automated tests. Verification is visual + lint.

## Architectural decisions

- Each page is a self-contained `.html` file. No templating.
- Navigation block is currently copy-pasted across pages. We plan to fix this
  eventually but NOT in the current build.
- No JavaScript framework. Vanilla JS only.
- No client-side routing. Each link is a real page.

## Environment quirks and lessons learned

- School server uses outdated mod_rewrite. All paths end in `.html` explicitly.
  No trailing slashes for canonical URLs.
- The laptop I use for grading does not have Node installed. Anything that
  requires Node must run on my main machine, not the grading laptop.
- 2026-02-14: Codex tried to extract repeated nav into a `<template>` element.
  Reverted. We are NOT templating until I'm ready. Add this to the architectural
  decisions list above.
```

Five sections. Under 200 lines (the example is about 35 lines; most teacher projects will land between 50 and 120). Checked into git. Every Codex session in this project starts with this context loaded.

The lessons-learned section will grow. Each entry is one date, one mistake, one fix. After a year of regular use, this section is the single most useful artifact you have for working in this project — and, as we will see in Chapter 13, it becomes a teaching artifact you can share with your students.

---

## What NOT to include

A common failure mode is the AGENTS.md that contains too much. Things that do *not* belong:

- **Things Codex can figure out from the code.** If the project uses Eleventy and the `package.json` says so, you do not need to tell Codex that. Codex reads `package.json`. Adding it to AGENTS.md wastes the budget.
- **Standard conventions.** Codex knows that HTML uses lowercase tag names. Codex knows that JavaScript uses semicolons (or doesn't — the project's existing files will tell it which). Save the AGENTS.md for the things Codex *would not* know.
- **Constantly changing state.** Don't put "the current branch is `feature/syllabus`" in AGENTS.md. Branches change. Put it in your prompt for the session.
- **Secrets, credentials, API keys.** AGENTS.md goes in git. Anything sensitive belongs in a `.env` file you do not commit, or in your shell environment, or in your password manager. Codex should never need a credential to do classroom build work.
- **Personal preferences unrelated to the project.** Your preference for two-space indentation belongs in your personal `~/.codex/AGENTS.md`, not the project AGENTS.md.

The discipline is: **does Codex need to know this *every* session in *this* project?** If yes, AGENTS.md. If no, prompt or omit.

<!-- → [TABLE: AGENTS.md include/exclude — two columns. Include: bash commands Codex can't guess, code style deviations, test runners, architectural decisions, quirks. Exclude: what Codex can figure out, standard conventions, changing content, secrets, personal preferences. No color.] -->

---

## AGENTS.md vs. the task queue

Two things look similar and are not. AGENTS.md is **persistent context** — the rules that govern every session in this project. The **task queue** (Chapter 9) is **session-specific work** — the things you want Codex to do in this session or to fire off into the background.

A rule of thumb: if you find yourself adding something to AGENTS.md and your second thought is "but this is just for this week," it does not belong in AGENTS.md. Put it in your prompt or in the task queue. AGENTS.md is the project's constitution. The task queue is its weekly agenda.

---

## How to start: `/init` and refine

Codex has a starter command. In the Codex app or CLI, `/init` generates a first-draft AGENTS.md by reading your codebase and proposing what it noticed. Run it on day one.

The starter will be imperfect. It will guess at conventions that are not yet visible. It will miss things you know that are not in the code. That is fine. **Treat `/init` as the rough draft. Your refinement is the work.**

A typical refinement pass:

1. Run `/init`. Read what Codex proposed.
2. Delete anything Codex obviously already knows from the code.
3. Add the architectural decisions you have made that aren't visible.
4. Add the environment quirks.
5. Start the lessons-learned section empty.
6. Save. Commit to git.

Total time: 20–30 minutes the first time. Much less for subsequent projects. This is the upstream investment that pays back every session for the life of the project.

---

## The `/memory` command

In the CLI, the `/memory` command shows you all the AGENTS.md files Codex has loaded for the current session — global, project root, subdirectories. Useful when Codex is doing something you didn't expect and you want to verify what context it is operating with. If a rule you wrote in AGENTS.md is being ignored, `/memory` is your first check.

---

## Common misconceptions

**"AGENTS.md is documentation for Codex."** Technically yes; pedagogically misleading. You write AGENTS.md *for yourself first*. The act of writing it forces you to make project decisions explicit. Codex is the secondary beneficiary. You are the primary one.

**"More is better."** No. The 200-line operational ceiling is real. A focused 80-line AGENTS.md that captures the decisions you actually need beats a 600-line one that tries to cover everything. If your AGENTS.md is over 200 lines, prune.

**"I'll start AGENTS.md when the project is bigger."** The smallest project benefits. Even a single-page experiment is easier to extend if Codex knows what you decided. Start AGENTS.md at minute one of the project; let it grow as the project does.

**"/init is sufficient."** /init is the starter. The refinement is the discipline. Treat the /init output as a draft you edit, not a finished document. Codex's read of your codebase is partial by design — it can only see what is in the code, not what you have decided not to put there.

**"AGENTS.md is for solo work; teams use something else."** No. AGENTS.md is exactly the thing teams use. The project AGENTS.md is committed to git and read by every team member's Codex. This is its team-level value: shared conventions, shared lessons-learned, shared "never do X" rules.

---

## Exercises

1. **(Apply)** Write an AGENTS.md for your class website project. Use `/init` to generate the starter, then refine. Five sections. Under 200 lines. Commit to git.

2. **(Analyze)** Run a Codex session in Ask Mode *without* your AGENTS.md (rename it temporarily), then with it. Ask Codex to propose a plan for adding a new page. Compare the two plans. Document three specific differences. Which assumptions did the AGENTS.md remove?

3. **(Evaluate)** One week from now, review your AGENTS.md. Which entries has Codex been ignoring? Which lessons-learned entries have you accumulated? Fix at least one entry that isn't working as written.

---

## Classroom activity

Have your students write an AGENTS.md for a provided starter project (a small open-source landing page, a CS-1 problem set scaffold, or any project with enough structure to have conventions but small enough to read in 20 minutes).

Constraints:
- Five sections, the same as yours.
- Under 200 lines.
- Each student commits to a private branch.

Class discussion:
- What did different students include?
- Where did they disagree on what was a deviation vs. a standard convention?
- Run the same prompt through Codex twice — once with one student's AGENTS.md, once with another's — and compare outputs. Whose AGENTS.md produced the closer-to-intended result?

This maps to Chapter 6 of the students book — *AGENTS.md as your project memory*. Your students are learning the same artifact from the student angle. Your build experience is what makes the activity teachable.

---

## Links

- AGENTS.md documentation: [developers.openai.com/codex/guides/agents-md](https://developers.openai.com/codex/guides/agents-md)
- OpenAI's own AGENTS.md (worth reading as a production example): [github.com/openai/codex/blob/main/AGENTS.md](https://github.com/openai/codex/blob/main/AGENTS.md)

---

## What would change my mind

The chapter's core operational claim is that **AGENTS.md materially improves session output quality** for non-trivial projects. If a controlled comparison — same project, same prompts, with and without an AGENTS.md — showed no measurable difference in output quality or in session length, the chapter's argument collapses. The artifact would still be a useful place to write decisions down for your own future reference; the *Codex benefit* would be in question.

OpenAI's own documentation, the broader practitioner literature, and personal experience all converge on the claim that AGENTS.md helps materially. A clean negative result would be surprising but not impossible.

---

## Still puzzling

- **When does AGENTS.md hurt more than it helps?** Anecdotally, bloated AGENTS.md files cause Codex to ignore instructions. The threshold is fuzzy. Practitioners use 200 lines as a rule of thumb; the actual cliff is undocumented.

- **AGENTS.override.md and managed-policy locations.** AGENTS.override.md takes precedence when present, and some enterprise Codex deployments enforce district-level AGENTS.md at a managed-policy location. The book's primary reader is the individual teacher; managed-policy is out of scope. Whether districts will adopt this pattern for K-12 is open.

- **AGENTS.md vs. Skills.** Codex Skills (a 2026 feature) are reusable workflow templates, conceptually adjacent to AGENTS.md but invoked on-demand rather than loaded automatically. The book uses AGENTS.md as the spine; Skills appear in Chapter 6 of the *Claude Code for Teachers* book under a different name. Whether Codex Skills will become central to teacher workflows by the next edition of this book is open.

---

## AI Wayback Machine

🕰️ **Donald Knuth** (born 1938) — computer scientist who created TeX and articulated the principle of **literate programming**: that a program should be written for humans to read, with the code as a side effect, so that both the human reader and the machine reader are served simultaneously.[^4] In *Literate Programming* (1984), Knuth wrote: *"Instead of imagining that our main task is to instruct a computer what to do, let us concentrate rather on explaining to human beings what we want a computer to do."* AGENTS.md is literate programming applied to AI collaboration. The human writes the explanation; both the human and Codex benefit. Knuth's 1984 paper is the conceptual ancestor of every project-context file in the 2024–2026 ecosystem — CLAUDE.md, AGENTS.md, CLI.md, DESIGN.md.

---

## Bridge

You have AGENTS.md. Codex knows your project. Chapter 3 teaches you to use the Ask Mode → Code Mode gate correctly — and to write Codex prompts that are not requests but specifications. The class website's first page is the build.

---

[^1]: OpenAI, "Custom instructions with AGENTS.md – Codex" (developers.openai.com/codex/guides/agents-md). The discovery hierarchy and 32 KiB combined-size limit are documented there.
[^2]: Subdirectory AGENTS.md files are particularly useful by Chapter 10, when the simulation build introduces a new subdirectory with simulation-only rules. The chapter's introduction to subdirectory AGENTS.md is the foreshadowing for that.
[^3]: OpenAI engineers, "How OpenAI Engineers use Codex to Tackle Big Projects with Rigor" (forum.openai.com, December 4, 2025).
[^4]: Knuth, D. E. "Literate Programming." *The Computer Journal* 27, no. 2 (1984): 97–111.
