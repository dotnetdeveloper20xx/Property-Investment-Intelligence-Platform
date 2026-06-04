# Phase-02-Property-Opportunity-Management.md

# Property Investment Intelligence Platform

## Phase 2 – Property Opportunity Management

---

# Introduction

Phase 1 established the technical foundation of the platform.

Users can now:

* Register
* Authenticate
* Access dashboards
* Manage profiles
* Use the platform securely

However, the platform still does not solve the user's core business problem.

Property investors are constantly reviewing opportunities.

Most investors manage opportunities using:

* Excel spreadsheets
* Notebooks
* Email folders
* Browser bookmarks
* Property website favourites
* WhatsApp messages
* Personal memory

This approach quickly becomes difficult as the number of opportunities increases.

A serious investor may review:

* 20 properties per week
* 100 properties per month
* 1,000 properties per year

Without a structured process, opportunities are forgotten, duplicated, misjudged, or lost completely.

Phase 2 introduces the first major business capability of the platform.

The system becomes a Property Opportunity Management Platform.

This phase allows investors to centralise, organise, monitor, and manage every property opportunity they are considering.

Think of this phase as building a CRM system for property investments.

Instead of managing customers, we are managing opportunities.

---

# Business Objectives

The primary objective is to help investors organise property opportunities.

The platform should become the central location where every potential investment is recorded and managed.

The investor should no longer need spreadsheets.

The platform becomes the investor's digital workspace.

---

# Core Business Concept

A Property Opportunity represents any property being evaluated as a potential investment.

Examples include:

* Auction property
* Buy-to-let property
* Off-market opportunity
* Development opportunity
* Distressed sale
* Commercial property
* Refurbishment project

Every opportunity should be stored within the platform and tracked throughout its lifecycle.

---

# Opportunity Lifecycle

One of the most important concepts introduced in this phase is the Opportunity Pipeline.

Investors move properties through different stages as their research progresses.

The lifecycle should include:

### Watching

Property has been discovered.

Initial interest exists.

---

### Researching

Investor is gathering information.

Documents may be uploaded.

Research may be ongoing.

---

### Interested

Property appears attractive.

Further investigation required.

---

### Bid Planned

Investor intends to bid or make an offer.

---

### Under Review

Property currently being analysed.

---

### Purchased

Property successfully acquired.

---

### Rejected

Investor decided not to proceed.

---

### Archived

Historical opportunity retained for reference.

---

This lifecycle creates structure and discipline around investment decisions.

---

# Opportunity Entity

The Property Opportunity becomes one of the platform's core business entities.

Each opportunity should contain:

### Basic Information

Property Name

Reference Number

Address

Postcode

Country

Property Type

Tenure

---

### Financial Information

Guide Price

Purchase Price

Expected Rental Income

Estimated Refurbishment Cost

Estimated Market Value

Expected Deposit

Expected Finance Amount

---

### Property Characteristics

Bedrooms

Bathrooms

Reception Rooms

Parking

Garden

Square Footage

Construction Type

Property Condition

---

### Opportunity Metadata

Created Date

Last Updated

Current Status

Opportunity Source

Assigned User

Notes Count

Document Count

---

# Property Types

Support multiple property categories.

Examples:

### Residential

House

Flat

Maisonette

Bungalow

---

### Commercial

Retail

Office

Industrial

Mixed Use

---

### Development

Land

Conversion Project

Development Site

---

### Specialist

HMO

Student Accommodation

Serviced Accommodation

Care Home

---

The design should be flexible enough for future expansion.

---

# Property Source Tracking

Understanding where opportunities originate is valuable.

Supported sources:

### Auction

Property auction websites.

---

### Estate Agent

Traditional property listings.

---

### Direct Vendor

Direct purchase opportunities.

---

### Property Sourcer

Third-party deal sourcing.

---

### Off Market

Private opportunities.

---

### Referral

Recommendations from contacts.

---

This data becomes valuable for future analytics.

---

# Property Images

Users must be able to upload property images.

Images should support:

### Main Property Image

Primary image displayed in listings.

---

### Gallery Images

Multiple supporting photographs.

---

### Property Condition Images

Evidence for future analysis.

---

Images become important later for AI-powered refurbishment analysis.

---

# Opportunity Notes

Investors constantly make observations.

The platform should support:

### General Notes

Research findings.

---

### Risk Notes

Potential concerns.

---

### Opportunity Notes

Potential upside.

---

### Action Notes

Tasks requiring follow-up.

---

Every note should include:

Author

Date

Timestamp

Category

Content

---

# Task Management

Investors frequently have follow-up actions.

Examples:

* Call auction house
* Request lease
* Contact solicitor
* Verify planning permission
* Obtain valuation

Each opportunity should support tasks.

Task fields:

Title

Description

Due Date

Status

Priority

