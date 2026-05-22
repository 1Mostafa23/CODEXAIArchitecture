---
task: "Revise GDD Machine Cadence and Buff Flow"
target: [[GameDesigner]]
input: [[GDD]]
---

# Handoff to GameDesigner
Revise [[GDD]] so the casino machine cadence matches the human owner's direction: the machine appears in each room and gives the player buffs. Also preserve the human owner's newer scope change: no pet/helper companion in MVP.

## Input Files
- `GDD.md`
- `Tasks/Done/09-revalidate-control-model.md`
- `STATUS.md`

## Required Changes
- Change the MVP machine cadence from 3 stops after rooms 2, 4, and 5 to a clear every-room cadence.
- If the intended behavior is post-combat, state it exactly as: after each combat room clear, rooms 1-5.
- Update every affected section: core loop, run structure, `Where the machine appears`, systems table, in-run progression, MVP scope, MVP acceptance criteria, and 10 MVP decisions.
- Make the buff role explicit: the machine presents buff cards and the player receives exactly 1 selected buff from each standard machine interaction.
- Define what happens when the player lacks tokens under the every-room cadence.
- Rebalance or define spin costs for all 5 machine stops.
- Confirm whether the optional cursed deal stays on the second machine stop.
- Remove any remaining active MVP pet/helper references.
- Decide whether the reward pool stays at 12 standard cards after removing helper cards or gets 3 replacement non-pet buff cards.
- Preserve movement-only portrait controls, auto-attack, automatic marked-vessel possession, one boss, and first meta unlock unless directly affected.

## Acceptance Criteria
- No active MVP section says the machine appears only after rooms 2, 4, and 5.
- The GDD clearly states whether the machine appears after each combat room clear or during each room.
- The player buff flow is implementation-ready: trigger, cost, card offer, selection, result, and insufficient-token behavior are defined.
- MVP acceptance criteria include the exact number of machine appearances and the exact number of buffs a full run can grant.
- Active MVP sections contain no pet/helper companion, helper upgrades, helper commands, helper reward category, or `Pisary` requirement.
- The standard reward pool count is exact and matches the listed cards after helper-card removal or replacement.
- BA can re-validate without asking whether the machine appears every room or only selected rooms.

## Deadline
Next GameDesigner session.

## GameDesigner Result - 2026-05-13
Revision completed in `GDD.md`.

Resolved:
- Rewrote the Sacred Demon Machine cadence from 3 selected stops to 5 automatic post-combat stops after rooms 1-5.
- Removed manual walk-up/manual spin flow from MVP; machine now auto-rolls after room clear.
- Defined standard buff flow: 3 visible standard cards, exactly 1 selected card, free and guaranteed after every combat room.
- Added 3 total reroll charges per run; reroll replaces all 3 visible standard cards and spends 1 charge.
- Locked duplicate rules: selected cards do not reappear during the run and duplicates cannot appear inside one offer.
- Kept the cursed deal only on machine stop 2 and made normal-card reroll unable to change it.
- Kept the active MVP reward pool at 12 standard cards after pet/helper removal.
- Preserved movement-only portrait controls, auto-attack, automatic marked-vessel possession, one boss, and the first meta unlock.

Next:
- [[BA]] re-validates using `Tasks/Open/11-revalidate-machine-cadence.md`.
