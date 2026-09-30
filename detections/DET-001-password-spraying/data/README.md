# DET-001 Data

This directory contains information related to datasets used during development and validation of DET-001.

Raw production or tenant authentication logs are not committed to this repository.

Any sample data included in this project must be sanitized or synthetically generated to prevent exposure of:

- User principal names
- Email addresses
- Public IP addresses
- Tenant identifiers
- Subscription identifiers
- Request identifiers
- Device identifiers
- Other sensitive environmental information

The primary telemetry source for DET-001 is the Microsoft Entra ID `SigninLogs` table in the project's Log Analytics workspace.