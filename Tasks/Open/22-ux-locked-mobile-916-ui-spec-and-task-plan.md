---
task: "Locked Mobile 9:16 UX/UI Specification and First UI Task Plan"
target: [[Architect]]
source_agent: [[UXDesigner]]
status: ready_for_architect
input:
  - Agents/UXDesigner.md
  - STATUS.md
  - GDD.md
  - Tasks/Open/16-mvp-mobile-portrait-ux-ui-specs.md
  - ux/README.md
  - ux/menu/main-menu.md
  - ux/gameplay/in-game-buttons-and-elements.md
  - ux/components/button-rules.md
  - Core/Conventions.md
inspection:
  unity_mcp_instance: "GAMECODEX@b926ad523db73a78"
  unity_project_root: "C:/Users/mm065/GAMECODEX"
  active_platform: "Android"
  inspected_scenes:
    - "Assets/_Project/Scenes/MainMenu.unity"
    - "Assets/_Project/Scenes/Game.unity"
    - "Assets/_Project/Scenes/GameOver.unity"
  inspected_prefabs:
    - "Assets/_Project/Prefabs/Core/MobileCanvasRoot.prefab"
    - "Assets/_Project/Prefabs/UI/CombatHud.prefab"
    - "Assets/_Project/Prefabs/UI/FloatingJoystick.prefab"
    - "Assets/_Project/Prefabs/UI/PrimaryButton.prefab"
    - "Assets/_Project/Prefabs/UI/SecondaryButton.prefab"
    - "Assets/_Project/Prefabs/UI/RewardCard.prefab"
    - "Assets/_Project/Prefabs/UI/ModalPanel.prefab"
    - "Assets/_Project/Prefabs/UI/LoadingOverlay.prefab"
no_unity_object_changes: true
---

# Locked Mobile 9:16 UX/UI Specification and First UI Task Plan

This is a UX/UI documentation handoff only. It does not request code changes, prefab edits, sprite edits, or Unity object changes. The active Unity MCP session was used to inspect the current screens and prefabs. The active Unity editor project is `C:/Users/mm065/GAMECODEX`; the architecture workspace for this document is `M:/CODEXAIArchitecture-feature-assetsfolders`.

## 1. Current UI Analysis

### 1. Current Canvas Setup

The current Unity implementation uses one root UGUI canvas per scene:

| Scene | Canvas | Children | Notes |
|---|---|---:|---|
| MainMenu | `MainMenuCanvas` | `SafeAreaRoot` | Has `MainMenuScreen` with title, key art placeholder, Broken Seal status, Start Run. |
| Game | `GameCanvas` | `SafeAreaRoot` | Has `CombatHud`, `RewardScreen`, `CursedDealModal`, `ResultsScreen`, `LoadingOverlay`. |
| GameOver | `GameOverCanvas` | `SafeAreaRoot` | Has `ResultsScreen`. |

All inspected canvases are Screen Space Overlay canvases with `GraphicRaycaster`, `CanvasScaler`, `PortraitCanvasScaler`, and `UIScreenRouter`.

The live Game View inspected through MCP was `338 x 600`, so each canvas reported a scale factor of `0.3125` against the 1080 x 1920 reference. This is acceptable for 9:16 verification.

### 2. Canvas Scaler Settings

All inspected scene canvases use:

- UI Scale Mode: Scale With Screen Size
- Reference Resolution: `1080 x 1920`
- Screen Match Mode: Match Width Or Height
- Match: `1.0` height
- Reference Pixels Per Unit: `100`
- Custom component: `PortraitCanvasScaler`

This is acceptable and should become the locked baseline.

### 3. Safe Area Handling

Each scene has a full-stretch `SafeAreaRoot` under the canvas with `SafeAreaFitter`.

`SafeAreaFitter` reads `Screen.safeArea`, converts it to normalized anchors, and applies those anchors to the root. This is the correct project-level safe-area approach.

Current issue: dim backgrounds are currently under `SafeAreaRoot`, so they may not cover unsafe device areas on notched or rounded screens. Interactive content must stay under safe area. Dim blockers may cover the full canvas if Architect wants full-screen dimming.

### 4. Current UI Hierarchy

