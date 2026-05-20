# Incident Response

Security incidents happen — what matters is how quickly and effectively you respond. If you think something might be an incident, treat it as one. It's always better to over-report than to stay quiet and let things get worse.

---

## What Counts as an Incident

Report immediately if you observe any of the following:

- **Leaked credentials** — a secret was committed to Git, shared publicly, or sent to an unauthorized person
- **Unauthorized access** — someone accessed a system, repo, or account they shouldn't have
- **Data breach** — customer data was exposed, downloaded, or shared outside the organization
- **Exposed PII** — personal information appeared in logs, error messages, public pages, or screenshots
- **Compromised account** — your GitHub, email, or any work account was accessed by someone else
- **Suspicious activity** — unexpected changes to code, infrastructure, or permissions that nobody on the team made

---

## Immediate Steps (Containment)

When you discover an incident, act fast. Do these in order:

### 1. Contain the Damage

- **Leaked credential?** Rotate/revoke it immediately. Don't wait for approval — revoke first, ask questions later.
- **Compromised account?** Change the password and enable 2FA right now.
- **Exposed data?** Take the affected service offline if you can, or remove the exposure.

### 2. Do NOT Destroy Evidence

> **DO**: Leave logs, commits, and messages intact for investigation.
>
> **DON'T**: Delete commits, clear logs, or edit chat messages to "hide" the incident.

> **DO**: Take screenshots of what you see.
>
> **DON'T**: Force-push to remove evidence from Git history.

### 3. Notify Your Team Lead

Tell your team lead immediately — in person, over a call, or via direct message. Do not wait until standup or your next meeting.

Include:
- What happened (brief description)
- When you discovered it
- What you've already done to contain it
- What systems or data are affected

---

## Notification Chain

1. **You** → Tell your **Team Lead** immediately
2. **Team Lead** → Escalates to **BizzNEST Leadership / Digital NEST IT**
3. **Leadership** → Determines if external notification is needed (users, partners, legal)

You are responsible for step 1. Do not skip it. Do not decide on your own that "it's not a big deal."

---

## Documentation

As soon as the immediate crisis is handled, write down what you know:

- **What happened?** (Describe the incident in plain language)
- **When did it happen?** (When was it introduced? When was it discovered?)
- **What was the impact?** (What data/systems were affected? How many users?)
- **What did you do?** (Steps you took to contain it)
- **What's still at risk?** (Anything that hasn't been resolved yet)

Write this in a private document or issue — not in a public channel.

---

## Post-Mortem Process

Within 48 hours of containment, the team conducts a blameless post-mortem:

### Rules

- **Blameless** — we focus on systems and processes, not individuals. Nobody gets punished for reporting an incident.
- **Honest** — we document exactly what happened, even if it's embarrassing.
- **Actionable** — every post-mortem must produce at least one concrete preventive measure.

### Post-Mortem Template

1. **Summary** — One paragraph describing the incident.
2. **Timeline** — Chronological list of events (when introduced, when discovered, when contained, when resolved).
3. **Root Cause** — What systemic issue allowed this to happen?
4. **Impact** — What was the blast radius? Users affected? Data exposed?
5. **What Went Well** — What helped us catch and contain this?
6. **What Went Wrong** — What made this possible or delayed our response?
7. **Action Items** — Specific, assigned tasks to prevent recurrence.

---

## DOs and DON'Ts

> **DO**: Report incidents immediately, even if you caused them.
>
> **DON'T**: Try to fix it quietly by yourself and hope nobody notices.

> **DO**: Revoke compromised credentials first, then investigate.
>
> **DON'T**: Spend time investigating while the credential is still active.

> **DO**: Preserve all evidence (logs, screenshots, commits).
>
> **DON'T**: Delete or modify evidence to cover tracks.

> **DO**: Treat post-mortems as learning opportunities.
>
> **DON'T**: Blame individuals — blame the process that allowed the mistake.

> **DO**: Follow up on action items from post-mortems.
>
> **DON'T**: Write action items and then forget about them.
