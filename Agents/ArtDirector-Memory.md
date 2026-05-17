---
type: InstanceFrame
owner: "[[ArtDirector]]"
---
# ArtDirector-Memory

> Write rule: append to **Recent**. Move oldest to **Archive** when Recent exceeds 3 entries.

## Recent
- 2026-05-17 - Created the planned empty `Assets/Generated/` folder tree and `Assets/Generated/_MANIFESTS/mvp_sprite_asset_pack.md` as the complete MVP sprite pack plan and Coder handoff. No PNGs were generated.
- 2026-05-17 - Exported the MVP sprite prompt pack from the manifest into `Assets/Generated/_MANIFESTS/asset_prompts.csv`, `Assets/Generated/_MANIFESTS/prompts_by_folder.md`, and one `.prompt.txt` file beside each planned PNG path. No PNGs, prefabs, or code were generated.
- 2026-05-17 - Fixed the `slot_machine_body_idle` prompt affordance risk by removing lever/button wording from the CSV, grouped prompt markdown, prompt txt, and source manifest. No PNGs were generated.

## Archive
*(none)*

## Asset Registry
| Asset | Path | Dimensions | Task |
|-------|------|------------|------|
| *(none)* | | | |

## FLUX Prompts That Worked
*(accumulate here — never archive, reuse across sessions)*

## Style Reference
*(set once in session 1, never change)*
- pixel_density: 512x512 minimum source; gameplay SpriteRenderer assets target 128 PPU; all assets must remain readable at 64x64 on phone screen.
- palette: charcoal `#17151A`, old gold `#C89B3C`, wax white `#E8DCC2`, crimson `#9E2431`, void violet `#6D4BC3`.
- outline_weight: bold charcoal outline, about 8 px at 512x512 source size, simplified enough to survive downscale to 64x64.

## Lessons
*(project-validated knowledge — overrides the professional KB in `Agents/X.md` when there is a conflict. Never archive. Append with session number.)*
