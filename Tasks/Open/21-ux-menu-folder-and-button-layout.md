---
task: "Create ux Folder and Menu/Button Layout Specs"
target: [[UXDesigner]]
source_agent: [[PM]]
input:
  - Agents/UXDesigner.md
  - STATUS.md
  - GDD.md
  - Tasks/Open/16-mvp-mobile-portrait-ux-ui-specs.md
  - Core/Conventions.md
status: completed
---

# Handoff to UXDesigner

Create a repo-root `ux/` documentation folder that explains how the game menu, buttons, and in-game UI elements should be arranged for the Android portrait MVP.

This is a UX/UI documentation task only. Do not write Unity code, create prefabs, generate art assets, or change gameplay mechanics.

## Context

The project already has a validated portrait MVP and a broad mobile UX/UI spec in `Tasks/Open/16-mvp-mobile-portrait-ux-ui-specs.md`. The owner now wants a dedicated `ux/` folder for practical layout guidance, especially:

- the main menu structure
- how buttons should be positioned
- how HUD and interaction elements should be arranged in-game
- how to avoid confusing the player with controls that do not exist in the MVP

## Scope Lock

Use only validated MVP behavior:

- Android portrait layout first.
- One movement-only floating joystick in combat.
- No dash button.
- No manual attack button.
- No manual possession button.
- No manual slot spin button.
- Auto-attack and automatic possession remain non-button systems.
- Reroll is a real button only inside the reward card screen.
- Result screens may include restart and menu buttons.
- All readable labels must be Unity UI text, not baked into generated art.

If the menu requires a gameplay feature not present in `GDD.md`, route the ambiguity to [[BA]] or [[GameDesigner]] instead of inventing it.

## Required Output

Create the folder and docs below:

- `ux/README.md`
  - UX folder index.
  - Supported orientation and baseline screen assumptions.
  - Shared safe-area and thumb-zone rules.
  - Links to each UX layout document.
- `ux/menu/main-menu.md`
  - UX/UI spec for the MainMenu scene.
  - Start/run entry CTA hierarchy.
  - Secondary actions allowed by the GDD, such as meta-unlock status if needed.
  - Button placement rules for portrait one-handed use.
  - Safe-area, locked/unavailable, and return-from-result behavior.
- `ux/gameplay/in-game-buttons-and-elements.md`
  - Practical placement rules for combat HUD, joystick, auto-attack indicator, possession charge, token count, room progress, reward reroll, reward cards, cursed deal popup, and result buttons.
  - Explicit "do not add" control zones for forbidden combat buttons.
  - Wireframes for the main gameplay states where buttons/elements appear.

Optional if useful:

- `ux/components/button-rules.md`
  - Shared button hierarchy, sizes, spacing, states, labels, and disabled-state rules.

## Required Format

Use `Agents/UXDesigner.md` output structure:

- UX first, UI second.
- Screen specs use `UX/UI Spec - [Screen Name]`.
- Flows use `UX/UI Flow - [Flow Name]`.
- Include handoff notes for [[Architect]], [[Coder]], [[ArtDirector]], and [[QA]] where implementation or testing is affected.

## Acceptance Criteria

- `ux/` exists at the repository root.
- The required files above exist and are internally linked from `ux/README.md`.
- MainMenu layout defines primary and secondary button hierarchy without adding out-of-scope systems.
- In-game layout clearly separates non-interactive HUD elements from real buttons.
- Combat layout keeps the lower-right area free of fake ability/combat controls.
- Reward layout identifies reroll as a reward-screen-only button, not a slot spin button.
- Result layout covers restart and return-to-menu buttons.
- Specs define safe-area behavior, thumb-zone behavior, minimum touch target guidance, visual hierarchy, component states, and wireframes.
- Specs do not contradict `GDD.md` or `Tasks/Open/16-mvp-mobile-portrait-ux-ui-specs.md`.
- Any unresolved requirement question is routed back to [[BA]], and any design conflict is routed back to [[GameDesigner]].

## Deadline

Next UXDesigner session.

## Output

Completed by [[UXDesigner]] on 2026-05-18:

- `ux/README.md`
- `ux/menu/main-menu.md`
- `ux/gameplay/in-game-buttons-and-elements.md`
- `ux/components/button-rules.md`

Architect handoff `Tasks/Open/17-architect-create-mvp-task-cards-from-ux-ui-specs.md` was updated to include these UX layout docs as implementation inputs.
