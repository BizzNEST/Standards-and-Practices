# Secrets Management

## The Golden Rule

**Never commit secrets to version control. Period.**

If a secret ends up in a Git commit — even if you delete it afterward — it lives in the Git history forever. Assume it has been compromised.

---

## What Counts as a Secret

- API keys and tokens (Stripe, Firebase, AWS, etc.)
- Database connection strings and passwords
- OAuth client secrets
- Private keys and certificates
- Internal URLs and IP addresses
- `.env` file contents

---

## Using .env Files

`.env` files are how we manage secrets locally. Follow these rules:

> **DO**: Add `.env` and `.env.*` to your `.gitignore` file.
>
> **DON'T**: Ever commit a `.env` file, even "temporarily."

> **DO**: Create a `.env.example` file with placeholder values that shows what variables are needed.
>
> **DON'T**: Put real values in `.env.example`.

### Example .env.example

```
# Database
DB_HOST=localhost
DB_USER=your_username_here
DB_PASS=your_password_here

# API Keys
STRIPE_SECRET_KEY=sk_test_xxxxxxxxxxxx
FIREBASE_API_KEY=your_key_here
```

---

## Key Rotation

Secrets should not live forever. Rotate them regularly and immediately if compromised.

> **DO**: Use different keys for development, staging, and production.
>
> **DON'T**: Use the same API key across all environments.

> **DO**: Rotate keys on a regular schedule (quarterly at minimum).
>
> **DON'T**: Keep using the same key for years because "it still works."

> **DO**: Revoke old keys immediately after rotation.
>
> **DON'T**: Leave old keys active "just in case."

---

## Secret Scanning

BizzNEST repos scan for secrets with [Betterleaks](https://github.com/betterleaks/betterleaks) in two places:

1. **On your machine, before each commit** (a pre-commit hook installed by Lefthook).
2. **On GitHub, for every Pull Request** (the `scan / betterleaks` check). On project repos a PR can't merge until it passes.

### Set Up (once per machine)

```bash
# Windows
winget install Betterleaks.Betterleaks

# macOS
brew install betterleaks
```

Restart your terminal, then run `npm install` in each repo you work in (Python repos: `lefthook install`). That installs the pre-commit hook.

### If the Scan Flags Something

- **Real secret:** don't push. Follow [What To Do If You Commit a Secret](#what-to-do-if-you-commit-a-secret).
- **False positive (test data, example values):** add a `betterleaks:allow` comment on that line, or open a PR to the allowlist in [security-config](https://github.com/BizzNEST/security-config).
- Use `git commit --no-verify` **only** for confirmed false positives. The GitHub check still runs, so a skipped secret is caught there.

Setup details, the shared config and how to add a repo live in [security-config](https://github.com/BizzNEST/security-config).

---

## What To Do If You Commit a Secret

This is critical — **deleting the commit is NOT enough.** The secret is in your Git history and may have already been pushed.

### Immediate Steps

1. **Tell Eli Manzo or Alex Rodriguez right away.** Name the repo, file and service. **Never paste the secret itself.** No blame: reporting fast matters more than anything else.
2. **Rotate the secret immediately.** Generate a new key/password and update it wherever it's used.
3. **Revoke the old secret.** Deactivate it in the provider's dashboard (AWS, Stripe, Firebase, etc.).
4. **Do NOT force-push to "hide" it.** Others may have already pulled the commit.

A secret that reached GitHub counts as leaked, even in a private repo and even on a feature branch.

### After Containment

5. Remove the secret from the code and commit the fix.
6. If the repo is public, assume the secret was scraped by bots within seconds.
7. Follow the [Incident Response](incident-response.md) process if the leaked secret had access to production data.

---

## Quick Reference

| Situation | Action |
|---|---|
| Need to use a secret in code | Put it in `.env`, access via `process.env.SECRET_NAME` |
| Setting up a new project | Create `.gitignore` with `.env*` BEFORE your first commit |
| Reviewing a PR | Check that no secrets are hardcoded or visible in diffs |
| Deploying to production | Use the hosting platform's environment variable settings |
| Scan flagged test data | Add a `betterleaks:allow` comment on that line |
| Accidentally committed a secret | Tell Eli or Alex immediately, then rotate |
