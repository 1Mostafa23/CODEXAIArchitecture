---
task: "Revise GDD After BA Review"
target: [[GameDesigner]]
input: [[GDD]]
---

# Handoff to GameDesigner
Revise [[GDD]] based on the BA review added on 2026-05-12.

## Input Files
- `GDD.md`
- `Tasks/Open/02-validate-gdd.md`
- `Tasks/Done/01-create-gdd.md`

## Required Changes
- Resolve every item under `BA Review — 2026-05-12 > Required Clarifications Before Approval`.
- Convert the "10 вопросов перед прототипом" section from open questions into concrete MVP decisions, or move any non-MVP questions into `Out of Scope (v1)`.
- Define exact MVP rules for controls, auto-attack targeting, room duration, slot-machine flow, possession, helper behavior, currencies, boss reward, and meta progression.
- Replace non-observable success criteria with QA-verifiable acceptance criteria.
- Keep the existing GDD structure; update the relevant sections directly instead of adding a separate design appendix.

## Acceptance Criteria
- No MVP requirement uses unresolved alternatives such as "или", "nearest or priority", "selected rooms", or "placeholder" where implementation behavior is required.
- A developer can create one-session task cards from the MVP without asking design questions about the core loop.
- BA can re-run validation and either approve the GDD or identify only non-blocking polish questions.

## Deadline
Next GameDesigner session.

## GameDesigner Result — 2026-05-12
Revision completed in `GDD.md`.

Resolved:
- Exact MVP control scheme: two-thumb portrait.
- Exact auto-attack targeting rule.
- Exact MVP room count and run duration target.
- Exact slot-machine appearances and interaction flow.
- Exact possession trigger and boundary rules.
- Писарь is automatic in MVP.
- MVP uses one currency: Индульгенционные жетоны.
- One concrete meta reward: **Сломанная Печать**.
- MVP success criteria replaced with QA-observable acceptance criteria.
