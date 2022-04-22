sequenceDiagram
	autonumber
  participant Developer
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
  Dev Instance -->> Git: Update set added to story branch
  Git -->> Jenkins: Deploy to QA
  Jenkins -->> QA Instance: Update set deployed
  Jenkins -->> Fortify: Run Scan (Currently optional)
  Jenkins -->> QA Instance: Unit testing
  Developer -->> Agile Development: Assign story to QA
  QA -->> QA Instance: fix any failing tests with Developer, Manual tests (if needed) / create defects
  QA -->> Agile Development: Assign story to developer move to passed QA
  Developer -->> Git: Merge to UAT branch
  Git -->> Jenkins: Deploy to UAT
  Jenkins -->> UAT Instance: Update set deployed
  Jenkins -->> UAT Instance: Unit testing
  Developer -->> Agile Development: Assign story to UAT
  BSA/PO -->> UAT Instance: Test/Validate
  BSA/PO -->> Agile Development: Accept story or request changes assign to Developer
  Developer -->> Git: Merge to Stage branch
  Developer -->> Agile Development: Pending Deployment
  Jenkins -->> Stage Instance: Update set deployed
  Jenkins -->> Stage Instance: Unit testing, regression run/scheduled
  Jenkins -->> Enterprise DevOps: Create Change Request
  Jenkins -->> Stage Instance: Healthscan (Developer fixes or asks Healthscan admins to close)
  Security Champion -->> Agile Development: Review Fortify findings and create defects
  Developer -->> Stage Instance: Commit Update Set
  Stage Instance -->> Git: Create change branch and pull request to master
  Peer Reviewer -->> Git: Approve PR
  Developer -->> Git: Merge PR
  Developer -->> Change Management: Regression must be complete, complete risk assessment (if higher than low for business application), Submit for approval
  IT App Ops -->> Change Management: checking tests have passed, healthscan passed, stories attached, schedule, for high risk change go to CAB, if during change freeze needs VP approval
  IT App Ops -->> Change Management: Approve Change
  Developer -->> Change Management: Wait for scheduled time, implement change
  Developer -->> Surf Admins: Inform and complete of any pre deploy manual steps and mark implementation task as success
  Enterprise DevOps -->> Jenkins: Continue job, close change task automatically
  Jenkins -->> Production Instance: Update Set Deployed
  Jenkins -->> DryRun Instance: Update Set Deployed
  Developer -->> Surf Admins: Inform and complete of any post manual steps
  Developer -->> Change Management: Validate and close validation task
  Developer -->> Agile Development: Complete story
