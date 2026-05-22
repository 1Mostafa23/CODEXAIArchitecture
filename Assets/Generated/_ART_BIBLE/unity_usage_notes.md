# Unity Usage Notes

## 1. World SpriteRenderer Assets

Use `SpriteRenderer` for world/gameplay sprites, imported as `Sprite (2D and UI)`, alpha enabled, mipmaps disabled, and `128 PPU` unless Architect sets a different global PPU before import.

World asset IDs:
```text
player_body_idle
player_body_hit
player_body_death
player_empty_shell_idle
player_possessed_overlay_active
enemy_weak_cultist_idle
enemy_weak_cultist_hit
enemy_weak_cultist_death
enemy_fast_fanatic_idle
enemy_fast_fanatic_hit
enemy_fast_fanatic_death
enemy_preacher_idle
enemy_preacher_hit
enemy_preacher_death
boss_mother_couponella_idle
boss_mother_couponella_hit
boss_mother_couponella_death
boss_attack_warning_marker_ready
possession_marked_vessel_ring_ready
possession_ready_marker_ready
possession_active_overlay_active
possession_exit_marker_active
arena_floor_corrupted_village_idle
prop_corrupted_village_house_idle
prop_altar_slot_machine_idle
prop_sacred_casino_candles_idle
prop_casino_religious_banner_idle
vfx_hit_impact_active
vfx_enemy_death_puff_active
vfx_possession_tether_flash_active
vfx_p03_explosion_active
```

## 2. UI Image Assets

Use `Unity UI Image` for Canvas assets. UI assets use Canvas/UI native scaling rather than gameplay PPU. Text, numbers, labels, card descriptions, and result copy must be Unity UI text layered separately.

UI asset IDs:
```text
ui_hp_frame_idle
ui_hp_fill_active
ui_possession_charge_frame_idle
ui_possession_charge_fill_active
ui_token_icon_idle
ui_room_progress_frame_idle
ui_room_progress_icon_active
ui_auto_attack_indicator_active
ui_auto_attack_indicator_disabled
ui_joystick_base_idle
ui_joystick_base_active
ui_joystick_knob_idle
ui_joystick_knob_active
slot_machine_body_idle
slot_machine_body_active
slot_reel_panel_idle
slot_symbol_token_idle
slot_symbol_candle_idle
slot_symbol_seal_idle
slot_symbol_eye_idle
ui_reward_card_frame_idle
ui_reward_card_frame_selected
ui_reward_card_frame_disabled
ui_reroll_icon_ready
ui_reroll_icon_disabled
reward_icon_standard_01
reward_icon_standard_02
reward_icon_p03_last_breath
reward_icon_standard_04
reward_icon_standard_05
reward_icon_standard_06
reward_icon_standard_07
reward_icon_standard_08
reward_icon_standard_09
reward_icon_standard_10
reward_icon_standard_11
reward_icon_standard_12
ui_cursed_deal_frame_active
ui_cursed_deal_icon_fanatical_credit
ui_victory_emblem_active
ui_defeat_emblem_active
ui_game_over_panel_bg_idle
ui_run_summary_frame_idle
ui_broken_seal_icon_idle
ui_meta_unlock_panel_decoration_idle
vfx_reward_reveal_sparkle_active
vfx_cursed_deal_smoke_active
```

## 3. Overlay/VFX Assets

Overlay and VFX sprites should be kept separate from base character sprites so Coder can toggle, pulse, scale, fade, or pool them safely.

Overlay/VFX asset IDs:
```text
player_possessed_overlay_active
boss_attack_warning_marker_ready
possession_marked_vessel_ring_ready
possession_ready_marker_ready
possession_active_overlay_active
possession_exit_marker_active
vfx_hit_impact_active
vfx_enemy_death_puff_active
vfx_possession_tether_flash_active
vfx_reward_reveal_sparkle_active
vfx_cursed_deal_smoke_active
vfx_p03_explosion_active
```

Rules:
- `possession_exit_marker_active` is non-damaging and must not call damage logic.
- `vfx_p03_explosion_active` is the only P03 Last Breath damaging possession-exit explosion.
- `player_possessed_overlay_active` and `possession_active_overlay_active` should layer over controlled bodies, not replace their base sprite.
- `boss_attack_warning_marker_ready` should render below characters but above arena floor.

## 4. Suggested Prefab Grouping

- `PlayerBodyPrefab`: `player_body_*`, `player_empty_shell_idle`, `player_possessed_overlay_active`.
- `WeakCultistPrefab`: `enemy_weak_cultist_*` plus optional possession marker attachments.
- `FastFanaticPrefab`: `enemy_fast_fanatic_*` plus optional possession marker attachments.
- `PreacherPrefab`: `enemy_preacher_*`.
- `MotherCouponellaPrefab`: `boss_mother_couponella_*` plus `boss_attack_warning_marker_ready` prefab reference.
- `CombatHudPrefab`: HP, possession charge, token, room progress, auto-attack indicator images.
- `FloatingJoystickPrefab`: joystick base/knob idle and active images only.
- `PossessionMarkerPrefab`: marked ring, ready marker, active overlay, exit marker, tether flash.
- `SlotRewardPresentationPrefab`: slot machine body states, reel panel, symbols, reward reveal VFX.
- `RewardCardPrefab`: reward card frame states plus reward icon image slot.
- `CursedDealPopupPrefab`: cursed deal frame/icon and smoke VFX.
- `ResultScreenPrefab`: victory/defeat emblems, game over panel, run summary frame.
- `MetaUnlockPanelPrefab`: Broken Seal icon and meta panel decoration.
- `EnvironmentRoomDecorPrefab`: arena floor plus non-interactive props.
- `CombatVfxPool`: hit impact, enemy death puff, P03 explosion.

