# Prompts By Folder

Source manifest: `Assets/Generated/_MANIFESTS/mvp_sprite_asset_pack.md`

## Folder: `Assets/Generated/characters/player`

# player_body_idle

Target PNG:
`Assets/Generated/characters/player/player_body_idle.png`

Prompt file:
`Assets/Generated/characters/player/player_body_idle.prompt.txt`

Purpose:
Default hero body, readable top-down/three-quarter silhouette.

Used by:
Player gameplay prefab, SpriteRenderer.

Required states:
idle

Prompt:
```text
hooded broken-faith pilgrim hero with compact body and oversized wax-white mask, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Import as SpriteRenderer sprite, 128 PPU, pivot center-bottom.

# player_body_hit

Target PNG:
`Assets/Generated/characters/player/player_body_hit.png`

Prompt file:
`Assets/Generated/characters/player/player_body_hit.prompt.txt`

Purpose:
Player hit feedback state.

Used by:
Player damage feedback, SpriteRenderer.

Required states:
hit

Prompt:
```text
hooded broken-faith pilgrim hero recoiling with crimson crack glow and wax-white mask intact, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Same bounds as idle to avoid visual popping.

# player_body_death

Target PNG:
`Assets/Generated/characters/player/player_body_death.png`

Prompt file:
`Assets/Generated/characters/player/player_body_death.prompt.txt`

Purpose:
Player defeat/death visual.

Used by:
Player death state, GameOver transition.

Required states:
death

Prompt:
```text
collapsed hooded pilgrim hero shell with broken halo chip and extinguished candle shape, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Keep silhouette simple; no gore detail needed.

# player_empty_shell_idle

Target PNG:
`Assets/Generated/characters/player/player_empty_shell_idle.png`

Prompt file:
`Assets/Generated/characters/player/player_empty_shell_idle.prompt.txt`

Purpose:
Empty hero shell left in arena while possession is active.

Used by:
Possession system, Player shell prefab.

Required states:
idle

Prompt:
```text
hollow abandoned pilgrim body shell with dim wax-white face and old-gold seal crack, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
SpriteRenderer; must remain distinct from dead body.

# player_possessed_overlay_active

Target PNG:
`Assets/Generated/characters/player/player_possessed_overlay_active.png`

Prompt file:
`Assets/Generated/characters/player/player_possessed_overlay_active.prompt.txt`

Purpose:
Overlay showing player is controlling a vessel.

Used by:
Possession prefab, SpriteRenderer overlay.

Required states:
active

Prompt:
```text
floating void-violet halo flame overlay shaped like cracked casino seal around a controlled body, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Additive/overlay candidate; no baked enemy body.

## Folder: `Assets/Generated/characters/enemies`

# enemy_weak_cultist_idle

Target PNG:
`Assets/Generated/characters/enemies/enemy_weak_cultist_idle.png`

Prompt file:
`Assets/Generated/characters/enemies/enemy_weak_cultist_idle.prompt.txt`

Purpose:
Weak cultist enemy base.

Used by:
Enemy prefab, Wave Director.

Required states:
idle

Prompt:
```text
scrawny candle-carrying cultist with crooked robe and coin-like halo, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
SpriteRenderer; leave outer silhouette clear for marker ring.

# enemy_weak_cultist_hit

Target PNG:
`Assets/Generated/characters/enemies/enemy_weak_cultist_hit.png`

Prompt file:
`Assets/Generated/characters/enemies/enemy_weak_cultist_hit.prompt.txt`

Purpose:
Weak cultist hit state.

Used by:
Enemy damage feedback.

Required states:
hit

Prompt:
```text
scrawny candle cultist flinching with wax splash and crimson impact crack, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Same footprint as idle.

# enemy_weak_cultist_death

Target PNG:
`Assets/Generated/characters/enemies/enemy_weak_cultist_death.png`

Prompt file:
`Assets/Generated/characters/enemies/enemy_weak_cultist_death.prompt.txt`

Purpose:
Weak cultist death state or last frame.

Used by:
Enemy death feedback.

Required states:
death

Prompt:
```text
scrawny cultist dissolving into wax smoke and old-gold chips with body still recognizable, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Can be swapped before death puff VFX.

# enemy_fast_fanatic_idle

Target PNG:
`Assets/Generated/characters/enemies/enemy_fast_fanatic_idle.png`

Prompt file:
`Assets/Generated/characters/enemies/enemy_fast_fanatic_idle.prompt.txt`

Purpose:
Fast fanatic enemy base.

Used by:
Enemy prefab, Wave Director.

Required states:
idle

