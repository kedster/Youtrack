List all projects

bash
Copy
Edit
curl -X GET "{{DOMAIN}}/api/admin/projects?fields=id,name,shortName" \
  -H "Authorization: Bearer {{TOKEN}}" \
  -H "Accept: application/json"
Get single project

bash
Copy
Edit
curl -X GET "{{DOMAIN}}/api/admin/projects/{{PROJECT_ID}}?fields=id,name,description" \
  -H "Authorization: Bearer {{TOKEN}}" -H "Accept: application/json"
List issues in a project

bash
Copy
Edit
curl -X GET "{{DOMAIN}}/api/issues?query=project:%22{{PROJECT_ID}}%22&fields=idReadable,summary,description,state(name)" \
  -H "Authorization: Bearer {{TOKEN}}" -H "Accept: application/json"
Get single issue details

bash
Copy
Edit
curl -X GET "{{DOMAIN}}/api/issues/{{ISSUE_ID}}?fields=idReadable,summary,description,fields(id,name,value),links(inward,name,outward,name)" \
  -H "Authorization: Bearer {{TOKEN}}" -H "Accept: application/json"
Create an issue (POST)

bash
Copy
Edit
curl -X POST "{{DOMAIN}}/api/issues?fields=id,idReadable" \
  -H "Authorization: Bearer {{TOKEN}}" -H "Accept: application/json" \
  -H "Content-Type: application/json" \
  -d '{"project":{"id":"{{PROJECT_ID}}"},"summary":"API Test Issue","description":"Created via API"}'
Link two issues (issue connection)

bash
Copy
Edit
curl -X POST "{{DOMAIN}}/api/issues/{{PARENT_ID}}/links?fields=id" \
  -H "Authorization: Bearer {{TOKEN}}" -H "Accept: application/json" \
  -H "Content-Type: application/json" \
  -d '{"relationship":"subtask of","issues":[{"id":"{{CHILD_ID}}"}]}'
Update issue status / field

bash
Copy
Edit
curl -X POST "{{DOMAIN}}/api/issues/{{ISSUE_ID}}?fields=fields(id,name,value)" \
  -H "Authorization: Bearer {{TOKEN}}" -H "Accept: application/json" \
  -H "Content-Type: application/json" \
  -d '{"fields":[{"id":"State","value":{"id":"{{NEW_STATE_ID}}","name":"{{NEW_STATE_NAME}}"}}]}'
Add a comment to an issue

bash
Copy
Edit
curl -X POST "{{DOMAIN}}/api/issues/{{ISSUE_ID}}/comments?fields=id,author,created" \
  -H "Authorization: Bearer {{TOKEN}}" -H "Accept: application/json" \
  -H "Content-Type: application/json" \
  -d '{"text":"API‑triggered update comment"}'
List workflows

bash
Copy
Edit
curl -X GET "{{DOMAIN}}/youtrack/api/admin/workflows?fields=id,name,attachedToProjectIds" \
  -H "Authorization: Bearer {{TOKEN}}" -H "Accept: application/json"
Attach workflow to project

bash
Copy
Edit
curl -X POST "{{DOMAIN}}/youtrack/api/admin/workflows/{{WORKFLOW_ID}}/attach?fields=id" \
  -H "Authorization: Bearer {{TOKEN}}" -H "Accept: application/json" \
  -H "Content-Type: application/json" \
  -d '{"project":"{{PROJECT_ID}}"}'
✅ Set B: Development (dev_youtrack_token, Dev_youtrack_domain)
List dev projects

bash
Copy
Edit
curl -X GET "{{DEV_DOMAIN}}/api/admin/projects?fields=id,name,shortName" \
  -H "Authorization: Bearer {{DEV_TOKEN}}" -H "Accept: application/json"
Get dev project

bash
Copy
Edit
curl -X GET "{{DEV_DOMAIN}}/api/admin/projects/{{PROJECT_ID}}?fields=id,name,description" \
  -H "Authorization: Bearer {{DEV_TOKEN}}" -H "Accept: application/json"
List dev project issues

bash
Copy
Edit
curl -X GET "{{DEV_DOMAIN}}/api/issues?query=project:%22{{PROJECT_ID}}%22&fields=idReadable,summary,fields(field(name,value))" \
  -H "Authorization: Bearer {{DEV_TOKEN}}" -H "Accept: application/json"
Get dev issue details

bash
Copy
Edit
curl -X GET "{{DEV_DOMAIN}}/api/issues/{{ISSUE_ID}}?fields=idReadable,summary,description,fields(id,name,value)" \
  -H "Authorization: Bearer {{DEV_TOKEN}}" -H "Accept: application/json"
Create dev issue

bash
Copy
Edit
curl -X POST "{{DEV_DOMAIN}}/api/issues?fields=id,idReadable" \
  -H "Authorization: Bearer {{DEV_TOKEN}}" -H "Content-Type: application/json" -H "Accept: application/json" \
  -d '{"project":{"id":"{{PROJECT_ID}}"},"summary":"Dev API Issue","description":"Triggered from dev API"}'
Link dev issues

bash
Copy
Edit
curl -X POST "{{DEV_DOMAIN}}/api/issues/{{PARENT_ID}}/links?fields=id" \
  -H "Authorization: Bearer {{DEV_TOKEN}}" -H "Accept: application/json" \
  -H "Content-Type: application/json" \
  -d '{"relationship":"relates to","issues":[{"id":"{{RELATED_ID}}"}]}'
Update dev issue status

bash
Copy
Edit
curl -X POST "{{DEV_DOMAIN}}/api/issues/{{ISSUE_ID}}?fields=fields(id,name,value)" \
  -H "Authorization: Bearer {{DEV_TOKEN}}" -H "Content-Type: application/json" \
  -d '{"fields":[{"id":"State","value":{"id":"{{DEV_STATE_ID}}","name":"{{DEV_STATE_NAME}}"}}]}'
Add dev comment

bash
Copy
Edit
curl -X POST "{{DEV_DOMAIN}}/api/issues/{{ISSUE_ID}}/comments?fields=id,created" \
  -H "Authorization: Bearer {{DEV_TOKEN}}" -H "Content-Type: application/json" \
  -d '{"text":"Dev‑environment comment"}'
List dev workflows

bash
Copy
Edit
curl -X GET "{{DEV_DOMAIN}}/youtrack/api/admin/workflows?fields=id,name" \
  -H "Authorization: Bearer {{DEV_TOKEN}}" -H "Accept: application/json"
Attach dev workflow

bash
Copy
Edit
curl -X POST "{{DEV_DOMAIN}}/youtrack/api/admin/workflows/{{WORKFLOW_ID}}/attach" \
  -H "Authorization: Bearer {{DEV_TOKEN}}" -H "Content-Type: application/json" \
  -d '{"project":"{{PROJECT_ID}}"}'
