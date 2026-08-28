# Security Log Investigation

## 1. Investigation Objective

The objective of this investigation is to analyze a synthetic authentication log and identify suspicious authentication behavior.

The investigation focuses on:

- Brute-force attempts
- Password spraying
- Unusual access patterns
- Incident timeline reconstruction

## 2. Dataset

The supplied authentication log contains the following fields:

| Field | Description |
|---|---|
| timestamp | Time of the authentication event |
| user_id | Account involved in the event |
| source_ip | IP address that generated the event |
| event | Authentication-related action |
| result | Success, failure, or blocked result |
| device | Device associated with the event |

## 3. Normalization

The following fields were normalized for analysis:

### Timestamp

All timestamps are recorded in UTC using ISO 8601 format.

Example:

`2026-08-01T09:00:12Z`

### IP Address

Source IP addresses were treated as consistent text values for grouping and comparison.

### Account

User IDs were used as account identifiers.

Examples:

- stu-104
- stu-117
- stu-209

### Actions

Events include:

- password_login
- account_lock
- rate_limit
- refresh_token

### Results

Results were classified as:

- success
- failure
- blocked
