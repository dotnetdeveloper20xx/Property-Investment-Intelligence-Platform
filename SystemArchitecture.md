# SystemArchitecture.md

# Property Investment Intelligence Platform

## Enterprise System Architecture

---

# Introduction

This document defines the complete technical architecture of the Property Investment Intelligence Platform.

The goal is not simply to build software.

The goal is to build a platform that:

* Is maintainable
* Is scalable
* Is testable
* Is understandable
* Supports future growth
* Supports AI integration
* Supports enterprise adoption

The architecture must allow a single developer to work efficiently today while also supporting future team growth.

Every technical decision should support the business vision.

---

# Architecture Principles

The platform follows several core principles.

## Business First

Technology exists to support business requirements.

Business concepts should drive architecture decisions.

---

## Simplicity First

Avoid unnecessary complexity.

Build the simplest solution that satisfies requirements.

---

## Local Development First

The platform must run entirely on a developer laptop.

No Docker required.

No cloud dependency required.

Developers should be able to clone the repository and start working quickly.

---

## Enterprise Standards

Even though the platform can run locally, the architecture should follow enterprise software engineering practices.

---

## Future Cloud Ready

The architecture should support future migration to cloud services without major redesign.

---

# Technology Stack

## Backend

* ASP.NET Core 10
* C#
* Entity Framework Core
* SQL Server
* MediatR
* FluentValidation

---

## Frontend

* Angular 20
* TypeScript
* Signals
* NgRx
* Tailwind CSS
* DaisyUI

---

## Database

* SQL Server
* LocalDB (Development)
* SQL Server Standard (Production)

---

## AI Integration

* OpenAI
* Claude
* Azure OpenAI (future)
* Local LLM support (future)

---

# High-Level Architecture

```text
Angular Frontend
        |
        v
ASP.NET Core API
        |
        v
Application Layer
(CQRS + MediatR)
        |
        v
Domain Layer
        |
        v
Infrastructure Layer
        |
        +------ SQL Server
        |
        +------ File Storage
        |
        +------ AI Providers
```

---

# Solution Structure

```text
src/

PropertyIntelligence.Domain

PropertyIntelligence.Application

PropertyIntelligence.Infrastructure

PropertyIntelligence.Api

PropertyIntelligence.Web
```

---

# Domain Layer

Purpose:

Contains business rules and business concepts.

Contains:

* Entities
* Value Objects
* Enums
* Domain Events
* Interfaces

Must not depend on:

* EF Core
* SQL Server
* APIs
* Angular

This is the heart of the application.

---

# Application Layer

Purpose:

Implements business use cases.

Contains:

* Commands
* Queries
* Handlers
* Validators
* DTOs
* Interfaces

This layer coordinates workflows.

Examples:

Create Opportunity

Calculate ROI

Generate Investment Score

Analyse Legal Pack

Generate AI Recommendation

---

# Infrastructure Layer

Purpose:

External systems.

Contains:

* EF Core
* Repositories
* AI Providers
* File Storage
* OCR Services
* Email Services
* Background Services

This layer can change without affecting business logic.

---

# API Layer

Purpose:

Expose functionality.

Contains:

* Controllers
* Middleware
* Authentication
* Authorization
* Swagger
* Dependency Injection

This becomes the public interface of the platform.

---

# Frontend Layer

Purpose:

User experience.

Contains:

* Pages
* Components
* State Management
* Forms
* Dashboards

The frontend should contain minimal business logic.

---

# CQRS Architecture

The entire platform follows CQRS.

---

## Commands

Modify state.

Examples:

CreateOpportunity

UpdateOpportunity

DeleteOpportunity

UploadLegalPack

GenerateInvestmentAnalysis

---

## Queries

Read state.

Examples:

GetOpportunity

GetPortfolio

GetInvestmentReport

GetRiskAssessment

---

Benefits:

* Separation of concerns
* Easier testing
* Easier maintenance
* Better scalability

---

# MediatR

All commands and queries should flow through MediatR.

Pattern:

Controller

↓

Command / Query

↓

Handler

↓

Repository / Service

This creates consistency throughout the solution.

---

# Validation Strategy

All validation handled using FluentValidation.

Examples:

CreateOpportunityValidator

RegisterUserValidator

CreatePortfolioValidator

Validation should occur before business processing.

---

# Database Architecture

Use Code First EF Core.

Advantages:

* Source controlled schema
* Repeatable migrations
* Easier evolution

---

# Entity Design

All entities inherit from:

BaseEntity

Contains:

* Id

---

