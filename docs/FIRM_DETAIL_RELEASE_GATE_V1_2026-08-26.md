# FIRM DETAIL RELEASE GATE V1

Date: 2026-08-26 JST
Status: CONFIRMED
Purpose: Shared release gate for all Firm detail pages.
Production code changes: NONE in this document.

This gate supplements, and does not replace, existing regression and Production release requirements.

---

# 1. Scope gate

Before implementation, confirm the release contains only the approved Firm-detail scope.

Do not combine with:

- Diagnosis changes
- Ranking changes
- Master schema redesign
- Platform registry rollout
- Payout real-data integration
- Evidence schema migration
- unrelated coupon engine changes
- unrelated campaign releases

If unrelated implementation is required, split the release.

---

# 2. Current Truth gate

Work must read the current Production source before editing.

Required:

- current Production version identified
- current route ownership identified
- current plan data identified
- current SourceHealth/status identified
- protected hashes/boundaries identified
- no unexplained local/remote divergence

GitHub Handoff summaries are supporting documentation only and must not overwrite current Production data by themselves.

---

# 3. Content source order

Use sources in this order:

1. Current Production-approved data
2. Current official primary evidence
3. Accepted verified extraction/spec documents
4. M11/M14 content packs
5. Editorial copy derived from the above

Never reverse this order by using old prose to overwrite newer verified facts.

---

# 4. Firm page minimum structure

Each page must have:

- H1 / intro
- Firm Snapshot
- first three checks
- plan section
- rule section
- platform summary
- Japan-specific checks
- payout summary only where verified
- FAQ
- related guides
- price/campaign/coupon secondary section
- official information link
- affiliate/conversion CTA where applicable
- checked date / verification state
- disclosure / disclaimer

A page may omit a subsection if the information is not verified; it must not fabricate content to make every page visually identical.

---

# 5. Commercial disclosure gate

If any affiliate relationship exists:

- disclose PR/affiliate relationship clearly
- disclosure must be visible near the commercial CTA
- official information link and affiliate link must be distinguishable
- affiliate commission/coupon must not influence factual verification, search order, diagnosis, or ranking

If a test/review account was supplied and the page relies on that testing:

- disclose the supplied-account relationship
- state that account provision does not guarantee favorable evaluation

If sponsorship materially relates to the content:

- disclose sponsorship in a visible, understandable form

---

# 6. Claims gate

Fail the release if unsupported claims include:

- guaranteed payout
- guaranteed profit
- guaranteed pass
- risk-free
- completely safe
- anyone can win
- best / safest / fastest / No.1 / most popular without adequate evidence
- “real capital” or equivalent where service documentation does not support the wording

Comparative claims require current, comparable evidence and a defined comparison scope.

---

# 7. Japan / regulatory gate

Keep separate:

- availability to users in Japan
- Japanese-language availability
- Japanese customer support
- legal/regulatory status in Japan

Never imply one proves another.

“Japan available” must not be displayed as “Japan licensed/approved”.

If legal classification is unclear, use neutral service-language and route the issue to human/legal review rather than infer a status.

---

# 8. Status gate

Public states must preserve meaning:

- verified -> 公式根拠で確認済み
- conditional -> 条件付き・追加確認が必要
- unverified -> 未確認
- unsupported -> 非対応
- unknown -> 情報不足・不明

Do not convert:

- unknown to false/unsupported
- conditional to verified
- conflict to verified
- HOLD to normal current data

---

# 9. Time-sensitive data gate

Separate:

- base price
- official campaign
- personal affiliate coupon
- legacy/ended plan
- current plan

Each changing item must have an appropriate checked/status field.

Do not calculate or display discounted final prices automatically unless that behavior is separately approved and validated.

---

# 10. FAQ gate

FAQ must follow M11/M14 safety rules.

Do not add to FAQ schema:

- HOLD entries
- coupon/referral content where volatile
- volatile eligibility claims
- limited historical variants where schema could overgeneralize
- content not visibly rendered on the page

Rendered FAQ and structured FAQ must match exactly when schema is used.

---

# 11. Payout gate

Until accepted payout source data exists:

- no fabricated payout routes
- no inferred provider chains
- no summary-to-record conversion
- no descriptor-to-record conversion
- no P00R/P01/P10 substitute records

Firm page may state only separately verified Firm-specific payout facts.

---

# 12. Platform gate

Until Platform Registry/route layer is separately accepted:

- existing platform display strings may be shown as current Firm data
- do not invent Firm × Platform mappings
- do not create links to routes that do not exist
- do not imply general platform capability is enabled at every Firm

---

# 13. Analytics / privacy gate

Use existing GA4 initialization only.

Do not send:

- name
- email
- KYC content/status details tied to an individual
- bank account data
- card data
- wallet addresses
- payout recipient data
- trading account identifiers

Commercial click tracking may use non-PII Firm/content/CTA identifiers only if separately approved.

---

# 14. Regression gate

At minimum:

- existing full regression PASS
- new Firm-detail tests PASS
- build PASS
- lint errors 0
- git diff --check PASS
- protected Master unchanged unless explicitly approved
- Diagnosis unchanged
- GA4 initialization unchanged
- affiliate changes limited to approved CTA rendering/data

Failure in unrelated existing tests must be investigated; do not suppress or delete tests to obtain PASS.

---

# 15. Route / SEO gate

For every new public Firm page:

- unique title
- unique meta description
- one clear H1
- self canonical
- intended indexability
- sitemap inclusion only after QA PASS
- no duplicate route ownership

Do not create ranking-style SEO titles unsupported by the editorial model.

---

# 16. 390px/mobile gate

Before publish:

- no horizontal overflow
- readable plan cards/tables
- long Japanese labels wrap
- CTA target height appropriate for mobile
- disclosure remains visible/readable
- accordion/details controls usable
- no critical text clipped

Fresh real-device iPhone Safari check is required for the Feature/Content release when executable.

---

# 17. Human review gate

Before publish, human reviewer confirms:

- page does not overstate Firm quality
- page does not hide a material caution behind a CTA
- Affiliate/PR disclosure is understandable
- Firm service nature is not misrepresented
- unresolved conflicts remain visible/omitted as required
- campaign/coupon wording is current
- final official links are correct

---

# 18. Rollback gate

Each Firm-detail rollout must have a clear rollback boundary.

Preferred release units:

- Pilot: Fundora + Fintokei only
- Wave 1: approved subset after pilot acceptance
- later waves: separate accepted release units

Do not combine all Firm pages with Platform/Payout feature launches.

Rollback must restore navigation, sitemap, routes, and page content to the last stable Production state without altering Diagnosis/Master data.

---

# 19. Stop conditions

Stop and return to Central Command if:

- current Production baseline cannot be identified
- authentication/repository state is unresolved
- a page requires guessed plan/rule values
- a HOLD value would need to be presented as verified
- a catalog entry must be invented
- Diagnosis/Master redesign becomes necessary
- payout source fabrication would be required
- regulatory/legal classification must be inferred
- existing GA4 initialization must be replaced
- regression fails
- protected data unexpectedly changes

Return status:

`HOLD_FIRM_DETAIL_RELEASE`

---

# 20. Acceptance status

A Firm-detail release is accepted only when all applicable gates pass.

Final expected status:

`FIRM_DETAIL_RELEASE_ACCEPTED`

or

`HOLD_FIRM_DETAIL_RELEASE`
