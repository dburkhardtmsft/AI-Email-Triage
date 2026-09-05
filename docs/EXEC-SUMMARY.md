# Executive Summary

**Automate Your Inbox — an AI chief‑of‑staff for email.**

One prompt turns Microsoft Scout into an intelligent, in‑tenant email‑triage assistant.

## The problem

Classic Outlook rules match **senders and keywords**. They can't tell a genuine customer escalation from an automated alert that shares the same word — so the mail carrying real business risk is exactly the mail that gets buried. They're AND‑only within a rule, blind to context, and require constant hand‑maintenance.

## The solution

A scheduled automation that reads your Inbox with AI judgment and:

- **Copies** only the mail that actually matters into a review folder — your Inbox is never moved or modified.
- **Flags** what needs your personal reply (an Outlook "Needs Reply" category you can filter on).
- **Self‑clears** each item the moment you answer, and re‑surfaces a thread if someone replies back.

One natural‑language policy replaces dozens of brittle rules. The review folder becomes a live action list, not a second archive.

## Why it matters

- **Free for Microsoft employees** — it runs on tooling we're already provisioned (Microsoft Scout + WorkIQ + Microsoft Graph). Setup is essentially one prompt.
- **In‑tenant by design** — unlike third‑party AI email tools, no mailbox content leaves the tenant, so there's no data‑governance exposure.
- **Scales to any role** — the same pattern serves any IC or manager. Managers can add *"anything from my direct reports,"* one of the most damaging things classic rules miss.

## How it compares

| Option | AI judgment | Copy (Inbox intact) | Self‑clears | Flags "needs reply" | Cost |
|---|---|---|---|---|---|
| Server‑side Outlook rules | No | Yes (API only) | No | No | Included |
| Power Automate + AI | Yes | Only via Graph connector (DLP‑gated) | Yes | Yes | Premium + AI capacity |
| Azure Logic App / Function | Yes | Yes | Yes | Yes | Azure subscription |
| M365 Copilot "Prioritize my inbox" | Yes | No (in‑place) | No | Partial | Copilot license |
| **Microsoft Scout (this project)** | **Yes** | **Yes** | **Yes** | **Yes** | **No extra license** |

## The one trade‑off

Scout runs locally, so your laptop must be on with Scout running for the scheduled triage to fire. Fully unattended operation means moving to a cloud option (Power Automate or a Logic App/Function) — subject to license, tenant DLP, and department budget.

---

*Full setup guide and technical details: see the [README](../README.md). Copy‑paste prompt: [`prompts/email-triage.prompt.md`](../prompts/email-triage.prompt.md).*
