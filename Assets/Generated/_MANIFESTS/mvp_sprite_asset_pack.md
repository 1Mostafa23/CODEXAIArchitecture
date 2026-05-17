# MVP Sprite Asset Pack Plan

Acting agent: [[ArtDirector]]

Project: mobile portrait roguelite "Евангелие Джекпота"

Scope: complete MVP sprite plan only. This file does not create PNGs, Unity prefabs, gameplay code, or final balancing.

Art lock for MVP:
- Style: stylized dark cartoon with grotesque religious-casino motifs.
- Mood: dark whimsical cult roguelite.
- Palette: charcoal `#17151A`, old gold `#C89B3C`, wax white `#E8DCC2`, crimson `#9E2431`, void violet `#6D4BC3`.
- Outline: bold charcoal outline, about 8 px at 512x512 source size, still readable after downscale to 64x64.
- Pixel density: gameplay SpriteRenderer assets generated at 512x512 minimum and imported at 128 PPU unless Coder has a stronger scene-scale reason; UI assets use native Canvas scaling.
- File format: PNG only.
- Transparency: transparent background for every planned sprite asset.
- Text rule: no readable text, letters, numbers, words, labels, watermarks, or baked UI copy inside generated images. All text belongs in Unity UI later.
- Explicit exclusions: no dash button, no manual possession button, no manual slot-machine spin button, no pet/helper system art, no post-MVP enemies, no post-MVP bosses, no JPG.

Standard negative prompt for every generated asset:

`photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background`

## 1. Folder Structure

Planned folder tree:

```text
Assets/Generated/
  _MANIFESTS/
  characters/
    player/
    enemies/
    boss/
  ui/
    hud/
    controls/
    rewards/
    results/
    meta/
  possession/
  slot_machine/
    body/
    symbols/
  environment/
    arenas/
    props/
  vfx/
    combat/
    possession/
    rewards/
    p03/
```

| Folder | Contains | Must Not Contain | Used Later By |
|---|---|---|---|
| `Assets/Generated/_MANIFESTS/` | Art manifests, prompt plans, asset inventory markdown. | PNG sprites, Unity prefabs, C# scripts, generated text-image mockups. | ArtDirector, Coder, PM. |
| `Assets/Generated/characters/player/` | Player body states, empty shell state, player possession overlay. | Enemy sprites, UI bars, boss sprites, manual ability buttons. | Gameplay prefabs, Coder, SpriteRenderers. |
| `Assets/Generated/characters/enemies/` | Weak cultist, fast fanatic, preacher states; all compatible with possession marker overlays. | Boss art, player body, post-MVP enemies, pet/helper assets. | Enemy prefabs, Wave Director, SpriteRenderers. |
| `Assets/Generated/characters/boss/` | Mother Couponella boss states and boss-specific warning marker if represented as character-adjacent art. | Standard enemies, reward cards, unrelated screen panels. | Boss prefab, boss attack telegraph, SpriteRenderers/VFX. |
| `Assets/Generated/ui/hud/` | HP bar art, possession charge bar art, token icon, room progress icon/frame, auto-attack status indicator. | Touch controls, reward cards, readable labels, gameplay sprites. | Unity UI Images, HUD prefabs, Coder. |
| `Assets/Generated/ui/controls/` | Floating joystick base and knob visual states. | Dash buttons, manual possession buttons, machine spin buttons, gameplay sprites. | Unity UI Images, input prefab. |
| `Assets/Generated/ui/rewards/` | Reward card frames, selected/disabled card states, reroll button visuals, standard reward icons, cursed deal frame/icon. | Baked card names, baked descriptions, machine body art, post-MVP rewards. | Reward UI, slot reward screen, Coder. |
| `Assets/Generated/ui/results/` | Victory emblem, defeat emblem, game over panel background, run summary decorative frame. | Gameplay sprites, readable summary text, post-MVP badges. | GameOver scene UI, Unity UI Images. |
| `Assets/Generated/ui/meta/` | Broken Seal icon and meta unlock panel decoration. | Other meta progression icons, text labels, shop/IAP art. | MainMenu/meta unlock UI. |
| `Assets/Generated/possession/` | Marked vessel ring, possession ready marker, active overlay, non-damaging possession exit marker. | P03 damaging explosion, manual possession button art, token pickups. | Possession prefabs, VFX, Coder. |
| `Assets/Generated/slot_machine/body/` | Sacred/demonic slot machine body states and reel panel frame. | Card frames, reroll button, manual spin controls, readable text. | Slot machine presentation prefab, reward screen backdrop. |
| `Assets/Generated/slot_machine/symbols/` | Reusable reel symbols without text: token, candle, seal, eye. | Currency numbers, letters, card names, jackpot labels. | Slot auto-roll animation, UI Images/SpriteRenderers. |
| `Assets/Generated/environment/arenas/` | Simple arena floor/background sprite for corrupted village combat rooms. | Decorative props, UI panels, baked path arrows or text. | Game scene background, SpriteRenderer/tile-like placement. |
| `Assets/Generated/environment/props/` | Corrupted village props, altar slot-machine prop, casino-religious decorations. | Interactive manual controls, enemies, UI text, post-MVP biome props. | Room decoration prefabs, SpriteRenderers. |
| `Assets/Generated/vfx/combat/` | Hit impact and enemy death puff. | Possession tether, reward reveal, P03 explosion. | VFX prefabs, pooled SpriteRenderers. |
| `Assets/Generated/vfx/possession/` | Possession tether/flash. | P03 explosion, generic combat hit VFX, UI icons. | Possession VFX prefabs. |
| `Assets/Generated/vfx/rewards/` | Reward reveal sparkle and cursed deal smoke. | Slot machine body, reward card frames, readable labels. | Reward UI VFX prefabs. |
| `Assets/Generated/vfx/p03/` | P03 Last Breath explosion only. | Default possession exit VFX, generic enemy death, non-damaging markers. | P03 VFX prefab and reward effect implementation. |

