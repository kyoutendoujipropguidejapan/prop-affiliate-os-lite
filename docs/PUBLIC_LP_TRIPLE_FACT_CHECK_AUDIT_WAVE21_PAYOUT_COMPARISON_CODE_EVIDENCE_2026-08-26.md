# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 21 / PAYOUT COMPARISON + CODE EVIDENCE

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / SUPERFUNDED UPDATE + CODE EVIDENCE BACKFILL / NO PRODUCTION CHANGE
Scope：`/prop-firm-payout-comparison`
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`
Policy：general/current facts = English-first

## 0. Route scope

Current route compares scoped payout/reward conditions for:
- Fintokei
- Funded7
- SuperFunded
- FTM
- The5ers Summer 200K

It also contains a blanket commercial statement:
`掲載コードは有効です`
and per-Firm labels such as `有効・運営者確認済み`.

## 1. Fintokei payout scope

Previously triple-checked and revalidated against current English FAQ structure:
- first reward timing: 14 days from first virtually-funded trade where applicable
- SwiftTrader cohort distinctions must not be confused with evaluation minimum days
- current SwiftTrader post-2026-07-15 conditions have separate minimum-profit-per-payout rules

Result:
`NO NEW CORRECTION FROM WAVE21`

## 2. Funded7 payout scope

Check 1 — current English payout FAQ
`https://funded7.com/faq/payouts-at-funded7-fast-flexible-and-secure/`
- payout frequency: every7 days from account creation / prior withdrawal
- minimum amount after profit split: $100
- monthly maximum: $10,000 per client

Check 2 — current English Rule1 FAQ
`https://beta.funded7.com/faqs/trading-rules/rule-1-consistency-the-gateway-to-pro/`
- minimum10 closed trades
- minimum3 active trading days
- other statistical/QC payout criteria

Check 3 — current English NEO cap FAQ
`https://beta.funded7.com/faqs/challenges/neo-plan-monthly-payout-cap-expansion-rules/`
- baseline global monthly cap $10,000
- qualifying NEO account can expand its own following-month capacity to $12,000 under stated conditions

Result:
`TRIPLE_VERIFIED_WITH_RULE1_COMPLEXITY`

Public summary is directionally correct but `Rule1` should remain visibly linked to full criteria; do not reduce Rule1 to only 10 trades +3 days.

## 3. SuperFunded minimum payout

Current public route says:
`公式FAQでは全プラン共通の最低申請額を確認できませんでした。`

This is overly conservative because current governing official Rules state a clear minimum.

Check 1 — current Rules and Conditions V2.0 dated2026-01-29
`https://superfunded.com/wp-content/uploads/2026/01/SuperFunded-Rules-and-Conditions.pdf`
- Minimum Payout: $100
- profit share is applied before minimum threshold check
- Payout Waiting Period:14 days

Check 2 — official Rules V1 2025-09
- Minimum Payout: $100

Check 3 — official Rules V1 2025-07
- Minimum Payout: $100

Fresh current V2 remains accessible and no current official product-specific override was identified in this audit.

Result:
`TRIPLE_VERIFIED_CURRENT_RULE / UPDATE_REQUIRED`

Safe public wording:
`最低申請額：利益配分適用後$100（現行Rules V2.0）。プラン固有の購入条件・Add-onは申請前に確認。`

Do not characterize current FAQ omission as absence of an official minimum.

## 4. FTM payout scope

Check 1 — current English minimum-days FAQ
`https://fundedtradermarkets.com/faq/is-there-a-requirement-for-a-minimum-number-of-trading-days`
For Nitro /2-Step Plus simulated-funded payout:
-5 qualifying days
- each >=0.5% profit

Check 2 — current English minimum withdrawal FAQ
`https://fundedtradermarkets.com/faq/is-there-a-required-minimum-amount-for-withdrawal-requests`
- minimum simulated profit =1% of Initial Balance

Check 3 — current English 24h guarantee official surfaces
Current homepage + official payout-guarantee FAQ support:
- on-demand when criteria met
-24-hour business-window guarantee
- double-requested-reward + free same-size account if eligible and late
- guarantee maximum payout amount $1,000
- third-party-method response conditions apply

Result:
`TRIPLE_VERIFIED_WITH_GUARANTEE_SCOPE`

Public wording `$1,000以下など適用条件あり` is appropriately cautious.

## 5. The5ers Summer 200K

No deletion/change instruction exists.
The route's current availability is asserted by the site operator/user.

The current English static Summer landing surface remains100K-led, while the purchase flow is dynamic and not fully extractable by the crawler.

Therefore:
- do not remove the Summer200K block
- do not rewrite to100K-only
- do not treat static absence as negative evidence
- detailed200K payout values remain `OFFICIAL_DYNAMIC_SOURCE_RECHECK_PENDING` before any future rewrite

Status:
`DO_NOT_CORRECT_FROM_CRAWLER / DETAILED_DYNAMIC_SOURCE_RECHECK_REQUIRED`

## 6. Blanket code-validity claim

Current route says:
`掲載コードは有効です`

Under the retrospective minimum-three-check standard, this wording is stronger than the currently retained public evidence record for every exclusive/operator-issued code.

Important:
- lack of public search result is NOT evidence that a partner code is invalid
- operator confirmation is legitimate evidence but should be retained as Evidence Packet
- each code's exact effect/scope can change independently

Status:
`EVIDENCE_BACKFILL_REQUIRED / DO_NOT_INVALIDATE_CODES`

Safer site-level wording until each code has retained current evidence:
`掲載コードは運営者が有効性を確認したものです。割引率・対象・併用可否・最終適用は購入画面で再確認してください。`

For exact effects such as `+10% split`, exact discount percentage, new-only/existing scope, or expiry:
- current checkout OR
- partner portal OR
- direct official partner confirmation
must be captured and then fresh-rechecked.

## 7. CTA compliance

The payout route already distinguishes some `公式の出金条件を確認` and `始める` links better than Home.
Post-auth implementation must still verify actual href targets:
- official-source CTA -> clean official URL
- commercial CTA -> affiliate/referral URL + nearby PR disclosure

## 8. Final

Production change: NONE

Final Status:
`WAVE21_COMPLETE_SUPERFUNDED_MINIMUM100_UPDATE_READY_CODES_REQUIRE_EVIDENCE_BACKFILL_NO_INVALIDATION`
