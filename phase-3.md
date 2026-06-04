# Phase-03-Investment-Analysis-Engine.md

# Property Investment Intelligence Platform

## Phase 3 – Investment Analysis Engine

---

# Introduction

Phase 1 established the platform foundation.

Phase 2 introduced Property Opportunity Management and transformed the system into a property investment workspace.

However, investors still face a major challenge.

They can store opportunities.

They can organise opportunities.

They can track opportunities.

But they still do not know whether an opportunity is financially attractive.

This is where Phase 3 begins.

Phase 3 introduces the first true intelligence capability of the platform.

The Investment Analysis Engine becomes the financial brain of the system.

Every successful property investor asks the same questions:

* Is this property profitable?
* What return can I expect?
* What are the risks?
* Is this deal better than other opportunities?
* How much should I pay?
* What happens if costs increase?
* What happens if rent falls?

Most investors answer these questions using spreadsheets.

Some investors use online calculators.

Many investors simply estimate.

The result is inconsistent decision making.

This phase standardises investment analysis and provides professional-grade calculations to every investor using the platform.

By the end of this phase, users will be able to evaluate opportunities with confidence and compare deals using consistent financial metrics.

---

# Business Objectives

The objective of this phase is simple.

Help investors answer:

### Is this a good investment?

The platform should provide accurate calculations and meaningful financial insights.

Instead of relying on intuition, investors should be able to make decisions using structured financial analysis.

---

# Core Investment Analysis Concept

Every property opportunity should have a dedicated Investment Analysis section.

The platform should gather financial information and automatically calculate key investment metrics.

Users should no longer need spreadsheets.

The platform becomes the investor's financial modelling tool.

---

# Financial Inputs

Before calculations can occur, the system must capture investment assumptions.

These assumptions should be stored against each property opportunity.

---

## Purchase Information

Purchase Price

Guide Price

Target Purchase Price

Maximum Bid

Deposit Percentage

Mortgage Amount

Mortgage Product

Arrangement Fees

Broker Fees

---

## Rental Information

Expected Monthly Rent

Expected Annual Rent

Occupancy Rate

Void Period Assumptions

Management Costs

Maintenance Costs

Insurance Costs

Ground Rent

Service Charges

---

## Refurbishment Information

Refurbishment Budget

Contingency Budget

Structural Costs

Decoration Costs

Kitchen Costs

Bathroom Costs

Professional Fees

---

## Exit Information

Expected Market Value

Expected Sale Price

Exit Costs

Estate Agent Fees

Legal Costs

Capital Gains Assumptions

---

# Gross Yield Calculation

Gross Yield is one of the most commonly used metrics in property investing.

Formula:

Annual Rental Income divided by Purchase Price multiplied by 100.

The platform should automatically calculate:

* Gross Yield
* Yield Bands
* Yield Ranking

Categories:

Poor

Average

Good

Excellent

This provides immediate visibility into rental performance.

---

# Net Yield Calculation

Gross Yield alone is misleading.

The platform must also calculate Net Yield.

Expenses included:

* Management
* Insurance
* Maintenance
* Ground Rent
* Service Charges
* Void Periods

Net Yield provides a more realistic view of profitability.

---

# Cash Flow Analysis

Cash flow is critical.

Many investors focus on yield while ignoring monthly cash generation.

The platform should calculate:

Monthly Income

Monthly Mortgage Payments

Monthly Costs

Monthly Cash Flow

Annual Cash Flow

This allows investors to identify profitable and loss-making opportunities.

---

# Return On Investment (ROI)

ROI measures how effectively capital is being used.

The platform should calculate:

Cash Invested

Annual Profit

Return Percentage

ROI should be available for:

* Cash Purchase
* Mortgage Purchase
* Refurbishment Projects

---

# Capital Growth Analysis

Not all profits come from rental income.

Many investors invest primarily for appreciation.

The system should calculate:

Projected Property Value

Growth Forecast

Annual Appreciation

Five-Year Growth

Ten-Year Growth

Multiple growth scenarios should be supported.

---

# BRRR Analysis

A major feature for UK property investors.

BRRR stands for:

Buy

Refurbish

Refinance

Rent

Repeat

The platform should provide a dedicated BRRR module.

Calculations include:

Purchase Price

Refurbishment Cost

End Value

Refinance Amount

Capital Recovered

Cash Left In Deal

Expected Rental Income

BRRR Suitability Score

This becomes a major selling feature.

---

# Refurbishment Planner

Refurbishment costs significantly impact profitability.

The platform should support:

### Light Refurbishment

Paint

Flooring

Minor Repairs

---

### Medium Refurbishment

Kitchen

Bathroom

Electrical

Plumbing

---

### Heavy Refurbishment

Structural Works

Extensions

Conversions

---

Users should create refurbishment budgets and monitor assumptions.

---

# Investment Score Foundation

Phase 6 introduces advanced scoring.

