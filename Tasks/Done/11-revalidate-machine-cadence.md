---
task: "Re-validate Machine Cadence and No-Pet MVP"
target: [[BA]]
input: [[GDD]]
---

# Handoff to BA
Re-validate [[GDD]] after the GameDesigner machine-cadence revision completed on 2026-05-13.

## Input Files
- `GDD.md`
- `Tasks/Done/10-revise-gdd-machine-each-room.md`
- `STATUS.md`

## Acceptance Criteria
- Confirm the active MVP run contains exactly 5 combat rooms, 5 automatic post-combat machine stops, and 1 boss.
- Confirm the Sacred Demon Machine appears automatically after every cleared combat room: rooms 1, 2, 3, 4, and 5.
- Confirm the player does not walk to the machine, does not press a manual spin button, and receives a short auto-roll animation before card selection.
- Confirm each machine stop shows 3 readable standard buff cards and the player chooses exactly 1 standard buff.
- Confirm standard room-clear buffs are guaranteed and free; tokens do not block normal buffs in MVP.
- Confirm the player starts with 3 total reroll charges per run, reroll replaces all 3 visible standard cards with 3 different visible cards, reroll spends 1 charge, and charges do not refresh during the run.
- Confirm selected standard cards never appear again in the same run and duplicate standard cards never appear inside one 3-card offer.
- Confirm the optional cursed deal appears only on machine stop 2 and rerolling normal cards does not reroll or change it.
- Confirm the player can receive up to 5 standard buffs per run, one after each combat room.
- Confirm the active MVP reward pool has exactly 12 standard cards and contains no pet/helper reward category.
- Confirm active MVP sections contain no Писарь, pet/helper companion, helper command, helper pickup, helper attack, helper reward card, or helper SFX requirement.
- Confirm movement-only portrait combat remains intact: one floating joystick, no dash button, no possession button, no helper command button, auto-attack always on, and automatic/contextual marked-vessel possession.

## Deadline
Next BA session.

## BA Result - 2026-05-13
Validation remains blocked.

Pass:
- Machine cadence is now implementation-ready: 5 combat rooms, 5 automatic post-combat machine stops, free guaranteed standard buffs, 3 total reroll charges, no manual spin/walk-up requirement, and stop-2-only cursed deal.
- No active MVP pet/helper scope or helper reward category remains.
- Movement-only portrait combat remains intact.

Blocker:
- Marked-vessel possession explosion behavior is not owner-clear. As written, basic possession does **not** automatically explode; only **P03 Последний вздох** causes an exit explosion. If the owner expects automatic explosion after possessing a marked enemy, the active GDD must be revised before [[Architect]] routing.

Next:
- [[GameDesigner]] clarifies possession explosion using `Tasks/Open/12-clarify-possession-explosion.md`.
