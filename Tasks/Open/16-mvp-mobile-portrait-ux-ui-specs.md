---
task: "MVP Mobile Portrait UX/UI Specs"
target: [[Architect]]
source_agent: [[UXDesigner]]
input:
  - GDD.md
  - Tasks/Open/15-create-mvp-ux-ui-specs.md
  - Tasks/Done/13-revalidate-possession-explosion.md
status: ready_for_architect
---

# MVP Mobile Portrait UX/UI Specs

Scope: active MVP only. These specs do not add gameplay, art assets, Unity prefabs, or code.

Platform: Android portrait.

Core guardrails:
- One floating joystick is the only combat input.
- No dash button.
- No manual possession button.
- No manual slot spin button or walk-up machine interaction.
- Auto-attack targets the nearest enemy.
- Possession auto-triggers only when charge is full and a marked vessel is in range.
- Default possession exit is non-damaging and must not look like an explosion.
- P03 Last Breath is the only MVP source of possession-exit explosion feedback.
- All readable text is Unity UI text, never baked into generated images.

Shared mobile rules:
- Safe area: all HUD and popup UI must stay inside device safe-area padding.
- Thumb zone: movement control belongs in the lower-left reach zone and may spawn near the first touch within the allowed lower half.
- Combat visibility: central arena and character silhouettes must remain unobstructed.
- Minimum touch target: 48x48 dp equivalent for buttons and selectable cards.
- Screen assumption: 9:16 portrait first; layouts must tolerate taller Android screens.
- Visual language: dark cartoon, grotesque sacred casino motifs, charcoal base, old-gold rewards, wax-white readable text panels, crimson danger, void-violet possession.

---

# UX/UI Spec - Combat HUD and Touch Controls

## PART 1 - UX SPEC

### 1. Screen Purpose
Show the run state during active room combat while keeping movement input simple and the arena readable.

### 2. Player Goal
Move around enemy waves, survive, collect tokens/passive progress, understand current health, possession charge, room progress, and auto-attack status without pressing combat buttons.

### 3. User Journey
1. Player enters a combat room.
2. HUD appears with health, possession charge, token count, room progress, and auto-attack indicator.
3. First touch in the lower-left movement zone creates or activates the floating joystick.
4. Releasing touch stops movement and fades joystick back to idle.
5. Auto-attack runs without player input.
6. When the room is clear, combat HUD remains visible briefly and the post-combat machine flow begins automatically.

### 4. Navigation Logic
- Entry: Game scene starts or next room begins.
- Exit: room clear routes automatically to post-combat machine reward flow for rooms 1-5; boss defeat routes to victory/result flow.
- Defeat: HP reaches zero and routes to Game Over defeat flow.
- No back/menu interaction is required for MVP combat.

### 5. Interaction Logic
- Floating joystick:
  - First valid touch in lower-left movement zone sets joystick center.
  - Drag controls movement vector.
  - Release returns movement vector to zero.
  - The joystick must not be a fixed button for any other action.
- Auto-attack:
  - Indicator communicates active or disabled state only.
  - Player cannot manually fire.
- HUD:
  - No HUD element should require taps during combat.
  - HUD must never obscure the player body, marked vessel ring, or boss warning marker.

### 6. UX States
- Room start: room progress updates and HUD settles before enemies become fully active.
- Normal combat: HP, possession charge, token count, and auto-attack indicator visible.
- Low HP: HP display uses stronger danger feedback but does not block control.
- Possession charging: charge fill grows clearly; no possession button appears.
- Auto-attack active: indicator shows active state.
- Auto-attack disabled/no target: indicator shows disabled state.
- Room clear: enemies gone, combat interaction pauses, transition into reward machine flow.
- Defeat: input disabled immediately, route to defeat result.

### 7. UX Rules
- The bottom-right area must remain free of fake ability buttons to avoid implying dash, possession, or attack input.
- HUD must support one-handed play with the thumb mostly in the lower-left quadrant.
- Health feedback should be readable at a glance without numeric dependency.
- Possession charge must communicate "not ready" vs "ready" before vessel proximity logic matters.
- Token count is informational only during combat.

## PART 2 - UI SPEC

### 1. Layout Structure
- Top safe-area band:
  - Left: HP frame/fill.
  - Center: room progress frame/icon.
  - Right: token icon/count.
- Upper-mid below top band:
  - Possession charge frame/fill as a compact horizontal bar or sealed gauge.
- Arena center:
  - No permanent UI panels.