Prompt:
```text
lanky sprinting fanatic with sharp triangular hood and casino-token kneepads, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Silhouette must differ from weak cultist in greyscale.

# enemy_fast_fanatic_hit

Target PNG:
`Assets/Generated/characters/enemies/enemy_fast_fanatic_hit.png`

Prompt file:
`Assets/Generated/characters/enemies/enemy_fast_fanatic_hit.prompt.txt`

Purpose:
Fast fanatic hit state.

Used by:
Enemy damage feedback.

Required states:
hit

Prompt:
```text
lanky sprinting fanatic staggering sideways with broken old-gold token shards, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Same bounds as idle.

# enemy_fast_fanatic_death

Target PNG:
`Assets/Generated/characters/enemies/enemy_fast_fanatic_death.png`

Prompt file:
`Assets/Generated/characters/enemies/enemy_fast_fanatic_death.prompt.txt`

Purpose:
Fast fanatic death state or last frame.

Used by:
Enemy death feedback.

Required states:
death

Prompt:
```text
lanky fanatic collapsing into a streak of wax smoke and cracked crimson ribbon shapes, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Can be paired with death puff VFX.

# enemy_preacher_idle

Target PNG:
`Assets/Generated/characters/enemies/enemy_preacher_idle.png`

Prompt file:
`Assets/Generated/characters/enemies/enemy_preacher_idle.prompt.txt`

Purpose:
Ranged preacher enemy base.

Used by:
Enemy prefab, Wave Director.

Required states:
idle

Prompt:
```text
squat preacher cultist with megaphone-shaped reliquary and blank prayer-ticket fan, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Keep blank papers free of letters or numbers.

# enemy_preacher_hit

Target PNG:
`Assets/Generated/characters/enemies/enemy_preacher_hit.png`

Prompt file:
`Assets/Generated/characters/enemies/enemy_preacher_hit.prompt.txt`

Purpose:
Preacher hit state.

Used by:
Enemy damage feedback.

Required states:
hit

Prompt:
```text
squat preacher cultist knocked back with blank ticket fan scattering and crimson shock shape, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Same footprint as idle.

# enemy_preacher_death

Target PNG:
`Assets/Generated/characters/enemies/enemy_preacher_death.png`

Prompt file:
`Assets/Generated/characters/enemies/enemy_preacher_death.prompt.txt`

Purpose:
Preacher death state or last frame.

Used by:
Enemy death feedback.

Required states:
death

Prompt:
```text
squat preacher cultist crumpling into void-violet sermon smoke and blank ticket scraps, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
No readable ticket markings.

## Folder: `Assets/Generated/characters/boss`

# boss_mother_couponella_idle

Target PNG:
`Assets/Generated/characters/boss/boss_mother_couponella_idle.png`

Prompt file:
`Assets/Generated/characters/boss/boss_mother_couponella_idle.prompt.txt`

Purpose:
Mother Couponella boss base sprite.

Used by:
Boss prefab, SpriteRenderer.

Required states:
idle

Prompt:
```text
enormous matriarch coupon priestess with blank coupon veil, slot-machine torso, candle crown, and clawed blessing pose, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
SpriteRenderer; pivot center-bottom; no readable coupon text.

# boss_mother_couponella_hit

Target PNG:
`Assets/Generated/characters/boss/boss_mother_couponella_hit.png`

Prompt file:
`Assets/Generated/characters/boss/boss_mother_couponella_hit.prompt.txt`

Purpose:
Mother Couponella hit feedback.

Used by:
Boss damage feedback.

Required states:
hit

Prompt:
```text
enormous coupon priestess boss recoiling as blank coupon veil tears and old-gold coins scatter, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
Match idle bounds as closely as possible.

# boss_mother_couponella_death

Target PNG:
`Assets/Generated/characters/boss/boss_mother_couponella_death.png`

Prompt file:
`Assets/Generated/characters/boss/boss_mother_couponella_death.prompt.txt`

Purpose:
Mother Couponella defeat sprite.

Used by:
Boss defeat transition, victory flow.

Required states:
death

Prompt:
```text
enormous coupon priestess boss collapsing into broken slot-machine reliquary with extinguished candle crown, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
Avoid gore; keep large readable silhouette.

# boss_attack_warning_marker_ready

Target PNG:
`Assets/Generated/characters/boss/boss_attack_warning_marker_ready.png`

Prompt file:
`Assets/Generated/characters/boss/boss_attack_warning_marker_ready.prompt.txt`

Purpose:
Floor warning marker for boss AOE/tape attack.

Used by:
Boss attack telegraph prefab.

Required states:
ready

Prompt:
```text
circular crimson and old-gold warning sigil shaped like blank coupon tape spiral with broken halo edge, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
SpriteRenderer or UI world-space image; transparent center acceptable.

