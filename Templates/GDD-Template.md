---
type: GDD
status: 📝 Draft
version: 1.0
last_validated: 
lead_designer: "[[GameDesigner]]"
validator: "[[BA]]"
---

# 📖 Game Design Document: [Project Name]

> [!abstract] Overview
> This is the central source of truth for the game's design. Every system, mechanic, and content piece defined here must be validated by [[BA]] and broken down into tasks by [[PM]].
> 
> **Instructions**: Fill each section. Do not delete headings; mark "N/A" if not used for MVP.

---

## 🗺️ Map of Content
| Section | Description | Status |
| :--- | :--- | :--- |
| [[#🚀 Elevator Pitch]] | High-level vision and player fantasy. | 📝 Draft |
| [[#🔄 Core Loop]] | The heartbeat of the gameplay. | 📝 Draft |
| [[#🎮 Platform & Controls]] | Mobile portrait UX and input model. | 📝 Draft |
| [[#⚙️ Systems (MVP)]] | Technical breakdown of core mechanics. | 📝 Draft |
| [[#👾 Content & Bestiary]] | Enemies, bosses, and environmental zones. | 📝 Draft |
| [[#🎨 Art Style]] | Visual direction and thematic goals. | 📝 Draft |
| [[#🎯 MVP Scope]] | Acceptance criteria and definition of "Done". | 📝 Draft |
| [[#🚫 Out of Scope]] | What we are explicitly NOT building. | 📝 Draft |

---

## 🚀 Elevator Pitch
### The Hook
*One sentence that sells the game.*

### Player Fantasy
*What does the player feel while playing? (e.g. "I am a powerful sorcerer but I can't stop sneezing")*

### The "Bet"
*Why will this game succeed? What is the unique combination?*

---

## 🔄 Core Loop
> [!info] The Loop
> 1. **[Action]**: [Primary mechanic]
> 2. **[Reward]**: [Immediate feedback/currency]
> 3. **[Upgrade]**: [Power curve/progression]
> 4. **[Goal]**: [Win/Loss condition]

### Win/Loss Conditions
- **Victory**: [Condition]
- **Defeat**: [Condition]

---

## 🎮 Platform & Controls
- **Target Platform**: Android (Portrait)
- **Input Model**: [e.g. Floating joystick, auto-attack]
- **Target Performance**: 60 FPS

### Control Table
| Input | Action | Logic |
| :--- | :--- | :--- |
| Tap | [Action] | [Behavior] |
| Drag | [Action] | [Behavior] |

---

## ⚙️ Systems (MVP)
> [!todo] System Specs
> These will be expanded into [[Tasks]] for [[Architect]] and [[Coder]].

| System | Description | Priority |
| :--- | :--- | :--- |
| [System 1] | [What it does] | P0 |
| [System 2] | [What it does] | P0 |

---

## 👾 Content & Bestiary
### Zones (Biomes)
- **[Zone 1]**: [Visual/Gameplay theme]

### Bestiary
| Name | Role | Behavior |
| :--- | :--- | :--- |
| [Enemy A] | Fodder | Chases player, deals contact damage. |
| [Boss B] | Finisher | Two phases, area-of-effect attacks. |

---

## 🎨 Art Style
- **Visual Direction**: [e.g. Stylized dark cartoon]
- **Key Palette**: [Colors or hex codes]
- **Key Asset Formulas**: [FLUX/ComfyUI prompt tips]

---

## 🎯 MVP Scope
> [!check] Acceptance Criteria
> Used by [[QA]] to verify the final build with [[STATUS]] and [[TASKS]].

- [ ] **[Feature A]**: [Description of behavior]
- [ ] **[Feature B]**: [Description of behavior]

---

## 🚫 Out of Scope (v1)
- Multiplayer
- Meta-progression
- IAP / Ads
