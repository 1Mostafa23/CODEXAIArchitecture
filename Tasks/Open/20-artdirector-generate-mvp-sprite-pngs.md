---
task: "Generate MVP Sprite PNGs"
target: [[ArtDirector]]
source_agent: [[Architect]]
status: ready_for_artdirector
input:
  - GDD.md
  - Assets/Generated/_MANIFESTS/asset_prompts.csv
  - Assets/Generated/_MANIFESTS/mvp_sprite_asset_pack.md
  - Assets/Generated/_MANIFESTS/prompts_by_folder.md
  - Assets/Generated/_ART_BIBLE/game_objects_catalog.md
  - Assets/Generated/_ART_BIBLE/object_states_matrix.csv
  - Assets/Generated/_ART_BIBLE/style_rules.md
  - Assets/Generated/_ART_BIBLE/sprite_generation_readiness.md
  - Assets/Generated/_ART_BIBLE/unity_usage_notes.md
---

# ArtDirector Task - Generate MVP Sprite PNGs

## Purpose

Allow [[ArtDirector]] to generate all approved MVP sprite PNG files cleanly and safely.

Immediate project goal:

```text
Prepare and unblock clean PNG sprite generation by ArtDirector.
```

This task is art generation only. Unity implementation is out of scope for now.

## Scope

- Generate only the 78 PNG assets already listed in `Assets/Generated/_MANIFESTS/asset_prompts.csv`.
- Output type: PNG only.
- Output destination: exact `target_png_path` from `asset_prompts.csv`.
- Manual review will be done by the user, not [[QA]].
- Do not create [[Coder]] task cards in this task.
- Do not create [[QA]] task cards in this task.
- Do not implement Unity prefabs, scripts, import settings, scenes, or gameplay.

## Source Of Truth

- Manifest source: `Assets/Generated/_MANIFESTS/asset_prompts.csv`
- Style source: `Assets/Generated/_ART_BIBLE/style_rules.md`
- Object/state source: `Assets/Generated/_ART_BIBLE/game_objects_catalog.md`
- Matrix source: `Assets/Generated/_ART_BIBLE/object_states_matrix.csv`
- Prompt pack reference: `Assets/Generated/_MANIFESTS/prompts_by_folder.md`
- Pack plan reference: `Assets/Generated/_MANIFESTS/mvp_sprite_asset_pack.md`
- Individual prompt source: each row's `prompt_file_path`

For each sprite, the manifest row controls:

```text
asset_id
target_png_path
prompt_file_path
category
purpose
used_by
required_states
prompt
negative_prompt
size
transparency
unity_note
```

## ArtDirector Rules

- Generate PNG files only.
- Use each `prompt_file_path` as the base prompt.
- Strengthen the prompt using `Assets/Generated/_ART_BIBLE/style_rules.md`.
- Save every generated PNG strictly to its `target_png_path`.
- Do not rename `asset_id`.
- Do not rename files.
- Do not move folders.
- Do not edit `asset_prompts.csv`.
- Do not edit prompt files.
- Do not modify `_MANIFESTS/`.
- Do not generate extra gameplay assets.
- Do not create new folders outside `Assets/Generated/`.

## Hard Visual Restrictions

Generated sprites must not contain:

- readable text
- letters
- numbers
- watermark
- photorealism
- 3D render
- manual dash button
- manual attack button
- manual possession button
- manual slot spin button
- lever
- handle
- pet/helper system
- post-MVP enemies
- post-MVP bosses

## Special Slot-Machine Restriction

`slot_machine_body_idle` must not contain a lever, handle, button, pull mechanism, or any manual spin affordance.

The slot machine is an automatic post-combat ritual presentation, not a manual casino machine.

## Required Generation Workflow

For each of the 78 rows in `asset_prompts.csv`:

1. Read the manifest row.
2. Open the matching `prompt_file_path`.
3. Confirm the `asset_id` in the prompt file matches the manifest row.
4. Build the generation prompt from the existing asset prompt plus the art bible style lock.
5. Apply the existing `negative_prompt` plus the global hard restrictions above.
6. Generate a clean transparent PNG at the row's declared `size`.
7. Save the PNG exactly to `target_png_path`.
8. Do not create alternate versions unless explicitly requested by the user.
9. If a sprite cannot be generated without violating the manifest or style rules, skip it and report the blocker.

## Quality Checklist Per Sprite

Before accepting each generated PNG:

- matches `asset_id`
- saved to exact `target_png_path`
- follows existing `prompt_file_path`
- follows `Assets/Generated/_ART_BIBLE/style_rules.md`
- transparent background
- readable at 64x64
- no text, letters, or numbers
- no watermark
- no photorealism
- no 3D render
- no forbidden mechanic affordance
- consistent with `unity_note`
- state variants keep consistent scale and footprint where applicable

## Output Report Required

After generation, report:

```text
Generated:
- asset_id -> target_png_path

Skipped:
- asset_id -> reason

Warnings:
- any style, path, prompt, or Unity concerns

Verdict:
- READY_FOR_UNITY_IMPORT: YES/NO
```

## Acceptance Criteria

- One ArtDirector PNG generation task card exists.
- The card clearly says to generate only the 78 manifest-listed PNGs.
- The card clearly says to save each PNG to `target_png_path`.
- The card clearly says not to modify manifest, prompts, asset IDs, or folder structure.
- The card clearly says manual review will be done by the user, not [[QA]].
- The card clearly says Unity implementation is out of scope for now.
- No [[Coder]] task cards are created.
- No [[QA]] task cards are created.

## Handoff

Next recommended agent: [[ArtDirector]]

PM should start [[ArtDirector]] on this card to generate the MVP PNG sprites.
