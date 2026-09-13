# The Rules

These are the load-bearing walls. The harness works without fancy tooling;
it does not work without these rules.

## 1. The subject-line rule
Every loop thread's subject contains the loop token. Work orders spawn new
threads — never rely on fixed thread IDs. The watcher finds the family with
`subject:<Token> newer_than:2d`. Three emails once slipped past because their
subjects didn't say the token. The rule was validated by the failure it was
built for.

## 2. The work-order rule
A work order's tracker entry gets filed **before** anyone acknowledges that
work order on email. Email is the talk layer; the tracker is the record.
Number them (WO-001, WO-002…). The personal seat files; the owning seat
acknowledges on-thread.

## 3. No auto-send
Nothing sends without the human's explicit approval: recipient, subject, and
body summary confirmed first. The watcher itself never sends — it only reports.
Exceptions require the human's written standing pre-approval for a named thread,
and even then the watcher stays read-only; only the personal seat may send.

## 4. Seat lanes
Each seat owns a lane and stays in it. Ours: personal seat = the human's
identity, taste, and filter; ops seat = business operations; build seat =
hands (code, deploys, documents). When one seat can't reach something, it asks
another seat to fetch it and relay the short version — it never asks the human
to go click around.

## 5. Loop narration
The personal seat narrates every loop email in chat: what was sent, what came
back. Background sweeps run on an explicit quiet cadence — silent unless
something genuinely needs the human. Make the deal explicit: "silent unless
it's worth interrupting you, fully present the moment you message."

## 6. Watermark everything
The watcher keeps a flat list of every seen loop message ID (the watermark).
Seed it with all current IDs on first run. Never rebuild it down to one
thread's IDs — that causes duplicate reports. Append-only.

## 7. Two mailboxes, one family
If the loop spans two accounts, watch both. Message IDs are mailbox-local:
watching only one means the other lane's replies go unseen. Seed both
accounts' IDs into the same watermark; dedupe by (sender, date, subject).
