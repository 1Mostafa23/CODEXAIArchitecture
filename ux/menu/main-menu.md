# UX/UI Spec - MainMenu

## PART 1 - UX SPEC

### 1. Screen Purpose

MainMenu is the run entry screen. It lets the player start a run, see limited MVP meta status, and enter allowed lore/status areas without adding a shop, upgrade tree, IAP, ads, or post-MVP systems.

### 2. Player Goal

Start the next run quickly and understand whether the fixed Broken Seal meta unlock is locked or owned.

### 3. User Journey

1. Player launches the game or returns from a result screen.
2. MainMenu appears with the game identity, a clear Start Run action, and secondary status entries.
3. Player taps Start Run.
4. The game transitions to the Game scene.
5. If the player has won before, Broken Seal status can show as owned and communicate the +1 starting token effect.

### 4. Navigation Logic

- Entry points:
  - App launch.
  - Return to menu from defeat result.
  - Return to menu from victory result.
  - Return to menu after Broken Seal unlock dismissal.
- Primary exit:
  - Start Run routes to the Game scene.
- Secondary exits:
  - Broken Seal status opens a simple info panel only if implemented.
  - Lore fragments may open a simple list only if already supported by MVP scope.
- Do not add:
  - Shop.
  - Upgrade tree.
  - Hero select.
  - Ads.
  - IAP.
  - Multiplayer.
  - Settings unless separately approved.

### 5. Interaction Logic

- Start Run is the only primary CTA.
- Start Run must be immediately reachable in the lower-middle thumb zone.
- Broken Seal status is secondary and must not compete visually with Start Run.
- Locked Broken Seal status is informational only; it must not look purchasable.
- Lore fragments, if present, are secondary navigation and must never block Start Run.
- Back behavior from any menu subpanel returns to MainMenu, not directly into gameplay.

### 6. UX States

- First launch:
  - Broken Seal locked.
  - Start Run available.
- Returning from defeat:
  - Start Run remains primary.
  - No shame loop or forced tutorial prompt.
- Returning from victory before unlock dismissal:
  - If unlock presentation has not been shown, route to the Broken Seal unlock modal before regular menu interaction.
- Returning after first victory unlock:
  - Broken Seal owned.
  - Status communicates +1 starting token.
- Loading transition:
  - Start Run enters pressed/loading state and disables repeat taps.
- Unavailable secondary content:
  - Show disabled or hidden, but do not present it as a monetized lock.

### 7. UX Rules

- Menu should support one-handed portrait use.
- The bottom action stack should not collide with Android gesture navigation.
- Primary CTA is visually stronger than secondary actions.
- Secondary actions must not imply unapproved systems.
- Broken Seal is the only MVP meta unlock.
- All readable text is Unity UI text.

## PART 2 - UI SPEC

### 1. Layout Structure

- Top safe-area band:
  - Game title or logo treatment.
  - Optional small build/status text only for development builds.
- Upper/mid content:
  - Main character, sacred casino machine motif, or menu background art.
  - Keep art behind UI low enough in contrast to preserve button readability.
- Mid-lower status area:
  - Broken Seal status strip or small panel.
  - Optional lore fragments entry if supported.
- Bottom safe-area action stack:
  - Primary Start Run button.
  - Secondary actions below or above primary depending on final art composition.

Recommended vertical order:

1. Title.
2. Visual identity art.
3. Broken Seal status.
4. Start Run primary CTA.
5. Secondary menu actions.

### 2. UI Components

- Title/logo container.
- Background or key art layer.
- Primary button:
  - Start Run.
- Secondary button or row:
  - Lore Fragments, only if implemented.
- Status component:
  - Broken Seal locked/owned.
- Optional info modal:
  - Broken Seal effect text.
- Loading blocker:
  - Minimal overlay or disabled Start Run state.

### 3. Visual Hierarchy

1. Start Run button.
2. Game identity/title.
3. Broken Seal status.
4. Lore/status secondary actions.
5. Decorative art.

### 4. Component States

- Start Run:
  - idle
  - pressed
  - loading
  - disabled during scene transition
- Broken Seal:
  - locked
  - newly unlocked pending presentation
  - owned
- Lore fragments:
  - available
  - empty/unavailable
  - disabled
- Info modal:
  - hidden
  - open
  - closing

### 5. Visual Style Direction

- Charcoal base with old-gold primary CTA treatment.
- Wax-white text on dark panels for readability.
- Crimson accents should be rare and reserved for danger or cursed material, not the main Start Run CTA.
- Void-violet can support Broken Seal and possession-adjacent status.
- Buttons should be clear, rectangular, and easy to scan.

### 6. Text / Copy

Use Unity UI text only:

- Start Run
- Broken Seal
- Locked
- Owned
- +1 Starting Token
- Lore Fragments, only if implemented

Avoid:

- Buy
- Upgrade
- Shop
- Watch Ad
- Equip
- Select Hero

### 7. Wireframe

```text
+------------------------------+
| safe area                     |
|          GAME TITLE           |
|                              |
|      character / machine      |
|         background art        |
|                              |
|  [Broken Seal status row]     |
|                              |
|        [ START RUN ]          |
|        [ Lore Fragments ]     |
| bottom safe padding           |
+------------------------------+
```

## PART 3 - HANDOFF

### 1. Handoff To [[Architect]]

- Define MainMenu as a separate Canvas/screen from combat HUD and reward UI.
- Provide safe-area anchors for title, status row, and bottom action stack.
- Keep Broken Seal status separate from the first-victory unlock modal.

### 2. Handoff To [[Coder]]

- Bind Start Run to Game scene entry.
- Disable Start Run during scene transition to prevent duplicate loads.
- Read Broken Seal ownership from persistent state.
- Do not implement shop, upgrade tree, hero select, IAP, ads, or multiplayer from this spec.

### 3. Handoff To [[ArtDirector]]

- Menu art must leave a readable lower-middle button zone.
- Do not bake Start Run, Broken Seal, or any label into art.
- Keep key silhouettes readable behind dark UI panels.

### 4. Handoff To [[QA]]

- Verify Start Run is reachable and loads the Game scene.
- Verify Broken Seal status reflects locked/owned state.
- Verify no out-of-scope menu systems appear.
- Verify all menu buttons stay inside the safe area on narrow and tall portrait devices.
