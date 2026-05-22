# UX/UI Spec - In-Game Buttons and Elements

## PART 1 - UX SPEC

### 1. Screen Purpose

Define where every in-game HUD element, button, modal, and touch control belongs during the MVP run so the player understands what is interactive and what is informational.

### 2. Player Goal

Move, survive, read run state, choose rewards, respond to the cursed deal, and finish or restart a run without being shown false combat buttons.

### 3. User Journey

1. Player starts a room.
2. Combat HUD appears with HP, room progress, token count, possession charge, auto-attack status, and lower-left movement joystick.
3. Player moves with the joystick while auto-attack and possession rules run without buttons.
4. Room clear opens the automatic machine reward flow.
5. Player chooses one reward card and may use reroll if charges remain.
6. On stop 2, player may accept or decline the cursed deal.
7. On defeat or victory, player uses result buttons to restart or return to MainMenu.

### 4. Navigation Logic

- Combat:
  - Game scene room start -> active combat.
  - Room clear -> automatic machine presentation.
  - HP zero -> defeat result.
- Reward:
  - Automatic machine presentation -> reward card screen.
  - Reward selected -> next room, boss route, or result route.
  - Stop 2 may open cursed deal modal.
- Results:
  - Defeat -> Restart or MainMenu.
  - Victory -> summary, first Broken Seal unlock if eligible, then Restart or MainMenu.

### 5. Interaction Logic

#### Combat Elements

| Element | Location | Interactive | Rule |
|---|---:|---:|---|
| Floating joystick | lower-left | yes, movement control | First touch sets center; release stops movement. |
| HP bar | top-left | no | Informational only. |
| Room progress | top-center | no | Informational only. |
| Token count | top-right | no | Informational only. |
| Possession charge | upper-mid | no | Shows charge/ready state; never a button. |
| Auto-attack indicator | right edge or upper side | no | Shows active/disabled state; never fires manually. |
| Marked vessel ring | world-space enemy marker | no | Proximity target, not a tap target. |
| Lower-right combat area | lower-right | no | Reserved empty zone; no ability cluster. |

#### Reward Elements

| Element | Location | Interactive | Rule |
|---|---:|---:|---|
| Slot machine reels | center/upper | no | Auto-roll presentation only. |
| Reward cards | central stack | yes | Player selects exactly one. |
| Reroll | lower-middle or near card footer | yes | Only in reward card screen; consumes one reroll charge. |
| Continue/apply | implicit after card selection | no extra button by default | Selection applies after short confirmation unless Architect chooses explicit confirm. |

#### Modal and Result Elements

| Element | Location | Interactive | Rule |
|---|---:|---:|---|
| Cursed Accept | modal bottom | yes | Stop 2 only. |
| Cursed Decline | modal bottom | yes | Must be equally reachable. |
| Result Restart | result bottom | yes | Primary result action. |
| Result MainMenu | result bottom | yes | Secondary result action. |
| Broken Seal Continue | unlock modal bottom | yes | Dismisses one-time unlock presentation. |

### 6. UX States

- Combat normal:
  - HUD visible.
  - Joystick available.
  - Lower-right empty.
- Combat low HP:
  - HP feedback becomes stronger, but no popup blocks movement.
- Possession ready:
  - Charge and vessel marker show readiness.
  - No possession button appears.
- Room clear:
  - Combat input pauses.
  - Reward flow starts automatically.
- Machine auto-roll:
  - Slot visuals animate.
  - No spin button appears.
- Reward choice:
  - Three reward cards are selectable.
  - Reroll is available only if charges remain.
- Cursed deal:
  - Modal blocks reward/background taps.
  - Accept and Decline are explicit choices.
- Result:
  - Combat input disabled.
  - Restart and MainMenu buttons available.

### 7. UX Rules

- Combat has exactly one direct touch control: the lower-left movement joystick.
- Never place dash, attack, possession, spin, pet, or ability buttons in combat.
- Persistent HUD elements are non-interactive unless explicitly listed as real buttons.
- The arena center must remain readable for player, enemies, markers, and telegraphs.
- Reward cards and reroll are inactive until combat is paused.
- Reroll must not be visually confused with slot spin.
- Result buttons must not become active until combat input is disabled.

## PART 2 - UI SPEC

### 1. Layout Structure

#### Combat HUD

- Top safe-area band:
  - HP bar left.
  - Room progress center.
  - Token count right.
- Upper-mid:
  - Possession charge.
- Arena center:
  - No permanent panels.
  - World-space markers and combat warnings only.
- Lower-left:
  - Floating joystick movement zone.
- Lower-right:
  - Empty reserved zone.
- Side/upper edge:
  - Small non-interactive auto-attack indicator.

#### Reward Screen

- Top:
  - Optional reward header and reroll count.
- Upper/mid:
  - Slot machine body/reel presentation while rolling.
- Mid:
  - Three reward cards in a vertical stack for narrow portrait.
  - Three compact columns may be allowed only if text remains readable and touch targets stay 48 dp or larger.
- Lower-middle:
  - Reroll button as secondary action.

#### Cursed Deal Modal

- Center:
  - Modal frame inside safe area.
- Top of modal:
  - Cursed deal icon.
- Middle:
  - Title and effect text.
- Bottom:
  - Accept and Decline.
  - Stack vertically if horizontal buttons would shrink.

#### Results

- Center:
  - Victory/defeat emblem and summary.
- Lower-middle:
  - Restart primary button.
  - MainMenu secondary button.
