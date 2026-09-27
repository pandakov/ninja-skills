---
name: measure-before-adopt-hermes
description: >-
  Hermes-specific variant of measure-before-adopt: decide whether a proposed
  tool, model, or integration fits this Hermes installation by measuring real
  volumes and existing mechanisms first, then re-rating the initial estimate
  against the data. Use when evaluating "should we adopt X?" in a Hermes agent
  setup, when the case rests on vendor-claimed numbers, or when revisiting an
  earlier recommendation after volumes changed. Companion to the universal
  measure-before-adopt skill; install one of the two, not both.
---

# Measure Before Adopt (Hermes variant)

Same method as [measure-before-adopt](../measure-before-adopt/SKILL.md):
hypothesis as a number -> inventory existing mechanisms -> measure volumes
from primary data -> re-rate -> report with an explicit verdict. This variant
replaces the generic Quick Reference with concrete Hermes tool calls and adds
Hermes-specific pitfalls. Read the universal skill for the full procedure and
the worked example; this file assumes it.

## Quick Reference - concrete Hermes measurements

All database work goes through `execute_code` (Python + sqlite3); shell work
through `terminal`. Resolve paths from `$HERMES_HOME` (do not hardcode them).

- **Agent wake-up sources.** Copy then query - a live WAL database refuses
  read-only opens in place:

  ```python
  # terminal: cp "$HERMES_HOME/state.db" /tmp/state_ro.db
  import sqlite3, time
  con = sqlite3.connect('/tmp/state_ro.db')
  now = int(time.time())
  rows = con.execute(
      "SELECT source, COUNT(*) FROM sessions "
      "WHERE COALESCE(started_at, last_activity_at, 0) >= ? "
      "GROUP BY source ORDER BY 2 DESC", (now - 30*86400,)).fetchall()
  ```

- **Which sessions a channel produced.** Same table, filter by source
  (`'email'`, `'webhook'`, `'telegram'`, `'cron'`, ...) and inspect
  `title`, `message_count`, `started_at` (integer unix seconds).
- **Mailbox volume vs mail-triggered sessions.** IMAP counts via `execute_code`
  (`imaplib`, credentials from the configured email secrets - never print
  them): folder totals, `UNSEEN`, `SINCE d-MMM-yyyy`; then compare with
  `SELECT COUNT(*) FROM sessions WHERE source='email'`.
- **Scheduled jobs.** `cronjob(action='list')` - schedule, `last_run_at`,
  `enabled`, `no_agent` (script-only jobs never wake the LLM).
- **Webhook routes and hidden pre-filters.** Read
  `$HERMES_HOME/webhook_subscriptions.json`: each route's `prompt` may embed a
  deterministic pre-filter (mode-deciding script, delta logic) that already
  closes the fork your hypothesis targets.
- **Verdicts in transcripts.** `messages.content` for sessions of a given
  source; match the authoritative tool-output format STRICTLY and count by
  role - see Pitfalls.
- **Repo activity.** `terminal(command="git -C <repo> log --oneline -20")`,
  `git -C <repo> shortlog -sn` - volume of real events per period.

## Procedure

Identical to the universal skill, with two Hermes-specific additions:

- In step 2 (inventory), always include `cronjob(action='list')` and the
  webhook subscriptions file - Hermes pipelines often already contain script
  gates (`no_agent` jobs, route scripts) that decide forks deterministically.
- In step 3 (measure), use the Quick Reference calls above; every figure in
  the final report must name the query that produced it.

## Pitfalls (Hermes-specific)

- **Prompt echo in transcripts.** A substring like `MODE:` matches the prompt
  template stored in user/assistant roles. Match the tool-result format (e.g.
  `MODE: DELTA` followed by `HEAD_SHA:`/`LAST_SHA:`) and restrict counting to
  `role='tool'` messages.
- **Literal `\n` in stored content.** Transcript content often stores escaped
  newlines as backslash-n, so line-anchored regex (`^...$`) silently fails.
  Match with a lookahead for the following field instead.
- **Timestamps are integers.** `sessions.started_at` is unix seconds; a string
  date filter returns zero rows without an error.
- **`hermes` CLI may be absent from the agent's shell PATH** even on a
  machine where Hermes runs. Prefer `cronjob`/`execute_code`/direct file reads
  over shelling out to `hermes ...`.
- **WAL copy first.** `sqlite3.connect('file:...state.db?mode=ro', uri=True)`
  on the live database fails with "unable to open database file"; copy to
  /tmp and query the copy.
- **Do not print secrets.** Email/IMAP and token material lives in env files;
  read, use, never echo. Report counts, not credentials.

## Verification

Same as the universal skill: hypothesis numbered and refutable up front,
every reported figure reproducible by a named query, explicit verdict,
re-rated estimate (before -> after), and any pre-existing mechanism named.
