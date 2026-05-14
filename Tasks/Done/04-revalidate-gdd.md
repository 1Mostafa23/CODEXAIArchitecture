---
task: "Re-validate Revised GDD"
target: [[BA]]
input: [[GDD]]
---

# Handoff to BA
Re-validate [[GDD]] after the GameDesigner revision completed on 2026-05-12.

## Input Files
- `GDD.md`
- `Tasks/Open/03-revise-gdd-ba-gaps.md`
- `Tasks/Open/02-validate-gdd.md`

## Acceptance Criteria
- Confirm the BA blocking issues from `BA Review — 2026-05-12` are resolved in the main GDD sections.
- Confirm MVP requirements are implementation-ready for [[Architect]] task breakdown.
- Confirm mobile feasibility: two-thumb portrait controls, no helper command button, 10-enemy cap, post-combat machine interaction, readable 3-card reward UI.
- Confirm acceptance criteria are observable by QA on an Android test device.
- If approved, mark the GDD ready for [[Architect]] routing; if blocked, add only the remaining blocking questions to `GDD.md`.

## Deadline
Next BA session.

## BA Result — 2026-05-12
Validation remains blocked. BA added `BA Re-validation — 2026-05-12` to `GDD.md`.

Remaining blockers:
- MVP says 15 standard reward cards, but only 10 standard cards are defined.
- The single MVP cursed deal needs one exact reward+curse pair.
- Post-MVP enemies/possession/boss examples need labels so Architect does not scope them into MVP.
- Portrait performance caps need explicit limits for projectiles, pickups, and active VFX.
