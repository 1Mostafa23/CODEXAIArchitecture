---
project: "[YOUR GAME NAME]"
phase: "design"
sprint: 1
build: "none"
last_updated: "2026-05-17"
---

# STATUS

## Done
- [x] Set up vault and [[AGENTS]]
- [x] Routed first game idea to [[GameDesigner]]
- [x] [[GameDesigner]] wrote the initial [[GDD]]
- [x] [[BA]] completed initial [[GDD]] validation and found blocking design gaps
- [x] [[GameDesigner]] revised [[GDD]] after BA review
- [x] [[BA]] re-validated revised [[GDD]] and found remaining cleanup blockers
- [x] [[GameDesigner]] completed the cleanup pass for [[GDD]]
- [x] [[BA]] approved cleaned [[GDD]] for [[Architect]] routing
- [x] [[BA]] reopened [[GDD]] after the human owner changed the control model
- [x] [[GameDesigner]] revised [[GDD]] for movement-only portrait controls, auto-attack, and automatic possession
- [x] [[BA]] approved the revised control model but blocked [[Architect]] routing on machine cadence
- [x] [[BA]] removed active MVP pet/helper scope from [[GDD]]
- [x] [[GameDesigner]] revised [[GDD]] for every-room machine cadence, guaranteed free buffs, rerolls, and no-pet reward flow
- [x] [[BA]] re-validated machine cadence and no-pet cleanup, then blocked [[Architect]] routing on possession-explosion ambiguity
- [x] [[GameDesigner]] clarified possession-explosion behavior as buff-only through **P03 Последний вздох**
- [x] [[BA]] approved the clarified possession-explosion behavior as validated requirements
- [x] [[PM]] integrated [[UXDesigner]] as the required pipeline step between [[BA]] and [[Architect]]
- [x] Superseded direct [[Architect]] handoff `Tasks/Done/14-architect-mvp-task-breakdown-superseded.md`
- [x] [[UXDesigner]] created mobile portrait MVP UX/UI specs in `Tasks/Open/16-mvp-mobile-portrait-ux-ui-specs.md`
- [x] [[ArtDirector]] fixed the BA-blocked `slot_machine_body_idle` prompt affordance issue

## In Progress
- [ ] [[BA]] re-checks fixed prompt pack using `Tasks/Open/19-ba-recheck-fixed-prompt-pack-before-generation.md`
- [ ] [[Architect]] creates MVP Unity implementation task cards using `Tasks/Open/17-architect-create-mvp-task-cards-from-ux-ui-specs.md`

## Next
- [ ] [[ArtDirector]] generates PNG sprites only after prompt re-check approval and/or Architect art-generation task cards
- [ ] [[Coder]], [[ArtDirector]], and [[QA]] execute task cards after [[Architect]] breakdown

## Blockers
- Production PNG generation is not formally approved until [[BA]] re-checks the fixed prompt pack and [[Architect]] creates implementation/art-generation task cards.

---

> [[PM]]: update this file at the end of every session.
> Keep Done/In Progress/Next accurate - all other agents read this first.
> Also update [[TASKS]] and regenerate [[CONTEXT]].
