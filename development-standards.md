# DevelopmentStandards.md

# Property Investment Intelligence Platform

## Development Standards & Engineering Guidelines

---

# Purpose

This document defines the engineering standards for the Property Investment Intelligence Platform.

Its purpose is to ensure that every developer, architect, AI coding assistant, contractor, and future team member follows the same standards when contributing to the project.

Consistency is more important than individual preference.

A good team with consistent standards will outperform a team of talented developers all working differently.

This document acts as the engineering constitution of the project.

All implementation work should follow these standards.

---

# Core Development Philosophy

Before writing code, every developer should understand the following principles.

---

## Business First

Always understand the business requirement before writing code.

Developers are solving business problems.

Not technical problems.

Every feature should clearly answer:

Why does this exist?

Who benefits?

What problem does it solve?

---

## Simplicity First

Prefer simple solutions.

Avoid over-engineering.

Avoid unnecessary abstraction.

Avoid creating frameworks within frameworks.

The simplest maintainable solution should always be preferred.

---

## Readability Over Cleverness

Code is read far more often than it is written.

Future developers should immediately understand:

* What the code does
* Why it exists
* How it works

Avoid clever solutions that reduce readability.

---

## Consistency Over Preference

Personal preferences should not override project standards.

The platform should feel as though it was built by a single engineering team.

---

# Solution Structure Standards

Every new feature must follow the approved architecture.

---

# Backend Project Structure

```text
src/

PropertyIntelligence.Domain

PropertyIntelligence.Application

PropertyIntelligence.Infrastructure

PropertyIntelligence.Api
```

Do not create additional projects unless approved by architecture review.

---

# Frontend Structure

```text
src/app

core

shared

features
```

Every business capability belongs inside a feature folder.

Avoid placing business logic in shared folders.

---

# Naming Standards

---

## Classes

Use PascalCase.

Examples:

PropertyOpportunity

InvestmentAnalysis

GenerateRiskAssessmentCommand

---

## Methods

Use PascalCase.

Examples:

CalculateYield()

GenerateReport()

CreateOpportunity()

---

## Variables

Use camelCase.

Examples:

purchasePrice

investmentScore

monthlyRent

---

## Private Fields

Use underscore prefix.

Examples:

_repository

_currentUser

_aiProvider

---

# Entity Standards

Every entity must inherit from:

```csharp
BaseAuditableEntity
```

Containing:

* Id
* CreatedDate
* CreatedBy
* LastModifiedDate
* LastModifiedBy

No entity should duplicate audit fields.

---

# Domain Standards

The Domain layer should contain:

* Entities
* Value Objects
* Enums
* Domain Events

The Domain layer must never reference:

* EF Core
* SQL Server
* ASP.NET
* Angular
* External APIs

The Domain layer must remain pure.

---

# CQRS Standards

Every business operation must follow CQRS.

---

## Commands

Commands modify state.

Examples:

CreateOpportunityCommand

UpdatePortfolioCommand

DeleteDocumentCommand

---

## Queries

Queries retrieve state.

Examples:

GetOpportunityQuery

GetPortfolioQuery

GetRiskAssessmentQuery

---

## Handlers

Every command and query requires its own handler.

Examples:

CreateOpportunityCommandHandler

GetOpportunityQueryHandler

---

# Folder Structure Standards

Commands:

```text
Features

Opportunities

Commands

CreateOpportunity
```

Inside folder:

```text
CreateOpportunityCommand.cs

CreateOpportunityCommandHandler.cs

CreateOpportunityCommandValidator.cs
```

This structure should be used consistently throughout the application.

---

# Validation Standards

All validation must use FluentValidation.

Validation should occur before business processing.

Examples:

Required Fields

Maximum Length

Ranges

Business Rules

Never place validation logic inside controllers.

---

# API Standards

Controllers should remain thin.

Controllers should:

Receive Request

Send Command or Query

Return Response

Controllers should not contain business logic.

---

# Response Standards

Use consistent API responses.

Success:

```json
{
  "success": true,
  "data": {}
}
```

Failure:

```json
{
  "success": false,
  "errors": []
}
```

Maintain consistency across all endpoints.

---

# Exception Handling Standards

Use centralized exception middleware.

Never expose:

* Stack traces
* Internal exceptions
* Database errors

Users should receive friendly messages.

Detailed information should be logged.

---

# Repository Standards

Avoid generic repositories where possible.

Prefer:

OpportunityRepository

PortfolioRepository

DocumentRepository

Instead of:

GenericRepository<T>

Repositories should reflect business concepts.

---

# Entity Framework Standards

Use:

Code First

Configurations

Migrations