## 5. Import Settings

- Texture Type: `Sprite (2D and UI)`.
- Sprite Mode: `Single`.
- Alpha Is Transparency: enabled.
- Generate Mip Maps: disabled.
- Filter Mode: `Bilinear` unless mobile readability tests favor `Point`.
- Compression: `None` or high quality for UI; gameplay compression only after readability testing.
- Pixels Per Unit: `128` for gameplay/world sprites.
- UI scaling: Canvas/UI native scaling for UI assets.
- Pivot: center-bottom for player, enemy, boss body, and prop sprites; center for UI, VFX, markers, reel symbols, arena floor, and overlays.
- UI frames may be sliced in Sprite Editor where useful.

## 6. Folder Ownership

- `Assets/Generated/_MANIFESTS/`: ArtDirector/PM documentation inputs. Do not edit during PNG generation without approval.
- `Assets/Generated/_ART_BIBLE/`: ArtDirector catalog and generation-readiness docs.
- `Assets/Generated/characters/`: Player, enemy, and boss source PNGs only.
- `Assets/Generated/possession/`: Possession marker/overlay source PNGs only.
- `Assets/Generated/slot_machine/`: Automatic reward machine body/reel/symbol source PNGs only.
- `Assets/Generated/ui/`: Canvas UI source PNGs only.
- `Assets/Generated/environment/`: Arena and non-interactive prop source PNGs only.
- `Assets/Generated/vfx/`: Combat, possession, reward, and P03 VFX source PNGs only.

## 7. Do-Not-Rename List

The following `asset_id` values are stable contract IDs for manifests, prompts, generation output, imports, prefabs, and Coder references:

```text
player_body_idle
player_body_hit
player_body_death
player_empty_shell_idle
player_possessed_overlay_active
enemy_weak_cultist_idle
enemy_weak_cultist_hit
enemy_weak_cultist_death
enemy_fast_fanatic_idle
enemy_fast_fanatic_hit
enemy_fast_fanatic_death
enemy_preacher_idle
enemy_preacher_hit
enemy_preacher_death
boss_mother_couponella_idle
boss_mother_couponella_hit
boss_mother_couponella_death
boss_attack_warning_marker_ready
ui_hp_frame_idle
ui_hp_fill_active
ui_possession_charge_frame_idle
ui_possession_charge_fill_active
ui_token_icon_idle
ui_room_progress_frame_idle
ui_room_progress_icon_active
ui_auto_attack_indicator_active
ui_auto_attack_indicator_disabled
ui_joystick_base_idle
ui_joystick_base_active
ui_joystick_knob_idle
ui_joystick_knob_active
possession_marked_vessel_ring_ready
possession_ready_marker_ready
possession_active_overlay_active
possession_exit_marker_active
slot_machine_body_idle
slot_machine_body_active
slot_reel_panel_idle
slot_symbol_token_idle
slot_symbol_candle_idle
slot_symbol_seal_idle
slot_symbol_eye_idle
ui_reward_card_frame_idle
ui_reward_card_frame_selected
ui_reward_card_frame_disabled
ui_reroll_icon_ready
ui_reroll_icon_disabled
reward_icon_standard_01
reward_icon_standard_02
reward_icon_p03_last_breath
reward_icon_standard_04
reward_icon_standard_05
reward_icon_standard_06
reward_icon_standard_07
reward_icon_standard_08
reward_icon_standard_09
reward_icon_standard_10
reward_icon_standard_11
reward_icon_standard_12
ui_cursed_deal_frame_active
ui_cursed_deal_icon_fanatical_credit
ui_victory_emblem_active
ui_defeat_emblem_active
ui_game_over_panel_bg_idle
ui_run_summary_frame_idle
ui_broken_seal_icon_idle
ui_meta_unlock_panel_decoration_idle
arena_floor_corrupted_village_idle
prop_corrupted_village_house_idle
prop_altar_slot_machine_idle
prop_sacred_casino_candles_idle
prop_casino_religious_banner_idle
vfx_hit_impact_active
vfx_enemy_death_puff_active
vfx_possession_tether_flash_active
vfx_reward_reveal_sparkle_active
vfx_cursed_deal_smoke_active
vfx_p03_explosion_active
```

## 8. Generation-to-Unity Handoff Rules

- PNG files must be saved strictly to `target_png_path`.
- `asset_id` values must not be renamed.
- Folder structure must not be changed without Architect approval.
- No new folders may be created outside `Assets/Generated/` without approval.
- Generated PNG passes must rely on `asset_prompts.csv`.
- Unity scripts must read/use already stable paths.
- Do not modify prompt files, `asset_prompts.csv`, or `_MANIFESTS` during a generation pass unless explicitly approved.
- Generated images must not contain readable text, letters, numbers, labels, watermarks, JPG artifacts, 3D render styling, or photorealism.
- No generated art may add dash buttons, manual possession buttons, manual slot spin buttons, pet/helper systems, post-MVP enemies, or post-MVP bosses.