## Folder: `Assets/Generated/ui/hud`

# ui_hp_frame_idle

Target PNG:
`Assets/Generated/ui/hud/ui_hp_frame_idle.png`

Prompt file:
`Assets/Generated/ui/hud/ui_hp_frame_idle.prompt.txt`

Purpose:
HP bar frame.

Used by:
HUD prefab, Unity UI Image.

Required states:
idle

Prompt:
```text
horizontal cracked reliquary health bar frame with old-gold corners and wax-white bone inlay, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Use as sliced UI Image; no numbers or labels.

# ui_hp_fill_active

Target PNG:
`Assets/Generated/ui/hud/ui_hp_fill_active.png`

Prompt file:
`Assets/Generated/ui/hud/ui_hp_fill_active.prompt.txt`

Purpose:
HP fill art.

Used by:
HUD fill Image.

Required states:
active

Prompt:
```text
crimson liquid wax health bar fill with subtle old-gold flecks and clean rectangular silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Use as filled UI Image; avoid gradients that vanish on mobile.

# ui_possession_charge_frame_idle

Target PNG:
`Assets/Generated/ui/hud/ui_possession_charge_frame_idle.png`

Prompt file:
`Assets/Generated/ui/hud/ui_possession_charge_frame_idle.prompt.txt`

Purpose:
Possession charge bar frame.

Used by:
HUD prefab, Unity UI Image.

Required states:
idle

Prompt:
```text
horizontal cracked halo charge frame with void-violet inner groove and old-gold casino corners, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Sliced UI Image; no possession button behavior.

# ui_possession_charge_fill_active

Target PNG:
`Assets/Generated/ui/hud/ui_possession_charge_fill_active.png`

Prompt file:
`Assets/Generated/ui/hud/ui_possession_charge_fill_active.prompt.txt`

Purpose:
Possession charge fill.

Used by:
HUD fill Image.

Required states:
active

Prompt:
```text
void-violet spirit wax charge fill with old-gold sparks and clean horizontal silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Filled Image; use color/alpha animation in Unity.

# ui_token_icon_idle

Target PNG:
`Assets/Generated/ui/hud/ui_token_icon_idle.png`

Prompt file:
`Assets/Generated/ui/hud/ui_token_icon_idle.prompt.txt`

Purpose:
Token currency icon.

Used by:
HUD, reward UI.

Required states:
idle

Prompt:
```text
old-gold casino token with cracked halo symbol and no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; text count added in Unity UI.

# ui_room_progress_frame_idle

Target PNG:
`Assets/Generated/ui/hud/ui_room_progress_frame_idle.png`

Prompt file:
`Assets/Generated/ui/hud/ui_room_progress_frame_idle.prompt.txt`

Purpose:
Room progress frame.

Used by:
HUD progress display.

Required states:
idle

Prompt:
```text
compact five-notch reliquary progress frame with blank sockets and old-gold cracked trim, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Coder can place icons/filled states; no room numbers baked in.

# ui_room_progress_icon_active

Target PNG:
`Assets/Generated/ui/hud/ui_room_progress_icon_active.png`

Prompt file:
`Assets/Generated/ui/hud/ui_room_progress_icon_active.prompt.txt`

Purpose:
Active/cleared room progress token.

Used by:
HUD progress display.

Required states:
active

Prompt:
```text
small old-gold cracked chapel-token marker with crimson inner glow and no number, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image repeated by code for progress slots.

# ui_auto_attack_indicator_active

Target PNG:
`Assets/Generated/ui/hud/ui_auto_attack_indicator_active.png`

Prompt file:
`Assets/Generated/ui/hud/ui_auto_attack_indicator_active.prompt.txt`

Purpose:
Optional indicator that auto-attack is active.

Used by:
HUD, Player combat feedback.

Required states:
active

Prompt:
```text
small targeting halo icon with old-gold reticle and wax-white spark, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image only; not a button.

# ui_auto_attack_indicator_disabled

Target PNG:
`Assets/Generated/ui/hud/ui_auto_attack_indicator_disabled.png`

Prompt file:
`Assets/Generated/ui/hud/ui_auto_attack_indicator_disabled.prompt.txt`

Purpose:
Optional inactive auto-attack indicator.

Used by:
HUD, Player combat feedback.

Required states:
disabled

Prompt:
```text
dim broken targeting halo icon with charcoal fill and faint wax-white spark, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image only; no manual attack button.

## Folder: `Assets/Generated/ui/controls`

# ui_joystick_base_idle

Target PNG:
`Assets/Generated/ui/controls/ui_joystick_base_idle.png`

Prompt file:
`Assets/Generated/ui/controls/ui_joystick_base_idle.prompt.txt`

Purpose:
Floating joystick base at rest.

Used by:
Input UI prefab.

Required states:
idle

Prompt:
```text
translucent circular old-gold and charcoal joystick base shaped like cracked chapel window with blank center, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image under touch area; no labels.

