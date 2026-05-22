# Game Objects Catalog

Source: `Assets/Generated/_MANIFESTS/asset_prompts.csv`, `Assets/Generated/_MANIFESTS/mvp_sprite_asset_pack.md`, `Assets/Generated/_MANIFESTS/prompts_by_folder.md`, and all sibling `.prompt.txt` files under `Assets/Generated/`.
Scope: manifest catalog only. This document does not add gameplay assets and does not authorize PNG generation by itself.
Generation status for every object: `ready_for_generation_review`; no PNG sprites are generated in this pass.

## Player

### player_body

object_id: player_body
display_name: Player Body
category: Characters - Player
folder: Assets/Generated/characters/player
target_png_path:
- player_body_idle: Assets/Generated/characters/player/player_body_idle.png
- player_body_hit: Assets/Generated/characters/player/player_body_hit.png
- player_body_death: Assets/Generated/characters/player/player_body_death.png
prompt_file_path:
- player_body_idle: Assets/Generated/characters/player/player_body_idle.prompt.txt
- player_body_hit: Assets/Generated/characters/player/player_body_hit.prompt.txt
- player_body_death: Assets/Generated/characters/player/player_body_death.prompt.txt
gameplay_role: player_body_idle: Default hero body, readable top-down/three-quarter silhouette. player_body_hit: Player hit feedback state. player_body_death: Player defeat/death visual.
visual_description:
- player_body_idle: hooded broken-faith pilgrim hero with compact body and oversized wax-white mask
- player_body_hit: hooded broken-faith pilgrim hero recoiling with crimson crack glow and wax-white mask intact
- player_body_death: collapsed hooded pilgrim hero shell with broken halo chip and extinguished candle shape
style_notes: Compact readable player silhouette; preserve same footprint across related states; overlays stay separate from base bodies.
required_states:
- player_body_idle: idle
- player_body_hit: hit
- player_body_death: death
unity_usage: player_body_idle: Used by Player gameplay prefab, SpriteRenderer. Unity note: Import as SpriteRenderer sprite, 128 PPU, pivot center-bottom. player_body_hit: Used by Player damage feedback, SpriteRenderer. Unity note: Same bounds as idle to avoid visual popping. player_body_death: Used by Player death state, GameOver transition. Unity note: Keep silhouette simple; no gore detail needed.
dependencies: Player controller, HP state, damage feedback, defeat routing.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, enemy silhouette confusion, gore detail
generation_status: ready_for_generation_review; PNG not generated.

### player_empty_shell

object_id: player_empty_shell
display_name: Player Empty Shell
category: Characters - Player
folder: Assets/Generated/characters/player
target_png_path:
- player_empty_shell_idle: Assets/Generated/characters/player/player_empty_shell_idle.png
prompt_file_path:
- player_empty_shell_idle: Assets/Generated/characters/player/player_empty_shell_idle.prompt.txt
gameplay_role: player_empty_shell_idle: Empty hero shell left in arena while possession is active.
visual_description:
- player_empty_shell_idle: hollow abandoned pilgrim body shell with dim wax-white face and old-gold seal crack
style_notes: Compact readable player silhouette; preserve same footprint across related states; overlays stay separate from base bodies.
required_states:
- player_empty_shell_idle: idle
unity_usage: player_empty_shell_idle: Used by Possession system, Player shell prefab. Unity note: SpriteRenderer; must remain distinct from dead body.
dependencies: Possession lifecycle, shell protection, player restore logic.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, explosion language, corpse gore
generation_status: ready_for_generation_review; PNG not generated.

### player_possessed_overlay

object_id: player_possessed_overlay
display_name: Player Possessed Overlay
category: Characters - Player
folder: Assets/Generated/characters/player
target_png_path:
- player_possessed_overlay_active: Assets/Generated/characters/player/player_possessed_overlay_active.png
prompt_file_path:
- player_possessed_overlay_active: Assets/Generated/characters/player/player_possessed_overlay_active.prompt.txt
gameplay_role: player_possessed_overlay_active: Overlay showing player is controlling a vessel.
visual_description:
- player_possessed_overlay_active: floating void-violet halo flame overlay shaped like cracked casino seal around a controlled body
style_notes: Compact readable player silhouette; preserve same footprint across related states; overlays stay separate from base bodies.
required_states:
- player_possessed_overlay_active: active
unity_usage: player_possessed_overlay_active: Used by Possession prefab, SpriteRenderer overlay. Unity note: Additive/overlay candidate; no baked enemy body.
dependencies: Possession active state, controlled body sorting layer.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, baked character body, manual possession button cues
generation_status: ready_for_generation_review; PNG not generated.

## Enemies

### enemy_weak_cultist

object_id: enemy_weak_cultist
display_name: Weak Cultist
category: Characters - Enemies
folder: Assets/Generated/characters/enemies
target_png_path:
- enemy_weak_cultist_idle: Assets/Generated/characters/enemies/enemy_weak_cultist_idle.png
- enemy_weak_cultist_hit: Assets/Generated/characters/enemies/enemy_weak_cultist_hit.png
- enemy_weak_cultist_death: Assets/Generated/characters/enemies/enemy_weak_cultist_death.png
prompt_file_path:
- enemy_weak_cultist_idle: Assets/Generated/characters/enemies/enemy_weak_cultist_idle.prompt.txt
- enemy_weak_cultist_hit: Assets/Generated/characters/enemies/enemy_weak_cultist_hit.prompt.txt
- enemy_weak_cultist_death: Assets/Generated/characters/enemies/enemy_weak_cultist_death.prompt.txt
gameplay_role: enemy_weak_cultist_idle: Weak cultist enemy base. enemy_weak_cultist_hit: Weak cultist hit state. enemy_weak_cultist_death: Weak cultist death state or last frame.
visual_description:
- enemy_weak_cultist_idle: scrawny candle-carrying cultist with crooked robe and coin-like halo
- enemy_weak_cultist_hit: scrawny candle cultist flinching with wax splash and crimson impact crack
- enemy_weak_cultist_death: scrawny cultist dissolving into wax smoke and old-gold chips with body still recognizable
style_notes: Enemy silhouette must be readable in greyscale and distinct from player, boss, and other enemy archetypes.
required_states:
- enemy_weak_cultist_idle: idle
- enemy_weak_cultist_hit: hit
- enemy_weak_cultist_death: death
unity_usage: enemy_weak_cultist_idle: Used by Enemy prefab, Wave Director. Unity note: SpriteRenderer; leave outer silhouette clear for marker ring. enemy_weak_cultist_hit: Used by Enemy damage feedback. Unity note: Same footprint as idle. enemy_weak_cultist_death: Used by Enemy death feedback. Unity note: Can be swapped before death puff VFX.
dependencies: Enemy controller, wave director, damage feedback, possession marker overlay.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, boss scale, post-MVP variants
generation_status: ready_for_generation_review; PNG not generated.

### enemy_fast_fanatic

object_id: enemy_fast_fanatic
display_name: Fast Fanatic
category: Characters - Enemies
folder: Assets/Generated/characters/enemies
target_png_path:
- enemy_fast_fanatic_idle: Assets/Generated/characters/enemies/enemy_fast_fanatic_idle.png
- enemy_fast_fanatic_hit: Assets/Generated/characters/enemies/enemy_fast_fanatic_hit.png
- enemy_fast_fanatic_death: Assets/Generated/characters/enemies/enemy_fast_fanatic_death.png
prompt_file_path:
- enemy_fast_fanatic_idle: Assets/Generated/characters/enemies/enemy_fast_fanatic_idle.prompt.txt
- enemy_fast_fanatic_hit: Assets/Generated/characters/enemies/enemy_fast_fanatic_hit.prompt.txt
- enemy_fast_fanatic_death: Assets/Generated/characters/enemies/enemy_fast_fanatic_death.prompt.txt
gameplay_role: enemy_fast_fanatic_idle: Fast fanatic enemy base. enemy_fast_fanatic_hit: Fast fanatic hit state. enemy_fast_fanatic_death: Fast fanatic death state or last frame.
visual_description:
- enemy_fast_fanatic_idle: lanky sprinting fanatic with sharp triangular hood and casino-token kneepads
- enemy_fast_fanatic_hit: lanky sprinting fanatic staggering sideways with broken old-gold token shards
- enemy_fast_fanatic_death: lanky fanatic collapsing into a streak of wax smoke and cracked crimson ribbon shapes
style_notes: Enemy silhouette must be readable in greyscale and distinct from player, boss, and other enemy archetypes.
required_states:
- enemy_fast_fanatic_idle: idle
- enemy_fast_fanatic_hit: hit
- enemy_fast_fanatic_death: death
unity_usage: enemy_fast_fanatic_idle: Used by Enemy prefab, Wave Director. Unity note: Silhouette must differ from weak cultist in greyscale. enemy_fast_fanatic_hit: Used by Enemy damage feedback. Unity note: Same bounds as idle. enemy_fast_fanatic_death: Used by Enemy death feedback. Unity note: Can be paired with death puff VFX.
dependencies: Enemy controller, rusher behavior, damage feedback, possession marker overlay.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, weak cultist silhouette duplication, post-MVP variants
generation_status: ready_for_generation_review; PNG not generated.

