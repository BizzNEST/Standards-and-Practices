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

## Pre-Commit Protection

Set up tools that prevent you from accidentally committing secrets.

### Recommended: git-secrets

```bash
# Install
brew install git-secrets

# Set up in your repo
git secrets --install
git secrets --register-aws  # blocks AWS keys automatically
```

You can also add custom patterns for your project's secrets (e.g., internal API key prefixes).

---

## What To Do If You Commit a Secret

This is critical — **deleting the commit is NOT enough.** The secret is in your Git history and may have already been pushed.

### Immediate Steps

1. **Rotate the secret immediately.** Generate a new key/password and update it wherever it's used.
2. **Revoke the old secret.** Deactivate it in the provider's dashboard (AWS, Stripe, Firebase, etc.).
3. **Tell your team lead.** They need to know so they can assess impact.
4. **Do NOT force-push to "hide" it.** Others may have already pulled the commit.

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
| Accidentally committed a secret | Rotate immediately, then notify your lead |