# ui_joystick_base_active

Target PNG:
`Assets/Generated/ui/controls/ui_joystick_base_active.png`

Prompt file:
`Assets/Generated/ui/controls/ui_joystick_base_active.prompt.txt`

Purpose:
Floating joystick base while touched.

Used by:
Input UI prefab.

Required states:
active

Prompt:
```text
glowing circular old-gold and void-violet joystick base shaped like cracked chapel window with blank center, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; Coder changes alpha/position by touch.

# ui_joystick_knob_idle

Target PNG:
`Assets/Generated/ui/controls/ui_joystick_knob_idle.png`

Prompt file:
`Assets/Generated/ui/controls/ui_joystick_knob_idle.prompt.txt`

Purpose:
Floating joystick knob at rest.

Used by:
Input UI prefab.

Required states:
idle

Prompt:
```text
small old-gold casino token joystick knob with cracked halo emblem and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; no text or numbers.

# ui_joystick_knob_active

Target PNG:
`Assets/Generated/ui/controls/ui_joystick_knob_active.png`

Prompt file:
`Assets/Generated/ui/controls/ui_joystick_knob_active.prompt.txt`

Purpose:
Floating joystick knob while dragged.

Used by:
Input UI prefab.

Required states:
active

Prompt:
```text
small glowing void-violet casino token joystick knob with old-gold cracked halo emblem and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; no dash or action affordance.

## Folder: `Assets/Generated/possession`

# possession_marked_vessel_ring_ready

Target PNG:
`Assets/Generated/possession/possession_marked_vessel_ring_ready.png`

Prompt file:
`Assets/Generated/possession/possession_marked_vessel_ring_ready.prompt.txt`

Purpose:
Ring showing valid marked vessel.

Used by:
Possession system, enemy overlay.

Required states:
ready

Prompt:
```text
circular old-gold cracked halo ring with void-violet inner flame and open center for enemy body, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Overlay SpriteRenderer; center must be transparent.

# possession_ready_marker_ready

Target PNG:
`Assets/Generated/possession/possession_ready_marker_ready.png`

Prompt file:
`Assets/Generated/possession/possession_ready_marker_ready.prompt.txt`

Purpose:
Marker that possession charge/proximity is ready.

Used by:
Possession feedback, HUD/world marker.

Required states:
ready

Prompt:
```text
floating void-violet eye halo with old-gold spark and compact readable silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Not a button; use as feedback above/around vessel.

# possession_active_overlay_active

Target PNG:
`Assets/Generated/possession/possession_active_overlay_active.png`

Prompt file:
`Assets/Generated/possession/possession_active_overlay_active.prompt.txt`

Purpose:
Active possession aura over controlled vessel.

Used by:
Possession prefab, controlled enemy overlay.

Required states:
active

Prompt:
```text
jagged void-violet spirit aura wrapped by old-gold broken halo fragments with transparent center, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Overlay SpriteRenderer; can pulse via script.

# possession_exit_marker_active

Target PNG:
`Assets/Generated/possession/possession_exit_marker_active.png`

Prompt file:
`Assets/Generated/possession/possession_exit_marker_active.prompt.txt`

Purpose:
Non-damaging default possession exit marker.

Used by:
Possession exit feedback.

Required states:
active

Prompt:
```text
quiet fading wax-white spirit wisp with small broken halo fragments and no blast shape, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Must not be used as explosion or damage indicator.

## Folder: `Assets/Generated/slot_machine/body`

# slot_machine_body_idle

Target PNG:
`Assets/Generated/slot_machine/body/slot_machine_body_idle.png`

Prompt file:
`Assets/Generated/slot_machine/body/slot_machine_body_idle.prompt.txt`

Purpose:
Sacred demonic slot machine body at rest.

Used by:
Slot machine presentation prefab.

Required states:
idle

Prompt:
```text
grotesque sacred casino slot machine altar with candle horns, blank display panels, old-gold sealed side shrine ornaments, and wax-drip side columns, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
SpriteRenderer or UI Image; no readable labels; passive auto-roll presentation only.

# slot_machine_body_active

Target PNG:
`Assets/Generated/slot_machine/body/slot_machine_body_active.png`

Prompt file:
`Assets/Generated/slot_machine/body/slot_machine_body_active.prompt.txt`

Purpose:
Slot machine during automatic post-combat roll.

Used by:
Slot auto-roll presentation.

Required states:
active

