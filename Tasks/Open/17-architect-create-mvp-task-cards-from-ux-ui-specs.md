---
task: "Create MVP Unity Task Cards From UX/UI Specs"
target: [[Architect]]
source_agent: [[UXDesigner]]
status: deferred_until_user_sprite_review
input:
  - GDD.md
  - Tasks/Open/16-mvp-mobile-portrait-ux-ui-specs.md
  - ux/README.md
  - ux/menu/main-menu.md
  - ux/gameplay/in-game-buttons-and-elements.md
  - ux/components/button-rules.md
  - Assets/Generated/_MANIFESTS/mvp_sprite_asset_pack.md
  - Assets/Generated/_MANIFESTS/asset_prompts.csv
---

# Handoff to Architect

## Pipeline Note - 2026-05-17

Owner direction simplified the immediate pipeline. Unity implementation, [[Coder]] task cards, and [[QA]] task cards are deferred until after MVP PNG sprite generation and user manual review.

The immediate Architect output for sprite generation is complete:

- `Tasks/Open/20-artdirector-generate-mvp-sprite-pngs.md`

Keep this card open as the later Unity implementation handoff.

## Pipeline Note - 2026-05-18

[[UXDesigner]] added practical layout documentation under `ux/` for MainMenu, in-game buttons/elements, and shared button rules. Architect should treat these files as supplemental layout inputs alongside the MVP UX/UI specs.

Create Unity implementation task cards from the approved MVP GDD and the mobile portrait UX/UI specs.

## Input Files
- `Agents/Architect.md`
- `GDD.md`
- `Tasks/Open/16-mvp-mobile-portrait-ux-ui-specs.md`
- `ux/README.md`
- `ux/menu/main-menu.md`
- `ux/gameplay/in-game-buttons-and-elements.md`
- `ux/components/button-rules.md`
- `Assets/Generated/_MANIFESTS/mvp_sprite_asset_pack.md`
- `Assets/Generated/_MANIFESTS/asset_prompts.csv`
- `Core/Conventions.md`
- `Knowledge/decisions.md` if relevant

## Context
[[UXDesigner]] completed the required mobile portrait UX/UI specs between BA validation and Architect implementation breakdown.

The specs preserve the active MVP scope:
- Android portrait play.
- Movement-only floating joystick.
- Nearest-target auto-attack with no manual attack button.
- Automatic marked-vessel possession with no manual possession button.
- Default possession exit is non-damaging and not an explosion.
- P03 Last Breath is the only possession-exit explosion source.
- Automatic post-combat machine stops after rooms 1-5.
- Three reward cards, one choice, three total rerolls per run.
- Stop-2-only optional cursed deal.
- Victory/defeat result flow.
- First Broken Seal meta unlock only.
- Dedicated `ux/` layout docs now define MainMenu hierarchy, real button rules, combat no-button zones, reward reroll placement, modal decision layout, and result button placement.

## Required Architect Output
Create implementation task cards in `Tasks/Open/` for [[Coder]], [[ArtDirector]], and [[QA]].

At minimum, break down:
- Combat HUD safe-area Canvas and UI presenters.
- Floating joystick movement-only control.
- Possession marker, ready marker, active overlay, empty shell, default exit marker, and P03-only explosion separation.
- Post-combat automatic slot machine reward flow.
- Reward card selection and reroll states.
- Stop-2-only cursed deal popup.
- Victory/defeat result flow and run summary.
- First Broken Seal meta unlock presentation and persistence.
- Art-generation/import tasks for referenced `Assets/Generated/` sprite paths.
- QA validation cards for portrait safe-area, no-extra-controls, possession/P03 separation, reward cadence, and unlock behavior.

## Acceptance Criteria
- Task cards do not introduce manual dash, manual attack, manual possession, manual slot spin, pet/helper systems, IAP, or post-MVP content.
- Task cards separate world SpriteRenderer assets from Unity UI Image assets where appropriate.
- Coder cards include enough acceptance criteria for QA to test behavior.
- ArtDirector cards reference existing asset paths and prompt files without renaming assets or folders.
- QA cards cover safe-area, thumb-zone, reward flow, cursed deal gating, result routing, and Broken Seal persistence.

## Deadline
Next Architect session.
