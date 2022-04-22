```mermaid
gitGraph
      commit
      checkout main
      branch blank
      checkout blank
      commit
      branch story1
      checkout story1
      commit
      commit
      branch UAT
      checkout UAT
      commit
      
      checkout story1
      branch STAGE
      checkout STAGE
      commit
      
      checkout story1
      branch change1
      checkout change1
      commit
      checkout main
      merge change1
```