Prompt:
```text
glowing grotesque sacred casino slot machine altar with void-violet reels and blank display panels, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
State swap during auto-roll; no manual interaction prompt.

# slot_reel_panel_idle

Target PNG:
`Assets/Generated/slot_machine/body/slot_reel_panel_idle.png`

Prompt file:
`Assets/Generated/slot_machine/body/slot_reel_panel_idle.prompt.txt`

Purpose:
Reusable reel panel frame.

Used by:
Slot auto-roll UI.

Required states:
idle

Prompt:
```text
three-window slot reel panel with blank dark windows, old-gold cracked frame, and wax-white accents, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; symbols layered separately.

## Folder: `Assets/Generated/slot_machine/symbols`

# slot_symbol_token_idle

Target PNG:
`Assets/Generated/slot_machine/symbols/slot_symbol_token_idle.png`

Prompt file:
`Assets/Generated/slot_machine/symbols/slot_symbol_token_idle.prompt.txt`

Purpose:
Reel token symbol.

Used by:
Slot reel animation.

Required states:
idle

Prompt:
```text
old-gold cracked casino token symbol with halo notch and no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image/SpriteRenderer; no currency amount.

# slot_symbol_candle_idle

Target PNG:
`Assets/Generated/slot_machine/symbols/slot_symbol_candle_idle.png`

Prompt file:
`Assets/Generated/slot_machine/symbols/slot_symbol_candle_idle.prompt.txt`

Purpose:
Reel candle symbol.

Used by:
Slot reel animation.

Required states:
idle

Prompt:
```text
wax-white bent candle symbol with crimson flame and old-gold base, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image/SpriteRenderer.

# slot_symbol_seal_idle

Target PNG:
`Assets/Generated/slot_machine/symbols/slot_symbol_seal_idle.png`

Prompt file:
`Assets/Generated/slot_machine/symbols/slot_symbol_seal_idle.prompt.txt`

Purpose:
Reel seal symbol.

Used by:
Slot reel animation.

Required states:
idle

Prompt:
```text
broken sacred seal symbol shaped like cracked wax stamp and roulette chip with no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image/SpriteRenderer.

# slot_symbol_eye_idle

Target PNG:
`Assets/Generated/slot_machine/symbols/slot_symbol_eye_idle.png`

Prompt file:
`Assets/Generated/slot_machine/symbols/slot_symbol_eye_idle.prompt.txt`

Purpose:
Reel eye symbol.

Used by:
Slot reel animation.

Required states:
idle

Prompt:
```text
void-violet sacred eye symbol inside old-gold casino chip rim with no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image/SpriteRenderer.

## Folder: `Assets/Generated/ui/rewards`

# ui_reward_card_frame_idle

Target PNG:
`Assets/Generated/ui/rewards/ui_reward_card_frame_idle.png`

Prompt file:
`Assets/Generated/ui/rewards/ui_reward_card_frame_idle.prompt.txt`

Purpose:
Standard reward card frame.

Used by:
Reward choice UI.

Required states:
idle

Prompt:
```text
vertical reward card frame with old-gold chapel arch corners, charcoal interior, and blank wax-white text area space, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 768x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
768x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; text and icon placed by Unity UI.

# ui_reward_card_frame_selected

Target PNG:
`Assets/Generated/ui/rewards/ui_reward_card_frame_selected.png`

Prompt file:
`Assets/Generated/ui/rewards/ui_reward_card_frame_selected.prompt.txt`

Purpose:
Selected reward card frame.

Used by:
Reward choice UI.

Required states:
selected

Prompt:
```text
vertical reward card frame glowing old-gold with void-violet chapel arch corners and blank interior, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 768x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
768x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image state; no baked selection label.

# ui_reward_card_frame_disabled

Target PNG:
`Assets/Generated/ui/rewards/ui_reward_card_frame_disabled.png`

Prompt file:
`Assets/Generated/ui/rewards/ui_reward_card_frame_disabled.prompt.txt`

Purpose:
Disabled/unavailable reward card frame.

Used by:
Reward choice UI.

Required states:
disabled

Prompt:
```text
dim vertical reward card frame with cracked charcoal chapel arch and faded wax-white interior, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 768x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
768x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image state; use for disabled card presentation only.

# ui_reroll_icon_ready

Target PNG:
`Assets/Generated/ui/rewards/ui_reroll_icon_ready.png`

Prompt file:
`Assets/Generated/ui/rewards/ui_reroll_icon_ready.prompt.txt`

Purpose:
Reroll visual icon/button art.

Used by:
Reward UI reroll control.

Required states:
ready

Prompt:
```text
circular old-gold reroll arrow icon made of broken halo fragments around a casino token, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Button Image; no text count baked in.

# ui_reroll_icon_disabled

