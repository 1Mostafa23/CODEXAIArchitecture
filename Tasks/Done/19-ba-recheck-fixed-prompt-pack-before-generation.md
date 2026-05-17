---
task: "Re-check Fixed Prompt Pack Before Image Generation"
target: [[BA]]
source_agent: [[PM]]
input:
  - Assets/Generated/_MANIFESTS/asset_prompts.csv
  - Assets/Generated/_MANIFESTS/prompts_by_folder.md
  - Assets/Generated/slot_machine/body/slot_machine_body_idle.prompt.txt
  - Tasks/Open/18-artdirector-fix-slot-machine-idle-prompt-affordance.md
  - GDD.md
status: approved_for_image_generation
---

# Handoff to BA

Re-check the fixed sprite prompt pack before any production PNG generation.

## Context
[[BA]] previously found one blocker in `slot_machine_body_idle`: the prompt used `lever-like ornament`, which could generate a manual-spin affordance.

[[ArtDirector]] fixed the prompt and updated:
- `Assets/Generated/_MANIFESTS/asset_prompts.csv`
- `Assets/Generated/_MANIFESTS/prompts_by_folder.md`
- `Assets/Generated/slot_machine/body/slot_machine_body_idle.prompt.txt`
- `Assets/Generated/_MANIFESTS/mvp_sprite_asset_pack.md`

## Required Validation
Confirm:
- `slot_machine_body_idle` no longer invites a handle, lever, button, manual spin, or walk-up interaction.
- The prompt pack still follows the approved MVP art direction.
- The prompt pack still preserves the no-readable-text rule.
- The prompt pack does not introduce dash, manual attack, manual possession, manual slot spin, pet/helper systems, IAP, or post-MVP content.
- No PNG files were generated during the fix.

## Expected Result
If approved, mark the prompt pack suitable for image generation.

## Deadline
Next BA session.

## BA Result - 2026-05-17

Validation approved.

Pass:
- `slot_machine_body_idle` no longer invites a handle, lever, button, manual spin, spin affordance, or walk-up interaction.
- The fixed `slot_machine_body_idle` prompt now uses sealed side shrine ornaments and wax-drip side columns as passive decoration.
- The prompt pack still follows the approved MVP art direction: stylized dark cartoon, grotesque religious-casino motifs, charcoal/old-gold/wax-white/crimson/void-violet palette, dark whimsical cult roguelite mood.
- All 78 CSV prompt rows keep the required prompt formula ending: `game asset, transparent background, no text, clean edges`.
- All 78 prompt rows use the standard negative prompt.
- All 78 prompt rows specify transparent output and source size of at least 512x512.
- No prompt introduces dash, manual attack, manual possession, manual slot spin, pet/helper systems, IAP, ads, multiplayer, or post-MVP content.
- No prompt invites readable text, labels, words, inscriptions, or typography.
- No PNG files were generated during the fix or re-check.

Decision:
- The prompt pack is suitable for image generation from a BA requirements standpoint.

Remaining pipeline note:
- Production PNG generation should still follow PM/Architect routing for implementation and art-generation task cards.