BaseAuditableEntity

Contains:

* CreatedDate
* CreatedBy
* LastModifiedDate
* LastModifiedBy

---

# Repository Strategy

Use repositories only where beneficial.

Avoid generic repositories everywhere.

Prefer:

OpportunityRepository

PortfolioRepository

DocumentRepository

Instead of:

GenericRepository<T>

Business-specific repositories are easier to understand.

---

# File Storage Architecture

Documents are critical.

Supported:

* PDF
* ZIP
* Images

Development:

```text
/uploads
```

Production:

Future Blob Storage.

Files should never be stored in SQL Server.

Only metadata stored in database.

---

# Document Processing Pipeline

```text
Upload
  ↓
Validation
  ↓
Storage
  ↓
OCR
  ↓
Classification
  ↓
Entity Extraction
  ↓
Risk Analysis
  ↓
AI Analysis
```

This becomes one of the platform's most important workflows.

---

# AI Architecture

The platform should never depend directly on a single AI provider.

---

# AI Provider Pattern

```text
IAIProvider
```

Implementations:

```text
OpenAIProvider

ClaudeProvider

AzureOpenAIProvider

LocalLlmProvider
```

---

# AI Context Builder

Every AI request should be context aware.

Inputs:

Property

Investment Analysis

Legal Findings

Risk Assessment

Market Intelligence

Portfolio Context

The AI should never operate blindly.

---

# Prompt Architecture

Prompts should be stored separately.

Examples:

InvestmentAnalysisPrompt

LegalReviewPrompt

RiskAssessmentPrompt

PortfolioAdvisorPrompt

Avoid hardcoding prompts in services.

---

# Background Processing

Many operations are long running.

Examples:

OCR

AI Analysis

Risk Calculations

Report Generation

Use:

BackgroundService

Future:

Hangfire

Azure Functions

---

# Caching Strategy

Introduce caching where appropriate.

Examples:

Market Data

Location Intelligence

School Data

Planning Data

Risk Calculations

Avoid unnecessary database calls.

---

# Angular Architecture

Use Feature Based Architecture.

---

# Angular Structure

```text
core/

shared/

features/

authentication/

dashboard/

opportunities/

analysis/

documents/

risk/

portfolio/

crm/

marketplace/
```

---

# Core Module

Contains:

* Auth
* Interceptors
* Guards
* Configuration

---

# Shared Module

Contains reusable components.

Examples:

Tables

Forms

Buttons

Cards

Modals

Charts

---

# Feature Modules

Each business area owns its functionality.

Benefits:

* Easier maintenance
* Easier onboarding
* Better scalability

---

# State Management

Use Signals first.

Use NgRx for:

* Complex state
* Shared state
* Long-lived state

Avoid overusing NgRx.

---

# UI Design System

Tailwind CSS

DaisyUI

Reusable components.

Goals:

* Consistency
* Accessibility
* Professional appearance

---

# Security Architecture

Authentication:

JWT

Authorization:

Role Based Access Control

Roles:

Admin

Investor

Analyst

Portfolio Manager

Viewer

---

# Audit Architecture

All significant actions logged.

Examples:

Login

Opportunity Created

Property Purchased

Document Uploaded

AI Recommendation Generated

This supports traceability.

---

# Testing Strategy

---

## Unit Tests

Commands

Queries

Services

Calculations

---

## Integration Tests

Database

Authentication

API Endpoints

---

## Frontend Tests

Components

Services

State Management

---

# Reporting Architecture

Future reports generated using dedicated services.

Examples:

Investment Report

Risk Report

Legal Report

Portfolio Report

Avoid report logic inside controllers.

---

# Deployment Strategy

Development:

LocalDB

Local File Storage

Angular Development Server

ASP.NET API

---

Future Production:

SQL Server

Blob Storage

App Service

CDN

AI Providers

---

# Monitoring Strategy

Initially:

Application Logs

Audit Logs

Error Logs

Future:

Application Insights

Telemetry

Performance Monitoring

---

# Scalability Strategy

The architecture should support:

Single Developer

↓

Small Team

↓

Startup

↓

Enterprise

without significant redesign.

---

# Architectural Success Criteria

The architecture is successful when:

* New developers understand the solution quickly.
* Features can be added without major rewrites.
* AI providers can be replaced easily.
* Database changes remain manageable.
* Business logic remains isolated.
* Testing is straightforward.
* The platform remains maintainable after years of development.

This architecture becomes the technical blueprint for the entire Property Investment Intelligence Platform and should be referenced before implementing any future feature.