Current screen structure is directionally correct:

- `MainMenuScreen`
  - `Title`
  - `KeyArtPlaceholder`
  - `BrokenSealStatus`
  - `StartRunButton`
- `CombatHud`
  - `HPBar`
  - `RoomText`
  - `TokenText`
  - `PossessionBar`
  - `AutoAttackActive`
  - `AutoAttackDisabled`
  - `FloatingJoystick`
- `RewardScreen`
  - `DimBackground`
  - `Header`
  - `AutoMachineVisual`
  - `RewardCard_1`
  - `RewardCard_2`
  - `RewardCard_3`
  - `RerollButton`
- `CursedDealModal`
  - `DimBackground`
  - `CursedDealPanel`
    - `Title`
    - `Body`
    - `PrimaryAction`
- `ResultsScreen`
  - `DimBackground`
  - `VictoryState`
  - `DefeatState`
  - `Summary`
  - `RestartButton`
  - `MainMenuButton`
- `LoadingOverlay`
  - `LoadingText`

### 5. Current Button Sizes

All current real buttons include `MinimumTouchTarget` with `minimumReferencePixels = 96`, which is acceptable for mobile.

Measured current reference-space sizes:

| Button | Current anchors | Current approximate size | Assessment |
|---|---|---:|---|
| Start Run | x .12-.88, y .11-.18 | 822 x 134 | Acceptable primary CTA. |
| Restart | x .14-.86, y .20-.27 | 779 x 134 | Acceptable primary result CTA. |
| MainMenu | x .14-.86, y .11-.18 | 779 x 134 | Acceptable secondary result CTA. |
| Reroll | x .22-.78, y .08-.15 | 606 x 134 | Size acceptable, placement overlaps reward card 3. |
| Reward cards | x .10-.90, height .12 | 865 x 230 | Acceptable card target size. |
| Cursed primary action | panel-relative x .12-.88, y .14-.28 | 690 x 140 | Size acceptable, but missing Decline choice. |
| Joystick base | fixed | 260 x 260 | Acceptable movement target. |

Critical implementation issue: inspected button background `Image` components have `raycastTarget = false`, and labels also have `raycastTarget = false`. Real buttons need a raycastable hit graphic or explicit hit-area graphic. HUD-only graphics should remain non-raycastable.

### 6. Current Text Sizes

Current text hierarchy is mostly usable:

| Use | Current size | Assessment |
|---|---:|---|
| Main menu title | 76, best fit | Acceptable size, placeholder copy must change. |
| Primary button labels | 36, best fit | Acceptable. |
| Broken Seal status | 30, best fit | Acceptable. |
| Combat room text | 28, best fit | Minimum acceptable. |
| Combat token text | 32, best fit | Acceptable. |
| Reward header | 54, best fit | Acceptable. |
| Reward card title | 42 | Acceptable. |
| Reward card description | 28 | Minimum acceptable. |
| Cursed modal title | 48 | Acceptable. |
| Cursed modal body | 30 | Acceptable. |
| Victory/Defeat title | 72 | Acceptable. |
| Run summary | 34 | Acceptable. |
| Loading text | 44 | Acceptable. |

Current fonts are default `UnityEngine.UI.Text`. That is acceptable for placeholders but not locked final presentation. Architect may keep UGUI Text for MVP, but all final text must follow this size hierarchy and contrast rules.

### 7. Current Spacing

Acceptable:

- Main menu vertical structure is clear: title top, art center, status above CTA, Start Run near lower-middle.
- Result buttons have a readable vertical stack.
- HUD elements leave the center arena clear.

Must improve:

- `RewardCard_3` uses y `.12-.24`; `RerollButton` uses y `.08-.15`. Their normalized anchors overlap from `.12` to `.15`. This creates a real collision risk and must be fixed before coding reward UI.
- Cursed deal has only one action. It needs two clearly separated actions: Accept and Decline.
- Several edit-mode screens are active at once. Runtime `UIScreenRouter` hides screens on Awake, but designers need deterministic preview states for 9:16 inspection.

### 8. Current Anchors

Acceptable anchor patterns:

- Scene roots and screen roots stretch x `0..1`, y `0..1`.
- `SafeAreaRoot` stretches under the canvas and is later fitted by `SafeAreaFitter`.
- Main menu title, art, status, and Start Run use normalized portrait zones.
- HUD top band uses normalized anchors.
- Joystick is lower-left fixed size with a normalized touch zone.

Must improve:

- Do not use overlapping normalized anchor bands.
- Do not use code-side pixel placement for screen UI.
- Screen content should use named layout zones, not ad hoc anchor values per coder.

### 9. Current Panels

Current panels are visual placeholders using plain Images:

- `KeyArtPlaceholder`
- `AutoMachineVisual`
- `DimBackground`
- `CursedDealPanel`
- `ResultsScreen`
- `LoadingOverlay`

This is acceptable as a temporary layout scaffold. It is not final UI.

### 10. Current 9:16 Behavior

Current behavior is mostly acceptable for a 9:16 baseline because:

- The root canvas reference is 1080 x 1920.
- Match height is used.
- Layouts mostly use normalized anchors.
- Buttons stay above the bottom gesture area in the tested 338 x 600 view.

Current risk:

- Taller or notched Android screens need explicit safe-area verification.
- Reward card/reroll overlap will worsen on some variants if not fixed.
- Current dim backgrounds under `SafeAreaRoot` may leave unsafe areas undimmed.

### 11. Current UI Placeholders

The following are placeholders and must not be treated as final:

- `GAMECODEX` title in MainMenu. Replace with the localized project title.
- `KeyArtPlaceholder`.
- `ArenaBoundsPlaceholder`.
- `AutoMachineVisual`.
- Reward card text: `Reward Name`, placeholder description.
- `Run summary placeholder`.
- `Victory`, `Defeat`, `Room Clear`, `Loading` are acceptable placeholder labels but need localization-ready ownership.
- Cursed deal only has `PrimaryAction`; it does not yet model the approved accept/decline decision.

## 2. What Is Acceptable

- 1080 x 1920 portrait reference resolution.
- CanvasScaler match-height setup.
- `PortraitCanvasScaler` component as the single scaler authority.
- `SafeAreaFitter` concept and `SafeAreaRoot` hierarchy.
- One movement-only joystick in lower-left with `normalizedTouchZone = x 0..0.55, y 0..0.52`.
- Lower-right combat area has no fake ability buttons.
- HUD bars, text, and auto-attack indicators are non-button elements.
- Reward cards are large full-card buttons.
- `MinimumTouchTarget` with 96 reference pixels.
- Primary and secondary button prefab sizes around 760 x 112 or scene-expanded 779-822 x 134.
- Current color direction matches the GDD palette: charcoal, old gold, wax white, crimson, void violet.
- `UIScreenId` flow already names the needed screens: MainMenu, CombatHud, Reward, CursedDeal, Results, MetaUnlock, Loading.

## 3. What Must Be Improved

1. Fix real button hit testing.
   Real button hit graphics need `raycastTarget = true`, or each button needs a dedicated invisible/transparent hit graphic. Do not make HUD-only indicators raycastable.

2. Fix reward screen overlap.
   The third reward card and reroll button currently overlap. Reserve a non-overlapping lower action zone for reroll.

3. Add explicit cursed deal decisions.
   Cursed deal must have Accept and Decline. A single Continue/PrimaryAction is not acceptable for approved gameplay.

4. Replace placeholder menu copy.
   `GAMECODEX` is not final title copy. Use the localized project title from approved game identity.

5. Split placeholder visuals from final UI contract.
   Placeholder rectangles are useful for scale checks, but coders must not treat them as final art slots without ArtDirector handoff.

6. Define one canonical Results implementation path.
   Results currently exist in both Game and GameOver contexts. Architect must decide whether GameOver scene reuses the same prefab or whether the Game scene routes to GameOver.

7. Add MetaUnlock screen to current implementation plan.
   `UIScreenId.MetaUnlock` exists, but no inspected live screen was present for Broken Seal unlock.

8. Make editor preview states readable.
   Runtime router behavior can hide screens, but edit-mode hierarchy currently shows multiple active screens. Provide a preview convention so designers and QA can inspect one state at a time.

9. Localize text ownership.
   Labels can be placeholder English now, but final UI text must be data/config/localization-owned, not baked into art or hidden in gameplay scripts.