Assigned User

---

# Opportunity Dashboard

Provide a dedicated dashboard.

Display:

### Total Opportunities

### Active Opportunities

### Purchased Properties

### Rejected Opportunities

### Upcoming Tasks

### Recent Activity

### Pipeline Breakdown

The goal is giving investors a quick overview of their current pipeline.

---

# Search & Filtering

Investors must quickly locate opportunities.

Search by:

Address

Postcode

Reference

Property Type

Status

Source

---

Filter by:

Price Range

Tenure

Bedrooms

Property Type

Status

Source

Date Created

---

# Opportunity Timeline

Every opportunity should maintain a timeline.

Record:

Created

Status Changes

Notes Added

Documents Uploaded

Tasks Completed

Purchases

Rejections

This provides a complete history of decision making.

---

# Document Foundation

Although legal analysis arrives later, document management starts now.

Support:

PDF Upload

ZIP Upload

Images

Documents

Supporting Files

Storage only.

Analysis comes in Phase 4.

---

# User Experience Goals

The platform should feel similar to:

A CRM system.

A project management system.

A property investment workspace.

Users should immediately understand:

What opportunities they have.

Where those opportunities are.

What actions are required.

What stage each opportunity is currently in.

---

# Reporting

Introduce initial reporting.

Examples:

### Opportunities By Status

### Opportunities By Source

### Opportunities By Property Type

### Opportunities Created This Month

### Opportunities Purchased

### Opportunities Rejected

This lays groundwork for future intelligence features.

---

# Technical Requirements

Backend:

* CQRS Commands
* CQRS Queries
* Validation
* EF Core
* Repository Pattern

Frontend:

* Angular Feature Module
* Signals
* NgRx State
* Reusable Components
* Responsive Design

Database:

PropertyOpportunities

OpportunityNotes

OpportunityTasks

PropertyImages

OpportunityDocuments

OpportunityHistory

PropertySources

PropertyTypes

OpportunityStatuses

---

# API Requirements

Examples:

GET api/opportunities

GET api/opportunities/{id}

POST api/opportunities

PUT api/opportunities/{id}

DELETE api/opportunities/{id}

POST api/opportunities/{id}/notes

POST api/opportunities/{id}/tasks

POST api/opportunities/{id}/documents

POST api/opportunities/{id}/images

---

# Definition Of Done

Phase 2 is complete when:

Users can create opportunities.

Users can edit opportunities.

Users can upload images.

Users can upload documents.

Users can create notes.

Users can create tasks.

Users can search opportunities.

Users can filter opportunities.

Users can move opportunities through pipeline stages.

Users can view opportunity history.

Users can manage their complete property research process within the platform.

At this point the Property Investment Intelligence Platform becomes genuinely useful for real investors even before any AI or risk analysis capabilities are introduced.

---

# AI Implementation Prompt

You are a Senior Solution Architect, Product Architect, ASP.NET Core Expert, Angular Expert, CQRS Expert, and Property Investment Domain Specialist.

Your task is to fully implement Phase 2 of the Property Investment Intelligence Platform.

Read and understand the entire solution before making changes.

Existing architecture:

* ASP.NET Core 10
* Clean Architecture
* CQRS
* MediatR
* EF Core
* SQL Server
* Angular 20
* Signals
* NgRx
* Tailwind CSS
* DaisyUI

Implement the complete Property Opportunity Management module.

Requirements:

1. Create Property Opportunity domain entities.
2. Create opportunity lifecycle workflow.
3. Create property source management.
4. Create property type management.
5. Create opportunity notes functionality.
6. Create opportunity task management.
7. Create opportunity image uploads.
8. Create opportunity document uploads.
9. Create opportunity activity timeline.
10. Create opportunity dashboard widgets.
11. Create opportunity search functionality.
12. Create advanced filtering.
13. Create opportunity history tracking.
14. Create all CQRS commands.
15. Create all CQRS queries.
16. Create handlers.
17. Create validators.
18. Create DTOs.
19. Create database migrations.
20. Create Angular pages.
21. Create Angular forms.
22. Create Angular services.
23. Create Angular state management.
24. Create responsive dashboards.
25. Create reusable property cards.
26. Create reusable tables.
27. Create document upload components.
28. Create image upload components.
29. Create opportunity pipeline views.
30. Create reporting dashboards.

Follow:

* SOLID principles
* Clean Architecture
* CQRS
* MediatR
* Enterprise coding standards

Generate production-ready code.

Do not provide examples.

Create all entities, commands, queries, handlers, validators, DTOs, pages, services, routes, database objects, and user interfaces required to complete Phase 2.

Ensure the solution compiles successfully.

At completion provide:

* Solution structure
* Database schema
* API endpoints
* Angular routes
* Component list
* Technical debt summary

Continue implementation until Phase 2 is fully completed.