However, Phase 3 begins collecting the financial data required.

Metrics contributing later include:

* Yield
* ROI
* Cash Flow
* Growth Potential

These become inputs into future intelligence engines.

---

# Scenario Modelling

One of the most valuable features in the platform.

Investors need to understand uncertainty.

Examples:

What if rent falls?

What if refurbishment costs increase?

What if interest rates rise?

What if the property sells for less?

The platform should provide:

Best Case

Expected Case

Worst Case

This encourages realistic decision making.

---

# Maximum Bid Calculator

One of the most commercially valuable features.

Investors often become emotional during negotiations and auctions.

The platform should calculate:

Maximum Safe Purchase Price

based on:

Target ROI

Expected Costs

Required Profit Margin

Risk Tolerance

The result becomes:

### Walk Away Price

This helps investors remain disciplined.

---

# Deal Comparison Engine

Investors rarely analyse a single opportunity.

The platform should allow:

Property A

vs

Property B

vs

Property C

Comparisons should include:

Yield

Cash Flow

ROI

Refurbishment Costs

Growth Potential

Investment Ranking

This helps investors prioritise opportunities.

---

# Financial Dashboards

Create dedicated visual dashboards.

Display:

Portfolio Yield

Average ROI

Monthly Cash Flow

Projected Growth

Refurbishment Exposure

Top Opportunities

Financial insights should be visual and easy to understand.

---

# User Experience Goals

The platform should feel like:

A professional investment analyst.

Not a spreadsheet.

Not a calculator.

Not an accounting system.

The user should feel they are receiving expert investment guidance.

---

# Reporting

Generate professional investment reports.

Reports should include:

Property Summary

Financial Inputs

Investment Metrics

Scenario Analysis

Maximum Bid

Recommendations

Reports should be exportable in future phases.

---

# Technical Requirements

Backend:

* CQRS Commands
* CQRS Queries
* Financial Calculation Services
* Domain Rules
* Validation

Frontend:

* Financial Forms
* Interactive Dashboards
* Charts
* Scenario Editors
* Comparison Views

Database:

InvestmentAnalysis

RefurbishmentPlans

CashFlowModels

ScenarioModels

ComparisonResults

FinancialAssumptions

---

# API Requirements

Examples:

GET api/investment-analysis/{id}

POST api/investment-analysis

PUT api/investment-analysis

POST api/investment-analysis/calculate

POST api/investment-analysis/compare

POST api/investment-analysis/scenarios

GET api/investment-analysis/report

---

# Definition Of Done

Phase 3 is complete when:

Users can enter financial assumptions.

Users can calculate:

* Gross Yield
* Net Yield
* Cash Flow
* ROI
* Capital Growth

Users can perform BRRR analysis.

Users can create refurbishment plans.

Users can run scenarios.

Users can calculate maximum bid prices.

Users can compare opportunities.

Users can view financial dashboards.

At this point the platform becomes a genuine investment decision support system rather than simply an opportunity tracker.

---

# AI Implementation Prompt

You are a Senior Solution Architect, Property Investment Specialist, Financial Modelling Expert, ASP.NET Core Expert, Angular Expert, and CQRS Architect.

Your task is to fully implement Phase 3 of the Property Investment Intelligence Platform.

Existing platform includes:

* User Management
* Authentication
* Property Opportunity Management
* Clean Architecture
* CQRS
* ASP.NET Core 10
* Angular 20

Implement the complete Investment Analysis Engine.

Requirements:

1. Create investment analysis domain models.
2. Create financial assumption entities.
3. Create refurbishment planning entities.
4. Create cash flow calculation services.
5. Create gross yield calculations.
6. Create net yield calculations.
7. Create ROI calculations.
8. Create capital growth calculations.
9. Create BRRR analysis engine.
10. Create maximum bid calculator.
11. Create scenario modelling engine.
12. Create comparison engine.
13. Create financial dashboards.
14. Create CQRS commands.
15. Create CQRS queries.
16. Create handlers.
17. Create validators.
18. Create DTOs.
19. Create EF configurations.
20. Create database migrations.
21. Create Angular pages.
22. Create Angular charts.
23. Create Angular forms.
24. Create Angular services.
25. Create Angular state management.
26. Create financial reports.
27. Create reusable calculation components.
28. Create comparison views.
29. Create dashboard widgets.
30. Create unit tests and integration tests.

Follow:

* SOLID principles
* Clean Architecture
* CQRS
* Enterprise coding standards
* Property investment best practices

Generate production-ready implementation.

Create all entities, commands, queries, handlers, validators, DTOs, APIs, pages, services, routes, database objects, and user interfaces required.

Ensure calculations are accurate and testable.

At completion provide:

* Solution structure
* Database schema
* Financial formulas
* API endpoints
* Angular routes
* Component inventory
* Technical debt summary

Continue implementation until Phase 3 is fully completed and production ready.
