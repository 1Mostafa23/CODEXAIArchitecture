---
type: InstanceFrame
owner: "[[UXDesigner]]"
---
# UXDesigner-Memory

> Write rule: append to **Recent**. Move oldest entries to **Archive** when Recent exceeds 3 entries.

## Recent

- 2026-05-18 - Created repo-root `ux/` layout docs: `ux/README.md`, `ux/menu/main-menu.md`, `ux/gameplay/in-game-buttons-and-elements.md`, and `ux/components/button-rules.md`. Updated the Architect handoff so implementation breakdown includes these practical placement specs.
- 2026-05-21 - Used active Unity MCP session `GAMECODEX@b926ad523db73a78` to inspect MainMenu, Game, GameOver, and current UI prefabs. Created `Tasks/Open/22-ux-locked-mobile-916-ui-spec-and-task-plan.md` locking the mobile 9:16 UI rules and first implementation tasks; no Unity objects, code, or assets were modified.
- 2026-05-21 - Implemented the approved UI framework foundation in the active Unity project. Created `Runtime/UI` category folders, `Prefabs/UI` category folders, and `Assets/_Project/Documentation/UI_GUIDELINES.md`. Verified MainMenu, Game, and GameOver still have one Canvas, one CanvasScaler, one EventSystem, one SafeAreaFitter, and 1080x1920 match-height scaling.

## Archive

- 2026-05-17 - Created `Tasks/Open/16-mvp-mobile-portrait-ux-ui-specs.md` covering combat HUD/touch controls, possession feedback, reward machine flow, cursed deal popup, result flow, and Broken Seal unlock. Created `Tasks/Open/17-architect-create-mvp-task-cards-from-ux-ui-specs.md` to route implementation breakdown to [[Architect]].

## Screen Patterns

| Screen | Pattern | Notes |
|--------|---------|-------|
| Combat HUD | Top safe-area status band plus lower-left floating joystick | No combat buttons; arena center stays clear. |
| Possession Feedback | World-space marker/overlay system | Default exit is quiet/non-damaging; P03 is the only explosion. |
| Reward Flow | Automatic machine roll into 3-card choice | Reroll is allowed only in reward screen; no manual spin. |
| Results | Victory/defeat emblem plus summary panel | Restart/menu actions after combat input is disabled. |
| Meta Unlock | Single centered modal | Broken Seal only; no full meta system in MVP. |
| MainMenu | Title/art with lower-middle primary CTA stack | Start Run is primary; Broken Seal and lore/status are secondary only. |

## UI Components Registry

| Component | Used In | Behavior |
|-----------|---------|----------|
| Floating joystick | Combat HUD | Lower-left movement-only control; first touch sets center. |
| HP/possession HUD bars | Combat HUD | Informational state displays inside safe area. |
| Marked vessel ring | Possession feedback | Identifies the one eligible vessel without creating a tap target. |
| Reward cards | Reward flow | Three selectable cards; selected/disabled states required. |
| Reroll control | Reward flow | Replaces all three cards; disabled when charges are gone. |
| Cursed deal modal | Stop 2 reward flow | Accept/decline one-shot choice; optional and stop-2-only. |
| Result panel | GameOver/Victory/Defeat | Shows run end state and summary with Unity UI text. |
| Broken Seal modal | First victory unlock | One-time unlock presentation and continue action. |
| Start Run button | MainMenu | Primary lower-middle CTA; disabled during scene load. |
| Result buttons | Results | Restart primary and MainMenu secondary after combat input is disabled. |

## UX Decisions

*(permanent project UX decisions - never archive)*

- Combat UI keeps the bottom-right area free of ability buttons so the MVP does not imply dash, attack, possession, or slot spin inputs.
- Default possession exit feedback must be visually quiet and non-explosive; P03 Last Breath owns all possession-exit explosion language.
- Reward machine presentation auto-rolls; the only player choice in the reward flow is card selection, optional reroll, and the stop-2 cursed deal accept/decline.
- MainMenu uses Start Run as the only primary CTA; Broken Seal is status/meta information and must not look purchasable.

## Lessons

*(project-validated knowledge - overrides the professional KB in `Agents/UXDesigner.md` when there is a conflict. Never archive. Append with session number.)*