### enemy_preacher

object_id: enemy_preacher
display_name: Preacher
category: Characters - Enemies
folder: Assets/Generated/characters/enemies
target_png_path:
- enemy_preacher_idle: Assets/Generated/characters/enemies/enemy_preacher_idle.png
- enemy_preacher_hit: Assets/Generated/characters/enemies/enemy_preacher_hit.png
- enemy_preacher_death: Assets/Generated/characters/enemies/enemy_preacher_death.png
prompt_file_path:
- enemy_preacher_idle: Assets/Generated/characters/enemies/enemy_preacher_idle.prompt.txt
- enemy_preacher_hit: Assets/Generated/characters/enemies/enemy_preacher_hit.prompt.txt
- enemy_preacher_death: Assets/Generated/characters/enemies/enemy_preacher_death.prompt.txt
gameplay_role: enemy_preacher_idle: Ranged preacher enemy base. enemy_preacher_hit: Preacher hit state. enemy_preacher_death: Preacher death state or last frame.
visual_description:
- enemy_preacher_idle: squat preacher cultist with megaphone-shaped reliquary and blank prayer-ticket fan
- enemy_preacher_hit: squat preacher cultist knocked back with blank ticket fan scattering and crimson shock shape
- enemy_preacher_death: squat preacher cultist crumpling into void-violet sermon smoke and blank ticket scraps
style_notes: Enemy silhouette must be readable in greyscale and distinct from player, boss, and other enemy archetypes.
required_states:
- enemy_preacher_idle: idle
- enemy_preacher_hit: hit
- enemy_preacher_death: death
unity_usage: enemy_preacher_idle: Used by Enemy prefab, Wave Director. Unity note: Keep blank papers free of letters or numbers. enemy_preacher_hit: Used by Enemy damage feedback. Unity note: Same footprint as idle. enemy_preacher_death: Used by Enemy death feedback. Unity note: No readable ticket markings.
dependencies: Ranged enemy controller, projectile/telegraph logic, damage feedback.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, readable sermon/ticket text, post-MVP variants
generation_status: ready_for_generation_review; PNG not generated.

## Boss

### boss_mother_couponella

object_id: boss_mother_couponella
display_name: Mother Couponella
category: Boss
folder: Assets/Generated/characters/boss
target_png_path:
- boss_mother_couponella_idle: Assets/Generated/characters/boss/boss_mother_couponella_idle.png
- boss_mother_couponella_hit: Assets/Generated/characters/boss/boss_mother_couponella_hit.png
- boss_mother_couponella_death: Assets/Generated/characters/boss/boss_mother_couponella_death.png
prompt_file_path:
- boss_mother_couponella_idle: Assets/Generated/characters/boss/boss_mother_couponella_idle.prompt.txt
- boss_mother_couponella_hit: Assets/Generated/characters/boss/boss_mother_couponella_hit.prompt.txt
- boss_mother_couponella_death: Assets/Generated/characters/boss/boss_mother_couponella_death.prompt.txt
gameplay_role: boss_mother_couponella_idle: Mother Couponella boss base sprite. boss_mother_couponella_hit: Mother Couponella hit feedback. boss_mother_couponella_death: Mother Couponella defeat sprite.
visual_description:
- boss_mother_couponella_idle: enormous matriarch coupon priestess with blank coupon veil, slot-machine torso, candle crown, and clawed blessing pose
- boss_mother_couponella_hit: enormous coupon priestess boss recoiling as blank coupon veil tears and old-gold coins scatter
- boss_mother_couponella_death: enormous coupon priestess boss collapsing into broken slot-machine reliquary with extinguished candle crown
style_notes: Boss art must be larger, heavier, and more ceremonial than standard enemies while staying readable at mobile scale.
required_states:
- boss_mother_couponella_idle: idle
- boss_mother_couponella_hit: hit
- boss_mother_couponella_death: death
unity_usage: boss_mother_couponella_idle: Used by Boss prefab, SpriteRenderer. Unity note: SpriteRenderer; pivot center-bottom; no readable coupon text. boss_mother_couponella_hit: Used by Boss damage feedback. Unity note: Match idle bounds as closely as possible. boss_mother_couponella_death: Used by Boss defeat transition, victory flow. Unity note: Avoid gore; keep large readable silhouette.
dependencies: Boss controller, boss HP, victory routing, summon/AOE systems.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, readable coupon text, non-MVP bosses, gore
generation_status: ready_for_generation_review; PNG not generated.

### boss_attack_warning_marker

object_id: boss_attack_warning_marker
display_name: Boss Attack Warning Marker
category: Boss
folder: Assets/Generated/characters/boss
target_png_path:
- boss_attack_warning_marker_ready: Assets/Generated/characters/boss/boss_attack_warning_marker_ready.png
prompt_file_path:
- boss_attack_warning_marker_ready: Assets/Generated/characters/boss/boss_attack_warning_marker_ready.prompt.txt
gameplay_role: boss_attack_warning_marker_ready: Floor warning marker for boss AOE/tape attack.
visual_description:
- boss_attack_warning_marker_ready: circular crimson and old-gold warning sigil shaped like blank coupon tape spiral with broken halo edge
style_notes: Boss art must be larger, heavier, and more ceremonial than standard enemies while staying readable at mobile scale.
required_states:
- boss_attack_warning_marker_ready: ready
unity_usage: boss_attack_warning_marker_ready: Used by Boss attack telegraph prefab. Unity note: SpriteRenderer or UI world-space image; transparent center acceptable.
dependencies: Boss attack timing and telegraph sorting layer.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, letters, numbers, reward icon language
generation_status: ready_for_generation_review; PNG not generated.

## Possession

### possession_marked_vessel_ring

object_id: possession_marked_vessel_ring
display_name: Marked Vessel Ring
category: Possession
folder: Assets/Generated/possession
target_png_path:
- possession_marked_vessel_ring_ready: Assets/Generated/possession/possession_marked_vessel_ring_ready.png
prompt_file_path:
- possession_marked_vessel_ring_ready: Assets/Generated/possession/possession_marked_vessel_ring_ready.prompt.txt
gameplay_role: possession_marked_vessel_ring_ready: Ring showing valid marked vessel.
visual_description:
- possession_marked_vessel_ring_ready: circular old-gold cracked halo ring with void-violet inner flame and open center for enemy body
style_notes: Use void violet and old gold as the possession identity; no possession art may imply a manual button.
required_states:
- possession_marked_vessel_ring_ready: ready
unity_usage: possession_marked_vessel_ring_ready: Used by Possession system, enemy overlay. Unity note: Overlay SpriteRenderer; center must be transparent.
dependencies: Marked vessel selection and enemy attachment point.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, button shape, manual possession cue
generation_status: ready_for_generation_review; PNG not generated.

### possession_ready_marker

object_id: possession_ready_marker
display_name: Possession Ready Marker
category: Possession
folder: Assets/Generated/possession
target_png_path:
- possession_ready_marker_ready: Assets/Generated/possession/possession_ready_marker_ready.png
prompt_file_path:
- possession_ready_marker_ready: Assets/Generated/possession/possession_ready_marker_ready.prompt.txt
gameplay_role: possession_ready_marker_ready: Marker that possession charge/proximity is ready.
visual_description:
- possession_ready_marker_ready: floating void-violet eye halo with old-gold spark and compact readable silhouette
style_notes: Use void violet and old gold as the possession identity; no possession art may imply a manual button.
required_states:
- possession_ready_marker_ready: ready
unity_usage: possession_ready_marker_ready: Used by Possession feedback, HUD/world marker. Unity note: Not a button; use as feedback above/around vessel.
dependencies: Possession charge, proximity check, 0.35s auto-trigger delay.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, button frame, tap prompt, manual possession cue
generation_status: ready_for_generation_review; PNG not generated.

### possession_active_overlay