## 2. Asset Naming Rules

- Use lowercase snake_case for every file name.
- Use English file names only.
- Do not use spaces.
- Do not use Cyrillic in file names.
- Keep folder names lowercase snake_case for consistency.
- Use one PNG per distinct state.
- Include state suffixes where needed:
  - `_idle`
  - `_active`
  - `_disabled`
  - `_selected`
  - `_ready`
  - `_hit`
  - `_death`
- Use descriptive nouns before state suffixes: `enemy_preacher_hit.png`, not `hit_preacher.png`.
- Do not encode card text, stat values, room numbers, or localized labels in file names unless the ID is already a stable design ID such as `p03`.
- Do not create texture atlases in this pass. Coder can atlas or pack later after import behavior is known.

## 3. Required Sprite List

### Characters

- `characters/player/player_body_idle.png` - default player body.
- `characters/player/player_body_hit.png` - damage flash/impact state.
- `characters/player/player_body_death.png` - defeat body state.
- `characters/player/player_empty_shell_idle.png` - empty hero shell left behind during possession.
- `characters/player/player_possessed_overlay_active.png` - overlay used when the player is controlling a vessel.

### Enemies

- `characters/enemies/enemy_weak_cultist_idle.png`
- `characters/enemies/enemy_weak_cultist_hit.png`
- `characters/enemies/enemy_weak_cultist_death.png`
- `characters/enemies/enemy_fast_fanatic_idle.png`
- `characters/enemies/enemy_fast_fanatic_hit.png`
- `characters/enemies/enemy_fast_fanatic_death.png`
- `characters/enemies/enemy_preacher_idle.png`
- `characters/enemies/enemy_preacher_hit.png`
- `characters/enemies/enemy_preacher_death.png`
- Marked vessels use the possession marker sprites in `Assets/Generated/possession/`; enemy silhouettes must stay readable with that ring/marker layered above them.

### Boss

- `characters/boss/boss_mother_couponella_idle.png`
- `characters/boss/boss_mother_couponella_hit.png`
- `characters/boss/boss_mother_couponella_death.png`
- `characters/boss/boss_attack_warning_marker_ready.png`

### Combat UI / HUD

- `ui/hud/ui_hp_frame_idle.png`
- `ui/hud/ui_hp_fill_active.png`
- `ui/hud/ui_possession_charge_frame_idle.png`
- `ui/hud/ui_possession_charge_fill_active.png`
- `ui/hud/ui_token_icon_idle.png`
- `ui/hud/ui_room_progress_frame_idle.png`
- `ui/hud/ui_room_progress_icon_active.png`
- `ui/hud/ui_auto_attack_indicator_active.png`
- `ui/hud/ui_auto_attack_indicator_disabled.png`

### Touch Controls

- `ui/controls/ui_joystick_base_idle.png`
- `ui/controls/ui_joystick_base_active.png`
- `ui/controls/ui_joystick_knob_idle.png`
- `ui/controls/ui_joystick_knob_active.png`

### Possession

- `possession/possession_marked_vessel_ring_ready.png`
- `possession/possession_ready_marker_ready.png`
- `possession/possession_active_overlay_active.png`
- `possession/possession_exit_marker_active.png`
- `vfx/p03/vfx_p03_explosion_active.png`

Important: `possession_exit_marker_active.png` is a non-damaging visual marker for default possession ending. It must not look like an explosion. The only damaging possession-exit explosion VFX is `vfx_p03_explosion_active.png`.

### Slot Machine / Rewards

- `slot_machine/body/slot_machine_body_idle.png`
- `slot_machine/body/slot_machine_body_active.png`
- `slot_machine/body/slot_reel_panel_idle.png`
- `slot_machine/symbols/slot_symbol_token_idle.png`
- `slot_machine/symbols/slot_symbol_candle_idle.png`
- `slot_machine/symbols/slot_symbol_seal_idle.png`
- `slot_machine/symbols/slot_symbol_eye_idle.png`
- `ui/rewards/ui_reward_card_frame_idle.png`
- `ui/rewards/ui_reward_card_frame_selected.png`
- `ui/rewards/ui_reward_card_frame_disabled.png`
- `ui/rewards/ui_reroll_icon_ready.png`
- `ui/rewards/ui_reroll_icon_disabled.png`
- `ui/rewards/reward_icon_standard_01.png`
- `ui/rewards/reward_icon_standard_02.png`
- `ui/rewards/reward_icon_p03_last_breath.png`
- `ui/rewards/reward_icon_standard_04.png`
- `ui/rewards/reward_icon_standard_05.png`
- `ui/rewards/reward_icon_standard_06.png`
- `ui/rewards/reward_icon_standard_07.png`
- `ui/rewards/reward_icon_standard_08.png`
- `ui/rewards/reward_icon_standard_09.png`
- `ui/rewards/reward_icon_standard_10.png`
- `ui/rewards/reward_icon_standard_11.png`
- `ui/rewards/reward_icon_standard_12.png`
- `ui/rewards/ui_cursed_deal_frame_active.png`
- `ui/rewards/ui_cursed_deal_icon_fanatical_credit.png`

