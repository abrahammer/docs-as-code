``` mermaid
sequenceDiagram
	autonumber
  actor Developer
  participant QA
  participant Peer Developer
  participant BSA/PO
  participant IT App Ops
  participant Surf Admins
  participant ServiceNow Instance
  participant Dev Instance
  participant QA Instance
  participant UAT Instance
  participant Stage Instance
  participant Production Instance
  participant DryRun Instance
  participant Jenkins
  participant Agile Development
  participant Enterprise DevOps
  participant Change Management
  participant Buildtools1
  

  Developer -->> ServiceNow Instance: Modify/Create code use story branch naming convention
  Developer -->> Dev Instance: Create/update test cases
  Developer -->> Dev Instance: Healthscan (mandatory before being able to commit) ~2 minutes
  Developer -->> Dev Instance: Code Review by peer ~ reliance on another team member
  Developer -->> Agile Development: Modify state on story and assign
  Developer -->> QA: Check if test cases are covered
  Developer -->> Dev Instance: Commit Update Set
 
```
