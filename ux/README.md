# UX Layout Index

Scope: Android portrait MVP layout guidance for MainMenu, in-game buttons, HUD elements, reward choices, modals, and shared button rules.

These docs are design inputs only. They do not add gameplay mechanics, Unity prefabs, code, or final art assets.

## Documents

- [MainMenu layout](menu/main-menu.md)
- [In-game buttons and elements](gameplay/in-game-buttons-and-elements.md)
- [Shared button rules](components/button-rules.md)

## Baseline Screen Assumptions

- Platform: Android portrait.
- Primary design ratio: 9:16.
- Layout must tolerate taller Android screens without stretching controls into unreachable corners.
- Minimum touch target: 48 x 48 dp equivalent.
- All readable labels, numbers, and descriptions are Unity UI text.
- Generated art must stay free of readable text.

## Shared Safe-Area Rules

- Keep all persistent HUD, menu buttons, modal buttons, and result buttons inside the device safe area.
- Reserve the top safe-area band for status, title, currency, room progress, and non-interactive indicators.
- Keep critical buttons away from notches, rounded corners, Android gesture bars, and system navigation zones.
- Center modals inside the safe area, with enough bottom padding for one-handed reach.
- Never place required gameplay decisions partly outside the safe area.

## Shared Thumb-Zone Rules

- Primary one-handed actions should sit in the lower-middle or lower-left reachable area.
- Combat movement is lower-left only through the floating joystick.
- Combat lower-right is intentionally empty in MVP so it does not imply attack, dash, possession, or ability buttons.
- Reward and result screens may use lower-middle buttons because combat input is paused there.
- Modal buttons should be stacked vertically on narrow screens unless side-by-side choices remain at least 48 dp tall and readable.

## Interactive Element Rules

Real buttons in MVP:

- MainMenu start/run entry.
- Reward cards.
- Reward reroll button, only on the reward card screen.
- Cursed deal Accept and Decline buttons, only in the stop-2 modal.
- Result Restart and MainMenu buttons.
- Broken Seal unlock Continue button.

Not buttons:

- HP bar.
- Possession charge.
- Token count.
- Room progress.
- Auto-attack indicator.
- Marked vessel ring.
- Possession ready marker.
- Slot machine spin/reel animation.
- Combat lower-right space.

## Layout Zones

```text
+------------------------------+
| top safe-area status/title    |
| compact secondary indicators  |
|                              |
| central content/gameplay      |
| kept readable and uncluttered |
|                              |
| lower-left movement zone      |
| lower-middle CTA/modal zone   |
| lower-right no-combat-buttons |
+------------------------------+
```

## Handoff Summary

- [[Architect]]: Use these docs to define Canvas roots, safe-area anchoring, modal layers, and prefab layout responsibilities.
- [[Coder]]: Bind only the real buttons listed above. Do not bind combat actions to HUD elements.
- [[ArtDirector]]: Keep art blank of readable text and leave clear spaces for Unity UI labels.
- [[QA]]: Verify no forbidden combat controls exist, and verify all required buttons remain safe-area compliant on narrow and tall Android portrait screens.
