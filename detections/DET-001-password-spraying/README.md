# DET-001: Password Spraying

## Detection Metadata

| Field | Value |
|---|---|
| Detection ID | DET-001 |
| Detection Name | Password Spraying |
| Status | Development |
| Data Source | Microsoft Entra ID Sign-in Logs |
| Log Analytics Table | SigninLogs |
| Detection Language | Kusto Query Language (KQL) |
| MITRE ATT&CK Tactic | Credential Access |
| MITRE ATT&CK Technique | T1110 - Brute Force |
| MITRE ATT&CK Sub-technique | T1110.003 - Password Spraying |
| Severity | TBD |
| Detection Decision | TBD |

## Detection Objective

Detect authentication behavior consistent with password spraying against Microsoft Entra ID accounts.

Password spraying differs from traditional brute-force activity because an attacker may attempt the same password, or a small number of passwords, against multiple accounts rather than repeatedly targeting a single account.

The detection will therefore focus on identifying failed authentication activity originating from a common source and targeting an abnormal number of distinct user accounts within a defined period.

## Detection Hypothesis

If a source generates failed authentication attempts against multiple distinct user accounts within a relatively short period, the activity may represent password spraying.

The initial hypothesis can be represented as:

Source IP
→ Failed authentication
→ Multiple distinct user accounts
→ Defined time window
→ Potential password spraying activity

## Required Telemetry

Primary telemetry:

- Microsoft Entra ID interactive sign-in logs
- Log Analytics `SigninLogs` table

Fields expected to be useful include:

- `TimeGenerated`
- `UserPrincipalName`
- `IPAddress`
- `AppDisplayName`
- `ResultType`
- `ResultDescription`
- `ConditionalAccessStatus`
- `LocationDetails`
- `UserAgent`

The final field selection will be validated against telemetry available in the lab environment.

## Detection Development Process

### Phase 1: Telemetry Validation

Confirm that Microsoft Entra ID authentication events are successfully ingested into the Log Analytics workspace.

### Phase 2: Baseline Analysis

Analyze normal authentication behavior before establishing detection thresholds.

Baseline analysis will include:

- Total authentication volume
- Successful versus failed authentication attempts
- Failed authentications by source IP
- Number of distinct accounts targeted by source IP
- Authentication activity over time
- Common applications and authentication patterns

### Phase 3: Initial Detection

Develop initial KQL logic that identifies source IP addresses producing failed authentication attempts against multiple distinct accounts.

No production-style threshold will be selected until sufficient baseline and test telemetry is available.

### Phase 4: Validation

Validate the detection using controlled activity within the lab environment.

Testing will evaluate whether the query identifies the intended behavior and whether normal authentication activity produces false positives.

### Phase 5: Tuning

Tune the detection using observed telemetry.

Potential tuning considerations include:

- Time window
- Failed authentication count
- Distinct account count
- Known or trusted source IP addresses
- Expected administrative activity
- Service or automation accounts
- Authentication result codes
- Application context

### Phase 6: Detection Decision

The detection will receive one of the following lifecycle decisions:

- Keep
- Tune
- Deprecate

The final decision and rationale will be documented after validation.

## False Positive Considerations

Potential benign scenarios may include:

- Shared egress IP addresses
- VPN infrastructure
- Misconfigured applications
- Expired or stale credentials
- Administrative testing
- Authentication proxies
- Large organizations using centralized network infrastructure

These scenarios will be evaluated during tuning rather than automatically excluded.

## Detection Limitations

This detection depends on authentication telemetry available to Microsoft Entra ID and the Log Analytics workspace.

A source-IP-based approach may have reduced effectiveness when:

- Attackers distribute authentication attempts across multiple IP addresses
- Large numbers of legitimate users share a single egress IP
- Authentication attempts are intentionally throttled
- Relevant authentication telemetry is unavailable

Additional identity, device, risk, network, and threat intelligence context may improve confidence.

## Current Status

The detection is currently under development.

Microsoft Entra ID diagnostic settings have been configured to forward `SignInLogs` and `AuditLogs` to the detection engineering Log Analytics workspace.

Source authentication events have been validated in Microsoft Entra ID. Log Analytics ingestion is pending before baseline analysis begins.