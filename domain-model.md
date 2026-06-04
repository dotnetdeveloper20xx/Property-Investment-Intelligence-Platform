# DomainModel.md

# Property Investment Intelligence Platform

## Domain Model & Business Entity Design

---

# Purpose

This document defines the core business entities that power the Property Investment Intelligence Platform.

Before creating databases, APIs, CQRS handlers, Angular pages, AI prompts, or reports, we must first understand the business objects that exist within the platform.

The domain model acts as the single source of truth for the entire application.

Every future feature, screen, report, workflow, and AI capability will ultimately depend upon these domain entities.

---

# Domain Philosophy

The platform is not a document management system.

The platform is not a CRM.

The platform is not an AI chatbot.

The platform is a Property Investment Intelligence Platform.

The domain model must reflect that vision.

The primary business concepts are:

* Investors
* Opportunities
* Properties
* Analysis
* Risks
* Documents
* Portfolios
* Assets
* Market Intelligence
* Professional Services

---

# Core Bounded Contexts

The platform is divided into the following business areas.

## Identity & Security

Responsible for:

* Users
* Authentication
* Authorization
* Roles
* Permissions

---

## Opportunity Management

Responsible for:

* Opportunities
* Notes
* Tasks
* Watchlists
* Pipelines

---

## Investment Analysis

Responsible for:

* ROI
* Yield
* Cash Flow
* BRRR
* Scenarios

---

## Legal Intelligence

Responsible for:

* Documents
* OCR
* Legal Risks
* Findings
* Reports

---

## AI Intelligence

Responsible for:

* Conversations
* Recommendations
* Summaries
* Checklists

---

## Risk Intelligence

Responsible for:

* Scores
* Risk Models
* Deal Killers
* Opportunity Detection

---

## Market Intelligence

Responsible for:

* Area Data
* Growth Metrics
* Schools
* Crime
* Planning

---

## Portfolio Management

Responsible for:

* Assets
* Mortgages
* Equity
* Cash Flow
* Net Worth

---

## Investor CRM

Responsible for:

* Contacts
* Investors
* Companies
* Partnerships

---

## Marketplace

Responsible for:

* Solicitors
* Surveyors
* Brokers
* Insurance Providers

---

# Core Entity: User

Represents a person using the platform.

Properties:

* Id
* FirstName
* LastName
* Email
* PasswordHash
* RoleId
* Status
* CreatedDate
* LastLoginDate

Relationships:

User owns many Opportunities.

User owns many Portfolios.

User creates Notes.

User creates Tasks.

---

# Core Entity: Opportunity

The most important entity in the platform.

Represents a potential property investment.

Properties:

* Id
* ReferenceNumber
* Title
* Address
* Status
* Source
* CreatedDate
* UserId

Relationships:

Opportunity has one Property.

Opportunity has many Notes.

Opportunity has many Tasks.

Opportunity has many Documents.

Opportunity has one InvestmentAnalysis.

Opportunity has one RiskAssessment.

Opportunity has one AIRecommendation.

---

# Core Entity: Property

Represents the physical property.

Properties:

* Id
* Address
* Postcode
* PropertyType
* Tenure
* Bedrooms
* Bathrooms
* FloorArea
* ConstructionType
* EPCRating

Relationships:

Property belongs to Opportunity.

Property belongs to Portfolio Asset after acquisition.

Property has many Documents.

Property has many Market Intelligence records.

---

# Opportunity Note

Investor observations.

Properties:

* Id
* OpportunityId
* Category
* Content
* CreatedBy
* CreatedDate

---

# Opportunity Task

Follow-up actions.

Properties:

* Id
* OpportunityId
* Title
* Description
* DueDate
* Priority
* Status

---

# Property Document

Uploaded files.

Properties:

* Id
* OpportunityId
* FileName
* FileType
* StoragePath
* UploadedDate

Relationships:

Document has Classification.

Document has OCR Content.

Document has Findings.

---

# Document Classification

Examples:

* Lease
* Title Register
* Search Report
* Tenancy Agreement
* EPC
* Planning Document

Properties:

* Id
* DocumentId
* ClassificationType
* ConfidenceScore

---

# Legal Finding

Extracted legal information.

Examples:

