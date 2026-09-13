# Setup — 30 minutes

## What you need

1. **Two (or more) email accounts.** One per lane. Example: a personal account
   for the personal seat, a business account for the ops/build seats.
   The loop lives in one mailbox that all seats can read; each seat sends from
   its own identity.
2. **A place for work orders.** We use a Notion database (schema in
   `work-orders/`). A GitHub project, a Trello board, or a markdown file all
   work — the rule matters more than the tool (see RULES.md).
3. **A scheduler** for the watcher: cron, a scheduled GitHub Action, or any
   agent platform with recurring tasks. Interval: 15 minutes.

## Steps

### 1. Name the loop
Pick a loop token — one word that appears in every loop subject line.
Ours is "Glint" (the personal seat's name). Yours could be the project name.
This token is how the watcher finds the loop family without tracking thread IDs.

### 2. Create the seats
For each seat, you need: an email identity, a system prompt (see `seats/`),
and mailbox access. The personal seat needs read access to the loop mailbox;
the ops and build seats need read + send.

### 3. Send the intro thread
The personal seat sends the first email to the loop mailbox:

- Subject includes the loop token: `"[Token] <> Ops <> Build — capabilities intro"`
- Body: who each seat is, what lane it owns, the work-order rule, the
  no-auto-send rule. This thread is the loop's constitution — link it often.

### 4. File the first work order
Create work order #1 in your tracker (template in `work-orders/`), then have
the personal seat email it to the loop. The seat that owns the work replies
on-thread. Watch it happen.

### 5. Start the watcher
Install the job spec in `watcher.md` on your scheduler at 15-minute intervals.
Seed the watermark with all current loop message IDs so old mail never
triggers a report.

### 6. Tell the human the deal
The loop is silent unless something genuinely needs the human. The personal
seat narrates every loop email in chat — what was sent, what came back —
so the human never feels out of the loop. Make this deal explicit on day one.