- Lower-left:
  - Floating joystick base and knob within thumb zone.
- Lower-right:
  - Empty during MVP combat except transient non-interactive feedback if needed.
- Right edge or lower-top corner:
  - Auto-attack status indicator, small and non-clickable.

### 2. UI Components
- HP bar:
  - `ui_hp_frame_idle`
  - `ui_hp_fill_active`
- Possession charge:
  - `ui_possession_charge_frame_idle`
  - `ui_possession_charge_fill_active`
- Token display:
  - `ui_token_icon_idle`
  - Unity UI text count.
- Room progress:
  - `ui_room_progress_frame_idle`
  - `ui_room_progress_icon_active`
  - Unity UI room count if needed.
- Auto-attack indicator:
  - `ui_auto_attack_indicator_active`
  - `ui_auto_attack_indicator_disabled`
- Floating joystick:
  - `ui_joystick_base_idle`
  - `ui_joystick_base_active`
  - `ui_joystick_knob_idle`
  - `ui_joystick_knob_active`

### 3. Visual Hierarchy
1. Player/enemies and threat telegraphs.
2. HP and possession charge.
3. Room progress and tokens.
4. Joystick feedback.
5. Auto-attack indicator.

### 4. Component States
- HP: normal, low, empty.
- Possession charge: empty, filling, full/ready, spent.
- Joystick: hidden/idle, active drag, release fade.
- Auto-attack: active, disabled/no target.
- Room progress: current room, boss room, completed.

### 5. Visual Style Direction
- HUD frames use old-gold and wax-white readability over charcoal.
- HP danger accents use crimson.
- Possession charge uses void-violet with old-gold seal accents.
- Joystick should be low-opacity when idle and stronger when active.
- All HUD icons should use clean silhouettes readable on small screens.

### 6. Text / Copy
- Unity UI text only:
  - HP values optional.
  - Token count.
  - Room progress optional, such as "Room 2/5" or localized equivalent.
- Do not bake labels, numbers, or words into art.

### 7. Wireframe
```text
┌──────────────────────────────┐
│ HP BAR      ROOM       TOKEN │
│        POSSESSION CHARGE     │
│                              │
│                              │
│          COMBAT ARENA         │
│                              │
│   player/enemies/markers      │
│                              │
│                              │
│  joystick                     │
└──────────────────────────────┘
```

## PART 3 - HANDOFF

### 1. Handoff To [[Architect]]
- Define Canvas safe-area root and world-space gameplay layering separately.
- Architect should specify whether HUD VFX overlays are Screen Space Overlay or Camera.
- Combat HUD prefab should be independent from reward/result UI.

### 2. Handoff To [[Coder]]
- Implement joystick as movement-only.
- Do not bind any combat, dash, possession, or spin action to UI buttons.
- Expose HP, charge, token, room, and auto-attack state to UI presenters.

### 3. Handoff To [[ArtDirector]]
- Generate HUD and joystick sprites only as blank/iconic art with no readable text.
- Keep joystick low visual noise; it must not look like an ability button.

### 4. Handoff To [[QA]]
- Verify one-handed lower-left joystick usability.
- Verify no manual combat/possession/spin controls exist.
- Verify HUD remains inside safe area on narrow and tall Android portrait layouts.

---

# UX/UI Spec - Possession Marker and State Feedback

## PART 1 - UX SPEC

### 1. Screen Purpose
Communicate when a marked vessel exists, when possession is ready, when possession auto-triggers, and whether the player is currently controlling a vessel.

### 2. Player Goal
Understand which enemy can be possessed and move close enough at full charge without needing a possession button.

### 3. User Journey
1. Rooms 2-5 can spawn one marked vessel.
2. The vessel gets a visible ring/marker that remains readable over enemy motion.
3. Possession charge fills through combat.
4. When charge is full and the player approaches the marked vessel, a short ready/lock-in feedback appears.
5. After the 0.35s delay, control transfers automatically.
6. The hero body remains as an empty shell.
7. Active overlay identifies the controlled vessel.
8. On default possession end, use a non-damaging exit marker only.
9. If P03 is active, use the P03 explosion VFX instead of the default exit marker.

### 4. Navigation Logic
- This is an in-combat overlay system, not a separate screen.
- Entry: marked vessel spawn.
- Active possession entry: charge full plus proximity plus auto-trigger delay.
- Exit: possession timer end, room clear, controlled-enemy death, or defeat state.