## 4. Locked UX/UI Rules

### 1. Reference Resolution

- Lock reference resolution to `1080 x 1920`.
- All UI measurements in this spec are reference pixels unless stated otherwise.
- 9:16 portrait is the primary design ratio.
- Taller screens may add vertical breathing room but must not move primary actions outside thumb reach.

### 2. Canvas Scaler Rules

- Every screen-space UI scene must use the `MobileCanvasRoot` pattern.
- CanvasScaler:
  - `Scale With Screen Size`
  - `Reference Resolution = 1080 x 1920`
  - `Screen Match Mode = Match Width Or Height`
  - `Match = 1.0`
  - `Reference Pixels Per Unit = 100`
- Do not set scaler values from gameplay scripts.
- Do not create secondary root canvases unless Architect approves a layering need.

### 3. Safe Area Rules

- All interactive controls and persistent readable text must live inside `SafeAreaRoot`.
- `SafeAreaRoot` must use `SafeAreaFitter`.
- Full-screen dim backgrounds may cover the full canvas, but modal panels and buttons must stay safe-area-bound.
- Bottom CTAs must keep at least 96 reference pixels plus device safe-area inset from the bottom edge.
- Top HUD/title elements must remain below notch/cutout safe-area limits.

### 4. Button Sizes

- Minimum touch target: `96 x 96` reference pixels.
- Primary CTA preferred size: `760-840 x 112-144`.
- Secondary CTA preferred size: `720-800 x 104-134`.
- Modal decision button preferred size:
  - Stacked: `690-760 x 112-140`.
  - Side-by-side only if each remains at least `300 x 112`.
- Reward card target: full card area, preferred `820-900 x 220-280`.
- Joystick base: `240-280`, current `260` is approved.
- Joystick knob: `96-120`, current `110` is approved.

### 5. Text Hierarchy

Use best fit only as overflow protection, not as the normal sizing strategy.

| Text role | Locked range |
|---|---:|
| Screen title / result title | 64-76 |
| Reward title / modal title | 48-56 |
| Reward card title | 38-44 |
| Button label | 34-40 |
| Summary / status | 30-36 |
| HUD values / short HUD labels | 28-34 |
| Body copy / reward descriptions | 28-32 |
| Absolute minimum after best fit | 24 for production text |

All readable text must be Unity UI text or a future approved text component. No readable text may be baked into generated sprites.

### 6. Spacing System

- Base spacing unit: `16`.
- Micro spacing: `8`.
- Small component spacing: `16`.
- Standard vertical spacing: `24`.
- Button stack spacing: `32-48`.
- Screen side margin: `64-108`.
- Modal inner padding: `72-96`.
- Reward card vertical gap: at least `48`.
- Do not overlap normalized anchor bands.

### 7. Panel Layout Rules

- Full-screen screen roots stretch to parent.
- Modal panels use x `.08-.92` max width and y `.22-.78` height as the default portrait frame.
- Do not place cards inside cards.
- Decorative panels may not own readable labels.
- Dim background alpha target: `0.64-0.72`.
- Modal panel alpha target: current `0.94` is acceptable.

### 8. HUD Layout Rules

- Top band:
  - HP left: x `.04-.32`, y `.91-.965`.
  - Room progress center: x `.36-.64`, y `.91-.965`.
  - Token count right: x `.72-.96`, y `.91-.965`.
- Possession charge:
  - x `.18-.82`, y `.85-.895`.
- Auto-attack indicator:
  - x `.84-.94`, y `.74-.80`.
  - Non-interactive.
- Joystick:
  - Lower-left only.
  - Allowed touch zone remains lower-left/lower-half.
- Lower-right:
  - Must stay empty during combat.
  - No attack, dash, possession, spin, pet, ultimate, or ability buttons.

### 9. Main Menu Layout Rules

- Title belongs in top safe area: current y `.82-.94` is acceptable.
- Key art belongs center/upper-mid: current y `.34-.76` is acceptable as a placeholder zone.
- Broken Seal status belongs above the CTA: current y `.25-.31` is acceptable.
- Start Run is the only primary CTA: current x `.12-.88`, y `.11-.18` is approved.
- Broken Seal status must not look purchasable.
- Do not add shop, hero select, upgrade tree, IAP, ads, or multiplayer UI.

