# Detection Rules

## Rule 1: Brute Force Detection

A brute-force attack is suspected when one IP address generates many failed login attempts against the same account within a short period.

### Detection Logic

- Same source IP
- Same user account
- 5 or more failed login attempts
- Within 10 minutes

### Alert

Generate a high-priority alert and temporarily block or rate-limit the IP address.

---

## Rule 2: Password Spraying Detection

Password spraying is suspected when one IP address attempts to log in to many different accounts and most attempts fail.

### Detection Logic

- Same source IP
- Multiple different user accounts
- Failed login attempts
- Activity occurs within a short period

### Alert

Generate a medium or high-priority alert and investigate the source IP.

---

## Rule 3: Unusual Access Detection

Unusual access is suspected when a successful login occurs after suspicious failed attempts or from an unusual IP address.

### Detection Logic

- Successful login after repeated failures
- New or unusual source IP
- Unexpected account access pattern

### Alert

Generate an alert for manual investigation.

---

## Rule 4: Account Lock Detection

Repeated failures followed by an account lock event may indicate an attack or repeated incorrect password attempts.

### Detection Logic

- Multiple failed login attempts
- Followed by an account_lock event

### Response

Review the affected account and source IP.
