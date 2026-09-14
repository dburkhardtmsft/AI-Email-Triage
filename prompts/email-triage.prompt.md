# Email Triage — Master Prompt

Paste this into Microsoft Scout. Fill in every `[bracketed]` field for your role, and the `+ blanks`. This one prompt (a) creates the review folder, (b) back‑tests the last 30 days into it, and (c) sets up a recurring automation left **paused** for you to review first.

---

```
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
  5. Customer/field mail — internal or EXTERNAL — about [my product], a deal / RFP /
     partnership / pricing / escalation, or that mentions me by name
  6. Strategic customer domains to always keep: [customer1.com, customer2.com]
  7. Career/strategy: promotion & recognition announcements (even from notification
     addresses), AI/strategy discussions, leadership AMAs, org changes
  8. My team's newsletter: [name]
  9. Anything sent only to me (sole recipient) and work-related
  + Also always KEEP: ______________________________________________
    (a project codename, partner, customer exec, topic specific to you)
  + Also always SKIP (optional): specific senders, domains, or categories to auto-skip
    (e.g., certain newsletters, tools, distribution lists). Leave blank for defaults: ______

SKIP routine noise: bulk marketing, automated replies, meeting accept/decline
notifications, access/approval-bot and identity notifications, news and retail
newsletters, and RSS digests. When something is borderline but could matter
professionally, prefer to KEEP.

FLAG "Needs Reply": for each email you copy in, decide whether it needs my personal
reply (a genuine question, request, approval/decision, or a person awaiting my
response) and, if so, tag the copy with a "Needs Reply" category. An email counts as
already replied only if I sent a response AFTER that specific message arrived (compare
to Sent Items, per-message, scoped by conversation) — so follow-ups in old threads
still surface.

When done, give me a digest grouped by reason (Leadership / Team / Customer-Field-Deal /
Promotion / AI-Career / Newsletter / Personally addressed / Needs-Reply / Other).

Finally, create a recurring automation that repeats this triage each [hour / morning at
7:00 AM], but leave it TURNED OFF/paused until I review the 30-day results and tell you
to enable it. On each run:
  - Only scan the last ~2 hours of new mail, and skip anything already in [#ToReview]
    (de-duplicate by message id) so nothing is copied twice.
  - REMOVE from [#ToReview] any message I have already replied to (per-message: I sent a
    reply after it arrived). If someone later replies back, that's a new message — copy
    it in again and re-evaluate whether it needs a reply.
  - Re-apply the "Needs Reply" flag only to newly copied messages; never re-flag ones
    already in the folder.

Tip: turn OFF conversation view in [#ToReview] so each message shows individually.
```

---

## Turning it on

Once you're happy with the 30‑day backfill:

```
Turn on my [#ToReview] triage automation.
(Optional: hourly vs. a specific daily time; keep Teams digests off.)
```

## Working the queue

- **Filter/sort `#ToReview` by the "Needs Reply" category** to see what's waiting on you.
- To dismiss something that doesn't need a reply, **remove the category** — no need to delete.
- Replying is detected automatically; the item clears on the next run.

---

## Questions or feature requests?

Have questions, feedback, or feature enhancement requests? Please feel free to reach out to **Dave Burkhardt** — [dburkhardt@microsoft.com](mailto:dburkhardt@microsoft.com). Contributions and forks are welcome.