### 5. Interaction Logic
- Player action is movement only.
- Proximity and charge determine possession; no tap target exists.
- Ready feedback should show cause and timing without requiring a button.
- The default exit marker must not imply damage, reward, or explosion.

### 6. UX States
- No vessel in room: no marker.
- Vessel marked but charge not full: marker ring visible, ready marker hidden or subdued.
- Charge full, out of range: marker ring becomes more visible.
- Charge full, in range: ready marker pulses during 0.35s delay.
- Possession active: controlled body gets overlay, hero shell remains visible and protected.
- Default exit: soft vanish/exit marker, no blast.
- P03 exit: explosion feedback with clear danger/damage identity.

### 7. UX Rules
- Marked vessel ring must be readable on weak cultist and fast fanatic silhouettes.
- Player must never interpret the default exit as an attack.
- P03 explosion must be visually stronger and clearly separate from default possession feedback.
- Possession UI must not block movement input.

## PART 2 - UI SPEC

### 1. Layout Structure
- World-space marker layered under or around the marked enemy.
- Ready marker layered above the marked enemy but below critical combat warnings.
- Active possession overlay attached to controlled enemy sprite.
- Empty shell remains in arena with subdued shell treatment.
- Possession charge HUD remains in top/upper area as defined in Combat HUD spec.

### 2. UI Components
- Marked vessel ring:
  - `possession_marked_vessel_ring_ready`
- Possession ready marker:
  - `possession_ready_marker_ready`
- Active possession overlay:
  - `possession_active_overlay_active`
  - `player_possessed_overlay_active` if layered on the player-controlled body.
- Exit marker:
  - `possession_exit_marker_active`
- Empty shell:
  - `player_empty_shell_idle`
- P03-only explosion:
  - `vfx_p03_explosion_active`

### 3. Visual Hierarchy
1. Enemy/player collision silhouettes.
2. Marked vessel ring and ready pulse.
3. Active possession overlay.
4. Exit/P03 feedback.
5. Charge HUD.

### 4. Component States
- Marker: hidden, marked, ready, triggering.
- Overlay: inactive, active, ending.
- Shell: absent, protected idle, restored.
- Exit: default non-damaging, P03 damaging.

### 5. Visual Style Direction
- Marking and active possession use void-violet with old-gold halo motifs.
- Default exit uses small, contained spirit release, no radial blast.
- P03 uses crimson and void-violet blast language with old-gold vessel halo fragments.

### 6. Text / Copy
- No text required in combat overlay.
- Optional tutorial/debug labels must remain Unity UI only and are not MVP production UI.

### 7. Wireframe
```text
┌──────────────────────────────┐
│        POSSESSION CHARGE     │
│                              │
│       enemy with marker      │
│          (ready pulse)       │
│                              │
│   empty shell     controlled │
│                 overlay body │
│                              │
│  joystick                    │
└──────────────────────────────┘
```

## PART 3 - HANDOFF

### 1. Handoff To [[Architect]]
- Separate default possession exit marker from P03 explosion VFX in task cards.
- Ensure layer ordering supports marker ring, enemy, overlay, and combat warnings.

### 2. Handoff To [[Coder]]
- Auto-trigger must be charge full plus marked-vessel range plus delay.
- Default exit must not apply area damage, extra token, pickup, or explosion VFX.
- P03 explosion trigger should be gated by reward ownership only.

### 3. Handoff To [[ArtDirector]]
- Generate default exit marker as a quiet spirit-release mark, not an explosion.
- Generate P03 VFX as the only explosion-like possession-exit art.

### 4. Handoff To [[QA]]
- Verify no possession button is present.
- Verify possession can be understood through movement/proximity.
- Verify P03 and default exit feedback are visually and mechanically distinct.

---

# UX/UI Flow - Post-Combat Machine Reward Flow

## PART 1 - UX FLOW

### 1. Flow Goal
Give the player one reward choice after each cleared room through an automatic sacred casino machine presentation.

### 2. Entry Points
- Room 1 clear.
- Room 2 clear, with cursed deal popup available.
- Room 3 clear.
- Room 4 clear.
- Room 5 clear before boss transition if the GDD sequence requires the fifth stop before final victory routing.

### 3. Step-by-Step Journey
1. Room clear freezes or soft-pauses combat threats.
2. Machine presentation appears automatically.
3. Slot body/reel panel animates an automatic roll; player does not press spin.
4. Three reward cards are revealed.
5. Player selects one card.
6. If reroll charges remain, player may reroll the three cards before selecting.
7. Selected card locks in, applies reward, then flow advances to next room or boss/result route.

