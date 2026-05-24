# Chapter 3 — From Prompts to Specifications: Ask Mode, Code Mode, and the First Build

> Ask Mode is for planning. Code Mode is for executing. Nothing goes to Code Mode without a reviewed plan. The class website is the first build.

---

## Learning outcomes

1. **(Apply)** Use Ask Mode to generate an implementation plan and review it before switching to Code Mode.
2. **(Apply)** Write a five-element specification prompt for a Code Mode task.
3. **(Analyze)** Identify the difference between a prompt that delegates and a specification that conducts.

---

## Opening

You have AGENTS.md. Codex knows your project. It is time to build something.

You take the smallest possible task: add one new page to your class website — a syllabus page that links from the navigation. You will use the Ask Mode → Code Mode gate. You will write a specification, not a prompt. You will review the plan before approving execution. When you are done, you will have built one deployable piece of your class website, *and* you will understand exactly why every choice you made was the right choice.

This is the pebble in the pond. Everything else in Act One expands outward from this one page.

![The Ask Mode / Code Mode sequence](images/04-prompts-to-specifications-fig-01.png)
*Figure 4.1 — The Ask Mode / Code Mode sequence*

---

## The gate, in operational detail

The previous chapter named the rule: nothing goes from Ask Mode to Code Mode without a reviewed plan. This chapter is how you actually do it.

