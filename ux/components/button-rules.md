# UX/UI Spec - Shared Button Rules

## PART 1 - UX SPEC

### 1. Screen Purpose

Define shared rules for all MVP buttons so MainMenu, reward screens, modals, and result screens use consistent placement, sizing, states, and interaction meaning.

### 2. Player Goal

Know which elements can be tapped and avoid mistaking decorative or informational HUD elements for actions.

### 3. User Journey

1. Player sees a screen with one clear primary action.
2. Secondary actions are visually weaker and placed near the primary action only when relevant.
3. Disabled actions clearly communicate unavailable state without implying payment.
4. Button press feedback confirms the tap and blocks duplicate activation when needed.

### 4. Navigation Logic

- MainMenu:
  - Start Run is primary.
- Reward:
  - Reward cards are primary choices.
  - Reroll is secondary.
- Cursed deal:
  - Accept and Decline are parallel decision buttons.
- Results:
  - Restart is primary.
  - MainMenu is secondary.
- Meta unlock:
  - Continue is primary.

### 5. Interaction Logic

- Buttons activate on tap release inside bounds.
- Pressed state appears immediately on touch down.
- Loading state disables repeat taps.
- Disabled state blocks input and gives no reward/action.
- Cards can behave as large buttons if the full card is the selectable area.
- HUD frames, status bars, counters, indicators, and slot reels are never buttons.

### 6. UX States

- idle
- pressed
- selected
- disabled
- loading
- hidden
- locked informational

### 7. UX Rules

- Minimum touch target: 48 x 48 dp equivalent.
- Preferred primary button height: 56 dp or larger.
- Keep at least 8 dp spacing between adjacent buttons; use 12 to 16 dp for decision pairs when space allows.
- Never use disabled state to imply a paid unlock.
- Do not place destructive or decline actions where a player expects the primary continue/start button.
- Do not use combat button styling for joystick or HUD indicators.

## PART 2 - UI SPEC

### 1. Layout Structure

- Primary CTA:
  - Lower-middle on menu, result, and unlock screens.
  - Full-width within safe margins, about 72% to 84% of screen width.
- Secondary CTA:
  - Below primary if it is a less important route.
  - Above or beside primary only when it is a true binary decision.
- Icon-only buttons:
  - Avoid in MVP unless the meaning is obvious and a text label is nearby.
- Reward cards:
  - Full-card selectable area.
  - Text area must stay readable.

### 2. UI Components

- Primary button.
- Secondary button.
- Parallel decision buttons.
- Reward card button.
- Disabled button state.
- Loading button state.
- Selected card state.

### 3. Visual Hierarchy

1. Primary CTA or selected reward card.
2. Parallel decision choices in modals.
3. Secondary navigation.
4. Disabled/unavailable controls.
5. Decorative frames and icons.

### 4. Component States

- Primary button:
  - idle
  - pressed
  - loading
  - disabled
- Secondary button:
  - idle
  - pressed
  - disabled
- Decision button:
  - idle
  - pressed
  - applying
- Reward card:
  - idle
  - highlighted
  - selected
  - disabled

### 5. Visual Style Direction

- Primary buttons: old-gold frame/accent, high contrast wax-white text.
- Secondary buttons: darker fill, thinner old-gold border, less glow.
- Cursed Accept: crimson/void-violet accent but still readable.
- Cursed Decline: available and clear, not hidden or minimized.
- Disabled: desaturated and dimmed, no sparkle, no currency motif.

### 6. Text / Copy

- Use short verb labels:
  - Start Run
  - Reroll
  - Accept
  - Decline
  - Restart
  - MainMenu
  - Continue
- Avoid explanatory text inside buttons.
- Place longer explanations in nearby Unity UI text fields.
- No text in generated button art.

### 7. Wireframe

```text
Primary stack:

  [        PRIMARY ACTION        ]
  [       secondary action       ]

Parallel decision:

  [         Accept         ]
  [         Decline        ]

Reward card stack:

  [ icon | name            ]
  [ description text area  ]
  [ full card is tappable  ]
```

## PART 3 - HANDOFF

### 1. Handoff To [[Architect]]

- Define shared button prefabs or style variants only if that fits the Unity implementation plan.
- Keep reward card selection separate from regular CTA buttons.
- Keep joystick outside the shared button system.

### 2. Handoff To [[Coder]]

- Ensure disabled buttons consume no action.
- Prevent duplicate activation during loading/apply states.
- Make reward cards selectable as one large target.
- Do not attach Button components to HUD-only indicators.

### 3. Handoff To [[ArtDirector]]

- Button sprites should include frames/backgrounds only.
- Leave labels to Unity UI text.
- Provide selected/disabled visual states where needed.

### 4. Handoff To [[QA]]

- Verify all real buttons meet minimum target size.
- Verify disabled buttons do nothing.
- Verify selected reward card state is visible.
- Verify HUD elements are not tappable buttons.
