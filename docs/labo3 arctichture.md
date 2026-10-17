
# Lab 3 — Cloud Issue Tracker Architecture

## 1. Application Goal

The goal is to design a three-layer application
for creating, viewing, and updating issues.

## 2. Functional Scope

- Create an issue.
- View all issues.
- Change an issue status.

## 3. Request Flow

### Create Issue

User -> Frontend -> POST /api/issues
-> API validation -> Data layer
<- 201 Created + JSON response

### View Issues

Page load -> GET /api/issues
-> API -> Data layer
<- 200 OK + JSON array

### Change Status

User clicks status button
-> PATCH /api/issues/{id}/status
-> API validation -> Data layer
<- 200 OK + updated issue

## 4. Trust Boundaries

The browser and its requests are user-controlled.
All incoming requests must be validated by the API.

The browser must not access the data layer directly.
The API returns only the required data and must not
expose internal errors or stack traces.

Issue text must be displayed as plain text, not HTML.
