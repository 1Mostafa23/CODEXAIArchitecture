# Style Rules

Game: Gospel of the Jackpot
Style: stylized dark cartoon with grotesque religious-casino motifs
Mood: dark whimsical cult roguelite

Palette:
- charcoal #17151A
- old gold #C89B3C
- wax white #E8DCC2
- crimson #9E2431
- void violet #6D4BC3

Technical:
- PNG only
- transparent background
- 512x512 minimum source size
- readable at 64x64
- bold charcoal outline around 8px at 512x512
- clean edges
- no text
- no letters
- no numbers
- no watermark
- no JPG
- no photorealism
- no 3D render

## Player Readability
- Player body must read as compact, masked, and controlled even in greyscale.
- Idle, hit, and death states must keep similar bounds to avoid visual popping.
- Empty shell must be visibly different from both live player and death state.
- Player possession overlays must not bake a character body into the overlay.

## Enemy Readability
- Weak cultist, fast fanatic, and preacher must differ by silhouette before color.
- Marked vessel overlays must remain readable on weak cultist and fast fanatic.
- Hit and death states must preserve the base enemy identity long enough for feedback.
- Do not create enemy variants outside the manifest.

## Boss Readability
- Mother Couponella must be larger and heavier than standard enemies.
- Coupon veil, slot-machine torso, and candle crown must remain blank of readable text.
- Boss hit/death states must retain the same overall footprint as the idle state.
- Boss warning marker must read as floor danger, not as a reward or UI icon.

## UI Readability
- UI sprites must leave blank space for Unity UI text.
- Never bake labels, values, card names, result headings, or localization into PNGs.
- HUD icons must be readable at phone scale without requiring text.
- Selectable reward frames may have idle, selected, and disabled states only where the manifest defines them.

## Possession Overlays
- Possession visuals use void violet and old gold as the primary identity.
- Marked vessel ring, ready marker, and active overlay must not look like buttons.
- Default possession exit marker must be quiet and non-damaging.
- P03 explosion is the only possession-exit explosion-like visual.

## Slot Machine Objects
- Slot machine body is an automatic reward presentation object, not a manual interaction prop.
- `slot_machine_body_idle` must not include lever, handle, button, press/tap target, or manual spin affordance.
- Reel panels and symbols must be blank of letters, numbers, jackpot labels, or currency values.
- Reroll icon is only for reward-card reroll, not for spinning the machine.

## Environment Props
- Environment props support the arena mood without attracting touch interaction.
- Props must stay lower contrast than player, enemies, boss warnings, and possession markers.
- Signs, banners, papers, and panels must remain blank or abstract.
- Do not create post-MVP biome props outside the manifest.

## VFX Sprites
- VFX must have transparent backgrounds and compact silhouettes.
- Combat hit and enemy death VFX must remain less intense than P03 explosion.
- Reward VFX may be UI overlay assets; do not include text, numbers, or reward promises.
- P03 explosion must be visually distinct from default possession exit and used only for P03.
