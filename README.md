# The Assumption Loop

A discovery workflow for UX and product designers. It turns messy upstream input (stakeholder meetings, system walkthroughs, user research, scattered documentation) into a requirements doc that is safe to hand off and safe to prototype from, then pressure-tests the prototype against whatever is still unverified.

Audience: designers running discovery, and the program managers they work with on a project.

---

## The problem this solves

In discovery, you sit through stakeholder meetings and slowly build a mental model of how a system works and who uses it. By the time you write the requirements doc, that model feels obvious to you. It is not obvious to anyone who was not in the room, and it is not complete. Every rule you wrote down has an exception you have stopped noticing. Every screen you are picturing has states you have not designed. And much of what you "know" about users came secondhand, from stakeholders describing what users do rather than from watching users do it.

That requirements doc then goes two places at once, to PMs for validation and to AI for prototyping, so any gap in it gets inherited by both paths and does not surface until a prototype is already built.

The assumption loop is a set of checkpoints that harden the doc before it propagates.

## How it pairs with the artifact loop

These are two validation loops that ask different questions:

- **Artifact loop** asks "is this artifact any good?" It reviews a thing that has been built (a screen, a prototype, a spec). Adversarial review, arbitration, revision.
- **Assumption loop** (this folder) asks "what are we assuming, and where does it break if we are wrong?" Most of it runs before anything is built, on meeting notes and the requirements doc. The last prompt runs on a prototype, but it targets the assumptions underneath, not the polish.

Same shape — draft, review, arbitrate, revise — pointed at a different risk.

## The one idea everything depends on

Every requirement in the doc carries a status tag:

- **CONFIRMED** — a named stakeholder confirmed it, with a date. Use this for business rules and system behavior.
- **VALIDATED** — observed in user research (interviews, usability tests, analytics, support tickets), with the study and date. Use this for anything about users: what they need, what they do, what they understand.
- **ASSUMED** — you are inferring it. The doc records what it is inferred from.
- **CONTRADICTED** — two sources implied different things. Both are recorded, unresolved.

One rule keeps the tags honest: **a stakeholder's claim about users is ASSUMED, not CONFIRMED.** A stakeholder can confirm how an approval rule works. They cannot confirm that users will understand the approval screen. Only research moves a user assumption to VALIDATED.

This is the spine. It gives the AI prompts something specific to attack, it gives PMs a precise job, and it tells you what your next round of research has to cover.

---

## For program managers — start here

You do not need to read every file. Here is your part:

1. The requirements doc you receive has every requirement tagged CONFIRMED, VALIDATED, ASSUMED, or CONTRADICTED.
2. Your review is not "read the whole doc and react." It is: **work the ASSUMED and CONTRADICTED list.** Each of those is a specific question, confirm it, correct it, or kill it.
3. Some ASSUMED items are about users rather than the business ("approvers check status daily," "customers know what a hold means"). Tell the designer whether they match what you have seen; that is useful. But your agreement does not make them VALIDATED. Those go on the research plan.
4. CONFIRMED and VALIDATED items already have a source attached. You can spot-check them, but the ASSUMED list is where your time pays off.

That is the whole ask. The doc is structured so your review is fast and high-signal instead of a vague pass over everything.

## For designers — how to run it

There are four drop-in AI prompts (`01` to `04`) plus an overview (`00`). Paste a prompt into any AI assistant, then paste in the material it asks for. Work through them in order across a project, running `01` after every session:

- `00-START-HERE-workflow-overview.md` — the full map and run-order diagram. Read this first.
- `01-after-each-meeting-gap-audit.md` — run after every stakeholder meeting, walkthrough, or user session; produces the next session's agenda and flags claims about users that need research.
- `02-when-notes-pile-up-contradiction-sweep.md` — run once notes from several sources have accumulated; finds quiet disagreements, including where stakeholders and users tell different stories.
- `03-before-handoff-requirements-review.md` — run on the requirements doc before it goes to PMs or AI; hostile review of the doc itself, including missing UI states and requirements with no user attached.
- `04-before-poke-holes-prototype-review.md` — run on a prototype before a poke-holes session or usability test; targets the unverified assumptions, about the business and about users.

Files 02, 03, and 04 pause partway through for you to edit the findings, then continue to arbitration. That pause is the point — it keeps the loop from being a mirror.

---

## Important limit

These prompts find gaps, contradictions, and undefined states in *how a system and its users are documented*. That is structural work and it is reliable.

They cannot tell anyone what a business rule, an approval chain, a pricing or eligibility threshold, or a compliance requirement *should actually be*. They also cannot tell anyone how real users will behave, what they will understand, or what they need. An AI will confidently invent either if asked. Every prompt is instructed to flag those and route them rather than guess: business rules to stakeholders, user behavior to research. Internal completeness and consistency are the AI's job. Business correctness stays with stakeholders and PMs; the truth about users comes from research.

---

## File list

```
README.md                                       this file
00-START-HERE-workflow-overview.md               the map; read first
01-after-each-meeting-gap-audit.md                run after each meeting or user session
02-when-notes-pile-up-contradiction-sweep.md      run when notes accumulate
03-before-handoff-requirements-review.md          run before PM/AI handoff
04-before-poke-holes-prototype-review.md          run before a poke-holes session or usability test
```
