---
task: "Clean Up GDD After BA Re-validation"
target: [[GameDesigner]]
input: [[GDD]]
---

# Handoff to GameDesigner
Make a small requirements cleanup pass on [[GDD]] based on `BA Re-validation — 2026-05-12`.

## Input Files
- `GDD.md`
- `Tasks/Open/04-revalidate-gdd.md`

## Required Changes
- Define the exact MVP slot-machine reward pool. If MVP keeps 15 standard cards, list all 15 exact card names and effects. If not, reduce the MVP count to the exact listed cards.
- Define the exact single MVP cursed deal as one reward plus one curse.
- Label non-MVP enemies, possession types, bosses, jackpot rewards, rerolls, and risk-deal examples as Post-MVP.
- Add explicit portrait performance caps for simultaneous enemy projectiles, visible pickups, and active VFX.

## Acceptance Criteria
- Architect can identify the MVP enemy list, MVP possession list, MVP reward pool, and Post-MVP examples without interpretation.
- BA can verify the portrait game constraints from the GDD without asking for object-count assumptions.
- No new mechanics are added beyond cleanup and labeling.

## Deadline
Next GameDesigner session.

## GameDesigner Result — 2026-05-12
Cleanup completed in `GDD.md`.

Resolved:
- Exact 15-card MVP reward pool is listed under `MVP reward pool`.
- Exact MVP cursed deal is listed as `Фанатичный кредит`.
- Non-MVP enemies, possession types, biomes, bosses, jackpot rewards, and risk-deal examples are labeled `Post-MVP`.
- Portrait performance caps now include enemies, enemy projectiles, visible pickups, and active VFX.