object_id: possession_active_overlay
display_name: Possession Active Overlay
category: Possession
folder: Assets/Generated/possession
target_png_path:
- possession_active_overlay_active: Assets/Generated/possession/possession_active_overlay_active.png
prompt_file_path:
- possession_active_overlay_active: Assets/Generated/possession/possession_active_overlay_active.prompt.txt
gameplay_role: possession_active_overlay_active: Active possession aura over controlled vessel.
visual_description:
- possession_active_overlay_active: jagged void-violet spirit aura wrapped by old-gold broken halo fragments with transparent center
style_notes: Use void violet and old gold as the possession identity; no possession art may imply a manual button.
required_states:
- possession_active_overlay_active: active
unity_usage: possession_active_overlay_active: Used by Possession prefab, controlled enemy overlay. Unity note: Overlay SpriteRenderer; can pulse via script.
dependencies: Possession ownership state and controlled vessel sorting layer.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, baked enemy body, explosion shape
generation_status: ready_for_generation_review; PNG not generated.

### possession_exit_marker

object_id: possession_exit_marker
display_name: Possession Exit Marker
category: Possession
folder: Assets/Generated/possession
target_png_path:
- possession_exit_marker_active: Assets/Generated/possession/possession_exit_marker_active.png
prompt_file_path:
- possession_exit_marker_active: Assets/Generated/possession/possession_exit_marker_active.prompt.txt
gameplay_role: possession_exit_marker_active: Non-damaging default possession exit marker.
visual_description:
- possession_exit_marker_active: quiet fading wax-white spirit wisp with small broken halo fragments and no blast shape
style_notes: Use void violet and old gold as the possession identity; no possession art may imply a manual button.
required_states:
- possession_exit_marker_active: active
unity_usage: possession_exit_marker_active: Used by Possession exit feedback. Unity note: Must not be used as explosion or damage indicator.
dependencies: Possession end event; separate from P03 explosion.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, radial blast, explosion, damage indicator, extra token pickup
generation_status: ready_for_generation_review; PNG not generated.

## Slot Machine

### slot_machine_body

object_id: slot_machine_body
display_name: Sacred Slot Machine Body
category: Slot Machine / Rewards
folder: Assets/Generated/slot_machine/body
target_png_path:
- slot_machine_body_idle: Assets/Generated/slot_machine/body/slot_machine_body_idle.png
- slot_machine_body_active: Assets/Generated/slot_machine/body/slot_machine_body_active.png
prompt_file_path:
- slot_machine_body_idle: Assets/Generated/slot_machine/body/slot_machine_body_idle.prompt.txt
- slot_machine_body_active: Assets/Generated/slot_machine/body/slot_machine_body_active.prompt.txt
gameplay_role: slot_machine_body_idle: Sacred demonic slot machine body at rest. slot_machine_body_active: Slot machine during automatic post-combat roll.
visual_description:
- slot_machine_body_idle: grotesque sacred casino slot machine altar with candle horns, blank display panels, old-gold sealed side shrine ornaments, and wax-drip side columns
- slot_machine_body_active: glowing grotesque sacred casino slot machine altar with void-violet reels and blank display panels
style_notes: Automatic sacred casino reward presentation only; no manual spin affordance or readable slot labels.
required_states:
- slot_machine_body_idle: idle
- slot_machine_body_active: active
unity_usage: slot_machine_body_idle: Used by Slot machine presentation prefab. Unity note: SpriteRenderer or UI Image; no readable labels; passive auto-roll presentation only. slot_machine_body_active: Used by Slot auto-roll presentation. Unity note: State swap during auto-roll; no manual interaction prompt.
dependencies: Post-combat auto-roll flow, reel panel, symbols, reward cards.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, lever, handle, button, manual spin affordance, walk-up interaction
generation_status: ready_for_generation_review; PNG not generated.

### slot_reel_panel

object_id: slot_reel_panel
display_name: Slot Reel Panel
category: Slot Machine / Rewards
folder: Assets/Generated/slot_machine/body
target_png_path:
- slot_reel_panel_idle: Assets/Generated/slot_machine/body/slot_reel_panel_idle.png
prompt_file_path:
- slot_reel_panel_idle: Assets/Generated/slot_machine/body/slot_reel_panel_idle.prompt.txt
gameplay_role: slot_reel_panel_idle: Reusable reel panel frame.
visual_description:
- slot_reel_panel_idle: three-window slot reel panel with blank dark windows, old-gold cracked frame, and wax-white accents
style_notes: Automatic sacred casino reward presentation only; no manual spin affordance or readable slot labels.
required_states:
- slot_reel_panel_idle: idle
unity_usage: slot_reel_panel_idle: Used by Slot auto-roll UI. Unity note: UI Image; symbols layered separately.
dependencies: Slot machine body and slot symbols.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, jackpot label, numbers, spin button
generation_status: ready_for_generation_review; PNG not generated.

### slot_symbol_token

object_id: slot_symbol_token
display_name: Slot Symbol Token
category: Slot Machine / Rewards
folder: Assets/Generated/slot_machine/symbols
target_png_path:
- slot_symbol_token_idle: Assets/Generated/slot_machine/symbols/slot_symbol_token_idle.png
prompt_file_path:
- slot_symbol_token_idle: Assets/Generated/slot_machine/symbols/slot_symbol_token_idle.prompt.txt
gameplay_role: slot_symbol_token_idle: Reel token symbol.
visual_description:
- slot_symbol_token_idle: old-gold cracked casino token symbol with halo notch and no letters or numbers
style_notes: Automatic sacred casino reward presentation only; no manual spin affordance or readable slot labels.
required_states:
- slot_symbol_token_idle: idle
unity_usage: slot_symbol_token_idle: Used by Slot reel animation. Unity note: UI Image/SpriteRenderer; no currency amount.
dependencies: Reel panel animation.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, currency numbers, readable label
generation_status: ready_for_generation_review; PNG not generated.

### slot_symbol_candle

object_id: slot_symbol_candle
display_name: Slot Symbol Candle
category: Slot Machine / Rewards
folder: Assets/Generated/slot_machine/symbols
target_png_path:
- slot_symbol_candle_idle: Assets/Generated/slot_machine/symbols/slot_symbol_candle_idle.png
prompt_file_path:
- slot_symbol_candle_idle: Assets/Generated/slot_machine/symbols/slot_symbol_candle_idle.prompt.txt
gameplay_role: slot_symbol_candle_idle: Reel candle symbol.
visual_description:
- slot_symbol_candle_idle: wax-white bent candle symbol with crimson flame and old-gold base
style_notes: Automatic sacred casino reward presentation only; no manual spin affordance or readable slot labels.
required_states:
- slot_symbol_candle_idle: idle
unity_usage: slot_symbol_candle_idle: Used by Slot reel animation. Unity note: UI Image/SpriteRenderer.
dependencies: Reel panel animation.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, readable label
generation_status: ready_for_generation_review; PNG not generated.

### slot_symbol_seal

object_id: slot_symbol_seal
display_name: Slot Symbol Seal
category: Slot Machine / Rewards
folder: Assets/Generated/slot_machine/symbols
target_png_path:
- slot_symbol_seal_idle: Assets/Generated/slot_machine/symbols/slot_symbol_seal_idle.png
prompt_file_path:
- slot_symbol_seal_idle: Assets/Generated/slot_machine/symbols/slot_symbol_seal_idle.prompt.txt
gameplay_role: slot_symbol_seal_idle: Reel seal symbol.
visual_description:
- slot_symbol_seal_idle: broken sacred seal symbol shaped like cracked wax stamp and roulette chip with no letters
style_notes: Automatic sacred casino reward presentation only; no manual spin affordance or readable slot labels.
required_states:
- slot_symbol_seal_idle: idle
unity_usage: slot_symbol_seal_idle: Used by Slot reel animation. Unity note: UI Image/SpriteRenderer.
dependencies: Reel panel animation.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, letters, numbers, readable label
generation_status: ready_for_generation_review; PNG not generated.

### slot_symbol_eye

object_id: slot_symbol_eye
display_name: Slot Symbol Eye
category: Slot Machine / Rewards
folder: Assets/Generated/slot_machine/symbols
target_png_path:
- slot_symbol_eye_idle: Assets/Generated/slot_machine/symbols/slot_symbol_eye_idle.png
prompt_file_path:
- slot_symbol_eye_idle: Assets/Generated/slot_machine/symbols/slot_symbol_eye_idle.prompt.txt
gameplay_role: slot_symbol_eye_idle: Reel eye symbol.
visual_description:
- slot_symbol_eye_idle: void-violet sacred eye symbol inside old-gold casino chip rim with no letters
style_notes: Automatic sacred casino reward presentation only; no manual spin affordance or readable slot labels.
required_states:
- slot_symbol_eye_idle: idle
unity_usage: slot_symbol_eye_idle: Used by Slot reel animation. Unity note: UI Image/SpriteRenderer.
dependencies: Reel panel animation.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, readable label
generation_status: ready_for_generation_review; PNG not generated.

