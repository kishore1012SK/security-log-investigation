# Incident Timeline and Findings

## Timeline

| Time (UTC) | Evidence | Interpretation |
|---|---|---|
| 09:00:12 | Successful password login for stu-104 from 192.0.2.18 | Normal successful login |
| 09:03:44 | Failed password login for stu-117 from 198.51.100.27 | Beginning of suspicious activity |
| 09:04:01 | Another failed login for stu-117 from 198.51.100.27 | Repeated failures against one account |
| 09:04:18 | Third failed login for stu-117 from 198.51.100.27 | Likely brute-force pattern |
| 09:05:03 | Account lock event for stu-117 | Defensive control responded to repeated failures |
| 09:21:10–09:21:22 | Failed logins from 203.0.113.42 against stu-209, stu-311, stu-415, and stu-502 | Likely password spraying pattern |
| 09:22:01 | Rate-limit event blocked activity from 203.0.113.42 | Defensive control responded to suspicious activity |
| 10:15:32 | Successful refresh token for stu-104 from 192.0.2.18 | Continued authenticated session activity |
| 11:47:09 | Successful login for stu-311 from 192.0.2.99 | Unusual access that should be investigated |

## Confirmed Evidence

The following facts are directly supported by the log:

- Multiple failed login attempts occurred against stu-117 from IP 198.51.100.27.
- An account_lock event followed the repeated failures.
- IP 203.0.113.42 attempted failed logins against four different accounts.
- A rate-limit control later blocked activity.
- A successful login for stu-311 later occurred from IP 192.0.2.99.

## Assumptions

The following conclusions are interpretations, not proven facts:

- The repeated failures against stu-117 are likely a brute-force attempt.
- The failures against multiple accounts from 203.0.113.42 are likely password spraying.
- The successful login for stu-311 may be unusual and requires further investigation.
- The log alone does not prove that any account was compromised.

## Recommended Response

1. Investigate the source IPs involved in suspicious activity.
2. Review the account stu-117 for additional authentication attempts.
3. Review the successful login for stu-311.
4. Maintain rate limiting and account lock controls.
5. Monitor for repeated attacks from the same IP ranges.
6. Improve logging by recording additional context such as location and user-agent history.
