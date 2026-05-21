# Secure Development Practices

Writing secure code is not just for security experts — it's part of every developer's job. These rules help you avoid introducing vulnerabilities into our projects.

---

## Input Validation

Never trust data that comes from outside your application. This includes form inputs, URL parameters, API request bodies, and anything a user can control.

> **DO**: Use parameterized queries for all database calls.
>
> **DON'T**: Concatenate user input directly into SQL strings.

> **DO**: Validate input on the server side, even if you also validate on the client.
>
> **DON'T**: Rely only on front-end validation — it can be bypassed.

> **DO**: Sanitize and escape output to prevent XSS (cross-site scripting).
>
> **DON'T**: Render raw user input directly into HTML.

### Example — SQL Injection

```javascript
// BAD — vulnerable to SQL injection
const query = `SELECT * FROM users WHERE email = '${userInput}'`;

// GOOD — parameterized query
const query = `SELECT * FROM users WHERE email = $1`;
const result = await db.query(query, [userInput]);
```

---

## Dependency Management

Every package you install is code you didn't write and didn't review. Treat dependencies as a potential risk.

> **DO**: Run `npm audit` before every pull request and fix critical/high vulnerabilities.
>
> **DON'T**: Ignore audit warnings or use `--force` to skip them without understanding why.

> **DO**: Remove packages you're no longer using.
>
> **DON'T**: Leave unused dependencies in `package.json` — they increase your attack surface.

> **DO**: Pin dependency versions or use lock files (`package-lock.json`).
>
> **DON'T**: Use `*` or overly broad version ranges in production.

---

## HTTPS Everywhere

All communication between clients and servers must be encrypted.

> **DO**: Use HTTPS for every endpoint, API call, and external resource.
>
> **DON'T**: Load scripts, images, or APIs over plain HTTP (mixed content).

> **DO**: Redirect HTTP requests to HTTPS.
>
> **DON'T**: Disable SSL certificate verification in your code, even in development.

---

## Least Privilege

Only request the minimum permissions your code needs to function. This limits the damage if something goes wrong.

> **DO**: Create database users with only the permissions they need (e.g., read-only for reporting).
>
> **DON'T**: Use a root or admin database account in your application code.

> **DO**: Request only the OAuth scopes your app actually uses.
>
> **DON'T**: Request broad permissions "just in case" you might need them later.

> **DO**: Run services with the minimum system permissions required.
>
> **DON'T**: Run application processes as root.

---

## Error Handling

Errors can leak sensitive information if you're not careful.

> **DO**: Return generic error messages to users (e.g., "Something went wrong").
>
> **DON'T**: Expose stack traces, file paths, database names, or internal IPs in error responses.

> **DO**: Log detailed errors server-side for debugging.
>
> **DON'T**: Include sensitive data (passwords, tokens, PII) in log messages.