The 12 standard reward icons are visual placeholders until exact reward definitions are assigned. `reward_icon_p03_last_breath.png` is reserved for the validated P03 explosion reward.

### Result Screens

- `ui/results/ui_victory_emblem_active.png`
- `ui/results/ui_defeat_emblem_active.png`
- `ui/results/ui_game_over_panel_bg_idle.png`
- `ui/results/ui_run_summary_frame_idle.png`

### Meta Unlock

- `ui/meta/ui_broken_seal_icon_idle.png`
- `ui/meta/ui_meta_unlock_panel_decoration_idle.png`

### Environment / Props

- `environment/arenas/arena_floor_corrupted_village_idle.png`
- `environment/props/prop_corrupted_village_house_idle.png`
- `environment/props/prop_altar_slot_machine_idle.png`
- `environment/props/prop_sacred_casino_candles_idle.png`
- `environment/props/prop_casino_religious_banner_idle.png`

### VFX

- `vfx/combat/vfx_hit_impact_active.png`
- `vfx/combat/vfx_enemy_death_puff_active.png`
- `vfx/possession/vfx_possession_tether_flash_active.png`
- `vfx/rewards/vfx_reward_reveal_sparkle_active.png`
- `vfx/rewards/vfx_cursed_deal_smoke_active.png`
- `vfx/p03/vfx_p03_explosion_active.png`

## 4. Asset Manifest

`STD_NEG` means the standard negative prompt defined at the top of this file:
`photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background`

### Characters - Player

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| player_body_idle | `Assets/Generated/characters/player/player_body_idle.png` | Default hero body, readable top-down/three-quarter silhouette. | Player gameplay prefab, SpriteRenderer. | idle | hooded broken-faith pilgrim hero with compact body and oversized wax-white mask, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Import as SpriteRenderer sprite, 128 PPU, pivot center-bottom. |
| player_body_hit | `Assets/Generated/characters/player/player_body_hit.png` | Player hit feedback state. | Player damage feedback, SpriteRenderer. | hit | hooded broken-faith pilgrim hero recoiling with crimson crack glow and wax-white mask intact, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Same bounds as idle to avoid visual popping. |
| player_body_death | `Assets/Generated/characters/player/player_body_death.png` | Player defeat/death visual. | Player death state, GameOver transition. | death | collapsed hooded pilgrim hero shell with broken halo chip and extinguished candle shape, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Keep silhouette simple; no gore detail needed. |
| player_empty_shell_idle | `Assets/Generated/characters/player/player_empty_shell_idle.png` | Empty hero shell left in arena while possession is active. | Possession system, Player shell prefab. | idle | hollow abandoned pilgrim body shell with dim wax-white face and old-gold seal crack, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | SpriteRenderer; must remain distinct from dead body. |
| player_possessed_overlay_active | `Assets/Generated/characters/player/player_possessed_overlay_active.png` | Overlay showing player is controlling a vessel. | Possession prefab, SpriteRenderer overlay. | active | floating void-violet halo flame overlay shaped like cracked casino seal around a controlled body, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Additive/overlay candidate; no baked enemy body. |

### Characters - Enemies

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| enemy_weak_cultist_idle | `Assets/Generated/characters/enemies/enemy_weak_cultist_idle.png` | Weak cultist enemy base. | Enemy prefab, Wave Director. | idle | scrawny candle-carrying cultist with crooked robe and coin-like halo, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | SpriteRenderer; leave outer silhouette clear for marker ring. |
| enemy_weak_cultist_hit | `Assets/Generated/characters/enemies/enemy_weak_cultist_hit.png` | Weak cultist hit state. | Enemy damage feedback. | hit | scrawny candle cultist flinching with wax splash and crimson impact crack, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Same footprint as idle. |
| enemy_weak_cultist_death | `Assets/Generated/characters/enemies/enemy_weak_cultist_death.png` | Weak cultist death state or last frame. | Enemy death feedback. | death | scrawny cultist dissolving into wax smoke and old-gold chips with body still recognizable, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Can be swapped before death puff VFX. |
| enemy_fast_fanatic_idle | `Assets/Generated/characters/enemies/enemy_fast_fanatic_idle.png` | Fast fanatic enemy base. | Enemy prefab, Wave Director. | idle | lanky sprinting fanatic with sharp triangular hood and casino-token kneepads, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Silhouette must differ from weak cultist in greyscale. |
| enemy_fast_fanatic_hit | `Assets/Generated/characters/enemies/enemy_fast_fanatic_hit.png` | Fast fanatic hit state. | Enemy damage feedback. | hit | lanky sprinting fanatic staggering sideways with broken old-gold token shards, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Same bounds as idle. |
| enemy_fast_fanatic_death | `Assets/Generated/characters/enemies/enemy_fast_fanatic_death.png` | Fast fanatic death state or last frame. | Enemy death feedback. | death | lanky fanatic collapsing into a streak of wax smoke and cracked crimson ribbon shapes, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Can be paired with death puff VFX. |
| enemy_preacher_idle | `Assets/Generated/characters/enemies/enemy_preacher_idle.png` | Ranged preacher enemy base. | Enemy prefab, Wave Director. | idle | squat preacher cultist with megaphone-shaped reliquary and blank prayer-ticket fan, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Keep blank papers free of letters or numbers. |
| enemy_preacher_hit | `Assets/Generated/characters/enemies/enemy_preacher_hit.png` | Preacher hit state. | Enemy damage feedback. | hit | squat preacher cultist knocked back with blank ticket fan scattering and crimson shock shape, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Same footprint as idle. |
| enemy_preacher_death | `Assets/Generated/characters/enemies/enemy_preacher_death.png` | Preacher death state or last frame. | Enemy death feedback. | death | squat preacher cultist crumpling into void-violet sermon smoke and blank ticket scraps, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | No readable ticket markings. |

