# ARC Layered Model v2: review decisions

Review of `v2-draft.md` with Joshua, started 2026-11-21. Each decision is his. The lead
(Claude) states its view first; Joshua accepts, changes or rejects it.

## Part 1: abstract, introduction, overview (§1–2)

- **A. Name "Auditable Reasoning & Cognition".** Accepted.
- **B. Main thesis: layers are escalation points, not abstractions (OSI inverted).** Accepted.
- **C. Layer 7.** Accepted as: a human, or a policy that a human approved, for small decisions. The approved
  policy must trace back to the person who approved it.
  > I agree with those, the way you are leaning with them
  (The lead had not stated its view on C before this answer; it stated it after, and recorded it here.
  Joshua can change it.)
- **C, refined by Joshua.** Layer 7 can also hold strict rules for some cases: blanket statements such as
  "do no harm to humans".
  > I think layer 7 can be strict rules in some situations, for example blanket statements like do no harm
  > humans. But I would honestly hope and assume that it would have been resolved before it got to this point
  Lead's first reading ("a last guard"; a case that only Layer 7 stops is a lower-layer defect) was
  rejected:
  > I'm not sure I should say it like that, last guard. It's really the ethical and moral stuff that is the
  > burden on humans to decide so they can decide either way
  **Recorded meaning:** Layer 7 is where ethical and moral decisions sit. That burden belongs to humans, and
  the humans can decide either way. The system does not decide the moral question for them. A strict rule at
  Layer 7 (for example "do no harm to humans") is a moral decision that humans made and wrote down; it is
  not a safety net for lower layers.

## Part 2: Sensors, Layers 1–3 (§3, §4)

- **D. Sensors section, with the body as evidence.** Accepted.
- **E. Fusion.** Accepted as a duty inside Layer 2, not a layer of its own. (Answers the draft's open question.)
- **F. "Salience is a routing decision, not just a score."** Open: Joshua asked for more information.
  - Joshua corrected the lead's example ("delete the customer's data?" as a Layer 7 case):
    > I think delete the customers data is not the right example, like dropping their database tables? Or
    > deleting some files or something within their task? I think the question of the scope of the impact
    > level 6 could figure this out or we would have to go to level 7 I suppose
    **Recorded:** a delete is not a moral question by itself. Scope and impact are a Layer 6 question
    (Layer 4 can flag "cannot be undone" or "out of scope" so that the signal climbs). It goes to Layer 7
    only when it becomes a question of right and wrong. Lead's proposed Layer 7 example: using a person's
    private messages to train a model when they did not agree (not yet confirmed).
