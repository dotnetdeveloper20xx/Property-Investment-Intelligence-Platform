# ApiDesign.md

# Property Investment Intelligence Platform

## API Design, Standards & Endpoint Specification

---

# Introduction

The API is the primary communication layer between the frontend, backend, AI services, mobile applications, reporting systems, and future third-party integrations.

This document defines the API architecture, standards, conventions, security requirements, endpoint design, request models, response models, and versioning strategy for the Property Investment Intelligence Platform.

The objective is consistency.

Every endpoint should behave predictably.

Developers should not need to guess:

* How endpoints are named
* How responses are structured
* How pagination works
* How filtering works
* How errors are returned

Consistency improves:

* Developer productivity
* Frontend development
* Mobile development
* Testing
* Documentation
* Long-term maintainability

---

# API Philosophy

The API exists to expose business capabilities.

Endpoints should represent business actions.

Good examples:

```text
POST /api/opportunities

POST /api/documents/upload

POST /api/investment-analysis/calculate
```

Poor examples:

```text
POST /api/doStuff

POST /api/propertyhandler

POST /api/general
```

Endpoints should clearly communicate intent.

---

# API Technology

Backend:

* ASP.NET Core 10
* REST API
* JSON
* JWT Authentication
* Swagger/OpenAPI

Future:

* GraphQL (Optional)
* Public API
* Mobile API
* Partner API

---

# Base URL Structure

Development:

```text
https://localhost:5001/api
```

Production:

```text
https://api.propertyintelligence.com/api
```

---

# API Versioning Strategy

Use URL versioning.

Examples:

```text
/api/v1/opportunities

/api/v1/portfolio

/api/v1/ai
```

Benefits:

* Backward compatibility
* Easier upgrades
* Predictable evolution

---

# Authentication

All protected endpoints require JWT authentication.

Header:

```http
Authorization: Bearer {token}
```

---

# Authorization

Role-based authorization.

Roles:

* Admin
* Investor
* Analyst
* PortfolioManager
* Viewer

Example:

```csharp
[Authorize(Roles = "Admin")]
```

---

# Standard Response Format

All endpoints should return a consistent response envelope.

Success:

```json
{
  "success": true,
  "message": "Operation completed successfully",
  "data": {}
}
```

---

Failure:

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": []
}
```

---

# Validation Response

Example:

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": [
    {
      "field": "purchasePrice",
      "message": "Purchase price is required"
    }
  ]
}
```

---

# Pagination Standard

All list endpoints must support pagination.

Query Parameters:

```text
?page=1&pageSize=20
```

Response:

```json
{
  "success": true,
  "data": [],
  "pagination": {
    "page": 1,
    "pageSize": 20,
    "totalRecords": 500,
    "totalPages": 25
  }
}
```

---

# Sorting Standard

Query Parameters:

```text
?sortBy=createdDate

?sortDirection=desc
```

---

# Filtering Standard

Examples:

```text
?status=Purchased

?propertyType=House

?investmentScoreMin=80
```

Filters should be composable.

---

# Search Standard

Example:

```text
?search=Manchester
```

Used across all searchable resources.

---

# Identity Endpoints

---

## Register User

```http
POST /api/v1/auth/register
```

Request:

```json
{
  "firstName": "",
  "lastName": "",
  "email": "",
  "password": ""
}
```

---

## Login

```http
POST /api/v1/auth/login
```

Response:

```json
{
  "token": "",
  "refreshToken": ""
}
```

---

## Refresh Token

```http
POST /api/v1/auth/refresh
```

---

## Logout

```http
POST /api/v1/auth/logout
```

---

## Current User

```http
GET /api/v1/auth/me
```

---

# Opportunity Endpoints

---

## Create Opportunity

```http
POST /api/v1/opportunities
```

CQRS:

CreateOpportunityCommand

---

## Update Opportunity

```http
PUT /api/v1/opportunities/{id}
```

CQRS:

UpdateOpportunityCommand

---

## Get Opportunity

```http
GET /api/v1/opportunities/{id}
```

CQRS:

GetOpportunityQuery

---

## Search Opportunities

```http
GET /api/v1/opportunities
```

Supports:

Search

Filtering

Pagination

Sorting

---

## Delete Opportunity

```http
DELETE /api/v1/opportunities/{id}
```

---

# Notes Endpoints

---

## Create Note

```http
POST /api/v1/opportunities/{id}/notes
```

---

## Update Note

```http
PUT /api/v1/notes/{id}
```

---

## Delete Note

```http
DELETE /api/v1/notes/{id}
```

---

# Task Endpoints

---

## Create Task

```http
POST /api/v1/tasks
```

---

## Complete Task

```http
POST /api/v1/tasks/{id}/complete
```

---

## Reassign Task

```http
POST /api/v1/tasks/{id}/assign
```

---

# Property Endpoints

---

## Create Property

```http
POST /api/v1/properties
```

---

## Get Property

```http
GET /api/v1/properties/{id}
```

---

## Update Property

```http
PUT /api/v1/properties/{id}
```