### Boss

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| boss_mother_couponella_idle | `Assets/Generated/characters/boss/boss_mother_couponella_idle.png` | Mother Couponella boss base sprite. | Boss prefab, SpriteRenderer. | idle | enormous matriarch coupon priestess with blank coupon veil, slot-machine torso, candle crown, and clawed blessing pose, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x1024 | Yes | SpriteRenderer; pivot center-bottom; no readable coupon text. |
| boss_mother_couponella_hit | `Assets/Generated/characters/boss/boss_mother_couponella_hit.png` | Mother Couponella hit feedback. | Boss damage feedback. | hit | enormous coupon priestess boss recoiling as blank coupon veil tears and old-gold coins scatter, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x1024 | Yes | Match idle bounds as closely as possible. |
| boss_mother_couponella_death | `Assets/Generated/characters/boss/boss_mother_couponella_death.png` | Mother Couponella defeat sprite. | Boss defeat transition, victory flow. | death | enormous coupon priestess boss collapsing into broken slot-machine reliquary with extinguished candle crown, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x1024 | Yes | Avoid gore; keep large readable silhouette. |
| boss_attack_warning_marker_ready | `Assets/Generated/characters/boss/boss_attack_warning_marker_ready.png` | Floor warning marker for boss AOE/tape attack. | Boss attack telegraph prefab. | ready | circular crimson and old-gold warning sigil shaped like blank coupon tape spiral with broken halo edge, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | SpriteRenderer or UI world-space image; transparent center acceptable. |

### Combat UI / HUD

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| ui_hp_frame_idle | `Assets/Generated/ui/hud/ui_hp_frame_idle.png` | HP bar frame. | HUD prefab, Unity UI Image. | idle | horizontal cracked reliquary health bar frame with old-gold corners and wax-white bone inlay, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x512 | Yes | Use as sliced UI Image; no numbers or labels. |
| ui_hp_fill_active | `Assets/Generated/ui/hud/ui_hp_fill_active.png` | HP fill art. | HUD fill Image. | active | crimson liquid wax health bar fill with subtle old-gold flecks and clean rectangular silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x512 | Yes | Use as filled UI Image; avoid gradients that vanish on mobile. |
| ui_possession_charge_frame_idle | `Assets/Generated/ui/hud/ui_possession_charge_frame_idle.png` | Possession charge bar frame. | HUD prefab, Unity UI Image. | idle | horizontal cracked halo charge frame with void-violet inner groove and old-gold casino corners, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x512 | Yes | Sliced UI Image; no possession button behavior. |
| ui_possession_charge_fill_active | `Assets/Generated/ui/hud/ui_possession_charge_fill_active.png` | Possession charge fill. | HUD fill Image. | active | void-violet spirit wax charge fill with old-gold sparks and clean horizontal silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x512 | Yes | Filled Image; use color/alpha animation in Unity. |
| ui_token_icon_idle | `Assets/Generated/ui/hud/ui_token_icon_idle.png` | Token currency icon. | HUD, reward UI. | idle | old-gold casino token with cracked halo symbol and no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image; text count added in Unity UI. |
| ui_room_progress_frame_idle | `Assets/Generated/ui/hud/ui_room_progress_frame_idle.png` | Room progress frame. | HUD progress display. | idle | compact five-notch reliquary progress frame with blank sockets and old-gold cracked trim, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x512 | Yes | Coder can place icons/filled states; no room numbers baked in. |
| ui_room_progress_icon_active | `Assets/Generated/ui/hud/ui_room_progress_icon_active.png` | Active/cleared room progress token. | HUD progress display. | active | small old-gold cracked chapel-token marker with crimson inner glow and no number, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image repeated by code for progress slots. |
| ui_auto_attack_indicator_active | `Assets/Generated/ui/hud/ui_auto_attack_indicator_active.png` | Optional indicator that auto-attack is active. | HUD, Player combat feedback. | active | small targeting halo icon with old-gold reticle and wax-white spark, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image only; not a button. |
| ui_auto_attack_indicator_disabled | `Assets/Generated/ui/hud/ui_auto_attack_indicator_disabled.png` | Optional inactive auto-attack indicator. | HUD, Player combat feedback. | disabled | dim broken targeting halo icon with charcoal fill and faint wax-white spark, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image only; no manual attack button. |

### Touch Controls

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| ui_joystick_base_idle | `Assets/Generated/ui/controls/ui_joystick_base_idle.png` | Floating joystick base at rest. | Input UI prefab. | idle | translucent circular old-gold and charcoal joystick base shaped like cracked chapel window with blank center, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image under touch area; no labels. |
| ui_joystick_base_active | `Assets/Generated/ui/controls/ui_joystick_base_active.png` | Floating joystick base while touched. | Input UI prefab. | active | glowing circular old-gold and void-violet joystick base shaped like cracked chapel window with blank center, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image; Coder changes alpha/position by touch. |
| ui_joystick_knob_idle | `Assets/Generated/ui/controls/ui_joystick_knob_idle.png` | Floating joystick knob at rest. | Input UI prefab. | idle | small old-gold casino token joystick knob with cracked halo emblem and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image; no text or numbers. |
| ui_joystick_knob_active | `Assets/Generated/ui/controls/ui_joystick_knob_active.png` | Floating joystick knob while dragged. | Input UI prefab. | active | small glowing void-violet casino token joystick knob with old-gold cracked halo emblem and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image; no dash or action affordance. |

