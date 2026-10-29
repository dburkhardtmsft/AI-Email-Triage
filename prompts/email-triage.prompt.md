# Email Triage — Master Prompt

Paste this into Microsoft Scout. Fill in every `[bracketed]` field for your role, and the `+ blanks`. This one prompt (a) creates the review folder, (b) back‑tests the last 30 days into it, and (c) sets up a recurring automation left **paused** for you to review first.

---

```
# AI Email Triage — Master Prompt
# Questions or feature requests? Open an issue: https://github.com/dburkhardtmsft/AI-Email-Triage/issues
# Source: https://github.com/dburkhardtmsft/AI-Email-Triage
# New to Scout? https://learn.microsoft.com/en-us/microsoft-scout/get-started

Set up my AI-Powered email triage.

Create an Outlook folder called [#ToReview] (if it doesn't exist) and use it as my
review folder. Then scan my Inbox for the last 30 days and place a COPY of every
email I need to review into that folder — never move or delete originals.

KEEP an email if it matches any of these (my standard list — include all of them):
  1. My leadership chain: [manager -> ... -> top]
  2. My org/product leaders: [VP/CVP + directs]
  3. My close collaborators: [names] (infer more from who I reply to in Sent Items)
  4. My staff: anything from my direct reports / anyone who reports to me
     (managers - never miss mail from your own team)
  5. Customer/field mail — internal or EXTERNAL, FROM ANY DOMAIN — about [my product], a
     deal / RFP / partnership / pricing / escalation, or that mentions me by name. Domain
     examples in #6 below are illustrative only — do NOT require a domain match; judge by
     content first.
  6. Strategic customer domains to always keep (examples, not exhaustive):
     [customer1.com, customer2.com]
  7. Career/strategy: promotion & recognition announcements (even from notification
     addresses), AI/strategy discussions, leadership AMAs, org changes
  8. My team's newsletter: [name]
  9. Anything sent only to me (sole recipient) and work-related
  10. APPROVALS / ACTIONS NEEDED — KEEP ONLY WHEN I MUST ACT: expense-report approvals,
     workflow approval notifications (e.g. your company's approval system), purchase/PO/
     procurement/invoice/timecard/access-request approvals — but ONLY when they show I
     (or someone in my leadership chain) am the pending approver who still needs to act
     (e.g. "Action required: Approve or deny...", "...is pending your approval"). SKIP
     already-resolved status/FYI notifications (e.g. "...was approved", "...has been
     approved/denied") where no action remains — these are noise even if I'm the sole
     recipient.
  11. INCIDENT / LIVE-SITE for my area: incident, outage, on-call (and on-call
     reminder), handoff, or RCA emails from my incident-management system (e.g. an
     IT service-management tool) that concern [my product/service] or name me in the
     notification/on-call chain. Keep even from automated incident addresses.
  12. TEAMS COLLABORATORS (auto-derived, no maintenance needed): before each run, fetch my
     recent 1:1 Teams chats (Microsoft Graph `/me/chats?$filter=chatType eq 'oneOnOne'
     &$expand=members&$orderby=lastUpdatedDateTime desc`). Anyone I've had a 1:1 chat with
     in the last 60 days gets the same KEEP treatment as #3 — this catches new close
     contacts (e.g. someone I just started working with) without me having to hand-list
     every name.
  13. UNFAMILIAR BUT DIRECT ASK: an email personally addressed to me by name (not a mass
     distribution, newsletter, or broad cc-blast) from a sender not on any list above,
     where the sender is directly requesting my personal involvement, input, help, or
     decision on a substantive matter (e.g. legal, compliance, security, executive
     escalation, or an explicit ask for assistance) — keep even if the sender or topic is
     unfamiliar. This exists specifically to catch important first-time senders (e.g.
     legal counsel reaching out directly about a matter naming you) that no static list
     would ever anticipate.
  + Also always KEEP: ______________________________________________
    (a project codename, partner, customer exec, topic specific to you)
  + Also always SKIP (optional): specific senders, domains, or categories to auto-skip
    (e.g., certain newsletters, tools, distribution lists). Leave blank for defaults: ______

EXTERNAL MARKETING / INDUSTRY NEWS DIGESTS — SKIP even on-topic: vendor e-newsletters,
sponsored whitepapers, conference/event marketing, "you don't often get email from..."
cold-sender banners, and industry news digests (e-news/analyst-newsletter senders) are
SKIP even when their subject matches a topic you care about (AI, security, your
product/industry vertical, etc). Topical relevance alone does NOT earn a KEEP — only a
named individual you know, or an item on your explicit always-KEEP list, does. (#7's
"career/strategy" bucket means your own organization's internal strategy content, not
external industry publications or vendor marketing that happens to mention AI/strategy
keywords.)

SKIP routine noise: bulk marketing, automated replies, meeting accept/decline
notifications, generic identity/access-bot notifications, news and retail
newsletters, and RSS digests. Exceptions (keep these even though they're automated):
action-required approval/expense/purchase requests (#10) and incident/on-call mail
about my area (#11). When something is borderline but could matter professionally,
prefer to KEEP (except the approvals rule in #10 and the external marketing/news rule
above, which are both strict — resolved/FYI status emails and on-topic vendor
marketing should be skipped even when borderline).

FLAG "Needs Reply": for each email you copy in, decide whether it needs my personal
reply (a genuine question, request, approval/decision, or a person awaiting my
response) and, if so, tag the copy with a "Needs Reply" category. An email counts as
already replied only if I sent a response AFTER that specific message arrived (compare
to Sent Items, per-message, scoped by conversation) — so follow-ups in old threads
still surface. (Automated approval/expense and incident/on-call notifications are kept
for visibility but are actioned in their own portal, not by an email reply — so don't
tag those "Needs Reply".)

When done, give me a digest grouped by reason (Leadership / Team / Customer-Field-Deal /
Promotion / AI-Career / Newsletter / Approvals-Actions / Incident-LiveSite /
Teams-Collaborator / Unfamiliar-Direct-Ask / Personally addressed / Needs-Reply / Other).

Finally, create a recurring automation that repeats this triage each [hour / morning at
7:00 AM], but leave it TURNED OFF/paused until I review the 30-day results and tell you
to enable it. On each run:
  - Re-fetch the Teams 1:1 collaborators list (#12) fresh every run — it's a single cheap
    Graph call and keeps the list current without any manual upkeep.
  - Only scan the last ~2 hours of new mail, and skip anything already in [#ToReview]
    (de-duplicate by message id) so nothing is copied twice.
  - ZERO-RESULT GUARDRAIL: if a run's scan of the last ~2 hours returns 0 candidate
    emails, do NOT assume that means "no new mail" and silently report no changes — a
    zero-result fetch can also be a transient API/filter glitch. First re-run the same
    query with a wider ~6-hour window as a sanity check. If that also returns 0, it's
    safe to report "no changes." If it returns messages, treat it as a recovered-window
    anomaly: process those messages normally (same keep/skip/de-dup logic) and say so
    explicitly in the run summary, so a silent skipped-run doesn't go unnoticed.
  - REMOVE from [#ToReview] any message I have already replied to (per-message: I sent a
    reply after it arrived). If someone later replies back, that's a new message — copy
    it in again and re-evaluate whether it needs a reply.
  - Re-apply the "Needs Reply" flag only to newly copied messages; never re-flag ones
    already in the folder.

Tip: turn OFF conversation view in [#ToReview] so each message shows individually.

# ---
# Questions, feedback, or feature enhancement requests?
# Open an issue: https://github.com/dburkhardtmsft/AI-Email-Triage/issues
# Source: https://github.com/dburkhardtmsft/AI-Email-Triage
```

---

## Turning it on

Once you're happy with the 30‑day backfill:

```
Turn on my [#ToReview] triage automation.
(Optional: hourly vs. a specific daily time; keep Teams digests off.)
```

Then enable **Scout → Settings → "Launch at system startup"** and **"Prevent Sleep"** so triage keeps running after reboots and your laptop doesn't doze off mid‑run. Managed Windows machines restart regularly (e.g. weekly Patch Tuesday updates); without auto‑launch, your scheduled triage silently stops until you reopen Scout.

## Working the queue

- **Filter/sort `#ToReview` by the "Needs Reply" category** to see what's waiting on you.
- To dismiss something that doesn't need a reply, **remove the category** — no need to delete.
- Replying is detected automatically; the item clears on the next run.

---

## Questions or feature requests?

Have questions, feedback, or feature enhancement requests? Please [open an issue](https://github.com/dburkhardtmsft/AI-Email-Triage/issues) on this repo. Contributions and forks are welcome.
