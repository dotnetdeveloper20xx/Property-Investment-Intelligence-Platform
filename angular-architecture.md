# AngularArchitecture.md

# Property Investment Intelligence Platform

## Angular 20 Enterprise Frontend Architecture

---

# Introduction

The frontend of the Property Investment Intelligence Platform is significantly more than a collection of screens.

The frontend is the primary workspace for investors.

Users will spend the majority of their time interacting with:

* Dashboards
* Opportunities
* Property Analysis
* Legal Reviews
* Risk Assessments
* AI Advisors
* Portfolios
* Reports

The frontend must therefore be designed as an enterprise application rather than a collection of pages.

This document defines the Angular architecture, project structure, state management approach, design system, component strategy, routing model, and frontend development standards.

The objective is to create a frontend that remains maintainable and scalable for many years.

---

# Frontend Vision

The platform should feel like:

* Bloomberg Terminal for Property Investors
* Investment Research Platform
* Property Operating System
* AI-Powered Investment Workspace

The frontend must communicate professionalism, trust, intelligence, and simplicity.

Users should feel confident making investment decisions using the platform.

---

# Technology Stack

Frontend Framework:

* Angular 20

Language:

* TypeScript

Styling:

* Tailwind CSS
* DaisyUI

State Management:

* Angular Signals
* NgRx (Selective Usage)

Forms:

* Reactive Forms

Charts:

* Chart.js
* ApexCharts (Optional)

Authentication:

* JWT

Testing:

* Jasmine
* Karma
* Playwright

---

# Architectural Principles

---

## Feature First

Everything should be organised around business capabilities.

Not technical categories.

Good:

```text
features/opportunities

features/portfolio

features/risk
```

Bad:

```text
components

pages

services

misc
```

The business should drive structure.

---

## Reusable By Default

Every component should be evaluated for reusability.

Avoid duplication.

Common patterns should become shared components.

---

## Signals First

Angular Signals should be the default state mechanism.

NgRx should be introduced only when complexity justifies it.

---

## API Driven

Frontend should consume APIs.

Business logic belongs primarily on the server.

---

# Angular Project Structure

```text
src/app

core

shared

layouts

features
```

---

# Core Layer

Contains application-wide services.

Purpose:

Infrastructure.

Not business functionality.

---

## Core Structure

```text
core

authentication

guards

interceptors

services

configuration

constants

models
```

---

# Authentication Module

Contains:

Login

Logout

Register

Token Management

Session Management

Route Protection

---

# Interceptors

Examples:

AuthInterceptor

ErrorInterceptor

LoadingInterceptor

LoggingInterceptor

---

# Guards

Examples:

AuthGuard

RoleGuard

PermissionGuard

---

# Shared Layer

Contains reusable UI.

Purpose:

Build once.

Use everywhere.

---

# Shared Structure

```text
shared

components

directives

pipes

models

services
```

---

# Shared Components

Examples:

AppButton

AppCard

AppModal

AppTable

AppBadge

AppSpinner

AppEmptyState

AppPagination

AppSearchBox

AppPageHeader

---

# Shared Directives

Examples:

PermissionDirective

DebounceDirective

AutoFocusDirective

---

# Shared Pipes

Examples:

CurrencyPipe

PercentagePipe

RiskLevelPipe

ScorePipe

DateAgoPipe

---

# Layout Layer

Responsible for application shells.

---

# Layout Structure

```text
layouts

authenticated

public
```

---

# Public Layout

Used for:

Login

Register

Forgot Password

Landing Pages

---

# Authenticated Layout

Used for:

Dashboard

Portfolio

Analysis

Reports

AI Assistant

All protected areas.

---

# Navigation Architecture

Primary Navigation:

Dashboard

Opportunities

Analysis

Documents

Risk

Portfolio

CRM

Reports

Marketplace

Settings

---

# Feature Architecture

Every business capability owns its code.

---

# Opportunities Module

```text
features

opportunities
```

Contains:

Opportunity List

Opportunity Detail

Create Opportunity

Edit Opportunity

Opportunity Notes

Opportunity Tasks

Opportunity Timeline

---

# Opportunities Components

Examples:

OpportunityCard

OpportunityTable

OpportunitySummary

OpportunityStatusBadge

OpportunityTimeline

---

# Property Module

```text
features

properties
```

Contains:

Property Details

Property Images

Property Information

Property History

---

# Investment Analysis Module

Contains:

ROI Calculators

Yield Analysis

Cash Flow Analysis

BRRR Analysis

Scenario Modelling

Comparison Engine

---

# Legal Intelligence Module

Contains:

Document Upload

Document Viewer

Legal Findings

Legal Risks

Legal Reports

Search

---

# AI Intelligence Module

One of the most important modules.

Contains:

AI Chat

Property Assistant

Investment Advisor