### 4. Navigation Map
```text
Room clear
  -> Auto machine roll
  -> Three reward cards
  -> Optional reroll if charges > 0
  -> Select one reward
  -> Confirm/apply automatically
  -> Next room / boss / result
```

### 5. UX Edge Cases
- No rerolls left: reroll control is disabled and visibly unavailable.
- One card selected: other cards disabled during apply.
- Cursed deal on stop 2: cursed deal popup appears as a separate optional decision point, not a fourth standard reward card unless Architect validates a specific presentation.
- Reward pool placeholders: UI must support 12 standard rewards while not depending on final icon meaning for unnamed placeholders.
- Interrupted by defeat: reward flow should not open if defeat is already routed.

## PART 2 - UI FLOW

### 1. Screen List
- Machine auto-roll presentation.
- Reward card choice screen.
- Optional cursed deal popup on stop 2.

### 2. Shared UI Components
- Slot machine body:
  - `slot_machine_body_idle`
  - `slot_machine_body_active`
  - `slot_reel_panel_idle`
- Slot symbols:
  - `slot_symbol_token_idle`
  - `slot_symbol_candle_idle`
  - `slot_symbol_seal_idle`
  - `slot_symbol_eye_idle`
- Reward card frames:
  - `ui_reward_card_frame_idle`
  - `ui_reward_card_frame_selected`
  - `ui_reward_card_frame_disabled`
- Reroll icon:
  - `ui_reroll_icon_ready`
  - `ui_reroll_icon_disabled`
- Reward icons:
  - 12 standard reward icon slots, including `reward_icon_p03_last_breath`.

### 3. Visual Consistency Rules
- Machine uses old-gold and crimson sacred casino emphasis.
- Reward cards should keep text areas blank in generated art; names/descriptions are Unity UI.
- Three card layout must be readable in portrait without horizontal scrolling.
- Reroll is a real button only in the reward screen, not in combat and not a spin button.

### 4. Transition / Animation Direction
- Room clear: short fade or snap to reward overlay.
- Auto-roll: reels animate without touch prompt.
- Card reveal: three cards reveal with old-gold sparkle.
- Reroll: cards flip or dissolve and reveal new set.
- Selection: chosen card enlarges slightly; unchosen cards dim.
- Apply: quick confirmation feedback, then transition out.

## PART 3 - HANDOFF

### 1. Architect Notes
- Create task cards for reward presentation UI, reward cards, reroll state, and stop routing.
- Keep machine auto-roll presentation distinct from card selection logic.

### 2. Coder Notes
- Do not implement a manual spin input.
- Reroll replaces all three cards and consumes one of three run charges.
- Selection applies one reward and closes the flow.

### 3. ArtDirector Notes
- Machine, reel, card frames, and symbols must have no readable text.
- Reward icon placeholders may stay abstract until final reward definitions are assigned.

### 4. QA Notes
- Verify exactly three standard reward cards appear.
- Verify reroll button availability matches remaining charges.
- Verify no paid buff, spin button, or extra reward choice appears.

---

# UX/UI Spec - Cursed Deal Popup on Stop 2

## PART 1 - UX SPEC

### 1. Screen Purpose
Offer the stop-2-only optional cursed deal as a clear risk/reward decision.

### 2. Player Goal
Understand that accepting Fanatical Credit grants attack power at the cost of max HP, and choose accept or decline without confusing it with standard rewards.

### 3. User Journey
1. Player clears room 2.
2. Machine reward flow runs.
3. Cursed deal popup appears at the stop-2 decision point.
4. Player chooses accept or decline.
5. Flow returns to reward progression or advances according to Architect's final ordering.

### 4. Navigation Logic
- Entry: only machine stop 2.
- Exit accept: apply cursed deal, close popup.
- Exit decline: close popup without effect.
- Popup must not appear on stops 1, 3, 4, 5, boss result, or MainMenu.

### 5. Interaction Logic
- Two explicit choices:
  - Accept.
  - Decline.
- Accept is not auto-selected.
- Decline must be reachable and visually clear.
- The popup blocks reward/background interactions while open.

### 6. UX States
- Available on stop 2.
- Accepted.
- Declined.
- Not available on all other stops.

### 7. UX Rules
- Cursed deal is optional.
- It must not be framed as a paid offer.
- It must not imply extra currencies or IAP.
- The cost and benefit must be readable as Unity UI text.

## PART 2 - UI SPEC

