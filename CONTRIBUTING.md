# Contributing

Thanks for your interest in improving **AI‑Email‑Triage**. This project is a lightweight, prompt‑driven pattern for in‑tenant email triage — contributions that make it clearer, safer, or more broadly useful are welcome.

## Ground rules

- **No personal, customer, or tenant‑specific data.** Everything here must stay generic. Do not add real names, customer domains, distribution lists, internal project codenames, org charts, or anything that identifies a specific person or account. Use `[bracketed]` placeholders.
- **Keep it in‑tenant.** The whole point is that mail never leaves the tenant. Don't propose flows that route mailbox content to third‑party services.
- **Be honest about limitations.** If a change adds a capability, document its sharp edges too (latency, permissions, failure modes).

## How to contribute

1. **Open an issue** first for anything non‑trivial, so we can align on the approach.
2. **Fork / branch**, make your change, and keep commits focused.
3. **Test the prompt** against a real inbox if you're changing triage behavior, and note what you saw.
4. **Open a pull request** with a clear description of the what and why.

## Good first contributions

- Additional keep/skip categories that generalize across roles.
- Role templates (e.g., a manager template, an IC template).
- Clarifications or corrections to the **Options considered** matrix (cite current Microsoft sources).
- Adaptations for adjacent surfaces (Teams messages, tasks) using the same copy‑queue + reply‑reconciliation pattern.

## Validating technical claims

The README makes specific claims about Microsoft Graph, Power Automate, and Outlook behavior. If you change any of these, **verify against current Microsoft Learn / Graph API / Power Platform docs** and cite your source in the PR.

## Code of conduct

This project follows the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