- Meta unlock modal:
  - Broken Seal icon, effect text, Continue button.

### 2. UI Components

- Combat HUD:
  - `ui_hp_frame_idle`
  - `ui_hp_fill_active`
  - `ui_possession_charge_frame_idle`
  - `ui_possession_charge_fill_active`
  - `ui_token_icon_idle`
  - `ui_room_progress_frame_idle`
  - `ui_room_progress_icon_active`
  - `ui_auto_attack_indicator_active`
  - `ui_auto_attack_indicator_disabled`
  - `ui_joystick_base_idle`
  - `ui_joystick_base_active`
  - `ui_joystick_knob_idle`
  - `ui_joystick_knob_active`
- Reward:
  - `slot_machine_body_idle`
  - `slot_machine_body_active`
  - `slot_reel_panel_idle`
  - `ui_reward_card_frame_idle`
  - `ui_reward_card_frame_selected`
  - `ui_reward_card_frame_disabled`
  - `ui_reroll_icon_ready`
  - `ui_reroll_icon_disabled`
- Cursed:
  - `ui_cursed_deal_frame_active`
  - `ui_cursed_deal_icon_fanatical_credit`
- Results:
  - `ui_victory_emblem_active`
  - `ui_defeat_emblem_active`
  - `ui_game_over_panel_bg_idle`
  - `ui_run_summary_frame_idle`
  - `ui_broken_seal_icon_idle`
  - `ui_meta_unlock_panel_decoration_idle`

### 3. Visual Hierarchy

1. Player, enemies, hazards, and target markers.
2. HP and possession charge.
3. Reward cards or modal decisions when combat is paused.
4. Primary result/reward buttons.
5. Secondary indicators and decorative panels.

### 4. Component States

- Joystick:
  - hidden/idle
  - active drag
  - release fade
- HUD:
  - normal
  - low HP
  - possession ready
  - room clear
- Reward cards:
  - hidden
  - reveal
  - selectable
  - selected
  - disabled
- Reroll:
  - ready
  - pressed
  - disabled/no charges
- Cursed modal:
  - hidden
  - open
  - accept applying
  - decline closing
- Results:
  - hidden
  - victory
  - defeat
  - buttons enabled
  - transition loading

### 5. Visual Style Direction

- Combat HUD should be compact and low-noise over gameplay.
- Reward UI may be more theatrical because combat is paused.
- Primary buttons use old-gold accents.
- Cursed decisions use crimson and void-violet danger accents.
- Disabled buttons should visibly dim and never look purchasable.
- Joystick should be translucent enough to avoid covering enemies.

### 6. Text / Copy

Use Unity UI text only:

- Room 1/5, or localized equivalent.
- Token number.
- Reroll x3, Reroll x2, Reroll x1, or No Rerolls.
- Accept.
- Decline.
- Restart.
- MainMenu.
- Continue.
- +1 Attack, -1 Max HP.
- +1 Starting Token.

No readable text should be baked into sprites or generated art.

### 7. Wireframes

#### Combat

```text
+------------------------------+
| HP          ROOM        TOKEN |
|        POSSESSION CHARGE      |
|                       AA icon |
|                              |
|          COMBAT ARENA         |
|   player / enemies / markers  |
|                              |
| joystick                      |
|                    empty zone |
+------------------------------+
```

#### Reward Cards

```text
+------------------------------+
|       reward / room clear     |
|      auto machine visual      |
|                              |
|       [ reward card 1 ]       |
|       [ reward card 2 ]       |
|       [ reward card 3 ]       |
|                              |
|          [ REROLL ]           |
+------------------------------+
```

#### Cursed Deal

```text
+------------------------------+
|      dimmed reward screen     |
|                              |
|        +--------------+       |
|        | cursed icon  |       |
|        | title/effect |       |
|        | [ Accept ]   |       |
|        | [ Decline ]  |       |
|        +--------------+       |
|                              |
+------------------------------+
```

#### Results

```text
+------------------------------+
|                              |
|       victory / defeat        |
|          run summary          |
|                              |
|          [ RESTART ]          |
|          [ MAINMENU ]         |
|                              |
+------------------------------+
```

## PART 3 - HANDOFF

### 1. Handoff To [[Architect]]

- Create separate layout roots for Combat HUD, Reward Screen, Cursed Deal Modal, Result Screen, and Meta Unlock Modal.
- Define a safe-area root for all screen-space UI.
- Keep world-space possession markers outside the screen-space button system.
- Preserve the lower-right combat empty zone in the implementation task cards.

### 2. Handoff To [[Coder]]

- Bind joystick only to movement.
- Do not bind attack, dash, possession, or slot spin actions to UI.
- Ensure HUD bars and indicators do not receive gameplay taps.
- Gate reroll to the reward card screen only.
- Gate cursed deal to stop 2 only.
- Disable combat input before result buttons become active.

### 3. Handoff To [[ArtDirector]]

- HUD, card, modal, and button sprites must not contain readable text.
- Leave blank areas for Unity UI labels and numeric values.
- Keep joystick art visually distinct from ability buttons.
- Keep reroll icon visually distinct from spin/start controls.

### 4. Handoff To [[QA]]

- Verify combat has no dash, attack, possession, spin, pet, or ability buttons.
- Verify lower-right combat area stays empty.
- Verify all real buttons are at least 48 x 48 dp equivalent.
- Verify reroll exists only on reward card screen and consumes a charge.
- Verify result buttons work only after combat is disabled.
- Verify safe-area behavior on narrow and tall portrait devices.
