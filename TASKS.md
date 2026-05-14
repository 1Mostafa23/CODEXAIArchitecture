# TASKS

| ID | Title | Agent | Status | Depends On | Notes |
|----|-------|-------|--------|------------|-------|
| T00 | Setup vault | PM | done | - | Initial scaffold |
| T01 | Route first game idea to GameDesigner | PM | done | T00 | Routed GameDesigner task; completed card now `Tasks/Done/01-create-gdd.md` |
| T02 | Create initial GDD | GameDesigner | done | T01 | Done card: `Tasks/Done/01-create-gdd.md`; wrote `GDD.md` |
| T03 | Validate initial GDD | BA | done | T02 | Done card: `Tasks/Done/02-validate-gdd.md`; BA found blocking design gaps |
| T04 | Revise GDD after BA review | GameDesigner | done | T03 | Done card: `Tasks/Done/03-revise-gdd-ba-gaps.md`; updated MVP rules in `GDD.md` |
| T05 | Re-validate revised GDD | BA | done | T04 | Done card: `Tasks/Done/04-revalidate-gdd.md`; BA found remaining cleanup blockers |
| T06 | Clean up GDD after BA re-validation | GameDesigner | done | T05 | Done card: `Tasks/Done/05-cleanup-gdd-ba-revalidation.md`; clarified reward pool, cursed deal, labels, and caps |
| T07 | Re-validate cleaned GDD | BA | done | T06 | Done card: `Tasks/Done/06-revalidate-cleaned-gdd.md`; BA approved GDD for Architect routing |
| T08 | Create MVP implementation task cards | Architect | blocked | T07 | Done/superseded card: `Tasks/Done/07-architect-mvp-task-breakdown.md`; blocked by later scope changes before Architect execution |
| T09 | Revise GDD control model | GameDesigner | done | T07 | Done card: `Tasks/Done/08-revise-gdd-control-simplification.md`; movement-only portrait, no dash, auto-attack, automatic marked-target possession |
| T10 | Re-validate revised control model | BA | done | T09 | Done card: `Tasks/Done/09-revalidate-control-model.md`; control model approved, machine cadence blocked Architect routing |
| T11 | Revise GDD machine cadence and buff flow | GameDesigner | done | T10 | Done card: `Tasks/Done/10-revise-gdd-machine-each-room.md`; BA re-validation done in `Tasks/Done/11-revalidate-machine-cadence.md` |
| T12 | Clarify marked-vessel possession explosion | GameDesigner | done | T11 | Done card: `Tasks/Done/12-clarify-possession-explosion.md`; chose buff-only explosion through **P03 Последний вздох** and updated GDD/P03/acceptance criteria |
| T13 | Re-validate possession explosion clarification | BA | done | T12 | Done card: `Tasks/Done/13-revalidate-possession-explosion.md`; approved buff-only possession explosion as validated requirements |
| T14 | Create MVP implementation task cards | Architect | done | T13 | Superseded card: `Tasks/Done/14-architect-mvp-task-breakdown-superseded.md`; direct BA-to-Architect route replaced by UXDesigner step |
| T15 | Create MVP UX/UI specs | UXDesigner | in_progress | T13 | Open card: `Tasks/Open/15-create-mvp-ux-ui-specs.md`; produce UX-first/UI-second mobile portrait specs before Architect routing |
| T16 | Create MVP implementation task cards from UX/UI specs | Architect | pending | T15 | Await UXDesigner output; Architect handoff should be created after UX/UI specs are complete |

---

> Agents: append new rows - never delete rows.
> [[PM]]: update Status column after each handoff.
> Status values: `pending` - `in_progress` - `done` - `blocked`
> See [[STATUS]] for current sprint state.
