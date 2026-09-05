# Security Policy

## Reporting security issues

Do **not** report security vulnerabilities through public GitHub issues.

Microsoft takes the security of our software and services seriously. If you believe you have found a security vulnerability, please report it to the Microsoft Security Response Center (MSRC) at [https://msrc.microsoft.com/create-report](https://msrc.microsoft.com/create-report), or by email to [secure@microsoft.com](mailto:secure@microsoft.com). See [https://www.microsoft.com/msrc](https://www.microsoft.com/msrc) for more information.

## Scope note for this project

This repository contains **documentation and prompt templates** for an email‑triage workflow. It does not ship executable services or store data. Two practical security considerations for anyone adopting the pattern:

- **Stay in‑tenant.** The design deliberately runs under the user's own Microsoft 365 permissions and never routes mailbox content to third‑party services. Do not adapt it in a way that exports mail outside the tenant.
- **No secrets or personal data in the repo.** Prompts and docs here must remain generic — no real names, customer domains, distribution lists, or tenant‑specific identifiers. Use `[bracketed]` placeholders.
