---
task: "Create MVP UX/UI Specs"
target: [[UXDesigner]]
input: [[GDD]]
---

# Handoff to UXDesigner
Create separated UX/UI specs for the approved active MVP before [[Architect]] creates Unity task cards.

## Input Files
- `Agents/UXDesigner.md`
- `GDD.md`
- `Tasks/Done/13-revalidate-possession-explosion.md`
- `STATUS.md`
- `Core/Conventions.md`

## Context
[[BA]] approved the active MVP GDD for implementation, but the pipeline now requires [[UXDesigner]] to produce mobile portrait UX/UI specs before [[Architect]] creates Unity task cards.

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
Create UX-first, UI-second specs in `Tasks/Open/` for at least these MVP flows/screens:
- Combat HUD and touch controls
- Possession marker and possession state feedback
- Post-combat machine reward flow
- Cursed deal popup on machine stop 2
- Game Over / Victory / Defeat result flow
- First meta unlock presentation

Use the output formats from `Agents/UXDesigner.md`.

## Acceptance Criteria
- UX sections come before UI sections in every spec.
- Specs define screen purpose, player goal, journey, navigation, interaction logic, UX states, and UX rules.
- Specs define layout, component hierarchy, HUD/card/button structure, labels, visual hierarchy, component states, wireframes, and feedback direction.
- Specs cover safe-area and thumb-zone behavior for portrait mobile.
- Specs include handoff notes for [[Architect]], [[Coder]], [[ArtDirector]], and [[QA]].
- Specs do not rewrite gameplay mechanics, create final art assets, or propose code.
- Any unclear requirement is routed back to [[BA]], and any core-design conflict is routed back to [[GameDesigner]].

## Deadline
Next UXDesigner session.
