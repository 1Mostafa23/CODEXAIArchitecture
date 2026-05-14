---
type: InstanceFrame
owner: "[[GameDesigner]]"
---
# GameDesigner-Memory

> Write rule: append to **Recent**. Move oldest to **Archive** when Recent exceeds 3 entries.

## Recent
- Session 4 - revised [[GDD]] after human control feedback; MVP now uses movement-only portrait input, no dash, no manual possession button, nearest-target auto-attack against enemies/bosses, and automatic possession of marked weak cultist/fast fanatic vessels.
- Session 5 - revised [[GDD]] after owner machine-cadence direction; MVP now has 5 automatic post-combat machine stops, free guaranteed standard buffs, 3 total reroll charges, stop-2-only cursed deal, 12-card no-pet reward pool, and no active helper/Pisary scope.
- Session 6 - clarified possession-explosion behavior as buff-only: default marked-vessel possession destroys the vessel without explosion, extra token, or pickup; only **P03 Последний вздох** creates a 2-damage, 2-meter enemy-only exit explosion with VFX-cap behavior.

## Archive
- Session 1 - wrote the initial [[GDD]] from `Tasks/Open/01-create-gdd.md`; key decisions were portrait arena roguelite, auto-attack with manual dodge, possession as active tactical button, helper as Guardian shard puppet, and demonic slot machine as fair in-run upgrade system.
- Session 2 - revised [[GDD]] after BA block; locked MVP to two-thumb portrait controls, deterministic nearest-target auto-attack, 5 combat rooms, 3 post-combat machine stops, one MVP currency, 40% HP possession trigger, automatic helper, one boss reward, and QA-observable acceptance criteria.
- Session 3 - completed BA cleanup pass; defined exact 15-card MVP reward pool, exact `Fanatichny kredit` cursed deal, MVP/Post-MVP scope labels for tables, and portrait caps for projectiles, pickups, and VFX.

## Rejected Ideas
- Manual dash is removed from MVP because the human owner preferred fewer portrait controls.
- Manual possession button is removed from MVP; possession is contextual/automatic through marked enemies.
- Manual machine spin and paid standard room-clear buffs are removed from MVP; the owner wants automatic post-combat machine rolls with free guaranteed buff selection.
- Pet/helper companion scope is removed from MVP, including Писарь, helper commands, helper pickups, helper attacks, helper reward cards, and helper SFX.

## Lessons
- Session 4 - For this project, comfortable portrait play means movement-only combat input first; additional combat buttons should be treated as scope risk unless the human owner re-approves them.
- Session 5 - For MVP, the Sacred Demon Machine is a post-combat reward presentation, not a shop: standard buffs are free, automatic, and guaranteed after every cleared combat room.
