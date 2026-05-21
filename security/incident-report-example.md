# Incident Report: Data Leak — Example

> **Note**: This is a fictional example to show BizzNEST interns what a completed incident report looks like. The names, dates, and details are all made up. Use the [Incident Report Template](incident-report-template.md) for real incidents.

---

## Report Details

| Field | Value |
|---|---|
| **Report Date** | 2026-03-15 |
| **Reported By** | Jamie Santos |
| **Incident Date** | 2026-03-14 (when the commit was pushed) |
| **Discovery Date** | 2026-03-15 (next morning during code review) |
| **Severity** | High |
| **Status** | Resolved |

---

## Summary

A Firebase API key and database URL were accidentally committed to the `main` branch of the client portal repository. The commit was pushed to the public-facing GitHub repo and was visible for approximately 14 hours before being discovered during a code review the next morning.

---

## Timeline

| Time | Event |
|---|---|
| 2026-03-14 5:45 PM | Jamie pushed a commit that included a hardcoded Firebase config object with the API key and database URL in `src/config.js` |
| 2026-03-14 5:46 PM | Commit was merged to `main` via auto-merge (PR had prior approval) |
| 2026-03-15 8:10 AM | Alex noticed the exposed key during a routine code review |
| 2026-03-15 8:15 AM | Alex notified Jamie and the team lead via Slack DM |
| 2026-03-15 8:22 AM | Jamie revoked the old Firebase API key in the Firebase console |
| 2026-03-15 8:30 AM | Jamie generated a new API key and updated the environment variables on the hosting platform |
| 2026-03-15 8:35 AM | Jamie pushed a new commit removing the hardcoded config and replacing it with `process.env` references |
| 2026-03-15 9:00 AM | Team lead confirmed containment and notified BizzNEST leadership |
| 2026-03-15 3:00 PM | Post-mortem meeting held with the team |

---

## What Was Leaked

- [x] API keys or tokens
- [ ] Database credentials
- [ ] Customer PII (names, emails, phone numbers, etc.)
- [x] Internal URLs or IP addresses
- [ ] Source code or proprietary business logic
- [ ] .env file contents
- [ ] Other

Specifically: Firebase API key (`AIzaSy...`) and Firebase Realtime Database URL (`https://project-name.firebaseio.com`).

---

## How It Happened

Jamie was debugging a connection issue with Firebase and temporarily hardcoded the config values directly in `src/config.js` to isolate the problem. After fixing the bug, Jamie forgot to move the values back to the `.env` file before committing. The PR had already been approved earlier in the day for a different change, so the auto-merge went through without a second review of the new commit.

---

## Who / What Was Affected

- **Systems affected**: Client portal Firebase project (database, authentication, storage)
- **Data scope**: The API key could have been used to read/write to the Firebase Realtime Database. No evidence of unauthorized access was found in Firebase audit logs.
- **External exposure**: The key was visible on the public GitHub repo for approximately 14 hours. GitHub secret scanning did not flag it because it was a Firebase key (not in their default patterns at the time).

---

## Containment Actions Taken

1. Revoked the exposed Firebase API key in the Firebase console
2. Generated a new API key with the same restrictions
3. Updated the environment variables on the hosting platform (Vercel) with the new key
4. Pushed a commit removing the hardcoded values from `src/config.js`
5. Checked Firebase audit logs for any unauthorized reads or writes during the exposure window — none found
6. Verified the application was working correctly with the new key

---

## Notification Chain

| Who | When Notified | How |
|---|---|---|
| Team Lead (Maria) | 2026-03-15 8:15 AM | Slack DM |
| BizzNEST Leadership | 2026-03-15 9:00 AM | Email from Maria |
| Digital NEST IT | Not notified | No customer data was exposed; leadership determined IT notification was not required |
| Affected Users | Not notified | No evidence of unauthorized access; no user data was compromised |

---

## Post-Mortem

### Root Cause

Two process gaps combined to cause this incident:

1. **No pre-commit hook** was installed to scan for secrets before commits. If `git-secrets` had been set up, the commit would have been blocked.
2. **Auto-merge after prior approval** meant a new commit bypassed review. The PR was approved for an earlier change, and the new commit with the hardcoded key went through without fresh eyes.

### What Went Well

- The leak was discovered within 14 hours during a routine code review
- The API key was revoked within 7 minutes of discovery
- Firebase audit logs confirmed no unauthorized access occurred
- The team responded calmly and followed the incident response process

### What Went Wrong

- No pre-commit secrets scanning was in place
- Hardcoding secrets "temporarily" for debugging — there's no such thing as temporary in Git
- Auto-merge allowed a new commit through without re-review
- The `.env.example` file didn't clearly list the Firebase config variables, making it less obvious they should come from environment variables

### Action Items

| Action | Owner | Due Date | Status |
|---|---|---|---|
| Install `git-secrets` on all active BizzNEST repos | Alex | 2026-03-22 | Complete |
| Add Firebase key patterns to `git-secrets` config | Alex | 2026-03-22 | Complete |
| Disable auto-merge on all repos — require re-approval after new commits | Maria | 2026-03-19 | Complete |
| Update `.env.example` in client portal to include all Firebase variables | Jamie | 2026-03-17 | Complete |
| Add "never hardcode secrets for debugging" to security onboarding docs | Maria | 2026-03-29 | Pending |

---

## Lessons Learned

1. **There's no such thing as "temporary" in Git.** If you hardcode a secret, even for 5 minutes, assume it will end up in a commit. Use environment variables from the start — even when debugging.
2. **Pre-commit hooks are a safety net, not a luxury.** `git-secrets` would have caught this before it ever left the developer's machine. Install it on every repo.
3. **Auto-merge is risky.** A PR approved for one change shouldn't automatically merge future commits. Require fresh approval after every new push.
