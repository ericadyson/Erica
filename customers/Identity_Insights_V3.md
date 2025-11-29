# Identity Insights

## Overview
Identity Insights gives you a complete view of who can access each application and where unmanaged accounts expose your organisation.

## What Identity Insights Does
Identity Insights brings together identity data that usually sits in different systems and shows you every account tied to every identity.

## Why Identity Visibility Matters
Many risky accounts never pass through your IDP or IGA. Identity Insights reveals these hidden accounts so you can review and fix access gaps.

# Core Concepts
Start here to understand the terms and ideas Identity Insights uses across the product.

## Identities and Accounts
Identities belong to people or systems. Accounts belong to applications. One identity often owns several accounts, and Orchid links them so you see the full picture.

## Identity Types
Human and non-human identities show up differently in applications. Knowing the type helps you understand how an account behaves.

| Identity Type | Description | Examples |
|---------------|-------------|----------|
| Human | A person who uses the application | Employee, contractor |
| NHI | A non-human identity that performs actions | Service account, automation, integration |

(Hybrid identities are not supported.)

# Requirements
Identity Insights shows different data depending on your setup. Use this table to confirm your environment has the pieces needed for full visibility.

## What Each Requirement Enables

Use this table to confirm that your environment has the setup needed to show all Identity Insights data.

| Requirement | What It Enables |
|------------|------------------|
| Microsoft Entra IDP Integration | MFA state, SSO type, orphan accounts, disconnected app detection |
| Application Database Access | Identity list, account list, authentication method |
| Audit License (optional) | Last Login, dormant accounts |
| Continuous Monitoring (optional) | Daily identity updates, active dormant detection |

# How Orchid Builds Identity Insights
Identity Insights pulls data from your applications, IDP, IGA, and audit sources. Orchid connects the records so you see one identity instead of scattered account fragments.

## Data Sources
Each source adds a different part of the identity story. Together, they show who has access and how they authenticate.

| Source | Purpose | Example Data |
|--------|---------|--------------|
| Application database | Retrieve accounts and attributes | Local users |
| Microsoft Entra | Understand expected identity state | MFA, SSO configuration, groups |
| SailPoint IIQ (on-prem) | Gather identity relationships | Roles, entitlements |
| Audit data | Track user activity | Login, logout |
| Database comparison | Detect identity changes | New accounts, removed accounts |

## Correlation Across Systems
Applications and identity systems often label the same person in different ways. Orchid matches these patterns so you see a unified identity.

# Special Cases
Sometimes Identity Insights cannot show full data. These scenarios explain what you’ll see and why it happens.

| Condition | What You See | Why It Happens |
|----------|--------------|----------------|
| No IDP integration | All accounts appear local. No orphan detection. Prompt to configure IDP. | Orchid cannot compare app accounts with the IDP. |
| No database access | Empty table. “Identity data unavailable.” No metrics. | Orchid cannot read local user data. |
| Database accessible but no users | 0% metrics. Prompt to configure IDP. | The app uses SSO only or stores no local users. |
| Application disconnected from IDP | “Disconnected” risk in Application Details. | Orchid detects the app does not authenticate with the IDP. |

# Monitoring Modes and Data Availability
Monitoring affects how often data updates and which metrics appear. Some values show only after a one-time scan; others need daily refresh or audit events. The table helps you decide when to enable continuous monitoring or change a mode.

| Mode | Refresh Behaviour | What You See |
|------|-------------------|--------------|
| One-time monitoring | One scan only | Data does not refresh |
| Continuous monitoring | Daily refresh | Identity data stays current |
| Audit enabled | Near real-time logins | Last Login and Dormant accounts |
| Audit disabled | No login activity | Lock icons on activity fields |

# Using the Identities Tab
The Identities tab shows every account for the application and the risks linked to it. Use it to review authentication types, MFA state, and account activity.

## Where You Find It
Open an application and select Identities. What you see depends on what Orchid can access and what your admin has enabled.

## Understanding the Accounts Table
Each column in the Accounts table surfaces a specific part of account risk. The tables below help you read and interpret the data.

# Identity Risk Indicators
Risk icons mark accounts that need attention. Each icon signals a different issue, such as privilege, orphan status, or lack of MFA.

| Risk Type | When It Appears and What It Means | What To Do |
|-----------|-----------------------------------|------------|
| Privileged account (Crown) | The account holds elevated roles. Orchid detects privileged patterns or you classify the role. | Review the access. Remove unnecessary privileges. |
| Orphan account (Orange rectangle) | Appears only with Entra. The account exists in the app but not the IDP. | Disable or remove the account. Fix offboarding gaps. |
| Dormant account (Cactus) | Appears only with audit + continuous monitoring. No login activity. | Remove the account if not needed. Confirm valid use cases. |
| Local account risk (Sofa) | App uses SSO but the account authenticates only locally. | Move the account to SSO unless you have a documented exception. |
| No MFA icon | MFA is disabled in Entra. Conditional MFA is not counted. | Enable MFA or document an exception. |

# Authentication Types
Accounts sign in through local credentials, SSO, or both. Knowing the method helps you assess consistency and risk.

| Auth Type | Meaning |
|-----------|---------|
| Local | Authenticates with the application |
| SSO | Authenticates through the IDP |
| Both | Can use local and SSO authentication |

# Account Attributes
These fields show how active and secure an account is. They highlight accounts with no MFA, excessive entitlements, or no login history.

| Attribute | Meaning | When It Appears |
|-----------|---------|------------------|
| MFA state | Shows whether MFA is enabled, disabled, or conditional. | With Entra integration |
| Z count | Total groups, roles, entitlements, and permissions for the account. | When Orchid reads the database |
| Last Login | Most recent successful login. | With audit enabled |

# Other Product Areas Affected
Identity Insights adds identity counts and risk markers to other parts of Orchid so you can spot issues before opening an application.

## Authorization Tab
You see how many identities belong to each role. You can classify or unclassify privileged roles.

## Application Inventory
You see an Accounts column and identity risk icons next to existing compliance indicators. This helps you find high-risk applications without opening each one.

# Licensing Behaviour and UI Messages
Licensing and configuration shape what Identity Insights reveals. These messages explain why some values appear locked or unavailable.

| Condition | What You See | Why |
|----------|--------------|-----|
| Audit license not enabled | Last Login locked. Dormant locked. | Activity data requires audit. |
| Audit license enabled | Last Login and Dormant visible. | Orchid collects login activity. |
| Continuous monitoring off | No Dormant data. Info icon prompts you to enable it. | Dormant requires continuous monitoring. |
| No IDP integration | No orphan or MFA data. All accounts appear local. | Orchid cannot read IDP details. |
| IDP integration enabled | MFA state, SSO type, orphan status available. | Orchid receives data from Entra. |
| Information icons shown | Guidance based on your setup. | Orchid tells you what to enable next. |