---

# Document Endpoints

---

## Upload Document

```http
POST /api/v1/documents/upload
```

Multipart Form Data

---

## Download Document

```http
GET /api/v1/documents/{id}/download
```

---

## Get Document

```http
GET /api/v1/documents/{id}
```

---

## Delete Document

```http
DELETE /api/v1/documents/{id}
```

---

## Document Processing Status

```http
GET /api/v1/documents/{id}/status
```

---

# Legal Intelligence Endpoints

---

## Get Legal Findings

```http
GET /api/v1/legal/findings/{opportunityId}
```

---

## Get Legal Risks

```http
GET /api/v1/legal/risks/{opportunityId}
```

---

## Generate Legal Summary

```http
POST /api/v1/legal/summary
```

---

## Generate Legal Report

```http
POST /api/v1/legal/report
```

---

# Investment Analysis Endpoints

---

## Calculate Investment Analysis

```http
POST /api/v1/investment-analysis/calculate
```

---

## Get Analysis

```http
GET /api/v1/investment-analysis/{opportunityId}
```

---

## Compare Opportunities

```http
POST /api/v1/investment-analysis/compare
```

---

## Calculate Maximum Bid

```http
POST /api/v1/investment-analysis/maximum-bid
```

---

# Risk Intelligence Endpoints

---

## Get Investment Score

```http
GET /api/v1/risk/investment-score/{opportunityId}
```

---

## Get Opportunity Score

```http
GET /api/v1/risk/opportunity-score/{opportunityId}
```

---

## Get Risk Assessment

```http
GET /api/v1/risk/assessment/{opportunityId}
```

---

## Get Deal Killers

```http
GET /api/v1/risk/deal-killers/{opportunityId}
```

---

# AI Endpoints

---

## Chat With Property Assistant

```http
POST /api/v1/ai/chat
```

Request:

```json
{
  "opportunityId": "",
  "question": ""
}
```

---

## Generate Recommendation

```http
POST /api/v1/ai/recommendation
```

---

## Generate Investment Committee Review

```http
POST /api/v1/ai/committee
```

---

## Generate Due Diligence Checklist

```http
POST /api/v1/ai/checklist
```

---

## Generate Property Summary

```http
POST /api/v1/ai/summary
```

---

# Market Intelligence Endpoints

---

## Get Area Intelligence

```http
GET /api/v1/market/area/{postcode}
```

---

## Get Rental Demand

```http
GET /api/v1/market/rental-demand/{postcode}
```

---

## Get Growth Analysis

```http
GET /api/v1/market/growth/{postcode}
```

---

## Compare Areas

```http
POST /api/v1/market/compare
```

---

# Portfolio Endpoints

---

## Create Portfolio

```http
POST /api/v1/portfolio
```

---

## Get Portfolio

```http
GET /api/v1/portfolio/{id}
```

---

## Portfolio Dashboard

```http
GET /api/v1/portfolio/dashboard
```

---

## Net Worth

```http
GET /api/v1/portfolio/net-worth
```

---

## Wealth Forecast

```http
GET /api/v1/portfolio/forecast
```

---

# CRM Endpoints

---

## Create Contact

```http
POST /api/v1/crm/contacts
```

---

## Search Contacts

```http
GET /api/v1/crm/contacts
```

---

## Create Company

```http
POST /api/v1/crm/companies
```

---

# Collaboration Endpoints

---

## Add Comment

```http
POST /api/v1/comments
```

---

## Get Activity Feed

```http
GET /api/v1/activity-feed
```

---

## Approval Workflow

```http
POST /api/v1/approvals
```

---

# Reporting Endpoints

---

## Generate Report

```http
POST /api/v1/reports/generate
```

---

## Download Report

```http
GET /api/v1/reports/{id}/download
```

---

## Report History

```http
GET /api/v1/reports
```

---

# Health Check Endpoints

---

## API Health

```http
GET /health
```

---

## Database Health

```http
GET /health/database
```

---

## AI Provider Health

```http
GET /health/ai
```

---

# Swagger Requirements

All endpoints must include:

Summary

Description

Request Example

Response Example

Authorization Requirements

Error Responses

Swagger documentation must be generated automatically.

---

# CQRS Mapping Standards

Every endpoint must map to:

Command

or

Query

Examples:

```text
POST /opportunities

→ CreateOpportunityCommand
```

```text
GET /opportunities/{id}

→ GetOpportunityQuery
```

No controller should contain business logic.

---

# Public API Future Strategy

Future versions may expose:

Opportunity Data

Market Intelligence

Property Scores

Reports

Marketplace Services

via subscription-based APIs.

The API design should support future monetisation.

---

# API Success Criteria

The API design is successful when:

* Endpoints are predictable.
* Responses are consistent.
* Authentication is secure.
* Pagination works uniformly.
* CQRS mapping is clear.
* Frontend integration is straightforward.
* Future mobile apps require no redesign.
* Future public APIs can be introduced safely.

This API becomes the formal contract between the backend, frontend, AI services, reporting engines, and future third-party integrations.