## UI HUD

### ui_hp_bar

object_id: ui_hp_bar
display_name: HP Bar
category: Combat UI / HUD
folder: Assets/Generated/ui/hud
target_png_path:
- ui_hp_frame_idle: Assets/Generated/ui/hud/ui_hp_frame_idle.png
- ui_hp_fill_active: Assets/Generated/ui/hud/ui_hp_fill_active.png
prompt_file_path:
- ui_hp_frame_idle: Assets/Generated/ui/hud/ui_hp_frame_idle.prompt.txt
- ui_hp_fill_active: Assets/Generated/ui/hud/ui_hp_fill_active.prompt.txt
gameplay_role: ui_hp_frame_idle: HP bar frame. ui_hp_fill_active: HP fill art.
visual_description:
- ui_hp_frame_idle: horizontal cracked reliquary health bar frame with old-gold corners and wax-white bone inlay
- ui_hp_fill_active: crimson liquid wax health bar fill with subtle old-gold flecks and clean rectangular silhouette
style_notes: Canvas UI art with blank space for Unity UI text; icons communicate state but are not controls unless specified.
required_states:
- ui_hp_frame_idle: idle
- ui_hp_fill_active: active
unity_usage: ui_hp_frame_idle: Used by HUD prefab, Unity UI Image. Unity note: Use as sliced UI Image; no numbers or labels. ui_hp_fill_active: Used by HUD fill Image. Unity note: Use as filled UI Image; avoid gradients that vanish on mobile.
dependencies: HUD presenter and HP model.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, baked HP text, numbers
generation_status: ready_for_generation_review; PNG not generated.

### ui_possession_charge_bar

object_id: ui_possession_charge_bar
display_name: Possession Charge Bar
category: Combat UI / HUD
folder: Assets/Generated/ui/hud
target_png_path:
- ui_possession_charge_frame_idle: Assets/Generated/ui/hud/ui_possession_charge_frame_idle.png
- ui_possession_charge_fill_active: Assets/Generated/ui/hud/ui_possession_charge_fill_active.png
prompt_file_path:
- ui_possession_charge_frame_idle: Assets/Generated/ui/hud/ui_possession_charge_frame_idle.prompt.txt
- ui_possession_charge_fill_active: Assets/Generated/ui/hud/ui_possession_charge_fill_active.prompt.txt
gameplay_role: ui_possession_charge_frame_idle: Possession charge bar frame. ui_possession_charge_fill_active: Possession charge fill.
visual_description:
- ui_possession_charge_frame_idle: horizontal cracked halo charge frame with void-violet inner groove and old-gold casino corners
- ui_possession_charge_fill_active: void-violet spirit wax charge fill with old-gold sparks and clean horizontal silhouette
style_notes: Canvas UI art with blank space for Unity UI text; icons communicate state but are not controls unless specified.
required_states:
- ui_possession_charge_frame_idle: idle
- ui_possession_charge_fill_active: active
unity_usage: ui_possession_charge_frame_idle: Used by HUD prefab, Unity UI Image. Unity note: Sliced UI Image; no possession button behavior. ui_possession_charge_fill_active: Used by HUD fill Image. Unity note: Filled Image; use color/alpha animation in Unity.
dependencies: Possession charge model and HUD presenter.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, button affordance, manual possession cue
generation_status: ready_for_generation_review; PNG not generated.

### ui_token_display_icon

object_id: ui_token_display_icon
display_name: Token Display Icon
category: Combat UI / HUD
folder: Assets/Generated/ui/hud
target_png_path:
- ui_token_icon_idle: Assets/Generated/ui/hud/ui_token_icon_idle.png
prompt_file_path:
- ui_token_icon_idle: Assets/Generated/ui/hud/ui_token_icon_idle.prompt.txt
gameplay_role: ui_token_icon_idle: Token currency icon.
visual_description:
- ui_token_icon_idle: old-gold casino token with cracked halo symbol and no letters or numbers
style_notes: Canvas UI art with blank space for Unity UI text; icons communicate state but are not controls unless specified.
required_states:
- ui_token_icon_idle: idle
unity_usage: ui_token_icon_idle: Used by HUD, reward UI. Unity note: UI Image; text count added in Unity UI.
dependencies: Token counter presenter.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, baked numbers, currency text
generation_status: ready_for_generation_review; PNG not generated.

### ui_room_progress

object_id: ui_room_progress
display_name: Room Progress
category: Combat UI / HUD
folder: Assets/Generated/ui/hud
target_png_path:
- ui_room_progress_frame_idle: Assets/Generated/ui/hud/ui_room_progress_frame_idle.png
- ui_room_progress_icon_active: Assets/Generated/ui/hud/ui_room_progress_icon_active.png
prompt_file_path:
- ui_room_progress_frame_idle: Assets/Generated/ui/hud/ui_room_progress_frame_idle.prompt.txt
- ui_room_progress_icon_active: Assets/Generated/ui/hud/ui_room_progress_icon_active.prompt.txt
gameplay_role: ui_room_progress_frame_idle: Room progress frame. ui_room_progress_icon_active: Active/cleared room progress token.
visual_description:
- ui_room_progress_frame_idle: compact five-notch reliquary progress frame with blank sockets and old-gold cracked trim
- ui_room_progress_icon_active: small old-gold cracked chapel-token marker with crimson inner glow and no number
style_notes: Canvas UI art with blank space for Unity UI text; icons communicate state but are not controls unless specified.
required_states:
- ui_room_progress_frame_idle: idle
- ui_room_progress_icon_active: active
unity_usage: ui_room_progress_frame_idle: Used by HUD progress display. Unity note: Coder can place icons/filled states; no room numbers baked in. ui_room_progress_icon_active: Used by HUD progress display. Unity note: UI Image repeated by code for progress slots.
dependencies: Room/wave director presenter.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, baked room numbers, labels
generation_status: ready_for_generation_review; PNG not generated.

### ui_auto_attack_indicator

object_id: ui_auto_attack_indicator
display_name: Auto-Attack Indicator
category: Combat UI / HUD
folder: Assets/Generated/ui/hud
target_png_path:
- ui_auto_attack_indicator_active: Assets/Generated/ui/hud/ui_auto_attack_indicator_active.png
- ui_auto_attack_indicator_disabled: Assets/Generated/ui/hud/ui_auto_attack_indicator_disabled.png
prompt_file_path:
- ui_auto_attack_indicator_active: Assets/Generated/ui/hud/ui_auto_attack_indicator_active.prompt.txt
- ui_auto_attack_indicator_disabled: Assets/Generated/ui/hud/ui_auto_attack_indicator_disabled.prompt.txt
gameplay_role: ui_auto_attack_indicator_active: Optional indicator that auto-attack is active. ui_auto_attack_indicator_disabled: Optional inactive auto-attack indicator.
visual_description:
- ui_auto_attack_indicator_active: small targeting halo icon with old-gold reticle and wax-white spark
- ui_auto_attack_indicator_disabled: dim broken targeting halo icon with charcoal fill and faint wax-white spark
style_notes: Canvas UI art with blank space for Unity UI text; icons communicate state but are not controls unless specified.
required_states:
- ui_auto_attack_indicator_active: active
- ui_auto_attack_indicator_disabled: disabled
unity_usage: ui_auto_attack_indicator_active: Used by HUD, Player combat feedback. Unity note: UI Image only; not a button. ui_auto_attack_indicator_disabled: Used by HUD, Player combat feedback. Unity note: UI Image only; no manual attack button.
dependencies: Auto-target/auto-attack state presenter.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, manual attack button affordance, tap prompt
generation_status: ready_for_generation_review; PNG not generated.

## UI Controls

### ui_joystick_base

object_id: ui_joystick_base
display_name: Floating Joystick Base
category: Touch Controls
folder: Assets/Generated/ui/controls
target_png_path:
- ui_joystick_base_idle: Assets/Generated/ui/controls/ui_joystick_base_idle.png
- ui_joystick_base_active: Assets/Generated/ui/controls/ui_joystick_base_active.png
prompt_file_path:
- ui_joystick_base_idle: Assets/Generated/ui/controls/ui_joystick_base_idle.prompt.txt
- ui_joystick_base_active: Assets/Generated/ui/controls/ui_joystick_base_active.prompt.txt
gameplay_role: ui_joystick_base_idle: Floating joystick base at rest. ui_joystick_base_active: Floating joystick base while touched.
visual_description:
- ui_joystick_base_idle: translucent circular old-gold and charcoal joystick base shaped like cracked chapel window with blank center
- ui_joystick_base_active: glowing circular old-gold and void-violet joystick base shaped like cracked chapel window with blank center
style_notes: Movement-only joystick visuals; no combat, dash, possession, or spin affordances.
required_states:
- ui_joystick_base_idle: idle
- ui_joystick_base_active: active
unity_usage: ui_joystick_base_idle: Used by Input UI prefab. Unity note: UI Image under touch area; no labels. ui_joystick_base_active: Used by Input UI prefab. Unity note: UI Image; Coder changes alpha/position by touch.
dependencies: Movement input controller and safe-area/thumb-zone layout.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, dash icon, attack icon, possession icon
generation_status: ready_for_generation_review; PNG not generated.