**Step 1: Ask Mode interrogation.** You start in Ask Mode (the default for the Codex app's new session; in the CLI, `codex --ask-for-approval on-request`). You describe what you want to build at a useful level of detail: not "add a page," not "add a syllabus page to my class website," but the something-in-between that gives Codex enough to propose a real plan and gives you enough material to evaluate it. Something like: *"I want to add a syllabus page to my class website. It will list units, dates, and topics. It should follow the same head/nav structure as `src/index.html` and use the existing CSS. I want it linked from the nav of every other page."*

**Step 2: Codex proposes a plan.** Codex reads the relevant files, considers what you asked, and returns a plan. The plan should list the files it will create, the files it will modify, the steps it will take, and any assumptions it has made. If the plan does not include this level of detail, ask for it explicitly: *"Show me the file list and the steps before you start."*

**Step 3: You review the plan.** This is the gate. The plan in front of you is what Codex will do if you say yes. Read it. Look for assumptions. The most common ones in a website build: which CSS file gets the new styles (a new file vs. the existing one?), how the navigation gets updated (does Codex modify all three current pages, or one shared component that doesn't exist yet?), what the "same head/nav structure" actually means in practice. If anything in the plan is wrong, you correct it in Ask Mode *before* approving — corrections in Ask Mode are cheap; corrections in Code Mode are not.

**Step 4: You approve and Codex switches to Code Mode.** This is the only point in the build where you say "yes, do this." After this point, Codex executes the approved plan step by step, asking for confirmation on each file write if your sandbox is set to on-request.

**Step 5: You verify.** When Codex reports done, you verify against the handoff conditions you wrote (next chapter). For a new page: does it render in the browser? Does the new nav link work? Does it still render correctly on mobile? Have any of the *other* pages broken?

The gate is between steps 3 and 4. That is where almost all of the conducting work happens. Once Codex starts executing, the available decisions narrow dramatically; the cheap decisions are upstream.

---

## The five-element specification

The prompt you write for Codex is different from the prompt you write for ChatGPT.

ChatGPT prompts can be requests: *"write me a syllabus page."* That kind of prompt produces a generic syllabus page — not wrong, but not yours. Codex, given that prompt, will produce something equally generic. The difference shows up when the generated thing has to live in your specific project, with your specific conventions, alongside your specific other pages.

A **specification** is a complete task definition. It has five elements:

**1. The specific operation.** *Create a new file*, not "add a page." *Implement a function*, not "build the feature." *Move existing content*, not "reorganize." The operation should be a single verb-noun pair, narrow enough that you can verify whether it happened.

**2. The invariants.** What must NOT change. The existing pages' rendering. The existing CSS file's contents (if you do not want it modified). The navigation links on other pages (if you are not updating them). The deployment pipeline. The lint configuration. Anything that should still be true after the build that was true before the build.

**3. The context.** Which AGENTS.md sections govern this task. Which existing files Codex should reference as templates. Which conventions apply. You do not need to repeat everything in AGENTS.md (Codex has it loaded), but pointing at the relevant sections sharpens the prompt: *"Use the head/nav structure from `src/index.html` as a template. Follow the code-style section of AGENTS.md."*

**4. The output format.** What "done" looks like. Where the new file goes (path). What the file contains at a structural level. What gets linked to it. The output format is your handoff condition (Chapter 4) in prose form — by writing it here, you make it harder for Codex to call something done that isn't.

**5. The negative constraint.** What Codex must NOT do. *No JavaScript.* *No new dependencies.* *Do not modify `styles.css`.* *Do not change the navigation block in `index.html` (we'll do that in a separate step).* Negative constraints are the most-underused element. They are also the element most likely to prevent the "while I'm here, let me also fix this other thing" failure mode that scope-creeps your build.

---

## Worked example: the syllabus page

Here is the same task as a prompt and as a specification.

**Prompt (don't do this):**

> *"Add a syllabus page to my class website."*

**Specification:**

> **Operation:** Create a new file `src/syllabus.html`.
>
> **Invariants:** No existing files modified except `src/index.html` to add the nav link (see output format). The existing CSS in `src/styles.css` not changed. All existing pages still render correctly.
>
> **Context:** Use the head and nav structure from `src/index.html` as a template. Follow the code-style section of AGENTS.md (two-space indentation, single quotes, semantic HTML5).
>
> **Output format:** A complete `src/syllabus.html` containing: standard head with title "Syllabus — AP Computer Science", the same nav block as `src/index.html`, a main element with the page's content (units, dates, topics — empty `<section>` blocks I will fill in later, not lorem ipsum). The nav in `src/index.html` updated to include a link to `syllabus.html` between "Units" and "Office Hours".
>
> **Negative constraint:** No JavaScript. No new dependencies. Do not modify `src/styles.css`. Do not modify the nav in any page other than `src/index.html` — we will update the others in a separate step. Do not add CSS classes that do not already exist in `src/styles.css`.

Same task. Same Codex. Two very different outcomes. The prompt produces a generic syllabus page that may or may not fit your project. The specification produces the page that fits.

Now run the specification through Ask Mode first. Codex returns a plan. You read the plan: it will create the file, modify the nav in `index.html`, and (it adds) it noticed that `src/units.html` is the only other page with a self-referential nav link and asks whether to update that one too. You say no, that's the separate step. The plan is now approved. You switch to Code Mode. Codex executes. The page exists. The nav link works. `styles.css` is untouched.

**The lesson:** A specification is a prompt with the cost of being wrong written into it. The five elements are the cheap insurance.

**The limit:** Specifications do not prevent all failures. They prevent the *avoidable* failures — the ones where Codex did something different from what you wanted because you didn't tell it what you wanted clearly. They do not prevent the dangerous middle (Chapter 8), which is a deeper failure mode.

| Item | Meaning |
| --- | --- |
| Prompt vs. specification | two columns. Five rows showing each element. Left: weak prompt version. Right: specification version. No color. |

---

## Plan mode in practice: the review moment

The plan-mode review step is where the conducting discipline is most visible.

When Codex returns a plan in Ask Mode, the temptation is to skim it. The plan looks reasonable. You want to get to the building. You approve.

This is the move that produces the dangerous middle six steps later. The plan-review moment is when assumptions are cheap to catch. Once Codex is in Code Mode, the assumptions are baked into the output, and undoing them is expensive.

Two practical patterns help.

**Pattern 1: Edit the plan in your editor.** In the Codex CLI, `Ctrl+G` opens the plan in your text editor. Edit it. Remove steps Codex shouldn't take. Add steps Codex missed. Save and return. The plan is now what *you* approved, not what Codex proposed. This is the most useful five seconds you will spend in any Codex session.

**Pattern 2: Find the one assumption Codex got wrong.** Every plan, in my experience, contains exactly one assumption that is wrong. Sometimes it is small (Codex assumes a file path you would have written differently). Sometimes it is larger (Codex assumes a new CSS file should be created when you intended to add styles to the existing one). Finding the one assumption is the review goal. If you cannot find one, look harder. If you genuinely cannot find one, approve.

The plan review is the gate. The gate is the discipline. Everything downstream depends on it.

---

## Give Codex a way to verify its own work

The OpenAI engineers who use Codex daily report a striking finding: when you give Codex a way to *check its own output* — a test, a lint command, a bash script — Codex iterates against the check and the output gets dramatically better. When you do not, Codex generates once and reports done.[^1]

For the class website build, this means: include the verification command in your specification. *"After writing the file, run `npm run lint-html` and report any errors. If there are errors, fix and re-verify."*

The verification command is the seed of the handoff condition (Chapter 4). It is also the practical reason your AGENTS.md test section matters — Codex needs to know what verification looks like to perform it.

---

## Common misconceptions

**"Specifications are for big builds."** Any operation that can fail silently deserves a specification. A one-line CSS change can break three pages if Codex modifies the wrong rule. The five-element format is the *minimum* for any change that touches files you care about.

**"More words make a better specification."** No. Precision per element. A 30-word specification can be excellent. A 200-word specification can be vague. The test is not length; it is whether each of the five elements is *specific enough that you could verify it after the fact*.

**"Codex doesn't need all five elements; it'll figure out the rest."** Codex will fill in defaults for missing elements. Those defaults are reasonable averages of what most projects do. Your project is not the average. If you want your project's defaults, you have to say so. (This is also why AGENTS.md matters — it sets your project's defaults so the specification only has to mention the per-task ones.)

**"I can edit the generated code afterward."** Sometimes. Often the generated code is "almost right" in a way that makes editing it harder than rewriting it. The cost of catching a problem at the specification stage is one revised sentence. The cost of catching it after Code Mode is reading the generated diff, deciding what to keep, and either editing or starting over.

**"The plan review slows me down."** It saves you time on builds longer than one prompt. The math is approximately: 30 seconds reviewing a plan saves 5 minutes of editing wrong output. Even for trivial tasks the math is usually favorable. For the syllabus page in this chapter's worked example, the plan review took 90 seconds and prevented Codex from updating the navigation in three places when you only wanted one — a fix that would have cost more time than the original build.

---

## Exercises

1. **(Apply)** Use Ask Mode to plan the next page of your class website. Read the plan. Edit it in your text editor before approving. Document at least one specific edit you made.

2. **(Analyze)** Take a prompt you have used for Codex (or for ChatGPT writing code) in the past week. Rewrite it as a five-element specification. Run both through Codex. Document three specific ways the outputs differ.

3. **(Create)** Design a classroom activity that teaches the five-element specification format *without using the word "specification."* The students' build task should produce evidence that they understood the format — for instance, they could submit a specification that another student executes via Codex, with the output evaluated against the specification's invariants and negative constraints. Sketch the activity in one paragraph.

---

## Classroom activity

Have students build their first page using the Ask Mode → Code Mode gate. The build task: add a page to a starter class-website-style project you provide.

Constraints:
- Specification must contain all five elements (operation, invariants, context, output format, negative constraint).
- Ask Mode plan must be reviewed and at least one edit made before approval.
- Code Mode execution must produce a working page.

Peer review: students exchange specifications (not code). Each student executes a peer's specification through Codex and evaluates whether the output matches what the specification promised. The grading is not on the page; it is on whether the specification was precise enough that a third party (Codex) could produce the right page from it.

This activity maps to Chapter 8 of the students book — *Writing Codex Prompts That Are Specifications*. Your build experience this chapter is the example you will use when you teach the activity.

---

## Links

- OpenAI Codex prompting guide: [developers.openai.com/codex](https://developers.openai.com/codex)
- Codex best practices: [developers.openai.com/codex/learn/best-practices](https://developers.openai.com/codex/learn/best-practices)

---

## What would change my mind

The chapter's strong operational claim is that **the five-element specification format produces materially better Code Mode output** than free-form prompts. This is plausible from prompt-engineering literature broadly and from OpenAI's own published guidance, but it is not directly measured for K-12 teacher builds. A controlled study comparing free-form prompts to five-element specifications on the same teacher-build tasks — and finding no measurable difference in output quality, build time, or correction rate — would soften the chapter's prescription from "do this every time" to "do this for non-trivial tasks." The format would remain a good first habit; it would no longer be load-bearing.

---

## Still puzzling

- **How much of the specification can be omitted as Codex improves?** Frontier model capabilities have improved between 2023 and 2026. Some elements that were essential two years ago — explicit invariants, explicit negative constraints — may become less essential as model behavior improves. The book's prescription assumes the current state. The right granularity for next year's models is open.

- **Is there a fast path for trivial changes?** A typo fix in HTML. A one-character CSS adjustment. The five-element format feels heavy for these. Practitioner consensus is to skip the format for changes where the entire task fits in one verifiable sentence. Where the threshold is exactly is open.

- **How well does the format transfer across agentic tools?** The five elements are framed for Codex but the conducting discipline applies to Claude Code, Gemini, and successors. The exact specification format may need adjustment for tools with different defaults. The principle (specify enough that the model cannot reasonably misinterpret) is tool-agnostic.

---

## AI Wayback Machine

🕰️ **George Pólya** (1887–1985) — Hungarian-American mathematician whose *How to Solve It* (1945) formalized problem-solving as a four-stage process: understand the problem, devise a plan, carry out the plan, look back.[^2] Pólya's first stage — understand the problem — is the work this chapter calls Ask Mode interrogation. His second — devise a plan — is the work the chapter calls the five-element specification. His third — carry out the plan — is Code Mode. His fourth — look back — is verification (Chapter 4). The Ask Mode / Code Mode gate is Pólya's sequence applied to AI-assisted development, sixty years before the tool existed that required it. Pólya wrote for human problem-solvers; the discipline he named scales.

---

## Bridge

You have built a page. Codex did what you specified, because you specified clearly. Chapter 4 names the gate between build steps — the handoff condition — and explains why "looks good" is not one.

---

[^1]: OpenAI engineers, "How OpenAI Engineers use Codex to Tackle Big Projects with Rigor" (forum.openai.com, December 4, 2025): *"When Codex has some way to check its work — like run tests or screenshot the UI — it can iterate and get dramatically better results."*
[^2]: Pólya, G. *How to Solve It*. Princeton University Press, 1945. The Princeton Science Library 2014 reprint is the standard recent edition.
