# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 16 / HOME COMMERCIAL LINK + DISCLOSURE

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / CORRECTION REQUIRED / NO PRODUCTION CHANGE
Scope：公開Homeの Firm CTA / Coupon CTA / PR disclosure / Official source separation
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md` + `COMPLIANCE_BASELINE_V1_2026-08-26.md`

## 0. Trigger

公開Homeの旧crawl/current-index surfaceでは、FirmカードのCTAラベルが `最新条件を見る` である一方、一部リンク先がAffiliate/Partner/Referral経路になっている。

Examples observed:
- Blueberry Funded -> affiliates.blueberryfunded.com
- SuperFunded -> partners.superfunded.com
- Funded7 -> my.funded7.com referral/commercial path
- Blueberry Futures -> portal.blueberryfutures.com referral/commercial path
- Trading Cult Pro -> referral-bearing commercial domain in project canonical links

同一HomeにはGlobal `PRを含みます` / affiliate disclosureがあるが、Compliance Baselineは Official information link と Affiliate conversion CTA の分離を要求している。

## 1. Check 1 — current/public surface

Public surface confirms:
- Global PR/affiliate notice exists.
- Special-code section itself explicitly says PR/affiliate.
- However, Firm discovery cards use information-seeking labels such as `最新条件を見る` while some destinations are commercial/referral links.

Result: structural ambiguity exists even when global disclosure exists.

## 2. Check 2 — internal approved Compliance Baseline

`docs/COMPLIANCE_BASELINE_V1_2026-08-26.md` explicitly requires:
- Affiliate CTA near commercial relationship disclosure
- Official information link and Affiliate conversion CTA separation
- Global disclosure alone is not automatically sufficient
- Production gate: `Official URL / Affiliate URL separation PASS`

Result: current observed pattern does not meet the approved target architecture.

## 3. Check 3 — current Consumer Affairs Agency official guidance

Current CAA stealth-marketing guidance/Q&A confirms that the overall display must make advertising nature clear, and that even where an affiliate site has a top-level disclosure, individual sections must not appear non-commercial where they are in fact commercial/advertising displays.

Official:
- https://www.caa.go.jp/policies/policy/representation/fair_labeling/stealth_marketing
- https://www.caa.go.jp/policies/policy/representation/fair_labeling/faq/stealth_marketing/

This audit does not make a legal violation determination. It uses CAA guidance as an operating-risk standard.

## 4. Result

Status:
`COMPLIANCE_CORRECTION_REQUIRED / CTA_SEPARATION`

This is not a demand to remove affiliate links.

Safe target pattern for each Firm surface:

1. `公式情報を確認` -> clean non-affiliate official Rules/Help/Product URL
2. `PR｜特典・申込みを確認` -> affiliate/referral conversion URL
3. commercial CTA has nearby concise PR disclosure
4. diagnosis/rules facts continue to be sourced from the official non-affiliate evidence path

## 5. Priority

P0/P1 after auth recovery and Production reconciliation.

Do not bundle this with Diagnosis scoring or Master migration.

First inspect exact current Production link targets before editing because crawler/index variants differ.

## 6. Special-code section

The dedicated coupon/code area already contains explicit PR language and is structurally safer.

Still required:
- verify each exclusive code via checkout / partner portal / direct official evidence packet
- do not use absence from public search as invalidation
- keep effect/scope/expiry cautious until evidence reaches the triple-check standard

## 7. Final

Production modification performed: NONE

Final Status:
`WAVE16_COMPLETE_HOME_INFORMATION_AND_AFFILIATE_CTA_SEPARATION_QUEUED`
