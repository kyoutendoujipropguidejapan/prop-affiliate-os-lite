# FIRM / PLATFORM / PAYOUT ENTITY LINKING CONTRACT

Date: 2026-08-26 JST
Status: ARCHITECTURE CONTRACT CONFIRMED
Production code changes: NONE

Purpose: Define the future cross-linking model between Firm detail pages, trading-platform pages, and payout pages without flattening all data into `app/master-data.json`.

---

# 1. Principle

The site will evolve around three independently governed entity families:

- Firm
- Trading Platform
- Payout

Each family has its own source/data boundary.

Do not create one giant merged master object.

---

# 2. Firm entities

Firm pages are the primary user-facing entity hub.

Example:

`/firms/fintokei/`

A Firm page may link to:

- current plans
- verified platform entities
- verified payout methods/providers/routes
- related rules/articles
- current campaigns/coupons

Firm pages must not infer a platform or payout relationship that is not supported by accepted mapping data.

---

# 3. Trading Platform entities

Future canonical platform routes:

- `/platforms/`
- `/platforms/mt5/`
- `/platforms/mt4/`
- `/platforms/tradelocker/`
- `/platforms/ctrader/`
- `/platforms/match-trader/`
- `/platforms/dxtrade/`
- `/platforms/blackarrow/`
- `/platforms/quantower/`
- `/platforms/volumetrica/`

Canonical IDs:

- mt5
- mt4
- tradelocker
- ctrader
- match-trader
- dxtrade
- blackarrow
- quantower
- volumetrica

MT4 / MT5 scope decision:
`docs/PLATFORM_ARCHITECTURE_DECISION_MT4_MT5_2026-08-26.md`

`planCatalog.platforms` remains a protected display-string layer until separately migrated/accepted. It is not automatically the canonical Platform Registry.

---

# 4. Firm × Platform relation

Create a separate relation layer rather than storing platform intelligence inside the Firm master.

Conceptual fields:

- firmId
- platformId
- programId / planId when verified
- relationStatus
- executionNotes
- marketDataNotes
- entitlementNotes
- evidenceRefs
- verifiedAt

Program/plan-level mapping may remain `UNKNOWN` even if Firm-level usage is verified.

Do not promote Firm-level mapping into all plans automatically.

---

# 5. Platform content boundary

A platform page describes general platform characteristics only from accepted evidence.

A Firm page describes how that Firm uses the platform only where separately verified.

Therefore:

`General Platform Capability != Firm-specific Enabled Capability`

Examples of fields that may vary by Firm and must not be generalized:

- symbols
- market-data package
- order types
- DOM access
- EA / algorithmic trading permission
- copy features
- account restrictions
- execution configuration
- server/connection details

---

# 6. Payout entity families

Payout is split into at least three concepts:

## Method

Examples of conceptual method types:

- bank transfer
- e-wallet
- stablecoin / crypto method

## Provider / Receiving Service

Examples may include named services only after accepted source verification.

## Route

A route is the complete movement path from Firm to user-receiving endpoint and, where relevant, onward conversion.

Do not treat Method, Provider, and Route as interchangeable terms.

---

# 7. Firm × Payout relation

Conceptual relation fields:

- firmId
- payoutMethodId
- providerId when applicable
- routeId when accepted
- availabilityStatus
- regionConditions
- feeNotes
- timingNotes
- verificationStatus
- evidenceRefs
- verifiedAt

No relation records may be created from memory, summaries, screenshots without accepted provenance, or inferred similarities with another Firm.

---

# 8. Payout Source Gate

Until required source archives are accepted:

- no real Route DB integration
- no provider-chain fabrication
- no Firm × Route production mapping
- no public Payout entity links that imply accepted route data

Firm pages may show only independently verified Firm-specific payout summary text.

---

# 9. Evidence linkage

Future entity relations should be able to reference Evidence IDs, but Evidence remains a separate governance layer.

Entity relation data must not automatically rewrite Evidence or Canonical Facts.

Likewise, commercial changes must not rewrite verification status.

---

# 10. Commercial boundary

Affiliate, coupon, sponsorship, and commission data must not affect:

- Firm × Platform mapping
- Firm × Payout mapping
- relation status
- verification status
- search order
- diagnosis
- SEO canonical

Commercial CTA is a presentation layer only.

---

# 11. Link activation policy

A public cross-link is enabled only when BOTH sides exist and the relation is accepted.

Examples:

Firm -> Platform page:
- Firm page exists
- Platform page exists
- relation verified/accepted

Platform -> Firm page:
- same requirements

Firm -> Payout Provider/Route:
- Payout entity page exists
- accepted source relation exists

Never create dead-link placeholders in public navigation merely because future architecture reserves a slug.

---

# 12. SEO boundary

Cross-linking is for user navigation and entity clarity, not automatic SEO keyword multiplication.

Each entity page must have its own primary purpose:

- Firm page: understand one Firm
- Platform page: understand one trading platform
- Payout page: understand one method/provider/route

Avoid duplicate copy across these pages.

---

# 13. Compliance boundary

Platform pages:
- do not imply platform availability equals Firm availability
- do not imply software capability equals enabled Firm functionality
- do not infer EA / algorithmic / copy permission from vendor-level features

Payout pages:
- disclose changing fees/regions/network conditions
- do not guarantee transfer success/timing
- do not present tax/legal conclusions as universal facts

Firm pages:
- do not imply Japan availability equals Japanese regulatory approval
- keep PR/affiliate disclosure separate from factual status

---

# 14. Implementation order

Cross-linking is not a standalone first-phase task.

Order:

1. Firm detail foundation
2. Platform Registry + pages
3. Accepted Firm × Platform mappings
4. Payout sources accepted
5. Payout entities/pages
6. Accepted Firm × Payout mappings
7. Cross-link QA
8. Public cross-link enablement

---

# 15. Acceptance rule

No future implementation may collapse these relations into `master-data.json` merely for convenience unless Central Command explicitly approves a new migration design.

Default architecture:

`Separate Registry + Separate Relation + Adapter + Public View`

Final architecture status:

`ENTITY_LINKING_CONTRACT_CONFIRMED_9_PLATFORM_SCOPE`