Never place EF configuration directly inside entities.

Create dedicated configuration classes.

Examples:

OpportunityConfiguration

PortfolioConfiguration

DocumentConfiguration

---

# Database Standards

Table names:

Plural.

Examples:

Properties

Opportunities

Portfolios

Documents

Primary Keys:

Id

Foreign Keys:

EntityNameId

Examples:

PropertyId

OpportunityId

PortfolioId

---

# Service Standards

Services should have a single responsibility.

Good:

InvestmentAnalysisService

RiskCalculationService

DocumentProcessingService

Bad:

PropertyServiceThatDoesEverything

---

# AI Service Standards

All AI providers must implement:

```csharp
IAIProvider
```

Never call providers directly.

Examples:

Good:

```csharp
_aiProvider.GenerateAsync()
```

Bad:

```csharp
new OpenAIClient()
```

This ensures provider independence.

---

# Prompt Standards

Prompts must be stored separately.

Do not embed large prompts inside services.

Examples:

InvestmentAnalysisPrompt

LegalReviewPrompt

RiskAssessmentPrompt

This improves maintainability.

---

# Angular Standards

---

## Feature-Based Development

Every business capability belongs inside:

```text
features
```

Examples:

opportunities

portfolio

risk

analysis

documents

---

## Component Naming

Examples:

opportunity-list.component.ts

opportunity-card.component.ts

portfolio-dashboard.component.ts

---

## Services

Examples:

opportunity.service.ts

portfolio.service.ts

risk.service.ts

---

# State Management Standards

Use Signals first.

Use NgRx only when:

* State is shared
* State is long lived
* State is complex

Do not use NgRx unnecessarily.

---

# UI Standards

All UI should use:

Tailwind CSS

DaisyUI

Avoid custom CSS where possible.

Prefer reusable components.

---

# Reusable Components

Examples:

Buttons

Cards

Tables

Forms

Modals

Charts

Do not duplicate UI patterns.

---

# Logging Standards

Log:

Errors

Warnings

Security Events

AI Requests

Document Processing

Avoid excessive logging.

Logs should be useful.

---

# Audit Standards

Track:

Created

Modified

Deleted

Reviewed

Approved

Auditability is critical.

---

# Testing Standards

Every feature must include tests.

---

## Unit Tests

Required for:

Handlers

Services

Calculations

Validators

---

## Integration Tests

Required for:

Authentication

Database Access

API Endpoints

Document Processing

---

## Calculation Testing

Especially important for:

ROI

Yield

Cash Flow

Investment Score

Risk Score

Financial calculations must be verifiable.

---

# Code Review Standards

Before merging:

Feature Compiles

Tests Pass

No Warnings

No Dead Code

No Debug Code

Naming Standards Followed

Architecture Standards Followed

---

# Pull Request Standards

Every pull request must include:

Summary

Business Purpose

Technical Changes

Testing Performed

Screenshots (if UI changes)

---

# Definition Of Done

A feature is complete only when:

Business Requirements Met

Code Implemented

Validation Implemented

Tests Written

Documentation Updated

Build Passes

Code Reviewed

No Known Critical Bugs

---

# Documentation Standards

Every major feature requires:

Business Description

Technical Design

Implementation Notes

API Documentation

Future Considerations

Documentation should evolve with the platform.

---

# Security Standards

Never trust client input.

Validate everything.

Sanitize uploaded content.

Protect file uploads.

Protect AI prompts.

Protect API keys.

Security is not optional.

---

# Performance Standards

Avoid:

N+1 Queries

Large Object Graphs

Excessive API Calls

Unnecessary Rendering

Measure before optimising.

---

# AI Coding Agent Standards

Applies to:

Kiro

Claude Code

Copilot

Cursor

ChatGPT

Any AI coding tool.

---

## AI Must

Read existing code first.

Follow architecture.

Follow naming conventions.

Follow CQRS.

Follow folder standards.

Generate tests.

Update documentation.

---

## AI Must Not

Create duplicate patterns.

Ignore existing architecture.

Introduce unnecessary frameworks.

Break project standards.

Implement partial solutions.

---

# Architectural Decision Rule

When faced with multiple solutions:

Choose the solution that is:

Most Readable

Most Maintainable

Most Consistent

Most Aligned With Existing Architecture

Not necessarily the most clever.

---

# Engineering Success Criteria

The engineering standards are successful when:

New developers can become productive quickly.

AI coding agents generate consistent code.

Features follow predictable patterns.

The codebase remains understandable after years of development.

The platform continues scaling without architectural chaos.

Every contributor should treat this document as the engineering constitution of the Property Investment Intelligence Platform.