### 1. Layout Structure
- Center modal inside safe area.
- Top: cursed deal icon/emblem.
- Middle: title and short effect copy as Unity UI text.
- Bottom: Accept and Decline buttons, side by side or stacked for narrow screens.
- Background: dimmed reward machine or reward screen.

### 2. UI Components
- `ui_cursed_deal_frame_active`
- `ui_cursed_deal_icon_fanatical_credit`
- Unity UI title text.
- Unity UI effect text.
- Accept button.
- Decline button.

### 3. Visual Hierarchy
1. Cursed deal title/icon.
2. Effect: plus attack, minus max HP.
3. Accept/decline choices.
4. Dimmed background.

### 4. Component States
- Modal: hidden, open, closing.
- Accept: idle, pressed, disabled during apply.
- Decline: idle, pressed, disabled during close.

### 5. Visual Style Direction
- Cursed deal uses crimson and void-violet danger accents with old-gold temptation.
- Frame should feel distinct from standard reward cards.
- Decline remains visually available, not hidden or minimized.

### 6. Text / Copy
- Unity UI text only:
  - Title: localized cursed deal name.
  - Effect: "+1 Attack, -1 Max HP" or localized equivalent.
  - Buttons: "Accept" and "Decline" or localized equivalents.
- No text baked into art.

### 7. Wireframe
```text
┌──────────────────────────────┐
│        dimmed reward UI       │
│      ┌────────────────┐       │
│      │ cursed icon     │       │
│      │ title           │       │
│      │ +attack / -hp   │       │
│      │ [Accept]        │       │
│      │ [Decline]       │       │
│      └────────────────┘       │
└──────────────────────────────┘
```

## PART 3 - HANDOFF

### 1. Handoff To [[Architect]]
- Define final ordering relative to standard reward selection if needed, but do not change stop-2-only rule.
- Cursed popup should be a modal UI task separate from standard card frame tasks.

### 2. Handoff To [[Coder]]
- Gate popup to stop 2 only.
- Ensure accept and decline are mutually exclusive and one-shot.
- Use Unity UI text for effect values.

### 3. Handoff To [[ArtDirector]]
- Generate cursed frame/icon without labels, numbers, letters, or baked copy.

### 4. Handoff To [[QA]]
- Verify popup appears only on stop 2.
- Verify accept applies both benefit and cost.
- Verify decline applies nothing.
- Verify no IAP/payment presentation exists.

---

# UX/UI Flow - Game Over, Victory, and Defeat Results

## PART 1 - UX FLOW

### 1. Flow Goal
End a run clearly, distinguish victory from defeat, summarize the run, and allow quick restart or return to MainMenu.

### 2. Entry Points
- Defeat: player HP reaches zero.
- Victory: boss Mother Couponella is defeated.

### 3. Step-by-Step Journey
1. Combat input is disabled.
2. Result transition plays.
3. Result screen shows victory or defeat emblem.
4. Run summary appears.
5. Player chooses quick restart or return to menu.
6. If first boss victory unlocks Broken Seal, meta unlock presentation follows victory result or appears after the player dismisses result summary.

### 4. Navigation Map
```text
HP zero -> Defeat result -> Restart / MainMenu
Boss defeated -> Victory result -> Summary -> First meta unlock if eligible -> Restart / MainMenu
```

### 5. UX Edge Cases
- Defeat during possession: result must still be based on hero body HP rule.
- Victory and defeat should be mutually exclusive.
- Restart clears run state but keeps earned meta unlocks.
- First victory unlock should not appear repeatedly after already unlocked.

## PART 2 - UI FLOW

### 1. Screen List
- Defeat result screen.
- Victory result screen.
- Run summary panel.
- First meta unlock presentation if eligible.

### 2. Shared UI Components
- `ui_victory_emblem_active`
- `ui_defeat_emblem_active`
- `ui_game_over_panel_bg_idle`
- `ui_run_summary_frame_idle`
- Unity UI result title, summary values, restart button, menu button.

### 3. Visual Consistency Rules
- Victory: old-gold and wax-white emphasis.
- Defeat: charcoal, crimson, and void-violet emphasis.
- Summary text must be readable over panel background.
- Buttons must be large enough for thumb tapping.

### 4. Transition / Animation Direction
- Defeat: quick dark fade, emblem settles.
- Victory: brighter old-gold burst, emblem settles.
- Summary: frame slides/fades in after emblem.
- Button press: brief visual depress and transition.

## PART 3 - HANDOFF

