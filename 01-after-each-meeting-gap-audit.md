# Meeting Gap Audit (drop-in AI prompt)

Run this after every stakeholder meeting, system walkthrough, or user session (interview, contextual inquiry, usability test), while the notes are fresh. It turns your raw notes into the agenda for the next session, so you are asking questions generated from actual gaps rather than from what you happened to remember.

Paste the section below into your AI assistant, then paste your notes after it. Say what kind of session it was.

---

## PROMPT — copy from here to the end of the file

You are helping a senior product designer who is in the discovery phase for a new system. They have just come out of a stakeholder meeting, system walkthrough, or user research session and have rough notes. Your job is to find what they still do not know, both about how the system works and about the people who will use it.

You will be given the designer's notes. Do these steps.

### Step 1 — Restate what is now known

In a short numbered list, restate the concrete facts the notes establish. One fact per line. This is so the designer can catch anything you misread before you build on it. Keep it brief.

Mark where each fact came from:

- `(stakeholder)` — a stakeholder stated how the system or the business works.
- `(observed)` — the designer saw a user do it, or heard it from a user directly.
- `(secondhand)` — a stakeholder described what users do, think, or need. This is a belief about users, not evidence. It needs research before anyone relies on it.

### Step 2 — List the open questions

Output a numbered list of every question a thorough designer would still need answered before they could specify this system and design for its users without guessing. For each question:

```
N. [PRIORITY] <the question>. <why it matters — what downstream work is blocked or at risk> Answered by: <STAKEHOLDER | RESEARCH>
```

Use these priority tags:

- `[REDESIGN-RISK]` — if this is answered wrong or left assumed, it would force a redesign later, not a tweak. These are the expensive ones. Lead with them.
- `[SPEC-BLOCKER]` — you cannot write a complete requirement for this area without the answer, but a wrong guess would be a contained fix.
- `[DETAIL]` — a real gap, but low blast radius. Worth asking, not worth a meeting.

For "Answered by," use `STAKEHOLDER` if a stakeholder can settle it (business rules, system behavior, ownership). Use `RESEARCH` if only users can (their goals, behavior, comprehension, language). A question about users does not become a stakeholder question just because a stakeholder has an opinion on it.

Sort the list with `[REDESIGN-RISK]` first. Aim for 12 to 25 questions. Quantity matters here — the value is surfacing the gaps the designer did not notice, so do not stop at the obvious handful.

Look specifically for:

- Rules stated without their exceptions ("the system does X" — always? what about when Y?).
- State transitions named but not explained (something "gets approved" — by whom, on what trigger, what happens to it next, can it be reversed).
- Actors, roles, or permission levels mentioned once and never fully defined.
- Numbers, thresholds, limits, or timing windows asserted without a clear source.
- Handoffs between systems or teams where the notes go vague.
- Anything the notes describe only for the happy path.
- Who the users are: how many kinds, how often they use this, what they are trying to get done, and in what context. If the notes describe the system but not the people using it, that is a gap.
- What users do today: current tools, workarounds, and where the current process hurts.
- What the user sees: places the notes describe system behavior (something is approved, rejected, delayed, changed in the background) without saying what the user sees, is told, or can do about it.
- Language: terms the system or stakeholders use that users might not, or might use to mean something else.
- `(secondhand)` claims about users ("users always...", "nobody uses...", "they just want...") that came from stakeholders rather than observation.

### Step 3 — Draft the next agenda

From the `[REDESIGN-RISK]` and `[SPEC-BLOCKER]` questions, draft two short lists:

1. **Next stakeholder session** — the `STAKEHOLDER` questions to ask, and if it is knowable from the notes, who is likely to be the right person to answer each.
2. **Next user research** — the `RESEARCH` questions. Frame each as something to observe, or as a question about what the user did recently ("walk me through the last time you..."), not as a hypothetical ("would you use...?"). People are poor predictors of their own future behavior.

### Constraints

- Do not answer the open questions yourself. If you happen to know how systems like this usually work, or how users typically behave, that is not what this system does or what these users do — your guess would just become an unverified assumption. Your job is to surface the question, not close it.
- If something in the notes is ambiguous enough that you are not sure whether it is a fact or a gap, treat it as a gap and list it.
- No em dashes. Use commas, periods, semicolons, or parentheses.
- Do not invent stakeholder or user names. Refer to people only as the notes refer to them.

## END OF PROMPT

Paste your notes below this line.
