# PAYOUT PROVIDER DETAIL CONTENT CONTRACT

Date: 2026-08-26 JST
Status: ARCHITECTURE / CONTENT CONTRACT CONFIRMED
Production code changes: NONE

Purpose: Define future individual payout-receiving service/provider pages while preserving the current SOURCE_REQUIRED gate for payout route data.

---

# 1. Source gate

This document defines future page structure only.

It does NOT authorize creation of real payout route/provider records.

Until accepted P00R / P01 / P10 source archives exist:

- no fabricated provider mappings
- no fabricated route chains
- no Firm × provider production mapping
- no public provider page that implies unsupported accepted route data

Payout real-data status remains:

`SOURCE_REQUIRED`

---

# 2. Entity separation

Keep separate:

## Payout Method
How value is paid or transferred.

## Provider / Receiving Service
A service used to receive, hold, transfer, convert, or withdraw value, where supported by accepted evidence.

## Payout Route
The complete end-to-end path from Firm to user endpoint and, where applicable, onward conversion.

Do not treat these as synonyms.

---

# 3. Future routes

Hub candidates:

- `/payout/`
- `/payout/methods/`
- `/payout/providers/`
- `/payout/routes/`

Provider detail route pattern:

- `/payout/providers/{provider-slug}/`

Do not publish these routes until source acceptance and a separate Payout release gate.

---

# 4. Provider page purpose

A provider/service page should answer:

- What type of service is this?
- Where can it appear in a payout flow?
- What must a Japanese user verify before using it?
- Which networks/currencies/regions are relevant where verified?
- Which verified Firms/routes use it?
- What fees/identity requirements may apply where verified?

It must not present a universal guaranteed route.

---

# 5. Shared page structure

1. Breadcrumb / H1
2. Service overview
3. Role in a payout flow
4. Supported asset/currency/network information where verified
5. Japan-specific availability/requirements where verified
6. KYC/identity requirement summary where publicly documented
7. Fees/limits/timing with checked date where verified
8. Security/transfer cautions
9. Verified Firm/route relationships
10. Conversion/withdrawal considerations
11. FAQ
12. Related payout methods/routes
13. Verification status / checked date
14. Disclaimer

Sections with no accepted evidence may be omitted.

---

# 6. Crypto/network safety boundary

For crypto-related routes/providers:

- network name must be explicit where relevant
- do not assume ERC20, Arbitrum, or another network are interchangeable
- do not infer bridge support
- do not infer deposit support at a receiving service
- do not promise recoverability of mis-sent assets

Any example route must be labeled as an example or verified route, never presented as universally valid.

---

# 7. Financial/legal/tax boundary

Provider pages are informational.

Do not make universal claims about:

- tax treatment
- legality
- regulatory classification
- bank reporting
- guaranteed settlement
- guaranteed conversion rate
- guaranteed transfer timing

Where such matters materially affect users, route to official provider documentation and appropriate professional advice rather than infer conclusions.

---

# 8. Japan-specific boundary

Keep separate:

- service availability in Japan
- Japanese UI
- Japanese customer support
- JPY support
- withdrawal to a Japanese bank
- regulatory/legal status

One does not prove another.

---

# 9. Fees / timing

Fees, minimums, limits, and processing times are time-sensitive.

Each displayed value requires:

- source
- verified/check date
- scope (method/network/region where relevant)

Avoid broad wording such as “free”, “instant”, or “same day” unless the exact scope and conditions are supported.

---

# 10. Firm relation boundary

A provider may appear on a provider detail page before any Firm relation is published only if the page is independently supported and release-approved.

However, do not list a Firm as using that provider until an accepted Firm × Payout relation exists.

Commercial relationships/affiliate status must not influence relation verification.

---

# 11. Privacy / analytics

Never send to GA4 or store in public page telemetry:

- wallet address
- bank account number
- recipient name
- personal KYC result
- transaction hash tied to an identifiable user
- payout account identifier

Future analytics may record only non-PII content interactions after separate approval.

---

# 12. Required disclaimer concept

`掲載している出金方法・受取サービス・経路は、対応地域、手数料、ネットワーク、本人確認条件、提供状況などが変更される場合があります。送金・受取前にプロップファームおよび各サービスの最新公式情報をご確認ください。`

For crypto-related content, add a network-specific warning when relevant.

---

# 13. Initial implementation strategy

Do not build provider detail pages before source acceptance simply because page templates can be coded safely.

Recommended order after source arrival:

1. Accept source archives
2. Build R1 Data Pack
3. Accept Payout data
4. Confirm entity model
5. Build Payout Hub
6. Pilot one Method page and one Provider page
7. QA / compliance / mobile
8. Add accepted Firm × Payout relations
9. Expand provider pages
10. Add Route pages last

---

# 14. Acceptance

No implementation may bypass:

- SOURCE_REQUIRED gate
- Evidence provenance
- Firm × Payout relation acceptance
- privacy restrictions
- compliance review

Final architecture status:

`PAYOUT_PROVIDER_DETAIL_CONTENT_CONTRACT_CONFIRMED`
