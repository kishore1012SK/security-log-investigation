# Incident Report

## Security Log Investigation

### 1. Executive Summary

A synthetic authentication log was investigated to identify suspicious login activity.

Two main suspicious patterns were identified:

- Likely brute-force activity against account stu-117.
- Likely password-spraying activity against multiple accounts.

The available log does not prove that an account was compromised.

---

## 2. Scope

The investigation analyzed authentication events from the supplied synthetic CSV log.

The following fields were reviewed:

- Timestamp
- User ID
- Source IP
- Event
- Result
- Device

---

## 3. Key Findings

### Finding 1: Likely Brute-Force Activity

Multiple failed password login attempts targeted the same account, stu-117, from IP address 198.51.100.27.

The repeated failures were followed by an account lock event.

**Assessment:** Likely brute-force attempt.

**Risk:** High

---

### Finding 2: Likely Password Spraying

IP address 203.0.113.42 generated failed password login attempts against multiple accounts:

- stu-209
- stu-311
- stu-415
- stu-502

The activity was followed by a rate-limit event.

**Assessment:** Likely password-spraying activity.

**Risk:** High

---

### Finding 3: Unusual Access Requiring Review

A later successful login occurred for stu-311 from IP address 192.0.2.99.

The log alone does not prove malicious activity.

**Assessment:** Requires investigation.

**Risk:** Medium

---

## 4. Evidence

The log directly shows:

- Repeated failed logins against stu-117.
- An account lock event.
- Failed login attempts against multiple accounts from one IP address.
- A rate-limit control blocking suspicious activity.
- A later successful login for stu-311.

---

## 5. Assumptions

The following are interpretations:

- The repeated failures against stu-117 are likely a brute-force attempt.
- The multi-account failures are likely password spraying.
- The successful login for stu-311 may be unusual.

These interpretations require additional evidence for confirmation.

---

## 6. Recommended Containment Actions

1. Continue blocking or rate-limiting suspicious source IPs.
2. Review affected accounts for additional suspicious activity.
3. Require password reset if compromise is suspected.
4. Review the successful login for stu-311.
5. Monitor for repeated authentication attacks.

---

## 7. Improved Logging Recommendations

The authentication system should record:

- User-agent information
- Geographic location where appropriate
- Session identifiers
- MFA events
- Detailed reason for authentication failure
- Alert severity and response actions

---

## 8. Conclusion

The investigation identified suspicious authentication patterns and confirmed that existing controls responded through account locking and rate limiting.

The evidence supports further investigation, but the available log does not prove account compromise.
