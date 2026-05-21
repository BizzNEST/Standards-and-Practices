# Incident Report: Data Leak

> **Instructions**: Copy this template when a data leak occurs. Fill in every section honestly and completely. This report is internal and confidential — do not share outside of BizzNEST leadership without approval. Refer to the [Incident Response guide](incident-response.md) for the full response process.

---

## Report Details

| Field | Value |
|---|---|
| **Report Date** | YYYY-MM-DD |
| **Reported By** | Your name |
| **Incident Date** | When the leak was introduced (if known) |
| **Discovery Date** | When the leak was discovered |
| **Severity** | Critical / High / Medium / Low |
| **Status** | Open / Contained / Resolved |

---

## Summary

_Write 2–3 sentences describing what happened in plain language. What data was leaked, how, and where._

---

## Timeline

| Time | Event |
|---|---|
| YYYY-MM-DD HH:MM | _What happened_ |
| YYYY-MM-DD HH:MM | _What happened next_ |
| YYYY-MM-DD HH:MM | _When it was discovered_ |
| YYYY-MM-DD HH:MM | _Containment actions taken_ |
| YYYY-MM-DD HH:MM | _Resolution confirmed_ |

---

## What Was Leaked

_Be specific. List the exact data that was exposed._

- [ ] API keys or tokens
- [ ] Database credentials
- [ ] Customer PII (names, emails, phone numbers, etc.)
- [ ] Internal URLs or IP addresses
- [ ] Source code or proprietary business logic
- [ ] .env file contents
- [ ] Other: _______________

---

## How It Happened

_Describe the root cause. How did the data end up where it shouldn't be? Be honest — this is blameless._

---

## Who / What Was Affected

- **Systems affected**: _List services, repos, databases, or environments impacted_
- **Data scope**: _How many records, users, or keys were exposed?_
- **External exposure**: _Was the data visible to the public internet? For how long?_

---

## Containment Actions Taken

_List every action taken to stop the leak, in the order they were performed._

1. _e.g., Revoked the leaked API key in the provider dashboard_
2. _e.g., Rotated the credential and updated environment variables_
3. _e.g., Notified team lead_
4. ...

---

## Notification Chain

| Who | When Notified | How |
|---|---|---|
| Team Lead | YYYY-MM-DD HH:MM | _Slack DM / Call / In person_ |
| BizzNEST Leadership | YYYY-MM-DD HH:MM | _How_ |
| Digital NEST IT | YYYY-MM-DD HH:MM | _How_ |
| Affected Users (if applicable) | YYYY-MM-DD HH:MM | _How_ |

---

## Post-Mortem

### Root Cause

_What systemic issue allowed this to happen? Go deeper than "someone made a mistake." Was there a missing safeguard, unclear process, or tooling gap?_

### What Went Well

- _e.g., Leak was discovered within 30 minutes_
- _e.g., Key was revoked immediately_

### What Went Wrong

- _e.g., No pre-commit hook to catch secrets_
- _e.g., Production credentials were stored in a shared document_

### Action Items

| Action | Owner | Due Date | Status |
|---|---|---|---|
| _e.g., Install git-secrets on all team repos_ | _Name_ | _YYYY-MM-DD_ | Pending |
| _e.g., Move shared credentials to password manager_ | _Name_ | _YYYY-MM-DD_ | Pending |
| _e.g., Add .env to .gitignore in project template_ | _Name_ | _YYYY-MM-DD_ | Pending |

---

## Lessons Learned

_Write 1–3 key takeaways that the team should remember. These may be added to our security documentation._

1. _..._
2. _..._
3. _..._
