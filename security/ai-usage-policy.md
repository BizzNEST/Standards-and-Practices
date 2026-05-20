# AI Usage Policy at BizzNEST

AI tools can help you write code faster, debug problems, and learn new concepts. But they also come with real risks — especially around data privacy and security. Follow these rules to use AI responsibly.

---

## Approved Tools

Refer to the [Digital NEST AI Policy](TODO) for the current list of approved and prohibited AI tools. If a tool is not on the approved list, **do not use it** for work-related tasks.

---

## What You CAN Share with AI

These are safe to include in prompts and conversations with approved AI tools:

- Public documentation and open-source code
- Generic code patterns and syntax questions
- Error messages **with secrets redacted**
- Questions about programming concepts, frameworks, or best practices
- Code snippets that contain no secrets, PII, or proprietary business logic

---

## What You MUST NOT Share with AI

Never paste, type, or upload any of the following into an AI tool:

- **API keys, tokens, or passwords** — not even "just to debug"
- **Database credentials or connection strings**
- **Customer PII** (names, emails, phone numbers, addresses)
- **Proprietary business logic** (pricing algorithms, internal workflows, trade secrets)
- **Contents of `.env` files**
- **Internal URLs, IP addresses, or infrastructure details**
- **Full configuration files** — they often contain secrets you might miss

> **DO**: Strip all secrets and PII from code before pasting it into an AI tool.
>
> **DON'T**: Paste entire files without reviewing them first — you might miss a hardcoded key.

> **DO**: Ask AI generic questions like "How do I connect to PostgreSQL with Node.js?"
>
> **DON'T**: Ask "Why can't I connect to postgres://admin:p4ssw0rd@prod.internal:5432/customers?"

---

## NO Database Access for AI

This is a hard rule with no exceptions:

**AI tools must never be given direct access to any database — development, staging, or production.**

This means:

- Do NOT paste database connection strings into AI prompts.
- Do NOT use AI tools that request database credentials to "help you query."
- Do NOT give AI plugins or extensions access to your database.
- Do NOT share database schemas that contain real table/column names tied to customer data.

If you need help writing a query, describe the schema in generic terms or use fake table names.

---

## Prompt Hygiene

Before you send a prompt to any AI tool, review it:

1. **Read through your code snippet.** Does it contain any hardcoded values, secrets, or PII?
2. **Replace real values with placeholders.** Use `YOUR_API_KEY`, `user@example.com`, `localhost` instead of real values.
3. **Don't paste entire config files.** Extract only the relevant section.
4. **Don't paste entire codebases.** Share only the specific function or file you need help with.

---

## Code Review of AI-Generated Output

AI-generated code is not automatically correct or safe. Treat it the same way you'd treat code from an untrusted source.

> **DO**: Review every line of AI-generated code before committing it.
>
> **DON'T**: Copy-paste AI output directly into your project without reading it.

> **DO**: Run and test AI-generated code — make sure it actually works.
>
> **DON'T**: Assume AI output is bug-free or follows our project's conventions.

> **DO**: Put AI-generated code through the normal [Code Review process](/standards/code-reviews.md).
>
> **DON'T**: Merge AI-generated code without peer review because "the AI wrote it correctly."

> **DO**: Understand what the code does before using it.
>
> **DON'T**: Use code you can't explain — if you can't explain it, you can't debug it.

---

## Quick Reference

| Question | Answer |
|---|---|
| Can I ask AI how to use a framework? | **Yes** |
| Can I paste my `.env` file to debug an issue? | **No** — redact secrets first |
| Can I give an AI plugin my DB connection string? | **Never** |
| Can I paste a code snippet that has no secrets? | **Yes** |
| Can I paste customer data to help format it? | **No** |
| Can I merge AI code without review? | **No** — normal review process applies |
| Can I use an AI tool not on the approved list? | **No** — check the Digital NEST AI Policy |