### Possession

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| possession_marked_vessel_ring_ready | `Assets/Generated/possession/possession_marked_vessel_ring_ready.png` | Ring showing valid marked vessel. | Possession system, enemy overlay. | ready | circular old-gold cracked halo ring with void-violet inner flame and open center for enemy body, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Overlay SpriteRenderer; center must be transparent. |
| possession_ready_marker_ready | `Assets/Generated/possession/possession_ready_marker_ready.png` | Marker that possession charge/proximity is ready. | Possession feedback, HUD/world marker. | ready | floating void-violet eye halo with old-gold spark and compact readable silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Not a button; use as feedback above/around vessel. |
| possession_active_overlay_active | `Assets/Generated/possession/possession_active_overlay_active.png` | Active possession aura over controlled vessel. | Possession prefab, controlled enemy overlay. | active | jagged void-violet spirit aura wrapped by old-gold broken halo fragments with transparent center, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Overlay SpriteRenderer; can pulse via script. |
| possession_exit_marker_active | `Assets/Generated/possession/possession_exit_marker_active.png` | Non-damaging default possession exit marker. | Possession exit feedback. | active | quiet fading wax-white spirit wisp with small broken halo fragments and no blast shape, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Must not be used as explosion or damage indicator. |

### Slot Machine / Rewards

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| slot_machine_body_idle | `Assets/Generated/slot_machine/body/slot_machine_body_idle.png` | Sacred demonic slot machine body at rest. | Slot machine presentation prefab. | idle | grotesque sacred casino slot machine altar with candle horns, blank display panels, old-gold sealed side shrine ornaments, and wax-drip side columns, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x1024 | Yes | SpriteRenderer or UI Image; no readable labels; passive auto-roll presentation only. |
| slot_machine_body_active | `Assets/Generated/slot_machine/body/slot_machine_body_active.png` | Slot machine during automatic post-combat roll. | Slot auto-roll presentation. | active | glowing grotesque sacred casino slot machine altar with void-violet reels and blank display panels, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x1024 | Yes | State swap during auto-roll; no manual interaction prompt. |
| slot_reel_panel_idle | `Assets/Generated/slot_machine/body/slot_reel_panel_idle.png` | Reusable reel panel frame. | Slot auto-roll UI. | idle | three-window slot reel panel with blank dark windows, old-gold cracked frame, and wax-white accents, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x512 | Yes | UI Image; symbols layered separately. |
| slot_symbol_token_idle | `Assets/Generated/slot_machine/symbols/slot_symbol_token_idle.png` | Reel token symbol. | Slot reel animation. | idle | old-gold cracked casino token symbol with halo notch and no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image/SpriteRenderer; no currency amount. |
| slot_symbol_candle_idle | `Assets/Generated/slot_machine/symbols/slot_symbol_candle_idle.png` | Reel candle symbol. | Slot reel animation. | idle | wax-white bent candle symbol with crimson flame and old-gold base, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image/SpriteRenderer. |
| slot_symbol_seal_idle | `Assets/Generated/slot_machine/symbols/slot_symbol_seal_idle.png` | Reel seal symbol. | Slot reel animation. | idle | broken sacred seal symbol shaped like cracked wax stamp and roulette chip with no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image/SpriteRenderer. |
| slot_symbol_eye_idle | `Assets/Generated/slot_machine/symbols/slot_symbol_eye_idle.png` | Reel eye symbol. | Slot reel animation. | idle | void-violet sacred eye symbol inside old-gold casino chip rim with no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image/SpriteRenderer. |
| ui_reward_card_frame_idle | `Assets/Generated/ui/rewards/ui_reward_card_frame_idle.png` | Standard reward card frame. | Reward choice UI. | idle | vertical reward card frame with old-gold chapel arch corners, charcoal interior, and blank wax-white text area space, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 768x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 768x1024 | Yes | UI Image; text and icon placed by Unity UI. |
| ui_reward_card_frame_selected | `Assets/Generated/ui/rewards/ui_reward_card_frame_selected.png` | Selected reward card frame. | Reward choice UI. | selected | vertical reward card frame glowing old-gold with void-violet chapel arch corners and blank interior, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 768x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 768x1024 | Yes | UI Image state; no baked selection label. |
| ui_reward_card_frame_disabled | `Assets/Generated/ui/rewards/ui_reward_card_frame_disabled.png` | Disabled/unavailable reward card frame. | Reward choice UI. | disabled | dim vertical reward card frame with cracked charcoal chapel arch and faded wax-white interior, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 768x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 768x1024 | Yes | UI Image state; use for disabled card presentation only. |
| ui_reroll_icon_ready | `Assets/Generated/ui/rewards/ui_reroll_icon_ready.png` | Reroll visual icon/button art. | Reward UI reroll control. | ready | circular old-gold reroll arrow icon made of broken halo fragments around a casino token, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Button Image; no text count baked in. |
| ui_reroll_icon_disabled | `Assets/Generated/ui/rewards/ui_reroll_icon_disabled.png` | Disabled reroll visual. | Reward UI reroll control. | disabled | dim circular reroll arrow icon made of cracked charcoal halo fragments with faint wax-white edge, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Button disabled Image; reroll count in Unity text. |
| reward_icon_standard_01 | `Assets/Generated/ui/rewards/reward_icon_standard_01.png` | Standard reward icon placeholder 01. | Reward cards. | none | old-gold crooked candle blessing icon with wax-white flame and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| reward_icon_standard_02 | `Assets/Generated/ui/rewards/reward_icon_standard_02.png` | Standard reward icon placeholder 02. | Reward cards. | none | crimson thorn dagger blessing icon wrapped in tiny old-gold token halo and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| reward_icon_p03_last_breath | `Assets/Generated/ui/rewards/reward_icon_p03_last_breath.png` | Standard reward icon for P03 Last Breath, the only possession-exit explosion source. | Reward cards, P03 effect UI. | none | void-violet final breath spirit icon bursting from a cracked old-gold vessel halo without damage numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Only icon tied to validated P03 explosion behavior. |
| reward_icon_standard_04 | `Assets/Generated/ui/rewards/reward_icon_standard_04.png` | Standard reward icon placeholder 04. | Reward cards. | none | cracked old-gold halo blessing icon with wax-white inner glow and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| reward_icon_standard_05 | `Assets/Generated/ui/rewards/reward_icon_standard_05.png` | Standard reward icon placeholder 05. | Reward cards. | none | wax-white heart reliquary icon inside old-gold casino chip rim and no letters, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| reward_icon_standard_06 | `Assets/Generated/ui/rewards/reward_icon_standard_06.png` | Standard reward icon placeholder 06. | Reward cards. | none | void-violet watching eye blessing icon with crimson tear and old-gold broken rim, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| reward_icon_standard_07 | `Assets/Generated/ui/rewards/reward_icon_standard_07.png` | Standard reward icon placeholder 07. | Reward cards. | none | black casino token blessing icon with old-gold rim, wax-white crack, and no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| reward_icon_standard_08 | `Assets/Generated/ui/rewards/reward_icon_standard_08.png` | Standard reward icon placeholder 08. | Reward cards. | none | thorny rosary loop icon made of tiny old-gold casino beads with crimson wax drop and no cross text, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| reward_icon_standard_09 | `Assets/Generated/ui/rewards/reward_icon_standard_09.png` | Standard reward icon placeholder 09. | Reward cards. | none | broken balance scale icon with old-gold pans shaped like casino chips and no markings, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| reward_icon_standard_10 | `Assets/Generated/ui/rewards/reward_icon_standard_10.png` | Standard reward icon placeholder 10. | Reward cards. | none | incense burner icon shaped like tiny slot altar with void-violet smoke and blank face, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| reward_icon_standard_11 | `Assets/Generated/ui/rewards/reward_icon_standard_11.png` | Standard reward icon placeholder 11. | Reward cards. | none | wax-white marked palm blessing icon holding old-gold token with no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| reward_icon_standard_12 | `Assets/Generated/ui/rewards/reward_icon_standard_12.png` | Standard reward icon placeholder 12. | Reward cards. | none | sealed chapel gate icon with old-gold lock and void-violet crack, no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Placeholder; does not define mechanics. |
| ui_cursed_deal_frame_active | `Assets/Generated/ui/rewards/ui_cursed_deal_frame_active.png` | Cursed deal card/popup frame. | Reward UI, cursed deal stop 2. | active | vertical cursed deal frame with crimson wax cracks, void-violet smoke corners, old-gold chapel arch, and blank interior, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 768x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 768x1024 | Yes | UI Image; cursed deal name/effect added via Unity text. |
| ui_cursed_deal_icon_fanatical_credit | `Assets/Generated/ui/rewards/ui_cursed_deal_icon_fanatical_credit.png` | Icon for Fanatical Credit cursed deal. | Reward UI, cursed deal offer. | none | cursed old-gold credit token chained to crimson wax heart with blank face and no numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Icon only; +1 Attack and -1 Max HP text must be Unity UI. |

