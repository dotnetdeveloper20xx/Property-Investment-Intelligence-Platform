# DatabaseDesign.md

# Property Investment Intelligence Platform

## Enterprise Database Design & Data Architecture

---

# Introduction

This document defines the complete database architecture for the Property Investment Intelligence Platform.

The purpose of this document is to translate the business domain model into a structured, scalable, and maintainable SQL Server database design.

The database is one of the most important assets within the platform.

Every investment opportunity, legal pack, AI recommendation, portfolio record, risk assessment, and market intelligence record ultimately becomes data.

Good database design creates:

* Better performance
* Better reporting
* Better maintainability
* Better scalability
* Better data quality

Poor database design creates technical debt that becomes increasingly expensive to fix.

This document establishes the data foundation of the entire platform.

---

# Database Philosophy

The database should represent business concepts.

Tables should reflect the language used by investors and business users.

Examples:

Good:

* Opportunities
* Properties
* Portfolios
* LegalRisks
* InvestmentAnalyses

Bad:

* TblData
* PropertyStuff
* RiskInfo

Business language should drive schema design.

---

# Database Technology

Development:

* SQL Server LocalDB

Production:

* SQL Server Standard
* SQL Server Enterprise (future)

ORM:

* Entity Framework Core

Approach:

* Code First Migrations

---

# Naming Standards

---

## Tables

Plural names.

Examples:

Users

Properties

Opportunities

Portfolios

Documents

---

## Primary Keys

Standard:

```sql
Id UNIQUEIDENTIFIER
```

All tables use GUID identifiers.

Reason:

* Easier integration
* Better API compatibility
* Future distributed support

---

## Foreign Keys

Pattern:

```sql
EntityNameId
```

Examples:

PropertyId

OpportunityId

PortfolioId

UserId

---

## Date Columns

Pattern:

```sql
CreatedDate

LastModifiedDate
```

---

# Audit Strategy

Every business table should contain:

```sql
Id

CreatedDate

CreatedBy

LastModifiedDate

LastModifiedBy
```

Benefits:

* Traceability
* Auditing
* Compliance
* Historical investigations

---

# Identity & Security Schema

---

# Users

Stores platform users.

Columns:

* Id
* FirstName
* LastName
* Email
* PasswordHash
* Status
* LastLoginDate

Indexes:

Email Unique

---

# Roles

Stores security roles.

Examples:

Admin

Investor

Analyst

PortfolioManager

Viewer

---

# UserRoles

Many-to-many relationship.

Links users and roles.

---

# RefreshTokens

Stores JWT refresh tokens.

Supports:

* Login
* Logout
* Session Management

---

# Opportunities Context

The heart of the platform.

---

# Opportunities

Stores investment opportunities.

Columns:

* Id
* ReferenceNumber
* PropertyId
* UserId
* StatusId
* SourceId
* Title
* Description

Indexes:

ReferenceNumber

StatusId

CreatedDate

---

# OpportunityStatuses

Lookup table.

Examples:

Watching

Researching

Interested

BidPlanned

Purchased

Rejected

Archived

---

# OpportunitySources

Lookup table.

Examples:

Auction

EstateAgent

OffMarket

PropertySourcer

Referral

---

# OpportunityNotes

Stores investor observations.

Columns:

* OpportunityId
* Category
* NoteText

---

# OpportunityTasks

Stores actions.

Columns:

* OpportunityId
* Title
* Description
* DueDate
* Priority
* Status

---

# OpportunityHistory

Tracks changes.

Stores:

Status Changes

Decision Changes

Activity Events

---

# Property Context

---

# Properties

Stores physical property information.

Columns:

* Address
* Postcode
* PropertyTypeId
* TenureTypeId
* Bedrooms
* Bathrooms
* FloorArea

Indexes:

Postcode

PropertyTypeId

---

# PropertyTypes

Lookup table.

Examples:

House

Flat

HMO

Commercial

Land

DevelopmentSite

---

# TenureTypes

Lookup table.

Examples:

Freehold

Leasehold

Commonhold

ShareOfFreehold

---

# PropertyImages

Stores image metadata.

Actual files stored separately.

---

# Investment Analysis Context

---

# InvestmentAnalyses

Stores investment assumptions.

Columns:

* PurchasePrice
* Deposit
* MortgageAmount
* MonthlyRent
* RefurbishmentCost

---

# ScenarioAnalyses

Stores:

Best Case

Expected Case

Worst Case

---

# BRRRAnalyses

Stores BRRR calculations.

---

# InvestmentComparisons

Stores comparison results.

---

# Legal Intelligence Context

---

# Documents

Stores uploaded document metadata.

Columns:

* OpportunityId
* FileName
* FilePath
* FileSize
* ContentType

Indexes:

OpportunityId

CreatedDate

---

# DocumentClassifications

Stores classification results.

Examples:

Lease

Search

Title Register

Planning Document

---

# DocumentOcrContent

Stores extracted text.

