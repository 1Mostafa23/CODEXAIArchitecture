---
task: "Create MVP Implementation Task Cards"
target: [[Architect]]
input: [[GDD]]
---

# Handoff to Architect
Create implementation-ready MVP task cards from the BA-approved [[GDD]].

## Input Files
- `GDD.md`
- `Tasks/Open/06-revalidate-cleaned-gdd.md`
- `STATUS.md`
- `Core/Conventions.md`

## Scope
- Use only MVP requirements from `GDD.md`.
- Treat all rows or examples labeled `Post-MVP` as out of scope.
- Decompose work into one-session implementation cards for [[Coder]] and [[ArtDirector]].

## Acceptance Criteria
- Create task cards in `Tasks/Open/` with target agent, input files, exact scope, observable acceptance criteria, explicit exclusions, and deadline session.
- Cover the MVP foundations: portrait controls, player combat, enemy wave rooms, possession, token economy, slot-machine rewards, helper behavior, boss encounter, run results, and first meta unlock.
- Keep each implementation card small enough for one focused coding or art session.
- Do not create tasks for Post-MVP enemies, biomes, bosses, jackpots, rerolls, live ops, monetization, or extra currencies.
- Add or reference architecture decisions only when required for implementation consistency.

## Deadline
Next Architect session.

## BA Superseded Result - 2026-05-13
Do not execute this Architect handoff yet. The human owner changed the MVP control direction after BA approval:
- portrait remains preferred;
- active combat buttons should be reduced;
- dash should be deleted from MVP;
- auto-attack should target nearest enemies and bosses.

This handoff is superseded by `Tasks/Open/08-revise-gdd-control-simplification.md`.
