---
type: InstanceFrame
owner: "[[BA]]"
---
# BA-Memory

> Write rule: append to **Recent**. Move oldest to **Archive** when Recent exceeds 3 entries.

## Recent
- Session 7 - re-validated machine cadence and no-pet cleanup as pass, but blocked [[GDD]] on marked-vessel explosion clarity: current active GDD says default possession does not explode and only `P03 Последний вздох` adds exit explosion.
- Session 8 - tightened `Tasks/Open/12-clarify-possession-explosion.md` into an explicit GameDesigner checklist covering the required decision, affected GDD sections, P03 behavior, VFX caps, token rule, and already approved MVP constraints.
- Session 9 - approved the possession-explosion clarification: default marked-vessel possession does not explode, **P03 Последний вздох** is the only exit-explosion source, and the active MVP GDD is validated for [[UXDesigner]] routing.

## Archive
- Session 1 - reviewed [[GDD]]; validation blocked due to unresolved MVP implementation decisions around controls, auto-targeting, run pacing, slot-machine flow, possession boundaries, helper behavior, currencies, meta progression, and measurable QA criteria.
- Session 2 - re-validated revised [[GDD]]; portrait two-thumb direction was feasible, but approval remained blocked by reward pool mismatch, undefined exact cursed deal, mixed MVP/Post-MVP implementation tables, and missing projectile/pickup/VFX caps.
- Session 3 - approved cleaned [[GDD]] for [[Architect]] routing; exact reward pool, cursed deal, MVP/Post-MVP separation, and portrait caps were implementation-ready.
- Session 4 - reopened [[GDD]] after human owner preferred fewer portrait controls: movement-only input, no dash, full auto-attack against nearest enemies/bosses, and automatic possession of marked valid enemies. GameDesigner must define exact trigger range and boundaries.
- Session 5 - validated revised control model as comfortable for portrait MVP, but blocked [[GDD]] because machine cadence still says 3 stops after rooms 2, 4, and 5 instead of appearing in each room and giving buffs.
- Session 6 - applied human request to remove the pet/helper from active MVP; `Pisary`, helper system, helper SFX, helper category, and helper reward cards are out. Active reward pool is now 12 cards unless GameDesigner adds non-pet replacements.

## Recurring Ambiguity Patterns
- Mobile control comfort can override technically valid requirements; validate input model with the human owner before implementation routing.
- Casino-machine cadence is core loop, not economy detail. It must be stated consistently in core loop, run structure, MVP scope, and acceptance criteria.
- If a system is removed from MVP, its reward cards, UI references, audio hooks, progression text, and acceptance criteria must be removed in the same pass.
- Possession exit behavior must distinguish "destroy vessel", "controlled enemy dies", and "explosion damage"; these are different implementation events.

## Lessons
*(project-validated knowledge - overrides the professional KB in `Agents/X.md` when there is a conflict. Never archive. Append with session number.)*