Potentially large table.

Full-text indexing enabled.

---

# LegalFindings

Stores extracted legal information.

Examples:

Lease Length

Ground Rent

Service Charges

Rights Of Way

---

# LegalRisks

Stores legal concerns.

Examples:

Flying Freehold

Possessory Title

Short Lease

Restrictive Covenant

---

# LegalReports

Stores generated reports.

---

# Risk Intelligence Context

---

# RiskAssessments

Master risk record.

Columns:

* OpportunityId
* InvestmentScore
* OpportunityScore
* ConfidenceScore

---

# RiskCategories

Stores category scores.

Examples:

Legal

Financial

Market

Mortgage

Tenant

Development

---

# DealKillers

Stores critical issues.

Examples:

Lease Below 60 Years

Major Structural Risk

Flood Risk

---

# Recommendations

Stores generated recommendations.

---

# AI Intelligence Context

---

# AIConversations

Stores conversations.

Columns:

* UserId
* OpportunityId
* Question
* Response

---

# AIRecommendations

Stores AI-generated guidance.

---

# AICommitteeOpinions

Stores persona responses.

Examples:

Conservative Investor

Yield Investor

Property Developer

---

# AIPrompts

Stores prompt templates.

Separating prompts from code improves maintainability.

---

# AIReports

Stores generated reports.

---

# Market Intelligence Context

---

# Areas

Represents geographic areas.

Examples:

Manchester

Leeds

Reading

Croydon

---

# MarketStatistics

Stores:

Price Growth

Average Prices

Demand Metrics

Supply Metrics

---

# RentalStatistics

Stores:

Rental Demand

Average Rent

Vacancy Rates

Rental Growth

---

# SchoolData

Stores local school intelligence.

---

# CrimeData

Stores area crime metrics.

---

# PlanningApplications

Stores planning intelligence.

---

# RegenerationProjects

Stores regeneration opportunities.

---

# LocationScores

Stores area scoring.

---

# Portfolio Context

---

# Portfolios

Stores investor portfolios.

---

# Assets

Represents owned properties.

Columns:

* PortfolioId
* PropertyId
* PurchasePrice
* PurchaseDate
* CurrentValue

---

# Mortgages

Stores mortgage information.

Columns:

* Lender
* InterestRate
* OutstandingBalance

---

# EquityRecords

Historical equity tracking.

Supports trend reporting.

---

# CashFlowRecords

Stores monthly performance.

---

# AssetValuations

Stores property valuations.

Historical records retained.

---

# WealthForecasts

Stores future projections.

---

# CRM Context

---

# Contacts

Stores CRM contacts.

---

# Companies

Stores businesses.

Examples:

Solicitors

Surveyors

Brokers

Investors

---

# ContactActivities

Stores communication history.

---

# Partnerships

Stores investor relationships.

---

# Collaboration Context

---

# Comments

Stores collaboration comments.

---

# ActivityFeeds

Stores platform activity.

---

# Notifications

Stores user notifications.

---

# Approvals

Stores approval workflow data.

---

# Watchlists

Stores custom investor watchlists.

---

# WatchlistItems

Links opportunities to watchlists.

---

# Knowledge Base Context

---

# KnowledgeBaseArticles

Stores lessons learned.

---

# ArticleCategories

Lookup table.

---

# ArticleTags

Tagging support.

---

# Marketplace Context

---

# MarketplaceProviders

Professional service providers.

Examples:

Solicitors

Surveyors

Mortgage Brokers

Insurance Providers

---

# ProviderServices

Services offered.

---

# ProviderReviews

User reviews.

---

# ProviderCoverageAreas

Geographic coverage.

---

# Reporting Context

---

# ReportDefinitions

Stores report templates.

---

# GeneratedReports

Stores generated reports.

---

# Performance Strategy

---

## Critical Indexes

Opportunities

Properties

Documents

LegalRisks

RiskAssessments

Assets

AIConversations

All heavily queried tables require proper indexing.

---

## Full Text Search

Enable on:

DocumentOcrContent

LegalFindings

KnowledgeBaseArticles

AIReports

Supports advanced searching.

---

## Archive Strategy

Future support:

Archive tables.

Older records can be moved for performance.

---

# Database Growth Strategy

Expected growth:

Properties:

100,000+

Documents:

1,000,000+

OCR Records:

10,000,000+

AI Records:

Millions

The design should support long-term expansion.

---

# Future Database Extensions

Potential future tables:

Auctions

Bids

Offers

InsurancePolicies

DevelopmentProjects

PropertyAlerts

InvestorBenchmarks

CommunityInsights

MachineLearningModels

MarketForecasts

---

# Database Success Criteria

The database design is successful when:

* Business concepts map directly to tables.
* Queries remain understandable.
* Reporting is efficient.
* Future features fit naturally.
* Data integrity is protected.
* Performance scales with growth.

This database architecture becomes the permanent data foundation of the Property Investment Intelligence Platform.
