
# API Test Plan

| ID | Test | Expected Result |
|---|---|---|
| T01 | GET /api/issues | 200, JSON array |
| T02 | POST valid issue | 201, complete issue |
| T03 | POST without title | 400, VALIDATION_ERROR |
| T04 | POST priority Critical | 400, VALIDATION_ERROR |
| T05 | PATCH status to Resolved | 200, updated issue |
| T06 | PATCH status to Deleted | 400, VALIDATION_ERROR |
| T07 | PATCH unknown issue ID | 404, ISSUE_NOT_FOUND |
| T08 | GET with no issues | 200, empty array |
| T09 | Send server-owned fields | Client cannot control authoritative fields |
