---
type: InstanceFrame
owner: "[[Coder]]"
---
# Coder-Memory

> Write rule: append to **Recent**. Move oldest to **Archive** when Recent exceeds 3 entries.

## Recent
- 2026-05-22 - Implemented playable MVP vertical slice in active Unity project `C:\Users\mm065\GAMECODEX`: MainMenu Start routing, Game scene player controller, simple enemy chase/combat loop, HUD binding, reward-card buff flow, result navigation button hit fixes, and scene wiring through Unity MCP.
- 2026-05-19 - Added Unity runtime foundation in active project `C:\Users\mm065\GAMECODEX`: service registry, app bootstrap, scene loader, mobile performance manager, portrait UGUI helpers, reusable UI controls/screens, generated scenes/prefabs, Android portrait settings, and URP mobile baseline. Fixed installer retry ordering and `MinimumTouchTarget.OnValidate` so generation does not add components during validation.
- 2026-05-18 - Created visual-only Unity UI prefab asset files under `Assets/Prefabs/UI/` for GameplayHUD, RewardScreen, SlotMachineResultScreen, GameOverRunSummaryScreen, and MetaUnlockScreen. Added PNG `.meta` files for referenced generated sprites only. No gameplay scripts were written.

## Archive
*(none)*

## Scripts Registry
| Script | Path | Task | Status |
|--------|------|------|--------|
| MvpPlayerController | `Assets/_Project/Scripts/Gameplay/Mvp/MvpPlayerController.cs` | MVP joystick movement, HP, auto-attack, run buffs | Implemented |
| MvpEnemy | `Assets/_Project/Scripts/Gameplay/Mvp/MvpEnemy.cs` | MVP enemy chase, contact damage, death | Implemented |
| MvpGameLoop | `Assets/_Project/Scripts/Gameplay/Mvp/MvpGameLoop.cs` | MVP waves, HUD, rewards, defeat result flow | Implemented |
| MvpSceneSetupUtility | `Assets/_Project/Scripts/Editor/MvpSceneSetupUtility.cs` | Editor-only scene wiring utility for MVP vertical slice | Implemented |

## Bugs Fixed
*(accumulate here — never archive, prevents repeating mistakes)*

## Lessons
*(project-validated knowledge — overrides the professional KB in `Agents/X.md` when there is a conflict. Never archive. Append with session number.)*