* Lease Length
* Ground Rent
* Restrictive Covenant

Properties:

* Id
* OpportunityId
* FindingType
* Value
* Confidence
* SourceDocument

---

# Legal Risk

Represents a legal concern.

Properties:

* Id
* OpportunityId
* RiskType
* Severity
* Confidence
* Recommendation

Examples:

* Short Lease
* Flying Freehold
* Possessory Title

---

# Investment Analysis

Financial evaluation.

Properties:

* Id
* OpportunityId
* PurchasePrice
* Deposit
* MortgageAmount
* Rent
* RefurbishmentCost

Calculated Fields:

* Yield
* ROI
* Cash Flow
* Growth Potential

---

# Scenario Analysis

Stores financial scenarios.

Properties:

* Id
* InvestmentAnalysisId
* ScenarioType

Examples:

* Best Case
* Expected Case
* Worst Case

---

# Risk Assessment

Master risk entity.

Properties:

* Id
* OpportunityId
* InvestmentScore
* OpportunityScore
* ConfidenceScore

Relationships:

Contains Risk Categories.

Contains Recommendations.

---

# Risk Category

Examples:

* Legal
* Financial
* Market
* Tenant
* Mortgage

Properties:

* Id
* RiskAssessmentId
* Category
* Score

---

# AI Conversation

Stores AI interactions.

Properties:

* Id
* UserId
* OpportunityId
* Question
* Response
* CreatedDate

---

# AI Recommendation

Stores AI-generated investment guidance.

Properties:

* Id
* OpportunityId
* RecommendationType
* Summary
* ConfidenceScore

---

# AI Committee Opinion

Stores individual viewpoints.

Examples:

* Conservative Investor
* Yield Investor
* Property Flipper

Properties:

* Id
* OpportunityId
* Persona
* Recommendation

---

# Market Intelligence

Represents area-level intelligence.

Properties:

* Id
* Postcode
* AreaName
* Population
* GrowthRate
* DemandRating

---

# Location Score

Properties:

* Id
* AreaId
* Score
* GeneratedDate

Components:

* Schools
* Crime
* Transport
* Growth

---

# Planning Activity

Properties:

* Id
* AreaId
* PlanningReference
* Status
* Description

---

# Portfolio

Represents a collection of owned assets.

Properties:

* Id
* UserId
* Name
* Description

Relationships:

Portfolio contains Assets.

---

# Asset

Represents a purchased property.

Properties:

* Id
* PortfolioId
* PropertyId
* PurchaseDate
* PurchasePrice
* CurrentValue

---

# Mortgage

Properties:

* Id
* AssetId
* Lender
* Product
* InterestRate
* Balance
* MonthlyPayment

---

# Cash Flow Record

Properties:

* Id
* AssetId
* Period
* Income
* Expenses
* NetCashFlow

---

# Equity Record

Properties:

* Id
* AssetId
* MarketValue
* MortgageBalance
* Equity

---

# Investor Contact

CRM contact.

Properties:

* Id
* Name
* Company
* Email
* Phone

---

# Company

Business entity.

Properties:

* Id
* Name
* Industry
* Website

Examples:

* Investor
* Solicitor
* Broker
* Surveyor

---

# Marketplace Provider

Professional service provider.

Properties:

* Id
* CompanyId
* ServiceType
* Rating
* CoverageArea

Examples:

* Solicitor
* Mortgage Broker
* Surveyor
* Insurance Provider

---

# Watchlist

Investor watchlist.

Properties:

* Id
* UserId
* Name

Relationships:

Contains many Opportunities.

---

# Knowledge Base Article

Stores lessons learned.

Properties:

* Id
* Title
* Category
* Content
* Author

---

# Future Domain Expansion

The model is intentionally designed for future growth.

Potential future entities:

* Auction
* Bid
* Offer
* Insurance Policy
* Development Project
* Planning Application Tracker
* AI Learning Dataset
* Market Forecast
* Investment Strategy

---

# Domain Model Success Criteria

The domain model is successful when:

* Every business concept has a clear home.
* Every future feature maps to existing contexts.
* Relationships remain understandable.
* Database design follows business design.
* CQRS handlers align with business language.
* AI prompts align with business terminology.

This document serves as the foundation for all future architecture and implementation decisions.
