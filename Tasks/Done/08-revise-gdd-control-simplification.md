---
task: "Revise GDD Control Model"
target: [[GameDesigner]]
input: [[GDD]]
---

# Handoff to GameDesigner
Revise [[GDD]] after the human owner rejected the current two-thumb action layout as uncomfortable.

## Input Files
- `GDD.md`
- `Tasks/Done/07-architect-mvp-task-breakdown.md`
- `STATUS.md`

## Confirmed Changes
- Keep portrait orientation, but reduce active combat buttons.
- Player controls movement; attacks are fully automatic.
- Delete manual dash from MVP.
- Auto-attack targets the nearest valid enemy, including bosses.
- Possession is automatic/contextual: the level spawns special valid possession enemies, those enemies are visibly marked, and possession triggers when the player is near a marked valid enemy.

## Required Design Decisions
- Define the exact automatic possession trigger:
  - how close the player must be to a marked valid enemy,
  - whether possession also requires a full charge meter,
  - what happens if multiple marked valid enemies are near,
  - what happens if the marked enemy dies before possession triggers,
  - how many possession-valid enemies can appear per room.
- Update the core loop, controls, MVP scope, acceptance criteria, and out-of-scope list to match the new control model.
- Remove or rewrite every MVP requirement that depends on manual dash.
- Preserve the 6-8 minute MVP run, 5 combat rooms, 3 machine stops, 15-card reward pool, single cursed deal, helper, boss, and first meta unlock unless the control revision makes a direct conflict.

## Acceptance Criteria
- The GDD no longer claims dash is part of MVP controls, combat, rewards, or acceptance criteria.
- The GDD has one clear combat input model: movement-only combat input, automatic attacks, and no manual dash or manual possession button.
- Auto-attack targeting is defined for normal enemies and bosses.
- Possession is implementation-ready as automatic/contextual possession of visibly marked valid enemies.
- BA can re-validate without finding contradictions between controls, MVP scope, and acceptance criteria.

## Deadline
Next GameDesigner session.

## GameDesigner Result - 2026-05-13
Revision completed in `GDD.md`.

Resolved:
- Rewrote MVP controls as movement-only portrait input with one floating joystick.
- Removed dash from MVP controls, combat scope, reward effects, audio SFX, and acceptance criteria.
- Replaced manual possession with automatic possession of visibly marked valid enemies.
- Defined exact automatic possession rules: rooms 2-5 each spawn exactly 1 marked weak cultist or fast fanatic vessel; trigger requires 100% charge and 0.35 seconds within 2.5 gameplay meters; no separate cooldown after possession.
- Updated auto-attack to target the nearest living enemy or boss within 6 gameplay meters.
- Updated MVP scope, acceptance criteria, reward cards, enemy possession rewards, and out-of-scope lines to match the simplified control model.
