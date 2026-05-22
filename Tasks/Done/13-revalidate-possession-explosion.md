---
task: "Re-validate Possession Explosion Clarification"
target: [[BA]]
input: [[GDD]]
---

# Handoff to BA
Re-validate [[GDD]] after the GameDesigner possession-explosion clarification on 2026-05-14.

## Input Files
- `GDD.md`
- `Tasks/Done/12-clarify-possession-explosion.md`
- `STATUS.md`

## Acceptance Criteria
- Confirm the active possession rules explicitly answer: marked-vessel possession does not explode by default.
- Confirm default possession exit destroys the vessel without explosion VFX, area damage, extra token, or pickup.
- Confirm **P03 Последний вздох** is the only MVP source of possession-exit explosion.
- Confirm **P03 Последний вздох** defines trigger timing for timer end, room clear, and controlled-enemy death.
- Confirm **P03 Последний вздох** defines exact damage, radius, target filters, hero-body damage rule, token/pickup rule, and VFX-cap behavior.
- Confirm MVP scope and MVP acceptance criteria match the buff-only explosion decision.
- Confirm the active MVP reward pool remains exactly 12 standard cards and **P03 Последний вздох** remains uniquely useful.
- Confirm no pet/helper system, dash button, manual possession button, or manual machine spin is reintroduced.

## Deadline
Next BA session.

## BA Result - 2026-05-14
Validation approved.

Pass:
- Active possession rules explicitly answer that marked-vessel possession does not explode by default.
- Default possession exit destroys the vessel without explosion VFX, area damage, extra token, or pickup.
- **P03 Последний вздох** is the only MVP source of possession-exit explosion.
- **P03 Последний вздох** defines trigger timing for timer end, room clear, and controlled-enemy death.
- **P03 Последний вздох** defines exact damage, radius, target filters, hero-body damage rule, token/pickup rule, and VFX-cap behavior.
- MVP scope and MVP acceptance criteria match the buff-only explosion decision.
- The active MVP reward pool remains exactly 12 standard cards, and **P03 Последний вздох** remains uniquely useful.
- No active MVP section reintroduces a pet/helper system, dash button, manual possession button, or manual machine spin.

Decision:
- [[GDD]] is approved as validated requirements for [[UXDesigner]] routing under the 8-agent pipeline.

Next:
- [[UXDesigner]] creates MVP UX/UI specs using `Tasks/Open/15-create-mvp-ux-ui-specs.md`.