### Result Screens

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| ui_victory_emblem_active | `Assets/Generated/ui/results/ui_victory_emblem_active.png` | Victory emblem after boss defeat. | GameOver/Victory UI. | active | old-gold broken seal victory emblem over wax-white candleburst with crimson cult cracks, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG emblem readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image; victory text added in Unity. |
| ui_defeat_emblem_active | `Assets/Generated/ui/results/ui_defeat_emblem_active.png` | Defeat emblem. | GameOver UI. | active | dim cracked halo defeat emblem with extinguished candle and void-violet smoke, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG emblem readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image; defeat text added in Unity. |
| ui_game_over_panel_bg_idle | `Assets/Generated/ui/results/ui_game_over_panel_bg_idle.png` | Game over panel background decoration. | GameOver scene UI. | idle | large dark chapel-casino panel background with blank parchment center and old-gold cracked border, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x1024 | Yes | Sliced or full UI Image; all summary text is Unity UI. |
| ui_run_summary_frame_idle | `Assets/Generated/ui/results/ui_run_summary_frame_idle.png` | Decorative frame for run summary stats. | GameOver scene UI. | idle | horizontal run summary frame with old-gold casino chapel corners, blank sockets, and wax-white trim, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x512 | Yes | UI Image; numbers/labels added in Unity. |

### Meta Unlock

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| ui_broken_seal_icon_idle | `Assets/Generated/ui/meta/ui_broken_seal_icon_idle.png` | First meta unlock icon: Broken Seal. | MainMenu/meta unlock UI. | idle | broken old-gold sacred seal icon with void-violet crack and wax-white glow, no letters or numbers, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG icon readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI Image; unlock name/effect text in Unity. |
| ui_meta_unlock_panel_decoration_idle | `Assets/Generated/ui/meta/ui_meta_unlock_panel_decoration_idle.png` | Meta unlock panel decoration. | MainMenu/meta unlock UI. | idle | compact chapel-casino unlock panel decoration with blank center, cracked old-gold border, and candle side ornaments, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x512 | Yes | UI Image; no unlock copy baked in. |