Target PNG:
`Assets/Generated/ui/rewards/ui_reroll_icon_disabled.png`

Prompt file:
`Assets/Generated/ui/rewards/ui_reroll_icon_disabled.prompt.txt`

Purpose:
Disabled reroll visual.

Used by:
Reward UI reroll control.

Required states:
disabled

Prompt:
```text
dim circular reroll arrow icon made of cracked charcoal halo fragments with faint wax-white edge, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Button disabled Image; reroll count in Unity text.

# reward_icon_standard_01

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_01.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_01.prompt.txt`

Purpose:
Standard reward icon placeholder 01.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
old-gold crooked candle blessing icon with wax-white flame and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# reward_icon_standard_02

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_02.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_02.prompt.txt`

Purpose:
Standard reward icon placeholder 02.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
crimson thorn dagger blessing icon wrapped in tiny old-gold token halo and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# reward_icon_p03_last_breath

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_p03_last_breath.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_p03_last_breath.prompt.txt`

Purpose:
Standard reward icon for P03 Last Breath, the only possession-exit explosion source.

Used by:
Reward cards, P03 effect UI.

Required states:
none

Prompt:
```text
void-violet final breath spirit icon bursting from a cracked old-gold vessel halo without damage numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Only icon tied to validated P03 explosion behavior.

# reward_icon_standard_04

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_04.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_04.prompt.txt`

Purpose:
Standard reward icon placeholder 04.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
cracked old-gold halo blessing icon with wax-white inner glow and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# reward_icon_standard_05

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_05.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_05.prompt.txt`

Purpose:
Standard reward icon placeholder 05.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
wax-white heart reliquary icon inside old-gold casino chip rim and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# reward_icon_standard_06

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_06.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_06.prompt.txt`

Purpose:
Standard reward icon placeholder 06.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
void-violet watching eye blessing icon with crimson tear and old-gold broken rim, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# reward_icon_standard_07

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_07.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_07.prompt.txt`

Purpose:
Standard reward icon placeholder 07.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
black casino token blessing icon with old-gold rim, wax-white crack, and no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# reward_icon_standard_08

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_08.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_08.prompt.txt`

Purpose:
Standard reward icon placeholder 08.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
thorny rosary loop icon made of tiny old-gold casino beads with crimson wax drop and no cross text, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# reward_icon_standard_09

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_09.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_09.prompt.txt`

Purpose:
Standard reward icon placeholder 09.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
broken balance scale icon with old-gold pans shaped like casino chips and no markings, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# reward_icon_standard_10

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_10.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_10.prompt.txt`

Purpose:
Standard reward icon placeholder 10.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
incense burner icon shaped like tiny slot altar with void-violet smoke and blank face, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# reward_icon_standard_11

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_11.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_11.prompt.txt`

Purpose:
Standard reward icon placeholder 11.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
wax-white marked palm blessing icon holding old-gold token with no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# reward_icon_standard_12

Target PNG:
`Assets/Generated/ui/rewards/reward_icon_standard_12.png`

Prompt file:
`Assets/Generated/ui/rewards/reward_icon_standard_12.prompt.txt`

Purpose:
Standard reward icon placeholder 12.

Used by:
Reward cards.

Required states:
none

Prompt:
```text
sealed chapel gate icon with old-gold lock and void-violet crack, no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Placeholder; does not define mechanics.

# ui_cursed_deal_frame_active

Target PNG:
`Assets/Generated/ui/rewards/ui_cursed_deal_frame_active.png`

Prompt file:
`Assets/Generated/ui/rewards/ui_cursed_deal_frame_active.prompt.txt`

Purpose:
Cursed deal card/popup frame.

Used by:
Reward UI, cursed deal stop 2.

Required states:
active

Prompt:
```text
vertical cursed deal frame with crimson wax cracks, void-violet smoke corners, old-gold chapel arch, and blank interior, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 768x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
768x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; cursed deal name/effect added via Unity text.

# ui_cursed_deal_icon_fanatical_credit

Target PNG:
`Assets/Generated/ui/rewards/ui_cursed_deal_icon_fanatical_credit.png`

Prompt file:
`Assets/Generated/ui/rewards/ui_cursed_deal_icon_fanatical_credit.prompt.txt`

Purpose:
Icon for Fanatical Credit cursed deal.

Used by:
Reward UI, cursed deal offer.

Required states:
none

Prompt:
```text
cursed old-gold credit token chained to crimson wax heart with blank face and no numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Icon only; +1 Attack and -1 Max HP text must be Unity UI.

## Folder: `Assets/Generated/ui/results`

# ui_victory_emblem_active

Target PNG:
`Assets/Generated/ui/results/ui_victory_emblem_active.png`

