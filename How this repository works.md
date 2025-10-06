# How this repository works

The idea here is to do all the little and big changes on the Alpha branch. Then, when it's supposedly polished enough, the branch passes to the Beta branch with a merge and squash command for a revision stage. If more changes are made in those files it repeates the process until there are no more important changes and the Beta branch is again merged into de Release branch where the content is polished enough to be used as study material.

This is an schematic view of how the repository is intended to be worked on.

```mermaid
---
config:
  theme: 'base'
  gitGraph:
    showBranches: true
    showCommitLabel: true
    mainBranchName: 'Release'
---
gitGraph
    commit id:"First Commit"
    branch Beta
    branch Alpha
    commit id:"A"
    commit id:"lot"
    commit id:"of"
    commit id:"important"
    commit id:"changes"
    checkout Beta
    merge Alpha id:"Squash merge"
    checkout Alpha
    commit id:"More"
    commit id:"little"
    commit id:"corrections"
    checkout Beta
    merge Alpha id:"Small merge"
    checkout Release
    merge Beta id:"Polished Content"
    checkout Alpha
    commit id:"Continue"
    commit id:"improving"
    commit id:"notes"
```