### Environment / Props

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| arena_floor_corrupted_village_idle | `Assets/Generated/environment/arenas/arena_floor_corrupted_village_idle.png` | Simple arena floor/background for five combat rooms. | Game scene background. | idle | circular corrupted village arena floor patch with cracked chapel stones, faint casino-chip geometry, and muddy charcoal edges, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 1024x1024 | Yes | SpriteRenderer background; can be scaled, avoid busy detail under enemies. |
| prop_corrupted_village_house_idle | `Assets/Generated/environment/props/prop_corrupted_village_house_idle.png` | Corrupted village background prop. | Room decoration prefab. | idle | crooked rotting village chapel-house prop with blank hanging sign and old-gold candle stains, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | SpriteRenderer; sign must remain unreadable/blank. |
| prop_altar_slot_machine_idle | `Assets/Generated/environment/props/prop_altar_slot_machine_idle.png` | Non-interactive altar slot-machine prop for arena dressing if needed. | Room decoration prefab. | idle | small broken altar slot-machine prop with blank reel windows and melted candles, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Decorative only; not the reward machine interaction. |
| prop_sacred_casino_candles_idle | `Assets/Generated/environment/props/prop_sacred_casino_candles_idle.png` | Casino-religious decorative candles. | Room decoration prefab. | idle | cluster of wax-white altar candles around old-gold casino chips with crimson wax drips, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | SpriteRenderer prop; keep low visual noise. |
| prop_casino_religious_banner_idle | `Assets/Generated/environment/props/prop_casino_religious_banner_idle.png` | Decorative banner without readable symbols. | Room decoration prefab. | idle | torn chapel banner with abstract casino-chip pattern, no letters, no numbers, old-gold trim and crimson cloth, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Decorative prop; no readable prayers or signage. |

### VFX

| Asset ID | File Path | Purpose | Used By | Required States | Prompt | Negative Prompt | Size | Transparency | Unity Note |
|---|---|---|---|---|---|---|---|---|---|
| vfx_hit_impact_active | `Assets/Generated/vfx/combat/vfx_hit_impact_active.png` | Generic hit impact sprite. | Combat VFX prefab. | active | compact crimson wax impact burst with old-gold chip shards and strong radial silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | SpriteRenderer VFX; Coder can scale/fade. |
| vfx_enemy_death_puff_active | `Assets/Generated/vfx/combat/vfx_enemy_death_puff_active.png` | Enemy death puff. | Enemy death VFX prefab. | active | small charcoal wax smoke puff with old-gold flecks and void-violet inner curl, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | SpriteRenderer VFX; not used for P03 explosion. |
| vfx_possession_tether_flash_active | `Assets/Generated/vfx/possession/vfx_possession_tether_flash_active.png` | Possession tether/flash between player and vessel. | Possession VFX prefab. | active | arcing void-violet spirit tether with old-gold broken halo sparks and clean readable curve, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Can be stretched/rotated by script or used as short flash. |
| vfx_reward_reveal_sparkle_active | `Assets/Generated/vfx/rewards/vfx_reward_reveal_sparkle_active.png` | Reward reveal sparkle. | Reward UI VFX prefab. | active | old-gold candle sparkle burst with wax-white glints and tiny void-violet cracks, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI overlay or SpriteRenderer VFX. |
| vfx_cursed_deal_smoke_active | `Assets/Generated/vfx/rewards/vfx_cursed_deal_smoke_active.png` | Cursed deal smoke. | Cursed deal UI VFX prefab. | active | curling crimson and void-violet cursed smoke with old-gold ember flecks and compact silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | UI overlay; no readable curse symbols. |
| vfx_p03_explosion_active | `Assets/Generated/vfx/p03/vfx_p03_explosion_active.png` | P03 Last Breath damaging possession-exit explosion. | P03 reward effect VFX prefab. | active | compact void-violet and crimson spirit explosion from cracked old-gold vessel halo with enemy-only blast silhouette, stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 512x512 source PNG VFX sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges | STD_NEG | 512x512 | Yes | Only use for P03; default possession exit must not call this VFX. |

## 5. Image Generation Prompt Pack

Prompt formula for every asset:

`[subject], [art style], [color palette], [mood], [technical spec], game asset, transparent background, no text, clean edges`

Global art style:

`stylized dark cartoon with grotesque religious-casino motifs`

Global color palette:

`charcoal old gold wax white crimson void violet palette`

Global mood:

`dark whimsical cult roguelite mood`

Global technical specs:

- Character/enemy/VFX/icon sprites: `512x512 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette`.
- Boss sprites: `1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette`.
- Card frames: `768x1024 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette`.
- Wide UI frames/bars: `1024x512 source PNG UI sprite readable at 64x64 with bold charcoal outline and centered silhouette`.
- Arena/background sprites: `1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette`.

Use the `Prompt` column in the asset manifest as the per-asset generation prompt pack. Every prompt already follows the formula and includes `game asset, transparent background, no text, clean edges`.

Use this negative prompt for every image:

`photorealistic, 3D render, blurry, text, watermark, extra limbs, deformed, low quality, noisy background`

Generation QA checklist:

