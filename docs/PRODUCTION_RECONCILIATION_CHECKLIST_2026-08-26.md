# PRODUCTION RECONCILIATION CHECKLIST

Date: 2026-08-26 JST
Status: CONFIRMED PRE-WORK GATE
Production code changes: NONE

Purpose: Prevent stale GitHub Handoff state, local pending commits, and actual OpenAI Sites Production state from being mixed before any new Firm-detail implementation.

---

# 1. Sources to reconcile

Work must distinguish:

A. Actual OpenAI Sites managed Production source
B. Current published Production version
C. Local Work repository state
D. Internal remote state (`git.chatgpt-team.site`)
E. GitHub Handoff repository (`prop-affiliate-os-lite`)
F. Accepted local commits waiting for remote/publish

GitHub Handoff is not the Production Application Source.

---

# 2. Known historical/current references

Handoff `docs/CURRENT_STATE.md` records Production Version 81.

Project central-command state later recorded Production Version 82 as accepted/published.

Therefore implementation must not assume either value without reading the actual current Production state at execution time.

Expected result after reconciliation:

- one explicit current Production version
- one explicit current Production commit/fingerprint where available
- local/remote ahead-behind known
- pending accepted commits known
- Worktree clean before new implementation

---

# 3. Pending accepted work

Before Firm-detail implementation, preserve existing accepted commits exactly as they exist in the Production implementation repository.

Known project references:

- Evidence MVP commit: `3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f`
- Fundora campaign commit: `2191f06dc56006b4018f16ec8c2ac51161d2f70a`

Do not amend, rebase, squash, recreate, or mix these with Firm-detail work.

---

# 4. Authentication gate

If `git.chatgpt-team.site` authentication/read/fetch remains unavailable:

- do not start new Production implementation
- do not create replacement commits in unrelated GitHub repositories
- do not migrate Production code to `prop-affiliate-os-lite`

Return:

`HOLD_AUTH_BLOCKER`

---

# 5. Baseline capture

After authentication is healthy and pending accepted work is handled, capture:

- Production version
- Production commit/fingerprint
- remote HEAD
- local HEAD
- ahead / behind
- Worktree status
- protected Master hash
- protected Diagnosis hash
- protected GA4 hash
- full regression baseline
- build status
- lint status
- sitemap route count
- public smoke status

This becomes the Firm-detail implementation baseline.

---

# 6. Protected boundaries

Before editing confirm no new Firm-detail work is allowed to redesign:

- `app/master-data.json`
- DiagnosisLogicV2
- 7-question order
- score
- eligibility
- ranking
- existing GA4 initialization
- affiliate/coupon/price influence on diagnosis

If implementation would require such a change, stop and return to Central Command.

---

# 7. Fundora time-sensitive handling

The accepted Fundora campaign is time-limited.

Before new Firm-detail implementation:

- determine whether its campaign window is still active
- if active, complete the already-accepted release path first
- if ended before publish, do not publish stale campaign messaging as active
- preserve normal Fundora Firm/Plan data separately from campaign lifecycle

Time-sensitive campaign handling must not be bundled with the new Firm-detail page release unless Central Command explicitly approves that release composition.

---

# 8. GitHub Handoff sync

After actual Production truth is captured, GitHub Handoff documentation may be updated to reflect the new snapshot.

Do not use a Handoff documentation update as proof that Production itself changed.

Recommended fields:

- actual Production version
- checked date/time JST
- Production commit/fingerprint
- pending local commits = 0/known
- latest regression
- known cautions

---

# 9. Start Gate for Firm Detail Pilot

Firm Detail Pilot may start only if all are true:

- authentication recovered
- current Production identified
- accepted pending work resolved/preserved
- Worktree clean
- local/remote relationship known
- protected hashes captured
- regression baseline PASS
- no unexplained Production/Handoff mismatch

Expected start status:

`FIRM_DETAIL_PILOT_START_GATE_PASS`

Otherwise:

`HOLD_FIRM_DETAIL_PILOT_START`

---

# 10. No implementation authority

This checklist does not authorize publish, version save, or Production changes by itself.

It is the mandatory reconciliation gate before the separately confirmed Firm Detail Pilot Implementation Spec is executed.
