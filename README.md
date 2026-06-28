
# Entra Guest Account Compliance
PowerShell tool for auditing Microsoft Entra ID guest users who have not accepted their invitation within a defined time period.



## Overview
This script uses Microsoft Graph PowerShell to identify guest users in Microsoft Entra ID who have not accepted their invitation after a configurable period (default: 30 days).

It is designed for identity governance, tenant hygiene, and external collaboration management.



## What it does
- Connects to Microsoft Graph
- Retrieves all guest users in the tenant
- Compares account creation date against a configurable threshold (default: 30 days)
- Identifies guests who have not accepted their invitation
- Outputs a filtered list for review or reporting



## Output

The script returns:

- Display Name
- Email Address
- User Principal Name
- Account Created Date
- External User State



## Requirements

- PowerShell 5.1+
- Microsoft Graph PowerShell SDK

### Required Permissions
- User.Read.All



## Usage

```powershell
Install-Module Microsoft.Graph
Connect-MgGraph -Scopes "User.Read.All"
```
.\Get-GuestInviteStatus.ps1

## Use Cases
-   External user access cleanup
-   Identity governance reporting
-   Security and compliance audits
-   Microsoft 365 tenant hygiene checks

## Notes
-   Designed for read-only audit operations
-   Does not modify or delete any users
-   Safe for production environments
