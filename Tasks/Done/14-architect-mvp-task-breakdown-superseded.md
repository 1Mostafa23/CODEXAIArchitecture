---
task: "Create MVP Implementation Task Cards"
target: [[Architect]]
input: [[GDD]]
---

# Handoff to Architect
Create implementation task cards for the approved active MVP GDD.

## Input Files
- `GDD.md`
- `Tasks/Done/13-revalidate-possession-explosion.md`
- `Core/Conventions.md`
- `Knowledge/decisions.md`

## Context
BA approved the active MVP GDD after the possession-explosion clarification on 2026-05-14. No design blockers remain for MVP architecture.

## Scope Lock
Use only active MVP requirements, not superseded historical BA notes.

The MVP includes:
- portrait Android play
- movement-only combat input with one floating joystick
- deterministic nearest-target auto-attack
- automatic marked-vessel possession
- default possession exit with no explosion
- **P03 Последний вздох** as the only possession-exit explosion source
- 5 combat rooms, 5 automatic post-combat machine stops, and 1 boss
- 12 standard reward cards
- 3 total reroll charges per run
- stop-2-only optional cursed deal
- one fixed meta unlock after first boss victory

The MVP excludes:
- pet/helper systems
- dash button
- manual possession button
- manual machine spin or walk-up machine interaction
- paid standard machine buffs
- Post-MVP enemies, biomes, bosses, reward cards, and currencies

## Required Output
- Create one-session implementation task cards in `Tasks/Open/` for the next relevant agents.
- Split cards by implementation ownership so each can be completed in one focused session.
- Include input files, required behavior, acceptance criteria, and explicit out-of-scope lines in each card.
- Preserve `Core/Conventions.md` requirements.

## Acceptance Criteria
- Each generated card is small enough for one implementation session.
- Cards cover the playable MVP path from run start through boss result.
- Cards include device-observable acceptance criteria suitable for QA.
- Cards do not reintroduce superseded scope.
- Cards identify dependencies between systems where needed.

## Deadline
Next Architect session.

## PM Supersession - 2026-05-14
This card is superseded by the new 8-agent pipeline that routes validated requirements to [[UXDesigner]] before [[Architect]].

Do not execute this Architect breakdown until UX/UI specs exist. New active handoff: `Tasks/Open/15-create-mvp-ux-ui-specs.md`.