Prompt file:
`Assets/Generated/ui/results/ui_victory_emblem_active.prompt.txt`

Purpose:
Victory emblem after boss defeat.

Used by:
GameOver/Victory UI.

Required states:
active

Prompt:
```text
old-gold broken seal victory emblem over wax-white candleburst with crimson cult cracks, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG emblem readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; victory text added in Unity.

# ui_defeat_emblem_active

Target PNG:
`Assets/Generated/ui/results/ui_defeat_emblem_active.png`

Prompt file:
`Assets/Generated/ui/results/ui_defeat_emblem_active.prompt.txt`

Purpose:
Defeat emblem.

Used by:
GameOver UI.

Required states:
active

Prompt:
```text
dim cracked halo defeat emblem with extinguished candle and void-violet smoke, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG emblem readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; defeat text added in Unity.

# ui_game_over_panel_bg_idle

Target PNG:
`Assets/Generated/ui/results/ui_game_over_panel_bg_idle.png`

Prompt file:
`Assets/Generated/ui/results/ui_game_over_panel_bg_idle.prompt.txt`

Purpose:
Game over panel background decoration.

Used by:
GameOver scene UI.

Required states:
idle

Prompt:
```text
large dark chapel-casino panel background with blank parchment center and old-gold cracked border, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
Sliced or full UI Image; all summary text is Unity UI.

# ui_run_summary_frame_idle

Target PNG:
`Assets/Generated/ui/results/ui_run_summary_frame_idle.png`

Prompt file:
`Assets/Generated/ui/results/ui_run_summary_frame_idle.prompt.txt`

Purpose:
Decorative frame for run summary stats.

Used by:
GameOver scene UI.

Required states:
idle

Prompt:
```text
horizontal run summary frame with old-gold casino chapel corners, blank sockets, and wax-white trim, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; numbers/labels added in Unity.

## Folder: `Assets/Generated/ui/meta`

# ui_broken_seal_icon_idle

Target PNG:
`Assets/Generated/ui/meta/ui_broken_seal_icon_idle.png`

Prompt file:
`Assets/Generated/ui/meta/ui_broken_seal_icon_idle.prompt.txt`

Purpose:
First meta unlock icon: Broken Seal.

Used by:
MainMenu/meta unlock UI.

Required states:
idle

Prompt:
```text
broken old-gold sacred seal icon with void-violet crack and wax-white glow, no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; unlock name/effect text in Unity.

# ui_meta_unlock_panel_decoration_idle

Target PNG:
`Assets/Generated/ui/meta/ui_meta_unlock_panel_decoration_idle.png`

Prompt file:
`Assets/Generated/ui/meta/ui_meta_unlock_panel_decoration_idle.prompt.txt`

Purpose:
Meta unlock panel decoration.

Used by:
MainMenu/meta unlock UI.

Required states:
idle

Prompt:
```text
compact chapel-casino unlock panel decoration with blank center, cracked old-gold border, and candle side ornaments, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI Image; no unlock copy baked in.

## Folder: `Assets/Generated/environment/arenas`

# arena_floor_corrupted_village_idle

Target PNG:
`Assets/Generated/environment/arenas/arena_floor_corrupted_village_idle.png`

Prompt file:
`Assets/Generated/environment/arenas/arena_floor_corrupted_village_idle.prompt.txt`

Purpose:
Simple arena floor/background for five combat rooms.

Used by:
Game scene background.

Required states:
idle

Prompt:
```text
circular corrupted village arena floor patch with cracked chapel stones, faint casino-chip geometry, and muddy charcoal edges, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
1024x1024 minimum source size

Transparency:
Yes, transparent background

Unity note:
SpriteRenderer background; can be scaled, avoid busy detail under enemies.

## Folder: `Assets/Generated/environment/props`

# prop_corrupted_village_house_idle

Target PNG:
`Assets/Generated/environment/props/prop_corrupted_village_house_idle.png`

Prompt file:
`Assets/Generated/environment/props/prop_corrupted_village_house_idle.prompt.txt`

Purpose:
Corrupted village background prop.

Used by:
Room decoration prefab.

Required states:
idle

Prompt:
```text
crooked rotting village chapel-house prop with blank hanging sign and old-gold candle stains, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
SpriteRenderer; sign must remain unreadable/blank.

# prop_altar_slot_machine_idle

Target PNG:
`Assets/Generated/environment/props/prop_altar_slot_machine_idle.png`

Prompt file:
`Assets/Generated/environment/props/prop_altar_slot_machine_idle.prompt.txt`

Purpose:
Non-interactive altar slot-machine prop for arena dressing if needed.

Used by:
Room decoration prefab.

Required states:
idle