### 10. Game Over / Victory Screen Rules

- Victory and Defeat share one results layout with different state visuals.
- Result title/emblem zone: x `.10-.90`, y `.63-.78`.
- Summary zone: x `.12-.88`, y `.42-.58`.
- Restart primary: x `.14-.86`, y `.20-.27`.
- MainMenu secondary: x `.14-.86`, y `.11-.18`.
- Combat input must be disabled before result buttons accept taps.
- Broken Seal unlock appears only after first victory and only once.

### 11. Popup / Modal Rules

- Modal background blocks underlying interactions.
- Modal panel sits centered inside safe area.
- Modal title: top 20-30 percent of panel.
- Modal body: middle 30-40 percent of panel.
- Modal actions: bottom 15-25 percent of panel.
- Binary decisions require two buttons. Cursed deal requires Accept and Decline.
- Decline must be as reachable as Accept and must not be hidden or minimized.

### 12. Navigation Flow

```text
Bootstrap
  -> MainMenu
      -> Start Run
          -> Game / CombatHud
              -> room clear
                  -> RewardScreen
                      -> optional CursedDealModal on stop 2 only
                      -> next room or boss route
              -> HP zero
                  -> Results Defeat
              -> boss defeated
                  -> Results Victory
                      -> MetaUnlock if first victory and Broken Seal not owned
      -> Results actions
          -> Restart goes to Game
          -> MainMenu goes to MainMenu
```

### 13. Prefab Requirements

Required reusable prefabs:

- `MobileCanvasRoot`
- `SafeAreaRoot` child pattern
- `PrimaryButton`
- `SecondaryButton`
- `FloatingJoystick`
- `CombatHud`
- `RewardScreen`
- `RewardCard`
- `RerollButton` or approved secondary-button variant
- `CursedDealModal`
- `ModalPanel`
- `ResultsScreen`
- `MetaUnlockScreen`
- `LoadingOverlay`

Each real button prefab must include:

- `RectTransform`
- raycastable hit graphic
- `Button`
- `MinimumTouchTarget`
- label text child
- disabled/pressed visual state

Each non-interactive HUD/panel graphic must not be raycastable unless it intentionally blocks a modal background.

### 14. Accessibility / Readability Rules

- Text contrast must remain readable on charcoal panels.
- Do not use crimson for normal primary actions.
- Minimum production text size is 24 reference pixels after best fit.
- Button labels should be short verbs or nouns.
- Long explanations go in body text, not buttons.
- Avoid relying on color alone for selected/disabled states.
- Reward cards need title, description, icon, selected state, and disabled state.
- The player must be able to understand combat without reading paragraphs during motion.

### 15. What Coders Are Not Allowed To Hardcode

Coders must not hardcode:

- Screen pixel positions.
- Device-specific notch, cutout, or gesture-bar padding.
- CanvasScaler values in gameplay scripts.
- Button sizes as scattered magic numbers.
- Scene names or build indices in UI click handlers.
- Reward card count assumptions outside reward UI config.
- English UI strings inside gameplay logic.
- Text baked into generated art.
- Attack, dash, possession, spin, pet, or ability inputs on combat UI.
- Manual slot spin behavior.
- Cursed deal availability outside stop 2.
- Broken Seal unlock repeat behavior.

## 5. Required UI Prefabs

| Prefab | Current status | Required next state |
|---|---|---|
| `MobileCanvasRoot` | Exists and acceptable. | Use in every screen-space UI scene. |
| `PrimaryButton` | Exists. | Fix hit testing and final pressed/disabled visuals. |
| `SecondaryButton` | Exists. | Fix hit testing and final pressed/disabled visuals. |
| `FloatingJoystick` | Exists and acceptable. | Keep movement-only and lower-left. |
| `CombatHud` | Exists. | Add final icons/art, preserve non-interactive HUD. |
| `RewardCard` | Exists. | Add final selected/disabled visuals and verified text bounds. |
| `RewardScreen` | Scene object, not confirmed reusable prefab. | Create or formalize reusable screen prefab. |
| `CursedDealModal` | Scene object using one action. | Convert to explicit Accept/Decline modal. |
| `ResultsScreen` | Exists in Game and GameOver contexts. | Make one canonical reusable result screen. |
| `MetaUnlockScreen` | Enum exists, inspected active scene lacks screen. | Create Broken Seal unlock screen/prefab. |
| `LoadingOverlay` | Exists. | Keep simple, safe-area readable, non-blocking when hidden. |

