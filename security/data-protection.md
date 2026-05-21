# Data Protection Standards

Protecting data is everyone's responsibility. Whether it's a customer's email address, an API key, or our proprietary code — if it's not public, it must be treated with care.

---

## Secrets and Credentials

Credentials are the keys to our systems. Treat them like your house keys — you wouldn't leave them on a park bench.

> **DO**: Store all secrets in environment variables (see [Secrets Management](secrets-management.md)).
>
> **DON'T**: Hardcode passwords, API keys, or tokens anywhere in your code.

> **DO**: Use a password manager for shared team credentials.
>
> **DON'T**: Share secrets over Slack, email, or text messages.

> **DO**: Use different credentials for development, staging, and production.
>
> **DON'T**: Use production credentials in your local development environment.

---

## Personally Identifiable Information (PII)

PII is any data that can identify a real person: names, emails, phone numbers, addresses, IP addresses, etc.

> **DO**: Minimize PII collection — only collect what you actually need.
>
> **DON'T**: Add extra form fields "just in case" we might need the data later.

> **DO**: Keep PII out of logs and error messages.
>
> **DON'T**: Log full user objects or request bodies that contain personal data.

> **DO**: Anonymize or redact PII in development and staging environments.
>
> **DON'T**: Copy production databases to local machines for testing.

### Example — Logging

```javascript
// BAD — logs PII
console.log('User login:', { email: user.email, password: user.password, ip: req.ip });

// GOOD — logs only what's needed for debugging
console.log('User login:', { userId: user.id, success: true });
```

---

## Customer Data

Production data belongs in production. Full stop.

> **DO**: Use seed data or mock data for local development.
>
> **DON'T**: Download production database exports to your laptop.

> **DO**: Use tools that generate realistic fake data (e.g., Faker.js).
>
> **DON'T**: "Borrow" real customer records for testing.

> **DO**: Ensure test/staging environments use anonymized data if they need real-ish data.
>
> **DON'T**: Share customer data with anyone outside the team, including in screenshots or demos.

---

## Proprietary Code and Intellectual Property

Our code and business logic are company assets. Protecting them is part of your job.

> **DO**: Keep all project repositories private within the BizzNEST organization.
>
> **DON'T**: Make repositories public without explicit approval from leadership.

> **DO**: Ask permission before using code from a project in a personal portfolio.
>
> **DON'T**: Post proprietary code snippets on Stack Overflow, public Gists, or forums.

> **DO**: Be careful what you share on screen during screen recordings or streams.
>
> **DON'T**: Include internal URLs, dashboards, or credentials in screenshots shared externally.

> **DO**: Remember that NDA agreements cover code, architecture, and business logic.
>
> **DON'T**: Discuss project internals in public Discord servers, forums, or social media.