Committee Reviews

Recommendations

Checklists

---

# Risk Intelligence Module

Contains:

Investment Score

Opportunity Score

Risk Heatmaps

Deal Killers

Risk Reports

Confidence Analysis

---

# Market Intelligence Module

Contains:

Location Analysis

Growth Analysis

Rental Demand

Crime Data

Schools

Transport

Planning Activity

---

# Portfolio Module

Contains:

Portfolio Dashboard

Assets

Mortgages

Cash Flow

Equity

Net Worth

Forecasting

---

# CRM Module

Contains:

Contacts

Companies

Partnerships

Investor Management

---

# Marketplace Module

Contains:

Solicitors

Surveyors

Mortgage Brokers

Insurance Providers

Reviews

Comparisons

---

# Reports Module

Contains:

Generated Reports

Downloads

Templates

History

---

# Settings Module

Contains:

Profile

Preferences

Notifications

Security

API Keys (Future)

---

# State Management Strategy

---

# Signals

Default state management solution.

Examples:

Opportunity Detail

Property View

Dashboard Widgets

Forms

Local UI State

---

# NgRx

Use only for:

Authentication

User Session

Global Notifications

Cross-Module State

Long-Lived Application State

Avoid excessive NgRx complexity.

---

# UI Component Hierarchy

---

# Atoms

Smallest components.

Examples:

Button

Icon

Badge

Label

Input

---

# Molecules

Grouped components.

Examples:

Search Box

Filter Panel

Score Indicator

Metric Card

---

# Organisms

Business-focused components.

Examples:

Opportunity Card

Portfolio Summary

Investment Score Panel

AI Recommendation Panel

---

# Pages

Full screens.

Examples:

Opportunity Detail Page

Portfolio Dashboard Page

Risk Analysis Page

---

# Dashboard Strategy

Dashboards are central to the platform.

Every major feature should have a dashboard.

Examples:

Opportunity Dashboard

Portfolio Dashboard

Risk Dashboard

AI Dashboard

Market Dashboard

CRM Dashboard

---

# Charting Strategy

Supported visualisations:

Bar Charts

Line Charts

Pie Charts

Heatmaps

Trend Charts

Forecast Charts

Comparison Charts

Visual intelligence should be prioritised.

---

# Form Strategy

Use:

Reactive Forms

Validation Services

Reusable Form Controls

Examples:

Currency Input

Percentage Input

Address Lookup

Property Selector

Document Upload

The user experience should be professional.

---

# Notification Strategy

Global notification service.

Types:

Success

Warning

Error

Information

Use toast notifications consistently.

---

# Error Handling Strategy

Display:

Friendly Messages

Clear Guidance

Actionable Feedback

Never display technical errors to users.

---

# Loading Strategy

All long-running operations should display:

Loading Indicators

Progress Bars

Processing Status

This is especially important for:

Document Processing

AI Analysis

Report Generation

---

# File Upload Architecture

Reusable upload framework.

Supports:

PDF

ZIP

Images

Documents

Features:

Drag & Drop

Multi Upload

Progress Tracking

Validation

Retry

---

# Search Architecture

Global Search:

Properties

Opportunities

Documents

Reports

Contacts

Knowledge Base

Search should feel fast and intelligent.

---

# Accessibility Standards

Support:

Keyboard Navigation

Screen Readers

ARIA Labels

Colour Contrast Compliance

The platform should be accessible to all users.

---

# Responsive Design Strategy

Support:

Desktop

Laptop

Tablet

Mobile

Primary optimisation target:

Desktop Investors

Secondary target:

Mobile Monitoring

---

# Theme Architecture

Initial Theme:

Professional Investment Theme

Future Themes:

Dark Mode

Light Mode

Custom Branding

Investor Theme

Corporate Theme

---

# Frontend Testing Strategy

---

## Unit Tests

Components

Services

Signals

State Management

---

## Integration Tests

API Integration

Routing

Authentication

Forms

---

## End-To-End Tests

Critical user journeys:

Register

Create Opportunity

Upload Legal Pack

Generate Analysis

View Portfolio

---

# Performance Standards

Use:

Lazy Loading

OnPush Strategy

Signals

Route-Level Loading

Avoid:

Large Bundles

Excessive State

Unnecessary API Calls

---

# Security Standards

Never store:

Passwords

Secrets

Sensitive Tokens

Protect:

Routes

Actions

File Uploads

Administrative Features

---

# Frontend Success Criteria

The frontend architecture is successful when:

* New features fit naturally into existing structures.
* Developers know exactly where code belongs.
* Components remain reusable.
* Performance remains strong.
* State remains manageable.
* User experience remains consistent.

The frontend should feel like a world-class investment platform rather than a traditional business application.

This document becomes the blueprint for all Angular development throughout the Property Investment Intelligence Platform.