## 6. Required UI Documentation

Before Coder begins final UI implementation, Architect should create or update:

- `ux/implementation/ui-metrics.md`
  - Reference resolution, scaler, spacing, text hierarchy, touch targets.
- `ux/implementation/screen-flow.md`
  - Exact UI navigation flow and `UIScreenId` ownership.
- `ux/implementation/prefab-registry.md`
  - Canonical prefab list, owners, and allowed usage.
- `ux/implementation/current-ui-audit.md`
  - Current accepted parts and required fixes from this document.
- Existing docs to keep linked:
  - `ux/README.md`
  - `ux/menu/main-menu.md`
  - `ux/gameplay/in-game-buttons-and-elements.md`
  - `ux/components/button-rules.md`

## 7. First UI Implementation Tasks

These are the first tasks Architect should break into Coder/ArtDirector/QA handoffs.

1. Formalize UI root and scene screen ownership.
   - Use `MobileCanvasRoot` and `SafeAreaRoot` consistently.
   - Decide whether Results lives in Game, GameOver, or one reusable prefab used by both.
   - Define preview-state rules for edit mode.

2. Fix button hit testing and shared button states.
   - Real buttons need raycastable hit graphics.
   - HUD indicators must remain non-raycastable.
   - Add pressed, disabled, loading, and selected state rules to prefabs.

3. Lock MainMenu implementation.
   - Replace placeholder title.
   - Keep Start Run as only primary CTA.
   - Keep Broken Seal informational and non-purchasable.
   - Do not add out-of-scope systems.

4. Lock Combat HUD implementation.
   - Preserve current HUD zones.
   - Keep lower-right empty.
   - Bind joystick only to movement.
   - Verify HP, possession, room, token, and auto-attack presenters.

5. Fix RewardScreen layout.
   - Remove RewardCard_3/Reroll overlap.
   - Keep exactly three selectable cards.
   - Keep reroll as reward-screen-only secondary action.
   - Keep slot machine visual non-interactive.

6. Rebuild CursedDealModal.
   - Add Accept and Decline.
   - Gate to stop 2 only.
   - Block reward/background taps while modal is open.
   - Ensure Decline is visible and reachable.

7. Build MetaUnlockScreen.
   - Broken Seal icon/title/effect/Continue only.
   - Trigger once after first boss victory.
   - No shop, upgrade tree, or broader meta UI.

8. Finalize ResultsScreen.
   - Support Victory and Defeat states.
   - Summary text must be data-driven.
   - Restart and MainMenu buttons use shared button rules.

9. Create QA portrait layout test card.
   - Test 9:16, tall portrait, narrow portrait, and safe-area/notch cases.
   - Verify all real buttons meet 96 reference-pixel minimum.
   - Verify forbidden combat controls do not exist.
   - Verify reward/card/modal/result flows.

## 8. Handoff

### Handoff To [[Architect]]

Create implementation task cards from the locked rules above. Start with root/prefab ownership, button hit testing, reward overlap, cursed modal decision structure, and canonical Results/MetaUnlock screens.

### Handoff To [[Coder]]

Do not implement additional gameplay buttons. Keep joystick movement-only. Do not hardcode screen positions, safe-area values, or UI strings in gameplay scripts. Fix button hit areas before relying on click tests.

### Handoff To [[ArtDirector]]

Generate final art only after prefab slots are confirmed. Sprites must not contain readable text. Provide distinct visual states for primary/secondary buttons, reward cards, selected reward, disabled controls, cursed modal, result states, and Broken Seal unlock.

### Handoff To [[QA]]

Prioritize mobile portrait layout verification and false-control checks. Validate safe area, touch target size, reward overlap removal, cursed accept/decline, result navigation, and Broken Seal one-time presentation.
