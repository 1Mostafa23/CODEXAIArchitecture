---
type: GDD
status: 📝 Draft
version: 1.1
last_validated: 2026-05-15
lead_designer: "[[GameDesigner]]"
validator: "[[BA]]"
---

# 📖 Game Design Document — Евангелие Джекпота

> [!abstract] Overview
> **Евангелие Джекпота** — это mobile-first roguelite в портретной ориентации, где посланник Хранителей Вселенной очищает зараженный культом мир, вселяется во врагов и после каждой очищенной комнаты получает случайное благословение от демонического автомата-казино.
> 
> Written by: [[GameDesigner]]
> Validation: [[BA]] approved on 2026-05-15

---

## 🗺️ Map of Content
| Section | Description | Status |
| :--- | :--- | :--- |
| [[#🚀 Elevator Pitch]] | Hook, Fantasy, and Design Bet. | ✅ Validated |
| [[#🔄 Core Loop]] | Gameplay heartbeat and Win/Loss rules. | ✅ Validated |
| [[#🎮 Platform & Controls]] | Input model and possession mechanics. | ✅ Validated |
| [[#⚙️ Systems (MVP)]] | Slot machine, reward pools, and progression. | ✅ Validated |
| [[#👾 Content & Bestiary]] | Zones, enemies, and boss specs. | ✅ Validated |
| [[#🎬 Scenes]] | Game flow and screen structure. | ✅ Validated |
| [[#🎨 Art Style]] | Visual direction and FLUX prompts. | ✅ Validated |
| [[#🎯 MVP Scope]] | Acceptance criteria for technical validation. | ✅ Validated |
| [[#🚫 Out of Scope]] | Explicitly excluded features. | ✅ Validated |

---

## 🚀 Elevator Pitch
### The Hook
Портретный roguelite про охоту на культ демона-лотереи: двигайся между волнами, заманивай отмеченных врагов под автоматическое вселение и выбирай благословения из автомата, который сам запускается после каждой комнаты.

### Player Fantasy
Игрок чувствует себя санитаром сломанной веры: он забирает у культа его же инструменты, превращает фанатиков и игровые автоматы против демона, осознавая, что "Хранители Вселенной" тоже не невинны.

### The "Bet"
Центральная ставка на две опоры:
1. **Демонический автомат-казино** как основной источник риска, юмора и лора.
2. **Временное вселение во врагов** как автоматическое контекстное событие (без лишних кнопок).

---

## 🔄 Core Loop
> [!info] The Loop
> 1. **Зачистка**: Игрок движется по арене, герой атакует ближайшую цель автоматически.
> 2. **Сбор**: Убийство врагов дает жетоны и заряжает шкалу вселения.
> 3. **Вселение**: Автоматический переход в отмеченный сосуд при сближении.
> 4. **Награда**: Появление Священного Автомата после зачистки комнаты и выбор баффа.

### Win/Loss Conditions
- **Victory**: Убийство босса Матушки Купонеллы в конце 5-й комнаты.
- **Defeat**: Здоровье тела героя падает до нуля (даже если он внутри врага).

---

## 🎮 Platform & Controls
- **Target Platform**: Android (Portrait)
- **Input Model**: Floating Virtual Joystick (Movement-only)
- **Target Performance**: 60 FPS | 7 min run target.

### Control Table
| Input | Action | Logic |
| :--- | :--- | :--- |
| Floating Stick | Movement | First touch sets center; release stops movement. |
| Automatic | Attack | Target nearest enemy within 6m; 0.75s interval. |
| Proximity | Possession | Auto-trigger at 100% charge within 2.5m of marked vessel (0.35s delay). |

### Possession Rules
- **Empty Shell**: Hero body remains on arena with 60% damage resistance.
- **Duration**: Base 6 seconds.
- **Vessels**: 1 marked vessel per rooms 2-5 (weak cultist or fast fanatic).

---

## ⚙️ Systems (MVP)
> [!todo] System Specs
> Key systems for the [[Architect]] to break down.

| System | Description | Priority |
| :--- | :--- | :--- |
| **Slot Machine** | Post-combat auto-roll, 3 cards, 1 choice. | P0 |
| **Wave Director** | 5 rooms + 1 boss; enemy & vessel spawning. | P0 |
| **Reward Engine** | Pool of 12 standard cards + 1 cursed deal. | P0 |

### Slot Machine Mechanics
- **Cadence**: Automatically appears after rooms 1, 2, 3, 4, and 5.
- **Rerolls**: 3 charges per run (replaces all 3 cards).
- **Cursed Deal**: "Фанатичный кредит" (+1 Attack, -1 Max HP) available ONLY on 2nd stop.

---

## 👾 Content & Bestiary
### Zones (Biomes)
- **Зараженная деревня "Приход Первого Спина"**: Гнилые домики, вывески-молитвы, алтарные автоматы.

### Bestiary
| Name | Role | Behavior |
| :--- | :--- | :--- |
| Слабый культист | Fodder | Chases in groups; candle toss/knife. |
| Быстрый фанатик | Rusher | Fast bursts of movement; jump attack. |
| Проповедник | Ranged | Stays at edges; shout cones/projectiles. |
| Матушка Купонелла | Boss | AOE "Discount Tapes" and cultist summons. |

---

## 🎬 Scenes
| Scene | Purpose |
| :--- | :--- |
| MainMenu | Start, Meta-unlocks (Broken Seal), Lore fragments. |
| Game | The 5-room + boss gameplay run. |
| GameOver | Summary, fragments found, quick restart. |

---

## 🎨 Art Style
- **Visual Direction**: Stylized dark cartoon; grotesque religious-casino motifs.
- **Key Palette**: Charcoal `#17151A`, Old Gold `#C89B3C`, Wax White `#E8DCC2`, Crimson `#9E2431`, Void Violet `#6D4BC3`.
- **FLUX Formula**: `dark whimsical cult roguelite, grotesque sacred casino machine, stylized mobile game asset, readable silhouette, old gold and crimson accents, black humor`.

---

## 🎯 MVP Scope
> [!check] Acceptance Criteria (Selected)
> - [ ] Movement-only portrait controls; no combat buttons.
> - [ ] 5 combat rooms + 1 boss (total 6-8 min run).
> - [ ] Slot machine auto-roll after every room (1-5).
> - [ ] Possession auto-trigger on marked vessels only.
> - [ ] Reward pool of 12 cards + 1 cursed deal.
> - [ ] Meta-unlock: "Broken Seal" (+1 Starting Token).

---

## 🚫 Out of Scope (v1)
- Manual dash/possession buttons.
- Multiple heroes or 6-zone campaign.
- IAP, Ads, or Multiplayer.
- Procedural map/branching routes.
