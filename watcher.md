# Thread-Watch Job Spec

The polling loop. Runs every 15 minutes. Read-only by design — it reports,
it never sends.

## On each run

1. **Find the family.** Search every loop mailbox for
   `subject:<LoopToken> newer_than:2d`. Do not rely on fixed thread IDs;
   work orders spawn new threads constantly.

2. **Diff against the watermark.** Compare message IDs against the flat
   seen-list (`seen.json`). Ignore the human's own sent messages.

3. **Report what's new.** For each new message, read it fully and hand the
   personal seat: which thread/subject, who replied, a tight summary of what
   they said. If the reply needs the human, the personal seat decides how to
   surface it (per the narration deal).

4. **Stay silent otherwise.** Nothing new → no output at all. Do not message
   the human.

5. **Update the watermark.** Append every message ID seen this run so nothing
   is reported twice.

## Scaling past the result cap

If a mailbox holds more results than one search page returns, determine
newness with an epoch-cutoff query per mailbox
(`subject:<Token> after:<epoch of last run>`) instead of diffing a capped
result set against the watermark. Use a full paged listing only when
rebuilding `seen.json` from scratch.

## Failure modes we hit

- **Single-mailbox watch:** every other-lane reply went unseen until we seeded
  both accounts into the watermark. (Rule 7.)
- **Subject without the token:** three threads slipped past the watcher.
  (Rule 1 — validated by failure.)
- **Watermark rebuilt to one thread:** duplicate reports for a day.
  Append-only, always. (Rule 6.)
