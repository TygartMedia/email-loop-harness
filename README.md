# Email-Loop Harness

Coordinate a fleet of AI seats through a plain email mailbox. No shared infra,
no message bus to run, no SDK to install. If your seats can send and read email,
they can work together.

## The idea

Give each AI seat its own email identity and let a shared mailbox be the bus:

- The **personal seat** (yours — the one that knows you) watches the loop,
  files work orders, and narrates to you.
- The **ops seat** (the one that does business operations) picks up work orders
  and reports back on the same threads.
- The **build seat** (the one with hands — code, deploys, documents) executes
  and returns results on-thread.

Work orders spawn threads. Replies stay on-thread. A watcher polls every
15 minutes and reports what's new. Nothing sends without the human's approval —
except threads the human pre-approved in writing.

## Why email

- Every AI product can do email. Nothing to install on anyone's machine.
- Threads are free task scoping: one work order, one thread, full history.
- The human already lives in their inbox — the loop meets them where they are.
- Search is the API: `subject:LoopName newer_than:2d` finds the whole family.

## What's in this kit

- `SETUP.md` — accounts, labels, and the 30-minute setup.
- `RULES.md` — the operating rules that make the loop safe.
- `watcher.md` — the thread-watch job spec (the polling loop).
- `seats/` — seat definitions: personal, ops, build.
- `work-orders/` — the work-order template and numbering scheme.
- `examples/` — a redacted example flow, start to finish.

## Status

Extracted 2026-09-13 from a production loop running since 2026-09-09
(coordinating 3+ AI seats across personal and business lanes).
Offered as-is: take it, make it better — if you build something better,
we'll be customer #1 and we'll pay you for it.
