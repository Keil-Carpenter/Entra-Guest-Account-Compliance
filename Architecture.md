This document describes the internal design and execution flow of the Entra Guest Account Compliance script.



\# Architecture – Entra Guest Account Compliance



\## Overview



This PowerShell script uses Microsoft Graph to audit guest users in Microsoft Entra ID and identify accounts that have not accepted their invitation within a defined time window.



It is a read-only governance tool designed for identity hygiene and external collaboration monitoring.



\---



\## Core Components



\### 1. Authentication Layer

\- Connects to Microsoft Graph using delegated permissions

\- Requires `User.Read.All`



\---



\### 2. Data Retrieval Layer

\- Queries guest users using:

&#x20; - `Get-MgUser -Filter "userType eq 'Guest'"`



\---



\### 3. Evaluation Logic

\- Defines threshold date (default: 30 days ago)

\- Compares:

&#x20; - `CreatedDateTime`

&#x20; - `ExternalUserState`



Identifies users where:

\- Account age exceeds threshold

\- Invitation status is not "Accepted"



\---



\### 4. Output Layer

Returns filtered dataset including:



\- DisplayName

\- Mail

\- UserPrincipalName

\- CreatedDateTime

\- ExternalUserState



\---



\## Execution Flow



1\. Import Microsoft Graph module

2\. Authenticate to Microsoft Graph

3\. Retrieve guest users

4\. Calculate cutoff date (30 days ago)

5\. Evaluate each guest account

6\. Filter unaccepted invitations

7\. Output results



\---



\## Design Characteristics



\- Read-only operation (no writes)

\- Stateless execution

\- Fully idempotent

\- Safe for production environments

\- Suitable for scheduled reporting (Task Scheduler / automation jobs)



\---



\## Dependencies



\- Microsoft Graph PowerShell SDK



\### Permissions

\- User.Read.All

