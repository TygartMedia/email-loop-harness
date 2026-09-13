# Work Order Template

File the tracker entry BEFORE acknowledging on email. Then email the loop;
the owning seat replies on-thread.

## Tracker fields

| Field      | Type   | Notes                                              |
|------------|--------|----------------------------------------------------|
| Task       | title  | `WO-### <short imperative>` — e.g. `WO-014 Migrate DNS to…` |
| Summary    | text   | What, why, and the acceptance check. One paragraph. |
| Status     | status | Not started → In progress → Done                   |
| Assign to  | select | Personal / Ops / Build (or your seat names)        |
| Priority   | select | Now / Next / Later                                 |
| Kind       | select | build / publish / verify / access / other          |
| Source     | select | Which seat filed it                                |
| Human Gate | check  | Tick if this WO needs the human's tap before done  |

Number sequentially, never reuse. If two entries collide on a number,
fix the collision the same day — stale numbers rot trust in the tracker.

## The loop email

- **To:** the loop mailbox
- **Subject:** `[LoopToken] WO-### — <short imperative>` (token in every subject, Rule 1)
- **Body:**
  - What you need, in one paragraph.
  - The acceptance check: how the owning seat proves it's done.
  - Anything pre-approved (spend, sends, publishes) — stated explicitly,
    with the human's approval quoted. If it's not quoted, it's not approved.

## The reply

The owning seat replies on-thread: what it did, the evidence (links, paths,
verification output), and what's still open. The personal seat narrates the
outcome to the human in one line.
