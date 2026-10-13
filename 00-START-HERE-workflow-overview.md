# The Assumption Loop — Workflow Overview (for a Senior Product Designer)

This is a process for taking upstream ambiguity (stakeholder meetings, walkthroughs, user research, scattered documentation) and turning it into a requirements doc you can trust enough to hand to PMs and to AI for prototyping. It is built around one idea: the requirements doc is your single point of failure, so the workflow exists to harden it before it propagates.

It pairs with the artifact loop you already use. The artifact loop asks whether a built thing is any good. This workflow asks what you are assuming, and where things break if you are wrong.

---

## The spine: assumption tags

Everything here depends on one discipline. In your requirements doc, every requirement carries a status tag:

- **CONFIRMED** — a named stakeholder confirmed this, with a date. Write down who and when. Use this for business rules and system behavior.
- **VALIDATED** — you observed this in user research. Write down the study and date (an interview round, a usability test, analytics, support tickets). Use this for claims about users: their goals, behavior, comprehension, and language.
- **ASSUMED** — you are inferring this. Write down what you are inferring it from (a doc, a half-answer in a meeting, analogy to another system, a stakeholder's description of what users do).
- **CONTRADICTED** — two sources implied different behavior. Write down both, unresolved.

The line between CONFIRMED and VALIDATED is the part that is easy to blur. When a stakeholder says "users always export to Excel first," that is not a confirmed requirement; it is a stakeholder's belief about users, and it stays ASSUMED until you see it in research. Stakeholders are the source of truth for how the business works. They are not the source of truth for how users behave.

This is not an AI step. It is a structural change to how you write the doc. It pays off everywhere downstream:

- The AI loops can attack the ASSUMED items specifically instead of treating everything as equally solid.
- PMs get a precise job. They are not "reviewing the doc," they are confirming or killing a specific list of ASSUMED items. Faster for them, higher-signal for you.
- Your research plan writes itself: the ASSUMED items about users are the questions your next study has to answer.
- When you prototype, you know exactly which edge cases sit on shaky ground.

If you do nothing else from this workflow, do this.

---

## The four prompts and when to run them

The errors get cheaper to fix the further left you catch them, so the prompts are ordered to catch them as early as possible.

| When | Prompt | What it catches |
|---|---|---|
| After each stakeholder meeting, walkthrough, or user session | `01-after-each-meeting-gap-audit.md` | Questions you still cannot answer; claims about users you only heard secondhand; what to put on the next agenda |
| Once you have notes from several sources | `02-when-notes-pile-up-contradiction-sweep.md` | Places two stakeholders implied different behavior, or where stakeholders and users tell different stories |
| Before the requirements doc goes to PMs or AI | `03-before-handoff-requirements-review.md` | Rules stated without exceptions, unsourced numbers, missing UI states, requirements with no user or goal attached |
| Before a poke-holes session or usability test | `04-before-poke-holes-prototype-review.md` | Where the UX breaks if a business or user assumption is wrong |

### Run order in practice

```
Session 1 (stakeholder or user) ──> [01 gap audit] ──> agenda for session 2
Session 2 (stakeholder or user) ──> [01 gap audit] ──> agenda for session 3
   ...
(enough notes) ──> [02 contradiction sweep] ──> conflicts to resolve with stakeholders or research
   ...
Draft requirements doc (with assumption tags)
   ──> [03 hostile review] ──> arbitrate ──> revise doc
   ──> doc goes to PMs (they work the ASSUMED list)
   ──> user assumptions go on the research plan
   ──> doc goes to AI to prototype
Prototype exists
   ──> [04 prototype review] ──> arbitrate ──> poke-holes session + usability test plan
   ──> (optional) artifact loop on the prototype itself
```

You will loop the early steps many times (one gap audit per session) and the later steps once or twice per cycle.

---

## How these prompts work (shared structure)

Prompts 02, 03, and 04 use the same arbitrate-then-revise shape as your artifact loop, because that is what gives them a pass/fail property instead of just generating more text:

1. The prompt produces a numbered list of findings.
2. It stops. You edit, add, or drop findings.
3. You say "continue" and it arbitrates each finding (VALID / INVALID / PARTIAL, or REAL / NOT-A-CONFLICT for the contradiction sweep).
4. Prompts 03 and 04 apply only what survived. Prompt 02 turns what survived into a list of questions to take back.

Prompt 01 (gap audit) is lighter — it just produces a prioritized question list, because there is nothing to arbitrate yet. You have not made claims, you are finding out what to ask.

The arbitration log is the audit trail. All the outputs together show what was challenged, what was kept, what was rejected, and why. That is what you show a skeptical PM or stakeholder.

---

## Important limit

These prompts are good at finding gaps, contradictions, and undefined states in your *documentation* of how a system works and who uses it. That is structural work and AI is reliable at it.

They cannot tell you what a business rule, approval chain, threshold, or compliance requirement *should actually be*, and they cannot tell you how real users will behave or what they will understand. An AI will confidently invent either if asked. Keep the prompts pointed at "is this doc internally complete and consistent." Keep "is this doc correct" with your stakeholders and PMs for business rules, and with research for user behavior. Every prompt below has this boundary written into it, but it is worth holding in your own head too.

---

## Where this lives

You do not need a new tool. The requirements doc lives wherever your requirements already live. The four prompt files live as files you paste into whatever AI assistant you use. The "workflow" is just knowing which file to paste when, which is what the table above is for.

If you want, keep this overview file pinned next to the requirements doc so the run order is always one click away.