### 1. Architect Notes
- Result UI should be scene or overlay compatible with GameOver scene.
- Separate victory, defeat, summary, and unlock routing responsibilities.

### 2. Coder Notes
- Disable combat input before result UI accepts taps.
- Provide restart and menu navigation.
- Trigger Broken Seal unlock only after first boss victory if not already unlocked.

### 3. ArtDirector Notes
- Result emblems and panels must be blank of readable text.
- Leave central panel room for Unity UI summary text.

### 4. QA Notes
- Verify defeat route from HP zero.
- Verify victory route from boss kill.
- Verify possession does not break defeat routing.
- Verify restart and menu buttons work from both result types.

---

# UX/UI Spec - First Meta Unlock Presentation

## PART 1 - UX SPEC

### 1. Screen Purpose
Present the first fixed meta unlock, Broken Seal, after first boss victory.

### 2. Player Goal
Understand that a permanent unlock was gained and that future runs start with +1 token.

### 3. User Journey
1. Player wins against the boss for the first time.
2. Victory result appears.
3. Meta unlock panel appears after result summary or as the next modal.
4. Player dismisses the panel.
5. Player can restart or return to MainMenu.

### 4. Navigation Logic
- Entry: first boss victory only.
- Exit: dismiss/continue.
- Repeat: do not show if Broken Seal is already unlocked.

### 5. Interaction Logic
- One primary continue/dismiss button.
- No shop, upgrade tree, IAP, or additional unlock list.
- Panel blocks background until dismissed.

### 6. UX States
- Locked before first boss victory.
- Newly unlocked presentation.
- Already unlocked, no popup.

### 7. UX Rules
- Keep the unlock presentation short.
- Do not imply a broader meta system beyond the fixed MVP unlock.
- The unlock effect must be Unity UI text, not baked image text.

## PART 2 - UI SPEC

### 1. Layout Structure
- Center modal panel inside safe area.
- Top: Broken Seal icon.
- Middle: unlock name and effect copy.
- Bottom: Continue button.
- Optional subdued result background behind modal.

### 2. UI Components
- `ui_broken_seal_icon_idle`
- `ui_meta_unlock_panel_decoration_idle`
- Unity UI title text.
- Unity UI effect text.
- Continue button.

### 3. Visual Hierarchy
1. Broken Seal icon.
2. Unlock title.
3. Effect text.
4. Continue button.

### 4. Component States
- Panel: hidden, reveal, open, dismissed.
- Continue: idle, pressed.
- Unlock: newly unlocked, already owned.

### 5. Visual Style Direction
- Old-gold sacred seal with void-violet crack.
- Less threatening than cursed deal; more ceremonial and clean.
- Panel decoration leaves a blank center for UI text.

### 6. Text / Copy
- Unity UI text only:
  - "Broken Seal" or localized equivalent.
  - "+1 Starting Token" or localized equivalent.
  - "Continue" or localized equivalent.
- No readable text baked into art.

### 7. Wireframe
```text
┌──────────────────────────────┐
│       dimmed victory UI       │
│      ┌────────────────┐       │
│      │ broken seal     │       │
│      │ unlock name     │       │
│      │ unlock effect   │       │
│      │ [Continue]      │       │
│      └────────────────┘       │
└──────────────────────────────┘
```

## PART 3 - HANDOFF

### 1. Handoff To [[Architect]]
- Create a small meta unlock presentation task; do not design a full meta progression system.
- Define persistent flag dependency for Broken Seal ownership.

### 2. Handoff To [[Coder]]
- Trigger once after first boss victory.
- Persist ownership.
- Apply +1 starting token on future runs.

### 3. Handoff To [[ArtDirector]]
- Generate icon and panel decoration without text.
- Keep icon readable at 64x64.

### 4. Handoff To [[QA]]
- Verify unlock appears only after first boss victory.
- Verify it does not repeat after ownership is set.
- Verify future run starts with the extra token.

---

# Consolidated Architect Checklist

Architect should create implementation task cards for:
- Combat HUD safe-area Canvas and state presenters.
- Floating joystick movement-only control.
- Possession marker/ready/active/default-exit/P03 feedback separation.
- Post-combat automatic slot machine reward flow.
- Reward card selection and reroll states.
- Stop-2-only cursed deal popup.
- Victory/defeat result flow and run summary.
- First Broken Seal meta unlock presentation.
- Art generation/import tasks for the sprite assets referenced above.
- QA cards for portrait safe-area, no-extra-controls, possession/P03 separation, reward cadence, and unlock persistence.
