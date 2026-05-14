---
task: "Clarify Marked-Vessel Possession Explosion"
target: [[GameDesigner]]
input: [[GDD]]
---

# Handoff to GameDesigner
Clarify whether marked-vessel possession automatically explodes after possession in the MVP.

## Input Files
- `GDD.md`
- `Tasks/Done/11-revalidate-machine-cadence.md`
- `STATUS.md`

## Context
BA re-validated the machine cadence and no-pet cleanup. Those parts pass. The remaining blocker is the possession-explosion rule.

Current active GDD behavior:
- Basic possession destroys the vessel on exit and does not grant an extra token.
- Explosion is available only through the standard buff **P03 Последний вздох**.

Human owner check:
- Confirm whether "after possessing a marked enemy it automatically explodes" is intended as default MVP behavior.

## Required Decision
Choose exactly one:
- **Default explosion**: every marked-vessel possession explodes on exit.
- **Buff-only explosion**: default marked-vessel possession does not explode; only **P03 Последний вздох** causes an exit explosion.

## GameDesigner Task Checklist
1. Add one active MVP rule in `GDD.md` named or phrased as the marked-vessel possession explosion rule.
2. Make the rule answer this question directly: "Does a marked possessed enemy automatically explode after possession?"
3. Update all affected active MVP sections, not only BA notes:
   - possession rules
   - MVP scope
   - MVP acceptance criteria
   - MVP reward pool entry for **P03**
   - VFX/performance caps if explosion behavior changes
4. Keep the decision consistent with the already approved MVP constraints:
   - movement-only portrait combat
   - no dash button
   - no manual possession button
   - automatic marked-vessel possession
   - 5 combat rooms, 5 automatic post-combat machine stops, 1 boss
   - 12 standard buff cards
   - no pet/helper system

## Required Changes If Default Explosion
- Update the possession section with exact trigger timing: timer end, room clear, controlled enemy death, and any other exit.
- Define exact damage and radius.
- State whether the explosion can damage the hero body.
- Update MVP scope and acceptance criteria with observable explosion behavior.
- Remove or redesign **P03 Последний вздох** so the reward pool does not duplicate default behavior.
- Check VFX cap implications.
- State whether default explosion grants any extra token or pickup. If not, explicitly keep the current no-extra-token rule.

## Required Changes If Buff-Only Explosion
- Add one explicit sentence to the possession section: default marked-vessel possession does not explode.
- Keep **P03 Последний вздох** as the only MVP source of possession-exit explosion.
- Add one observable MVP acceptance criterion confirming default possession exit has no explosion unless **P03** is selected.
- Confirm **P03** has implementation-ready explosion rules: trigger timing, damage, radius, target filters, hero-body damage rule, and VFX behavior.

## Acceptance Criteria
- BA can answer yes/no to: "Does a marked possessed enemy automatically explode after possession?"
- The answer is stated in the active possession rules, not only in BA notes.
- MVP scope and acceptance criteria match the chosen behavior.
- The **P03 Последний вздох** card either remains uniquely useful or is redesigned.
- No pet/helper system is reintroduced.

## Deadline
Next GameDesigner session.

## GameDesigner Result - 2026-05-14
Revision completed in `GDD.md`.

Resolved:
- Chose **Buff-only explosion** for MVP.
- Added an explicit active possession rule: default marked-vessel possession does not explode after possession.
- Confirmed basic possession exit destroys the vessel without extra token, pickup, explosion VFX, or area damage.
- Kept **P03 Последний вздох** as the only MVP source of possession-exit explosion.
- Defined **P03 Последний вздох** trigger timing: timer end, room clear, or controlled-enemy death.
- Defined **P03 Последний вздох** effect details: 2 damage, 2 gameplay meter radius, living enemy units only, no hero-body damage, no extra token or pickup, 1 VFX object, and damage still applies if the VFX cap blocks the visual.
- Updated MVP scope, acceptance criteria, reward row, and 10 MVP decisions to match the buff-only decision.
- Preserved movement-only portrait controls, no dash, no manual possession, 5 rooms, 5 machine stops, 12-card reward pool, and no pet/helper scope.

Next:
- [[BA]] re-validates using `Tasks/Open/13-revalidate-possession-explosion.md`.