### ui_joystick_knob

object_id: ui_joystick_knob
display_name: Floating Joystick Knob
category: Touch Controls
folder: Assets/Generated/ui/controls
target_png_path:
- ui_joystick_knob_idle: Assets/Generated/ui/controls/ui_joystick_knob_idle.png
- ui_joystick_knob_active: Assets/Generated/ui/controls/ui_joystick_knob_active.png
prompt_file_path:
- ui_joystick_knob_idle: Assets/Generated/ui/controls/ui_joystick_knob_idle.prompt.txt
- ui_joystick_knob_active: Assets/Generated/ui/controls/ui_joystick_knob_active.prompt.txt
gameplay_role: ui_joystick_knob_idle: Floating joystick knob at rest. ui_joystick_knob_active: Floating joystick knob while dragged.
visual_description:
- ui_joystick_knob_idle: small old-gold casino token joystick knob with cracked halo emblem and no letters
- ui_joystick_knob_active: small glowing void-violet casino token joystick knob with old-gold cracked halo emblem and no letters
style_notes: Movement-only joystick visuals; no combat, dash, possession, or spin affordances.
required_states:
- ui_joystick_knob_idle: idle
- ui_joystick_knob_active: active
unity_usage: ui_joystick_knob_idle: Used by Input UI prefab. Unity note: UI Image; no text or numbers. ui_joystick_knob_active: Used by Input UI prefab. Unity note: UI Image; no dash or action affordance.
dependencies: Movement input controller and joystick base.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, dash/action/attack/possession cue
generation_status: ready_for_generation_review; PNG not generated.

## UI Rewards

### ui_reward_card_frame

object_id: ui_reward_card_frame
display_name: Reward Card Frame
category: Slot Machine / Rewards
folder: Assets/Generated/ui/rewards
target_png_path:
- ui_reward_card_frame_idle: Assets/Generated/ui/rewards/ui_reward_card_frame_idle.png
- ui_reward_card_frame_selected: Assets/Generated/ui/rewards/ui_reward_card_frame_selected.png
- ui_reward_card_frame_disabled: Assets/Generated/ui/rewards/ui_reward_card_frame_disabled.png
prompt_file_path:
- ui_reward_card_frame_idle: Assets/Generated/ui/rewards/ui_reward_card_frame_idle.prompt.txt
- ui_reward_card_frame_selected: Assets/Generated/ui/rewards/ui_reward_card_frame_selected.prompt.txt
- ui_reward_card_frame_disabled: Assets/Generated/ui/rewards/ui_reward_card_frame_disabled.prompt.txt
gameplay_role: ui_reward_card_frame_idle: Standard reward card frame. ui_reward_card_frame_selected: Selected reward card frame. ui_reward_card_frame_disabled: Disabled/unavailable reward card frame.
visual_description:
- ui_reward_card_frame_idle: vertical reward card frame with old-gold chapel arch corners, charcoal interior, and blank wax-white text area space
- ui_reward_card_frame_selected: vertical reward card frame glowing old-gold with void-violet chapel arch corners and blank interior
- ui_reward_card_frame_disabled: dim vertical reward card frame with cracked charcoal chapel arch and faded wax-white interior
style_notes: Reward UI leaves names, descriptions, values, and counts to Unity UI text; frames/icons remain blank.
required_states:
- ui_reward_card_frame_idle: idle
- ui_reward_card_frame_selected: selected
- ui_reward_card_frame_disabled: disabled
unity_usage: ui_reward_card_frame_idle: Used by Reward choice UI. Unity note: UI Image; text and icon placed by Unity UI. ui_reward_card_frame_selected: Used by Reward choice UI. Unity note: UI Image state; no baked selection label. ui_reward_card_frame_disabled: Used by Reward choice UI. Unity note: UI Image state; use for disabled card presentation only.
dependencies: Reward choice UI, selection state, disabled/apply state.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, baked reward name, baked effect text, numbers
generation_status: ready_for_generation_review; PNG not generated.

### ui_reroll_icon

object_id: ui_reroll_icon
display_name: Reroll Icon
category: Slot Machine / Rewards
folder: Assets/Generated/ui/rewards
target_png_path:
- ui_reroll_icon_ready: Assets/Generated/ui/rewards/ui_reroll_icon_ready.png
- ui_reroll_icon_disabled: Assets/Generated/ui/rewards/ui_reroll_icon_disabled.png
prompt_file_path:
- ui_reroll_icon_ready: Assets/Generated/ui/rewards/ui_reroll_icon_ready.prompt.txt
- ui_reroll_icon_disabled: Assets/Generated/ui/rewards/ui_reroll_icon_disabled.prompt.txt
gameplay_role: ui_reroll_icon_ready: Reroll visual icon/button art. ui_reroll_icon_disabled: Disabled reroll visual.
visual_description:
- ui_reroll_icon_ready: circular old-gold reroll arrow icon made of broken halo fragments around a casino token
- ui_reroll_icon_disabled: dim circular reroll arrow icon made of cracked charcoal halo fragments with faint wax-white edge
style_notes: Reward UI leaves names, descriptions, values, and counts to Unity UI text; frames/icons remain blank.
required_states:
- ui_reroll_icon_ready: ready
- ui_reroll_icon_disabled: disabled
unity_usage: ui_reroll_icon_ready: Used by Reward UI reroll control. Unity note: UI Button Image; no text count baked in. ui_reroll_icon_disabled: Used by Reward UI reroll control. Unity note: UI Button disabled Image; reroll count in Unity text.
dependencies: Reward reroll count and reward screen state.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, slot spin cue, jackpot cue, manual machine interaction
generation_status: ready_for_generation_review; PNG not generated.

### reward_icon_standard_placeholders

