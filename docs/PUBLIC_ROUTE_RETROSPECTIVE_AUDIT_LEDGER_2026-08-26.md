# PUBLIC ROUTE RETROSPECTIVE AUDIT LEDGER

更新日：2026-08-26 JST
Status：ACTIVE / AUTH-RECOVERY RECONCILIATION REQUIRED FOR COMPLETION
Purpose：途中・未観測・監査済みrouteを一か所で追跡し、再開漏れを防ぐ。

## 0. Rules

- `AUDITED` = 対象routeの重要Factを3-check基準で監査済み。全ページ全Factが永久にVerifiedという意味ではない。
- `PARTIAL` = 一部重要項目のみ監査済み。
- `PUBLIC_NOT_OBSERVED` = current crawler/indexで確認できなかっただけ。未実装・削除・404を意味しない。
- `PRODUCTION_RECONCILIATION_REQUIRED` = internal Sites repo/auth復旧後にactual source/route/sitemap/browserで確定する。

## 1. Accessible / audited public routes

| Route / Surface | Status | Main audit |
|---|---|---|
| `/` Home | `PARTIAL_HIGH_RISK_AUDITED` | Firm cards, codes, CTA separation, service nature, selected current-plan corrections, Blue Guardian Japan eligibility, The5ers100K current-pick freshness |
| `/prop-firm-payout-comparison` | `AUDITED_HIGH_RISK` | payout conditions, SuperFunded minimum, code-evidence wording, Summer200K protection |
| `/pay-after-pass-payg` | `AUDITED_HIGH_RISK` | Funded7 PAYG, Trading Cult PAP, FundedElite Flash |
| `/one-step-two-step-instant` | `AUDITED_STRUCTURE` | FTMO/Fintokei/Funded7/FTM/TradingCult/FundedElite evaluation structure |
| `/funded-trader-markets` | `AUDITED_HIGH_RISK` | current program count, Nitro X, Instant Pro conflict |
| `/the5ers-summer-plan` | `PARTIAL / DO_NOT_REMOVE_200K` | static-vs-dynamic availability boundary; detailed200K fresh dynamic-source check still pending |
| `/beginner-guide` | `PARTIAL_AUDITED` | service-nature/general educational wording |
| `/articles/minimum-trading-days` | `AUDITED_GENERIC_FRAME` | generic article supported; future named examples need fresh checks |
| `/articles/news-trading-rules` | `AUDITED_GENERIC_FRAME` | generic article supported; stage/plan differences preserved |

## 2. Content scopes audited even where current public route is not reliably observed

### Fintokei Free Trial scope — Wave24
Status:
`CONTENT_FACTS_AUDITED / PRODUCTION_ROUTE_RECONCILIATION_REQUIRED`

Current official scope:
- English general/top-level programs:4 × up to2 =8
- Japan current listed plan variants including Slim:5 ×2 =10

If any Japan-facing Production route says unqualified `最大8回`, enqueue scope-aware correction after source inspection.

### Fintokei Academy — Wave25
Status:
`CONTENT_FACTS_AUDITED / PUBLIC_NOT_OBSERVED / PRODUCTION_ROUTE_RECONCILIATION_REQUIRED`

Verified current core facts:
- Japan-only current availability
- Learn / Drills / simulated Trade / Analytics / Roadmap
- app-specific XP / levels / milestones / rewards
- simulation-based trading

Governance:
- Academy XP and MyFintokei Loyalty XP are not merged without explicit future official evidence
- universal Academy-completion ->50% Challenge discount remains evidence-required/HOLD

## 3. Planned/source-known routes not reliably observed in current public crawler

The following are present in Handoff content/SEO planning but current public search/crawl did not reliably expose them in this audit session.

Status for all below:
`PUBLIC_NOT_OBSERVED / PRODUCTION_RECONCILIATION_REQUIRED`

- `/articles/max-drawdown`
- `/articles/static-drawdown`
- `/articles/trailing-drawdown`
- `/articles/eod-drawdown`
- `/articles/prop-firm-free-trial`
- `/articles/weekend-holding-rules`
- `/articles/prop-firm-disqualification-rules`
- other M09/M09B article-route variants where slug between planning and Production may differ
- any Fintokei Academy dedicated route if present in Production but not observable in current crawler

Important：
Do not say these routes are absent from Production until actual Production source + sitemap + browser are checked.

## 4. Known public/content surfaces requiring further route-level audit

### P0 after source access
- Home exact current Firm/Plan count and rendered version
- Home all current Firm-card facts after actual source reconciliation
- Home special-code actual current values + Evidence backfill
- Fintokei dedicated/current surfaces including Free Trial / Academy if present in Production
- all FAQ answers containing Firm-specific current numeric facts

### P1
- all coupon/campaign history entries
- first-purchase benefit route/content
- price-history route/content
- remaining Firm-specific articles
- all source-link destinations and affiliate-vs-official separation
- Academy current CTA/reward claims and any in-app benefit claims

### P2
- beginner/general articles without named current numeric facts
- metadata/freshness labels
- internal-link integrity and canonical/sitemap

## 5. Mandatory post-auth route inventory

When internal Git authentication is restored, Work must read-only enumerate before any new feature implementation:

1. actual Production route source
2. sitemap routes
3. current canonical URLs
4. Home actual current Firm/Plan counts
5. all `/articles/*`
6. all Firm/current dedicated routes
7. all campaign/coupon/history routes
8. all FAQ/schema blocks
9. all Affiliate CTA href targets
10. all official-source href targets
11. any Academy/Free-Trial routes/content
12. all page/section freshness metadata

Compare this list to the ledger.
Any route found but not audited -> enqueue.
Any planned route not present -> classify only after source confirmation.

## 6. Real-world QA still unfinished

Separate from factual audit:
- actual iPhone Safari390px production rendering
- CTA-level PR disclosure visibility
- GA4 real-send verification without PII
- cache/render divergence check against actual browser

These remain post-auth / browser-access gates and are not treated as completed by static crawler review.

## 7. Other intentionally paused streams

Not forgotten:
- Firm Detail Pilot -> after reconciliation/corrections
- Platform -> after Firm foundation
- Payout -> exact source ZIPs required, strict HOLD
- M15 Monitoring -> later Evidence phase, currently not active

Final Status：
`ROUTE_LEDGER_ACTIVE_THROUGH_WAVE25_NO_UNOBSERVED_ROUTE_TREATED_AS_MISSING`
