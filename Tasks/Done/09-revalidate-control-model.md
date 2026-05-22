---
task: "Re-validate Revised Control Model"
target: [[BA]]
input: [[GDD]]
---

# Handoff to BA
Re-validate [[GDD]] after the GameDesigner control-model revision completed on 2026-05-13.

## Input Files
- `GDD.md`
- `Tasks/Open/08-revise-gdd-control-simplification.md`
- `STATUS.md`

## Acceptance Criteria
- Confirm MVP combat input is now implementation-ready as movement-only portrait control with one floating joystick.
- Confirm dash is removed from active MVP controls, combat requirements, reward effects, audio requirements, MVP scope, and acceptance criteria.
- Confirm auto-attack targets the nearest living enemy or boss within 6 gameplay meters with a deterministic tie-breaker.
- Confirm automatic possession is implementation-ready: marked vessel spawn rules, marker visibility, charge requirement, trigger distance/time, no manual button, no separate cooldown, target death behavior, and empty-body fail rule are all defined.
- Confirm the 15-card MVP reward pool still has exactly 15 standard cards and no card depends on manual dash.
- If approved, mark [[GDD]] ready for [[Architect]] routing again. If blocked, add only remaining blocking questions to `GDD.md`.

## Deadline
Next BA session.

## BA Result - 2026-05-13
Validation remains blocked. BA added `BA Control and Machine Re-validation - 2026-05-13` to `GDD.md` and created `Tasks/Open/10-revise-gdd-machine-each-room.md` for [[GameDesigner]].

Pass:
- Movement-only portrait controls are comfortable enough for MVP.
- Dash/manual possession removal is clear.
- Auto-attack and automatic possession rules are implementation-ready.
- The 15-card reward pool remains intact and no standard card depends on manual dash.

Blocker:
- The GDD still says the casino machine appears only after rooms 2, 4, and 5. It does not match the requested direction that the machine appears in each room and gives the player buffs.