object_id: reward_icon_standard_placeholders
display_name: Standard Reward Placeholder Icons
category: Slot Machine / Rewards
folder: Assets/Generated/ui/rewards
target_png_path:
- reward_icon_standard_01: Assets/Generated/ui/rewards/reward_icon_standard_01.png
- reward_icon_standard_02: Assets/Generated/ui/rewards/reward_icon_standard_02.png
- reward_icon_standard_04: Assets/Generated/ui/rewards/reward_icon_standard_04.png
- reward_icon_standard_05: Assets/Generated/ui/rewards/reward_icon_standard_05.png
- reward_icon_standard_06: Assets/Generated/ui/rewards/reward_icon_standard_06.png
- reward_icon_standard_07: Assets/Generated/ui/rewards/reward_icon_standard_07.png
- reward_icon_standard_08: Assets/Generated/ui/rewards/reward_icon_standard_08.png
- reward_icon_standard_09: Assets/Generated/ui/rewards/reward_icon_standard_09.png
- reward_icon_standard_10: Assets/Generated/ui/rewards/reward_icon_standard_10.png
- reward_icon_standard_11: Assets/Generated/ui/rewards/reward_icon_standard_11.png
- reward_icon_standard_12: Assets/Generated/ui/rewards/reward_icon_standard_12.png
prompt_file_path:
- reward_icon_standard_01: Assets/Generated/ui/rewards/reward_icon_standard_01.prompt.txt
- reward_icon_standard_02: Assets/Generated/ui/rewards/reward_icon_standard_02.prompt.txt
- reward_icon_standard_04: Assets/Generated/ui/rewards/reward_icon_standard_04.prompt.txt
- reward_icon_standard_05: Assets/Generated/ui/rewards/reward_icon_standard_05.prompt.txt
- reward_icon_standard_06: Assets/Generated/ui/rewards/reward_icon_standard_06.prompt.txt
- reward_icon_standard_07: Assets/Generated/ui/rewards/reward_icon_standard_07.prompt.txt
- reward_icon_standard_08: Assets/Generated/ui/rewards/reward_icon_standard_08.prompt.txt
- reward_icon_standard_09: Assets/Generated/ui/rewards/reward_icon_standard_09.prompt.txt
- reward_icon_standard_10: Assets/Generated/ui/rewards/reward_icon_standard_10.prompt.txt
- reward_icon_standard_11: Assets/Generated/ui/rewards/reward_icon_standard_11.prompt.txt
- reward_icon_standard_12: Assets/Generated/ui/rewards/reward_icon_standard_12.prompt.txt
gameplay_role: reward_icon_standard_01: Standard reward icon placeholder 01. reward_icon_standard_02: Standard reward icon placeholder 02. reward_icon_standard_04: Standard reward icon placeholder 04. reward_icon_standard_05: Standard reward icon placeholder 05. reward_icon_standard_06: Standard reward icon placeholder 06. reward_icon_standard_07: Standard reward icon placeholder 07. reward_icon_standard_08: Standard reward icon placeholder 08. reward_icon_standard_09: Standard reward icon placeholder 09. reward_icon_standard_10: Standard reward icon placeholder 10. reward_icon_standard_11: Standard reward icon placeholder 11. reward_icon_standard_12: Standard reward icon placeholder 12.
visual_description:
- reward_icon_standard_01: old-gold crooked candle blessing icon with wax-white flame and no letters
- reward_icon_standard_02: crimson thorn dagger blessing icon wrapped in tiny old-gold token halo and no letters
- reward_icon_standard_04: cracked old-gold halo blessing icon with wax-white inner glow and no letters
- reward_icon_standard_05: wax-white heart reliquary icon inside old-gold casino chip rim and no letters
- reward_icon_standard_06: void-violet watching eye blessing icon with crimson tear and old-gold broken rim
- reward_icon_standard_07: black casino token blessing icon with old-gold rim, wax-white crack, and no letters or numbers
- reward_icon_standard_08: thorny rosary loop icon made of tiny old-gold casino beads with crimson wax drop and no cross text
- reward_icon_standard_09: broken balance scale icon with old-gold pans shaped like casino chips and no markings
- reward_icon_standard_10: incense burner icon shaped like tiny slot altar with void-violet smoke and blank face
- reward_icon_standard_11: wax-white marked palm blessing icon holding old-gold token with no letters or numbers
- reward_icon_standard_12: sealed chapel gate icon with old-gold lock and void-violet crack, no letters or numbers
style_notes: Reward UI leaves names, descriptions, values, and counts to Unity UI text; frames/icons remain blank.
required_states:
- reward_icon_standard_01: none
- reward_icon_standard_02: none
- reward_icon_standard_04: none
- reward_icon_standard_05: none
- reward_icon_standard_06: none
- reward_icon_standard_07: none
- reward_icon_standard_08: none
- reward_icon_standard_09: none
- reward_icon_standard_10: none
- reward_icon_standard_11: none
- reward_icon_standard_12: none
unity_usage: reward_icon_standard_01: Used by Reward cards. Unity note: Placeholder; does not define mechanics. reward_icon_standard_02: Used by Reward cards. Unity note: Placeholder; does not define mechanics. reward_icon_standard_04: Used by Reward cards. Unity note: Placeholder; does not define mechanics. reward_icon_standard_05: Used by Reward cards. Unity note: Placeholder; does not define mechanics. reward_icon_standard_06: Used by Reward cards. Unity note: Placeholder; does not define mechanics. reward_icon_standard_07: Used by Reward cards. Unity note: Placeholder; does not define mechanics. reward_icon_standard_08: Used by Reward cards. Unity note: Placeholder; does not define mechanics. reward_icon_standard_09: Used by Reward cards. Unity note: Placeholder; does not define mechanics. reward_icon_standard_10: Used by Reward cards. Unity note: Placeholder; does not define mechanics. reward_icon_standard_11: Used by Reward cards. Unity note: Placeholder; does not define mechanics. reward_icon_standard_12: Used by Reward cards. Unity note: Placeholder; does not define mechanics.
dependencies: Future reward data mapping by Architect/Coder.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, final mechanics text, stat numbers, post-MVP effects
generation_status: ready_for_generation_review; PNG not generated.

### reward_icon_p03_last_breath

object_id: reward_icon_p03_last_breath
display_name: P03 Last Breath Reward Icon
category: Slot Machine / Rewards
folder: Assets/Generated/ui/rewards
target_png_path:
- reward_icon_p03_last_breath: Assets/Generated/ui/rewards/reward_icon_p03_last_breath.png
prompt_file_path:
- reward_icon_p03_last_breath: Assets/Generated/ui/rewards/reward_icon_p03_last_breath.prompt.txt
gameplay_role: reward_icon_p03_last_breath: Standard reward icon for P03 Last Breath, the only possession-exit explosion source.
visual_description:
- reward_icon_p03_last_breath: void-violet final breath spirit icon bursting from a cracked old-gold vessel halo without damage numbers
style_notes: Reward UI leaves names, descriptions, values, and counts to Unity UI text; frames/icons remain blank.
required_states:
- reward_icon_p03_last_breath: none
unity_usage: reward_icon_p03_last_breath: Used by Reward cards, P03 effect UI. Unity note: Only icon tied to validated P03 explosion behavior.
dependencies: P03 reward ownership and P03 VFX trigger logic.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, baked P03 text, extra reward mechanics
generation_status: ready_for_generation_review; PNG not generated.

### ui_cursed_deal_offer

object_id: ui_cursed_deal_offer
display_name: Cursed Deal Offer
category: Slot Machine / Rewards
folder: Assets/Generated/ui/rewards
target_png_path:
- ui_cursed_deal_frame_active: Assets/Generated/ui/rewards/ui_cursed_deal_frame_active.png
- ui_cursed_deal_icon_fanatical_credit: Assets/Generated/ui/rewards/ui_cursed_deal_icon_fanatical_credit.png
prompt_file_path:
- ui_cursed_deal_frame_active: Assets/Generated/ui/rewards/ui_cursed_deal_frame_active.prompt.txt
- ui_cursed_deal_icon_fanatical_credit: Assets/Generated/ui/rewards/ui_cursed_deal_icon_fanatical_credit.prompt.txt
gameplay_role: ui_cursed_deal_frame_active: Cursed deal card/popup frame. ui_cursed_deal_icon_fanatical_credit: Icon for Fanatical Credit cursed deal.
visual_description:
- ui_cursed_deal_frame_active: vertical cursed deal frame with crimson wax cracks, void-violet smoke corners, old-gold chapel arch, and blank interior
- ui_cursed_deal_icon_fanatical_credit: cursed old-gold credit token chained to crimson wax heart with blank face and no numbers
style_notes: Reward UI leaves names, descriptions, values, and counts to Unity UI text; frames/icons remain blank.
required_states:
- ui_cursed_deal_frame_active: active
- ui_cursed_deal_icon_fanatical_credit: none
unity_usage: ui_cursed_deal_frame_active: Used by Reward UI, cursed deal stop 2. Unity note: UI Image; cursed deal name/effect added via Unity text. ui_cursed_deal_icon_fanatical_credit: Used by Reward UI, cursed deal offer. Unity note: Icon only; +1 Attack and -1 Max HP text must be Unity UI.
dependencies: Stop-2 cursed deal routing and accept/decline UI.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, baked +1/-1 text, paid offer/IAP cues
generation_status: ready_for_generation_review; PNG not generated.

## UI Results

### ui_result_emblems

object_id: ui_result_emblems
display_name: Victory and Defeat Emblems
category: Result Screens
folder: Assets/Generated/ui/results
target_png_path:
- ui_victory_emblem_active: Assets/Generated/ui/results/ui_victory_emblem_active.png
- ui_defeat_emblem_active: Assets/Generated/ui/results/ui_defeat_emblem_active.png
prompt_file_path:
- ui_victory_emblem_active: Assets/Generated/ui/results/ui_victory_emblem_active.prompt.txt
- ui_defeat_emblem_active: Assets/Generated/ui/results/ui_defeat_emblem_active.prompt.txt
gameplay_role: ui_victory_emblem_active: Victory emblem after boss defeat. ui_defeat_emblem_active: Defeat emblem.
visual_description:
- ui_victory_emblem_active: old-gold broken seal victory emblem over wax-white candleburst with crimson cult cracks
- ui_defeat_emblem_active: dim cracked halo defeat emblem with extinguished candle and void-violet smoke
style_notes: Result UI art provides blank panels and emblems only; summary text and buttons are Unity UI.
required_states:
- ui_victory_emblem_active: active
- ui_defeat_emblem_active: active
unity_usage: ui_victory_emblem_active: Used by GameOver/Victory UI. Unity note: UI Image; victory text added in Unity. ui_defeat_emblem_active: Used by GameOver UI. Unity note: UI Image; defeat text added in Unity.
dependencies: Victory/defeat routing.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, victory/defeat text, score numbers
generation_status: ready_for_generation_review; PNG not generated.

