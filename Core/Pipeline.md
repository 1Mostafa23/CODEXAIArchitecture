---
type: AbstractFrame
---
# Pipeline

The ordered flow of work through the 8-agent team. [[PM]] owns this flow.

## Flow
```
Idea -> [[GameDesigner]] -> [[GDD]] -> [[BA]] -> validated requirements
     -> [[UXDesigner]] -> separated UX/UI specs
     -> [[Architect]] -> Unity task cards
     -> [[Coder]] + [[ArtDirector]]
     -> [[QA]] -> APK / build validation
```

## Trigger Table
| When this is ready | PM routes to |
|---|---|
| Game idea from human | [[GameDesigner]] |
| [[GDD]] written | [[BA]] |
| [[GDD]] validated | [[UXDesigner]] |
| UX/UI specs separated and ready | [[Architect]] |
| Unity task card in `Tasks/Open/` | [[Coder]] or [[ArtDirector]] |
| Feature in Unity | [[QA]] |
| QA APPROVED | mark done in [[TASKS]] |
| QA BUG | [[Coder]] with bug report |

## Loop
QA bugs feed back to Coder without re-running BA, UXDesigner, or Architect.
UX/UI ambiguity feeds back to UXDesigner.
Requirement ambiguity feeds back to BA.
Scope changes feed back to GameDesigner and restart from BA.