Prompt:
```text
small broken altar slot-machine prop with blank reel windows and melted candles, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Decorative only; not the reward machine interaction.

# prop_sacred_casino_candles_idle

Target PNG:
`Assets/Generated/environment/props/prop_sacred_casino_candles_idle.png`

Prompt file:
`Assets/Generated/environment/props/prop_sacred_casino_candles_idle.prompt.txt`

Purpose:
Casino-religious decorative candles.

Used by:
Room decoration prefab.

Required states:
idle

Prompt:
```text
cluster of wax-white altar candles around old-gold casino chips with crimson wax drips, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
SpriteRenderer prop; keep low visual noise.

# prop_casino_religious_banner_idle

Target PNG:
`Assets/Generated/environment/props/prop_casino_religious_banner_idle.png`

Prompt file:
`Assets/Generated/environment/props/prop_casino_religious_banner_idle.prompt.txt`

Purpose:
Decorative banner without readable symbols.

Used by:
Room decoration prefab.

Required states:
idle

Prompt:
```text
torn chapel banner with abstract casino-chip pattern, no letters, no numbers, old-gold trim and crimson cloth, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Decorative prop; no readable prayers or signage.

## Folder: `Assets/Generated/vfx/combat`

# vfx_hit_impact_active

Target PNG:
`Assets/Generated/vfx/combat/vfx_hit_impact_active.png`

Prompt file:
`Assets/Generated/vfx/combat/vfx_hit_impact_active.prompt.txt`

Purpose:
Generic hit impact sprite.

Used by:
Combat VFX prefab.

Required states:
active

Prompt:
```text
compact crimson wax impact burst with old-gold chip shards and strong radial silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
SpriteRenderer VFX; Coder can scale/fade.

# vfx_enemy_death_puff_active

Target PNG:
`Assets/Generated/vfx/combat/vfx_enemy_death_puff_active.png`

Prompt file:
`Assets/Generated/vfx/combat/vfx_enemy_death_puff_active.prompt.txt`

Purpose:
Enemy death puff.

Used by:
Enemy death VFX prefab.

Required states:
active

Prompt:
```text
small charcoal wax smoke puff with old-gold flecks and void-violet inner curl, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
SpriteRenderer VFX; not used for P03 explosion.

## Folder: `Assets/Generated/vfx/possession`

# vfx_possession_tether_flash_active

Target PNG:
`Assets/Generated/vfx/possession/vfx_possession_tether_flash_active.png`

Prompt file:
`Assets/Generated/vfx/possession/vfx_possession_tether_flash_active.prompt.txt`

Purpose:
Possession tether/flash between player and vessel.

Used by:
Possession VFX prefab.

Required states:
active

Prompt:
```text
arcing void-violet spirit tether with old-gold broken halo sparks and clean readable curve, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Can be stretched/rotated by script or used as short flash.

## Folder: `Assets/Generated/vfx/rewards`

# vfx_reward_reveal_sparkle_active

Target PNG:
`Assets/Generated/vfx/rewards/vfx_reward_reveal_sparkle_active.png`

Prompt file:
`Assets/Generated/vfx/rewards/vfx_reward_reveal_sparkle_active.prompt.txt`

Purpose:
Reward reveal sparkle.

Used by:
Reward UI VFX prefab.

Required states:
active

Prompt:
```text
old-gold candle sparkle burst with wax-white glints and tiny void-violet cracks, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI overlay or SpriteRenderer VFX.

# vfx_cursed_deal_smoke_active

Target PNG:
`Assets/Generated/vfx/rewards/vfx_cursed_deal_smoke_active.png`

Prompt file:
`Assets/Generated/vfx/rewards/vfx_cursed_deal_smoke_active.prompt.txt`

Purpose:
Cursed deal smoke.

Used by:
Cursed deal UI VFX prefab.

Required states:
active

Prompt:
```text
curling crimson and void-violet cursed smoke with old-gold ember flecks and compact silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
UI overlay; no readable curse symbols.

## Folder: `Assets/Generated/vfx/p03`

# vfx_p03_explosion_active

Target PNG:
`Assets/Generated/vfx/p03/vfx_p03_explosion_active.png`

Prompt file:
`Assets/Generated/vfx/p03/vfx_p03_explosion_active.prompt.txt`

Purpose:
P03 Last Breath damaging possession-exit explosion.

Used by:
P03 reward effect VFX prefab.

Required states:
active

Prompt:
```text
compact void-violet and crimson spirit explosion from cracked old-gold vessel halo with enemy-only blast silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

Negative prompt:
photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background

Size:
512x512 minimum source size

Transparency:
Yes, transparent background

Unity note:
Only use for P03; default possession exit must not call this VFX.

