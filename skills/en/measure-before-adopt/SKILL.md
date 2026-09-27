---
name: measure-before-adopt
description: >-
  Decide whether a proposed tool, model, or integration fits this installation
  by measuring real volumes and existing mechanisms first, then re-rating the
  initial estimate against the data. Use when evaluating "should we adopt X?",
  when the case rests on vendor-claimed numbers, or when revisiting an earlier
  recommendation after volumes changed. Not for choosing between equivalent
  tools on quality - that is benchmarking, not volume measurement.
---

# Measure Before Adopt

A method for evaluating "is this tool/model/integration worth adopting in THIS
installation": measure real volumes and inventory existing mechanisms first,
then re-rate the initial estimate against the data. Born from a failure: an
"8/10" rating for a decision-model email filter dropped to 3/10 after one
mailbox query, and the hypothesis "an noul filter will skip empty PR deltas"
dropped to 1/10 after one SQLite query (see Worked example). Rule: an estimate
made before the data is a guess, not an answer.

## When to Use

- A tool, model, or service is proposed for adoption ("let's connect X") and the case rests on vendor marketing numbers or general reasoning.
- You need to know whether a new component fills a real gap in this specific installation, not in some average one.
- Revisiting an earlier recommendation after volumes changed (new course, new channel, new team).

Don't use for:

- Choosing between equivalent tools on quality - run benchmarks instead.
- Tasks with no measurable stream (one-off scripts, design work).

## Procedure

1. **State the hypothesis as a number.** Write one line: predicted figure and
   the refutation threshold. Example: "empty deltas are >= 20% of PR runs ->
   the filter pays off; < 5% -> dead". Completion: the hypothesis is written
   with a number.

2. **Inventory existing mechanisms.** Find scripts/gates/filters that ALREADY
   decide this fork deterministically: search the project's scripts, list
   scheduled jobs, read webhook route definitions and their prompts (prompts
   often hide pre-filters). If a fork is already closed by code (SHA
   comparison, regex gate, threshold) - the hypothesis is dead; stop and
   report. Completion: a list of existing mechanisms OR an explicit "none
   found".

3. **Measure volumes from primary data.** Typical measurements are in Quick
   Reference. No "roughly", only query output. Completion: every figure in the
   future assessment has a source (query + number).

4. **Compare with the hypothesis and re-rate.** Verdict: refuted / confirmed /
   partially confirmed. Applicability rating: before -> after. Completion: a
   before/after table is drawn up and the discrepancy is explained.

5. **Report with figures and queries.** Format: measurements -> verdict ->
   re-rated recommendation. Never leave the initial estimate standing without
   a re-rate - even when it was confirmed. Completion: the answer contains an
   explicit verdict and a new rating.

## Quick Reference - typical measurements

- **Agent wake-up sources** (what wakes the agent, how often): agent state
  databases usually have a `sessions` table with a `source` column. Copy the
  database file to a temp location first (a live WAL database may refuse
  read-only opens), then `SELECT source, COUNT(*) FROM sessions GROUP BY
  source;`. Filter periods with an integer unix timestamp:
  `WHERE COALESCE(started_at, last_activity_at, 0) >= ?` with
  `time.time() - N*86400`.
- **Mailboxes:** IMAP folder counts - `ALL`, `UNSEEN`, `SINCE d-MMM-yyyy`;
  correlate with sessions whose source is the mail channel.
- **Schedulers and webhooks:** list cron jobs (schedule, last run, enabled,
  agent vs script-only) and webhook routes; route prompts often contain
  hidden deterministic pre-filters.
- **Verdicts in transcripts:** match STRICTLY to the machine-output format of
  the authoritative script (e.g. `MODE: X` followed by a checksum line) and
  verify the message role; a loose substring like `MODE:` also matches the
  prompt template echoed in user/assistant roles.

## Pitfalls

- **Prompt echo.** Substring search over transcript messages matches the
  prompt template stored in user/assistant roles. Match the tool-output
  format and count by role.
- **Column types.** Session timestamps are often integer unix seconds, not
  strings; a string date filter silently returns zero rows.
- **Live WAL.** Do not open a live state database read-only in place - copy it
  to a temp path first, or you get "unable to open database file".
- **Self-overestimation.** Your own estimate of "how many judgment calls I
  make per day" is systematically inflated; trust only queries (89 emails a
  month and 1 mail-triggered session is reality against "email is the ideal
  use case").
- **A script already exists.** A cheap deterministic pre-filter in the
  pipeline devalues any hypothesis about an "intelligent" decision - look for
  it FIRST.
- **Vendor numbers.** Latency, speedup, and savings claims do not transfer to
  your installation - measure the local load profile.

## Verification

- The hypothesis had an explicit number and refutation threshold before measurement.
- Every figure in the final answer is reproducible by a query from Quick Reference.
- The verdict is stated explicitly (refuted / confirmed) and the rating was
  re-rated (before -> after).
- If the hypothesis died because a mechanism already exists - that mechanism is named.

## Worked example (2026-09-27)

Hypothesis: "a fast decision-model filter will skip empty PR-review deltas;
some agent runs are wasted" (rating 8/10). Inventory: a bash pre-filter script
already decides the review mode deterministically from git SHAs. Measurement:
199 webhook-triggered agent sessions; of the 185 with an authoritative mode
verdict, FULL=119, DELTA=65, EMPTY_DELTA=1 (0.5%). Verdict: hypothesis
refuted (threshold was <5%). Re-rate: empty-delta filter 8/10 -> 1/10; email
triage 8/10 -> 3/10 (89 emails/month, 1 mail-triggered session). The surviving
candidate (severity re-classification of review findings) is a quality gain,
not a cost saving: ~5/10.
