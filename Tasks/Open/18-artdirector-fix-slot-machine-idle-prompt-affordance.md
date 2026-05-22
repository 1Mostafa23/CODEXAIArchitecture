---
task: "Fix Slot Machine Idle Prompt Affordance"
target: [[ArtDirector]]
source_agent: [[BA]]
input:
  - Assets/Generated/_MANIFESTS/asset_prompts.csv
  - Assets/Generated/_MANIFESTS/prompts_by_folder.md
  - Assets/Generated/slot_machine/body/slot_machine_body_idle.prompt.txt
  - GDD.md
status: fixed_ready_for_ba_recheck
---

# Handoff to ArtDirector

BA reviewed the MVP prompt pack for suitability before PNG generation.

## Result
The prompt pack is broadly suitable for the approved MVP art direction and scope, but one prompt should be revised before generating images.

## Blocking Prompt Issue

Asset:
- `slot_machine_body_idle`

Path:
- `Assets/Generated/slot_machine/body/slot_machine_body_idle.png`

Current risk:
- The prompt includes `lever-like ornament that is not a button`.
- Image generators may ignore the negation and produce a visible slot-machine lever or manual-spin affordance.
- That conflicts with the MVP rule: the machine auto-rolls and has no manual spin button or walk-up interaction.

## Required Edit
Update the prompt everywhere it appears:
- `Assets/Generated/_MANIFESTS/asset_prompts.csv`
- `Assets/Generated/_MANIFESTS/prompts_by_folder.md`
- `Assets/Generated/slot_machine/body/slot_machine_body_idle.prompt.txt`

Preserve:
- `asset_id`
- target PNG path
- prompt file path
- folder structure
- negative prompt
- size
- transparency
- Unity note meaning

Suggested subject replacement:

```text
grotesque sacred casino slot machine altar with candle horns, blank display panels, old-gold sealed side shrine ornaments, and no handle or lever
```

The final prompt must still follow:

```text
[subject], stylized dark cartoon with grotesque religious-casino motifs, charcoal old gold wax white crimson void violet palette, dark whimsical cult roguelite mood, 1024x1024 source PNG sprite readable at 64x64 with bold charcoal outline and centered silhouette, game asset, transparent background, no text, clean edges
```

## Acceptance Criteria
- No prompt for `slot_machine_body_idle` contains `lever-like`.
- No prompt for `slot_machine_body_idle` invites a handle, lever, button, or manual-spin affordance.
- No PNG images are generated in this task.
- No asset IDs, file paths, or folders are renamed.
- All readable text remains reserved for Unity UI.

## ArtDirector Result - 2026-05-17

Fixed.

Updated:
- `Assets/Generated/_MANIFESTS/asset_prompts.csv`
- `Assets/Generated/_MANIFESTS/prompts_by_folder.md`
- `Assets/Generated/slot_machine/body/slot_machine_body_idle.prompt.txt`
- `Assets/Generated/_MANIFESTS/mvp_sprite_asset_pack.md`

New subject:

```text
grotesque sacred casino slot machine altar with candle horns, blank display panels, old-gold sealed side shrine ornaments, and wax-drip side columns
```

Validation:
- `slot_machine_body_idle` prompt no longer contains `lever-like`, `handle`, `lever`, `button`, `manual spin`, or `spin affordance`.
- Prompt formula, negative prompt, target path, prompt file path, size, and transparency are preserved.
- No PNG files were generated.