- Source PNG is at least 512x512.
- Background is transparent, not black, white, grey, or noisy.
- No readable text, letters, digits, watermark, or pseudo-writing.
- Silhouette remains recognizable at 64x64 on a phone screen.
- Same palette, outline weight, and visual density as the rest of this pack.
- Player, enemy, and boss silhouettes remain distinguishable in greyscale.
- UI sprites leave space for Unity text and icons without baking labels.
- Default possession exit visual does not resemble an explosion.
- P03 explosion is visually stronger and clearly separate from default possession exit.

## 6. Coder Handoff Notes

Import folders:

- Import everything under `Assets/Generated/` once the PNGs are generated.
- Do not import `_MANIFESTS/` as gameplay content; it is documentation only.
- Use `characters/`, `environment/`, `possession/`, and `vfx/` mostly as SpriteRenderer sources.
- Use `ui/`, `slot_machine/`, and some `vfx/rewards/` assets mostly as Unity UI Images, depending on scene implementation.

Sprites that become Unity UI Images:

- `ui/hud/*`
- `ui/controls/*`
- `ui/rewards/*`
- `ui/results/*`
- `ui/meta/*`
- `slot_machine/body/slot_reel_panel_idle.png` if the reward flow is Canvas-based.
- `slot_machine/symbols/*` if the auto-roll is Canvas-based.

Sprites that become SpriteRenderers:

- `characters/player/*`
- `characters/enemies/*`
- `characters/boss/*`
- `possession/*` when used as world overlays.
- `environment/arenas/*`
- `environment/props/*`
- `vfx/combat/*`
- `vfx/possession/*`
- `vfx/p03/*`
- `slot_machine/body/slot_machine_body_idle.png` and `slot_machine/body/slot_machine_body_active.png` if the machine appears in-world.

Placeholder assets:

- `reward_icon_standard_01.png`
- `reward_icon_standard_02.png`
- `reward_icon_standard_04.png`
- `reward_icon_standard_05.png`
- `reward_icon_standard_06.png`
- `reward_icon_standard_07.png`
- `reward_icon_standard_08.png`
- `reward_icon_standard_09.png`
- `reward_icon_standard_10.png`
- `reward_icon_standard_11.png`
- `reward_icon_standard_12.png`

These placeholders represent 11 of the 12 standard reward card icon slots and must not be treated as final mechanics. `reward_icon_p03_last_breath.png` is the only standard reward icon in this manifest tied to a validated named effect.

Text that must be created in Unity UI, never baked into PNGs:

- Game title.
- HP values.
- Possession charge numbers or labels.
- Token counts.
- Room progress numbers.
- Reward card names.
- Reward card descriptions.
- Reroll count.
- Cursed deal name: "Фанатичный кредит".
- Cursed deal effect: `+1 Attack, -1 Max HP`.
- Result screen headings and run summary values.
- Meta unlock name: "Broken Seal".
- Any localization.

Assets needing scripts later:

- Floating joystick base/knob needs input positioning, drag, release, alpha/state changes.
- HP and possession bars need fill control.
- Room progress frame/icon needs state updates.
- Auto-attack indicator needs active/disabled state updates if UX keeps it.
- Marked vessel ring and ready marker need possession eligibility/state logic.
- Possession active overlay and tether flash need possession lifecycle logic.
- Default possession exit marker needs non-damaging exit event logic.
- P03 explosion VFX needs P03-only trigger logic, damage application, VFX cap handling, and separation from default possession exit.
- Slot machine body/reel/symbols need automatic post-combat roll presentation.
- Reward cards need selection, disabled, selected, and reroll state logic.
- Cursed deal frame/icon needs stop-2-only presentation logic.
- Result screen frames/emblems need win/defeat routing.
- Broken Seal icon/panel needs first meta unlock state logic.

Assets needing prefabs later:

- Player body prefab.
- Empty shell prefab.
- Weak cultist prefab.
- Fast fanatic prefab.
- Preacher prefab.
- Mother Couponella boss prefab.
- Boss attack warning prefab.
- HUD prefab.
- Floating joystick prefab.
- Possession marker prefab.
- Possession active overlay prefab.
- Possession exit marker prefab.
- P03 explosion VFX prefab.
- Slot machine reward presentation prefab.
- Reward card prefab.
- Cursed deal offer prefab.
- Game over/result screen prefab or scene UI object.
- Broken Seal meta unlock panel prefab.
- Arena floor/background prefab.
- Environment prop prefabs.
- Combat hit/death VFX prefabs.

Unity import recommendations:

- Texture Type: `Sprite (2D and UI)`.
- Sprite Mode: `Single`.
- Alpha Is Transparency: enabled.
- Generate Mip Maps: disabled.
- Filter Mode: `Bilinear` for stylized cartoon art unless project testing favors `Point`.
- Compression: `None` or high-quality for UI; normal compression acceptable for gameplay sprites after mobile readability test.
- Pixels Per Unit: `128` for gameplay/world sprites unless architecture sets a different global PPU before import.
- Pivot: center-bottom for characters and props; center for icons, VFX, markers, and UI.
- UI frames should be prepared for slicing in Sprite Editor where useful.
- Keep generated source PNGs under `Assets/Generated/`; do not move them into `Assets/Scripts/` or `Assets/Prefabs/`.

Implementation guardrails:

- Default possession exit destroys the vessel without explosion VFX, area damage, extra token, or pickup.
- `vfx_p03_explosion_active.png` is only for P03 Last Breath.
- There is no manual possession button art in this pack.
- There is no dash button art in this pack.
- There is no manual machine interaction or spin button art in this pack.
- There are no pet/helper assets in this pack.