### ui_game_over_panel

object_id: ui_game_over_panel
display_name: Game Over Panel Background
category: Result Screens
folder: Assets/Generated/ui/results
target_png_path:
- ui_game_over_panel_bg_idle: Assets/Generated/ui/results/ui_game_over_panel_bg_idle.png
prompt_file_path:
- ui_game_over_panel_bg_idle: Assets/Generated/ui/results/ui_game_over_panel_bg_idle.prompt.txt
gameplay_role: ui_game_over_panel_bg_idle: Game over panel background decoration.
visual_description:
- ui_game_over_panel_bg_idle: large dark chapel-casino panel background with blank parchment center and old-gold cracked border
style_notes: Result UI art provides blank panels and emblems only; summary text and buttons are Unity UI.
required_states:
- ui_game_over_panel_bg_idle: idle
unity_usage: ui_game_over_panel_bg_idle: Used by GameOver scene UI. Unity note: Sliced or full UI Image; all summary text is Unity UI.
dependencies: GameOver/Victory result UI layout.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, summary text, buttons, score numbers
generation_status: ready_for_generation_review; PNG not generated.

### ui_run_summary_frame

object_id: ui_run_summary_frame
display_name: Run Summary Frame
category: Result Screens
folder: Assets/Generated/ui/results
target_png_path:
- ui_run_summary_frame_idle: Assets/Generated/ui/results/ui_run_summary_frame_idle.png
prompt_file_path:
- ui_run_summary_frame_idle: Assets/Generated/ui/results/ui_run_summary_frame_idle.prompt.txt
gameplay_role: ui_run_summary_frame_idle: Decorative frame for run summary stats.
visual_description:
- ui_run_summary_frame_idle: horizontal run summary frame with old-gold casino chapel corners, blank sockets, and wax-white trim
style_notes: Result UI art provides blank panels and emblems only; summary text and buttons are Unity UI.
required_states:
- ui_run_summary_frame_idle: idle
unity_usage: ui_run_summary_frame_idle: Used by GameOver scene UI. Unity note: UI Image; numbers/labels added in Unity.
dependencies: Result summary presenter.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, baked labels, numbers
generation_status: ready_for_generation_review; PNG not generated.

## UI Meta

### ui_broken_seal_icon

object_id: ui_broken_seal_icon
display_name: Broken Seal Icon
category: Meta Unlock
folder: Assets/Generated/ui/meta
target_png_path:
- ui_broken_seal_icon_idle: Assets/Generated/ui/meta/ui_broken_seal_icon_idle.png
prompt_file_path:
- ui_broken_seal_icon_idle: Assets/Generated/ui/meta/ui_broken_seal_icon_idle.prompt.txt
gameplay_role: ui_broken_seal_icon_idle: First meta unlock icon: Broken Seal.
visual_description:
- ui_broken_seal_icon_idle: broken old-gold sacred seal icon with void-violet crack and wax-white glow, no letters or numbers
style_notes: Meta unlock art is limited to Broken Seal MVP presentation and must not imply a full upgrade/shop system.
required_states:
- ui_broken_seal_icon_idle: idle
unity_usage: ui_broken_seal_icon_idle: Used by MainMenu/meta unlock UI. Unity note: UI Image; unlock name/effect text in Unity.
dependencies: First boss victory persistent unlock.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, baked unlock name, +1 text
generation_status: ready_for_generation_review; PNG not generated.

### ui_meta_unlock_panel

object_id: ui_meta_unlock_panel
display_name: Meta Unlock Panel
category: Meta Unlock
folder: Assets/Generated/ui/meta
target_png_path:
- ui_meta_unlock_panel_decoration_idle: Assets/Generated/ui/meta/ui_meta_unlock_panel_decoration_idle.png
prompt_file_path:
- ui_meta_unlock_panel_decoration_idle: Assets/Generated/ui/meta/ui_meta_unlock_panel_decoration_idle.prompt.txt
gameplay_role: ui_meta_unlock_panel_decoration_idle: Meta unlock panel decoration.
visual_description:
- ui_meta_unlock_panel_decoration_idle: compact chapel-casino unlock panel decoration with blank center, cracked old-gold border, and candle side ornaments
style_notes: Meta unlock art is limited to Broken Seal MVP presentation and must not imply a full upgrade/shop system.
required_states:
- ui_meta_unlock_panel_decoration_idle: idle
unity_usage: ui_meta_unlock_panel_decoration_idle: Used by MainMenu/meta unlock UI. Unity note: UI Image; no unlock copy baked in.
dependencies: Meta unlock presentation route.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, upgrade-tree cues, shop/IAP cues, baked text
generation_status: ready_for_generation_review; PNG not generated.

## Environment Arenas

### arena_floor_corrupted_village

object_id: arena_floor_corrupted_village
display_name: Corrupted Village Arena Floor
category: Environment / Props
folder: Assets/Generated/environment/arenas
target_png_path:
- arena_floor_corrupted_village_idle: Assets/Generated/environment/arenas/arena_floor_corrupted_village_idle.png
prompt_file_path:
- arena_floor_corrupted_village_idle: Assets/Generated/environment/arenas/arena_floor_corrupted_village_idle.prompt.txt
gameplay_role: arena_floor_corrupted_village_idle: Simple arena floor/background for five combat rooms.
visual_description:
- arena_floor_corrupted_village_idle: circular corrupted village arena floor patch with cracked chapel stones, faint casino-chip geometry, and muddy charcoal edges
style_notes: Arena background must stay low-noise and lower priority than characters, warnings, and possession markers.
required_states:
- arena_floor_corrupted_village_idle: idle
unity_usage: arena_floor_corrupted_village_idle: Used by Game scene background. Unity note: SpriteRenderer background; can be scaled, avoid busy detail under enemies.
dependencies: Room scene/background prefab.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, path arrows, readable signs
generation_status: ready_for_generation_review; PNG not generated.

## Environment Props

### prop_corrupted_village_house

object_id: prop_corrupted_village_house
display_name: Corrupted Village House Prop
category: Environment / Props
folder: Assets/Generated/environment/props
target_png_path:
- prop_corrupted_village_house_idle: Assets/Generated/environment/props/prop_corrupted_village_house_idle.png
prompt_file_path:
- prop_corrupted_village_house_idle: Assets/Generated/environment/props/prop_corrupted_village_house_idle.prompt.txt
gameplay_role: prop_corrupted_village_house_idle: Corrupted village background prop.
visual_description:
- prop_corrupted_village_house_idle: crooked rotting village chapel-house prop with blank hanging sign and old-gold candle stains
style_notes: Props are non-interactive dressing and must stay blank of readable signage.
required_states:
- prop_corrupted_village_house_idle: idle
unity_usage: prop_corrupted_village_house_idle: Used by Room decoration prefab. Unity note: SpriteRenderer; sign must remain unreadable/blank.
dependencies: Room decoration prefab placement.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, readable sign text, interaction cue
generation_status: ready_for_generation_review; PNG not generated.

### prop_altar_slot_machine

object_id: prop_altar_slot_machine
display_name: Altar Slot Machine Prop
category: Environment / Props
folder: Assets/Generated/environment/props
target_png_path:
- prop_altar_slot_machine_idle: Assets/Generated/environment/props/prop_altar_slot_machine_idle.png
prompt_file_path:
- prop_altar_slot_machine_idle: Assets/Generated/environment/props/prop_altar_slot_machine_idle.prompt.txt
gameplay_role: prop_altar_slot_machine_idle: Non-interactive altar slot-machine prop for arena dressing if needed.
visual_description:
- prop_altar_slot_machine_idle: small broken altar slot-machine prop with blank reel windows and melted candles
style_notes: Props are non-interactive dressing and must stay blank of readable signage.
required_states:
- prop_altar_slot_machine_idle: idle
unity_usage: prop_altar_slot_machine_idle: Used by Room decoration prefab. Unity note: Decorative only; not the reward machine interaction.
dependencies: Room decoration only.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, lever, handle, spin button, reward interaction cue
generation_status: ready_for_generation_review; PNG not generated.

### prop_sacred_casino_candles

object_id: prop_sacred_casino_candles
display_name: Sacred Casino Candles Prop
category: Environment / Props
folder: Assets/Generated/environment/props
target_png_path:
- prop_sacred_casino_candles_idle: Assets/Generated/environment/props/prop_sacred_casino_candles_idle.png
prompt_file_path:
- prop_sacred_casino_candles_idle: Assets/Generated/environment/props/prop_sacred_casino_candles_idle.prompt.txt
gameplay_role: prop_sacred_casino_candles_idle: Casino-religious decorative candles.
visual_description:
- prop_sacred_casino_candles_idle: cluster of wax-white altar candles around old-gold casino chips with crimson wax drips
style_notes: Props are non-interactive dressing and must stay blank of readable signage.
required_states:
- prop_sacred_casino_candles_idle: idle
unity_usage: prop_sacred_casino_candles_idle: Used by Room decoration prefab. Unity note: SpriteRenderer prop; keep low visual noise.
dependencies: Room decoration prefab placement.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, pickup cue, currency number
generation_status: ready_for_generation_review; PNG not generated.

