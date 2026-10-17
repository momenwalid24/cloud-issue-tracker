
# API Contract: Issues API

## Data Dictionary: Issue

| Field | Type | Source | Rule |
|---|---|---|---|
| id | string | Server | Unique and immutable |
| title | string | Client | Required; 3-100 characters |
| description | string | Client | Required; 5-500 characters |
| priority | enum | Client | Low, Medium, High |
| status | enum | Server / controlled update | Open, Resolved |
| createdAt | ISO 8601 string | Server | Immutable |

## Contract 1: View All Issues

- Request: GET /api/issues
- Request body: None
- Success: 200 OK with a JSON array
- Error: 500

## Contract 2: Create an Issue

- Request: POST /api/issues
- Header: Content-Type: application/json

Request body:

```json
{
  "title": "Projector not detected",
  "description": "Laptop cannot detect the classroom projector.",
  "priority": "Medium"
}
```

- Success: 201 Created with the complete issue
- Errors: 400, 415, 500

## Contract 3: Change Issue Status

- Request: PATCH /api/issues/{id}/status
- Header: Content-Type: application/json

Request body:

```json
{
  "status": "Resolved"
}
```

- Success: 200 OK with the updated issue
- Errors: 400, 404, 415, 500

## Error Responses

Every error uses this structure:

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Title must contain between 3 and 100 characters."
  }
}
```

| Status | Error Code |
|---|---|
| 400 | VALIDATION_ERROR |
| 404 | ISSUE_NOT_FOUND |
| 415 | UNSUPPORTED_MEDIA_TYPE |
| 500 | INTERNAL_ERROR |
``