### prop_casino_religious_banner

object_id: prop_casino_religious_banner
display_name: Casino Religious Banner Prop
category: Environment / Props
folder: Assets/Generated/environment/props
target_png_path:
- prop_casino_religious_banner_idle: Assets/Generated/environment/props/prop_casino_religious_banner_idle.png
prompt_file_path:
- prop_casino_religious_banner_idle: Assets/Generated/environment/props/prop_casino_religious_banner_idle.prompt.txt
gameplay_role: prop_casino_religious_banner_idle: Decorative banner without readable symbols.
visual_description:
- prop_casino_religious_banner_idle: torn chapel banner with abstract casino-chip pattern, no letters, no numbers, old-gold trim and crimson cloth
style_notes: Props are non-interactive dressing and must stay blank of readable signage.
required_states:
- prop_casino_religious_banner_idle: idle
unity_usage: prop_casino_religious_banner_idle: Used by Room decoration prefab. Unity note: Decorative prop; no readable prayers or signage.
dependencies: Room decoration prefab placement.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, readable prayers, letters, numbers
generation_status: ready_for_generation_review; PNG not generated.

## VFX Combat

### vfx_hit_impact

object_id: vfx_hit_impact
display_name: Hit Impact VFX
category: VFX
folder: Assets/Generated/vfx/combat
target_png_path:
- vfx_hit_impact_active: Assets/Generated/vfx/combat/vfx_hit_impact_active.png
prompt_file_path:
- vfx_hit_impact_active: Assets/Generated/vfx/combat/vfx_hit_impact_active.prompt.txt
gameplay_role: vfx_hit_impact_active: Generic hit impact sprite.
visual_description:
- vfx_hit_impact_active: compact crimson wax impact burst with old-gold chip shards and strong radial silhouette
style_notes: Compact world VFX with transparent backgrounds; combat feedback must not overpower boss/P03 visuals.
required_states:
- vfx_hit_impact_active: active
unity_usage: vfx_hit_impact_active: Used by Combat VFX prefab. Unity note: SpriteRenderer VFX; Coder can scale/fade.
dependencies: Damage feedback event/pool.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, huge boss-scale explosion
generation_status: ready_for_generation_review; PNG not generated.

### vfx_enemy_death_puff

object_id: vfx_enemy_death_puff
display_name: Enemy Death Puff VFX
category: VFX
folder: Assets/Generated/vfx/combat
target_png_path:
- vfx_enemy_death_puff_active: Assets/Generated/vfx/combat/vfx_enemy_death_puff_active.png
prompt_file_path:
- vfx_enemy_death_puff_active: Assets/Generated/vfx/combat/vfx_enemy_death_puff_active.prompt.txt
gameplay_role: vfx_enemy_death_puff_active: Enemy death puff.
visual_description:
- vfx_enemy_death_puff_active: small charcoal wax smoke puff with old-gold flecks and void-violet inner curl
style_notes: Compact world VFX with transparent backgrounds; combat feedback must not overpower boss/P03 visuals.
required_states:
- vfx_enemy_death_puff_active: active
unity_usage: vfx_enemy_death_puff_active: Used by Enemy death VFX prefab. Unity note: SpriteRenderer VFX; not used for P03 explosion.
dependencies: Enemy death event/pool.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, P03 blast identity, reward pickup cue
generation_status: ready_for_generation_review; PNG not generated.

## VFX Possession

### vfx_possession_tether_flash

object_id: vfx_possession_tether_flash
display_name: Possession Tether Flash VFX
category: VFX
folder: Assets/Generated/vfx/possession
target_png_path:
- vfx_possession_tether_flash_active: Assets/Generated/vfx/possession/vfx_possession_tether_flash_active.png
prompt_file_path:
- vfx_possession_tether_flash_active: Assets/Generated/vfx/possession/vfx_possession_tether_flash_active.prompt.txt
gameplay_role: vfx_possession_tether_flash_active: Possession tether/flash between player and vessel.
visual_description:
- vfx_possession_tether_flash_active: arcing void-violet spirit tether with old-gold broken halo sparks and clean readable curve
style_notes: Possession VFX should read as tether/transition feedback, not damage or explosion.
required_states:
- vfx_possession_tether_flash_active: active
unity_usage: vfx_possession_tether_flash_active: Used by Possession VFX prefab. Unity note: Can be stretched/rotated by script or used as short flash.
dependencies: Possession auto-trigger event.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, button cue, explosion
generation_status: ready_for_generation_review; PNG not generated.

## VFX Rewards

### vfx_reward_reveal_sparkle

object_id: vfx_reward_reveal_sparkle
display_name: Reward Reveal Sparkle VFX
category: VFX
folder: Assets/Generated/vfx/rewards
target_png_path:
- vfx_reward_reveal_sparkle_active: Assets/Generated/vfx/rewards/vfx_reward_reveal_sparkle_active.png
prompt_file_path:
- vfx_reward_reveal_sparkle_active: Assets/Generated/vfx/rewards/vfx_reward_reveal_sparkle_active.prompt.txt
gameplay_role: vfx_reward_reveal_sparkle_active: Reward reveal sparkle.
visual_description:
- vfx_reward_reveal_sparkle_active: old-gold candle sparkle burst with wax-white glints and tiny void-violet cracks
style_notes: Reward VFX supports card/modal reveal and contains no reward text or numbers.
required_states:
- vfx_reward_reveal_sparkle_active: active
unity_usage: vfx_reward_reveal_sparkle_active: Used by Reward UI VFX prefab. Unity note: UI overlay or SpriteRenderer VFX.
dependencies: Card reveal animation.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, text, numbers, currency reward promise
generation_status: ready_for_generation_review; PNG not generated.

### vfx_cursed_deal_smoke

object_id: vfx_cursed_deal_smoke
display_name: Cursed Deal Smoke VFX
category: VFX
folder: Assets/Generated/vfx/rewards
target_png_path:
- vfx_cursed_deal_smoke_active: Assets/Generated/vfx/rewards/vfx_cursed_deal_smoke_active.png
prompt_file_path:
- vfx_cursed_deal_smoke_active: Assets/Generated/vfx/rewards/vfx_cursed_deal_smoke_active.prompt.txt
gameplay_role: vfx_cursed_deal_smoke_active: Cursed deal smoke.
visual_description:
- vfx_cursed_deal_smoke_active: curling crimson and void-violet cursed smoke with old-gold ember flecks and compact silhouette
style_notes: Reward VFX supports card/modal reveal and contains no reward text or numbers.
required_states:
- vfx_cursed_deal_smoke_active: active
unity_usage: vfx_cursed_deal_smoke_active: Used by Cursed deal UI VFX prefab. Unity note: UI overlay; no readable curse symbols.
dependencies: Cursed deal popup state.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, readable curse symbols, IAP/payment cue
generation_status: ready_for_generation_review; PNG not generated.

## VFX P03

### vfx_p03_explosion

object_id: vfx_p03_explosion
display_name: P03 Last Breath Explosion VFX
category: VFX
folder: Assets/Generated/vfx/p03
target_png_path:
- vfx_p03_explosion_active: Assets/Generated/vfx/p03/vfx_p03_explosion_active.png
prompt_file_path:
- vfx_p03_explosion_active: Assets/Generated/vfx/p03/vfx_p03_explosion_active.prompt.txt
gameplay_role: vfx_p03_explosion_active: P03 Last Breath damaging possession-exit explosion.
visual_description:
- vfx_p03_explosion_active: compact void-violet and crimson spirit explosion from cracked old-gold vessel halo with enemy-only blast silhouette
style_notes: P03 explosion is the only damaging possession-exit blast and must stay visually distinct from default exit.
required_states:
- vfx_p03_explosion_active: active
unity_usage: vfx_p03_explosion_active: Used by P03 reward effect VFX prefab. Unity note: Only use for P03; default possession exit must not call this VFX.
dependencies: P03 reward effect, possession exit event, damage application.
must_not_include: readable text, letters, numbers, watermark, photorealism, 3D render, JPG output, opaque/noisy background, default possession exit use, non-P03 trigger, text
generation_status: ready_for_generation_review; PNG not generated.


