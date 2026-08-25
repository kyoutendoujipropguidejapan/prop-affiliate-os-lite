# PLATFORM DETAIL CONTENT CONTRACT

Date: 2026-08-26 JST
Status: ARCHITECTURE / CONTENT CONTRACT CONFIRMED
Production code changes: NONE

Purpose: Define future individual trading-platform pages while keeping Platform data separate from the existing plan display-string layer and from Firm-specific configuration.

---

# 1. Future routes

Hub:
- `/platforms/`

Detail routes:
- `/platforms/tradelocker/`
- `/platforms/ctrader/`
- `/platforms/match-trader/`
- `/platforms/dxtrade/`
- `/platforms/blackarrow/`
- `/platforms/quantower/`
- `/platforms/volumetrica/`

Compare route may be added later:
- `/platforms/compare/`

Do not create public routes until a separate Platform implementation/release gate is approved.

---

# 2. Canonical platform IDs

- tradelocker
- ctrader
- match-trader
- dxtrade
- blackarrow
- quantower
- volumetrica

`planCatalog.platforms` remains a protected display-string layer until separately migrated/accepted.

---

# 3. Page purpose

A Platform detail page should answer:

- What is this trading platform?
- What type of interface/workflow does it use?
- What should a prop-firm user check before choosing a Firm that uses it?
- Which verified Firms use it?
- Which capabilities vary by Firm?

The page must not act as a universal specification sheet for every Firm implementation.

---

# 4. Shared page structure

1. Breadcrumb / H1
2. Platform overview
3. Beginner summary
4. Web / desktop / mobile availability where verified
5. Order-entry / charting / workflow overview
6. Connection / execution concepts
7. Market data / entitlement concepts
8. DOM / advanced features where verified
9. What may differ by Firm
10. Verified Firms using the platform
11. Common checks before purchase
12. FAQ
13. Related Firm pages
14. Verification status / checked date
15. Disclaimer

---

# 5. Firm-specific boundary

Never assume a general platform capability is enabled by every Firm.

The following may vary and require Firm × Platform evidence:

- symbols
- market-data package
- DOM access
- account permissions
- order types
- copy functionality
- server/connection
- execution configuration
- data entitlement

General platform information and Firm-specific configuration must be visually and semantically separated.

---

# 6. Comparison boundary

Platform comparison is educational, not a ranking contest.

Do not create unsupported labels such as:

- best platform
- safest platform
- fastest execution
- lowest latency
- most reliable

unless a defined, current, comparable evidence set exists.

Safer comparison dimensions include verified workflow differences such as:

- browser/app availability
- chart workflow
- order-entry model
- DOM availability where verified
- integration style
- Firm support breadth

---

# 7. Japan-specific content

May include:

- Japanese UI availability where verified
- Japanese documentation availability where verified
- mobile usability notes
- terminology explanation

Do not equate Japanese UI with Japanese Firm support.

Do not equate platform availability with Japan eligibility of a Firm.

---

# 8. SEO

Each detail page should have:

- unique title
- unique meta description
- single H1
- self canonical
- no index until QA/release acceptance

Avoid keyword-stuffed duplicate copy across seven platform pages.

---

# 9. Compliance

Required disclaimer concept:

`同じ取引プラットフォームでも、プロップファームごとに利用可能な機能、銘柄、市場データ、約定環境、口座仕様などが異なる場合があります。実際の利用条件は各ファームの最新情報をご確認ください。`

Do not claim execution quality/performance without evidence.

Do not imply software/platform use itself guarantees trading results.

---

# 10. Analytics boundary

Future approved events may include:

- platform_view
- platform_compare
- platform_firm_matrix_open

Use existing GA4 initialization only. No new `gtag("config")`.

No PII or trading-account identifiers.

---

# 11. Initial pilot strategy

When implementation begins, do not launch all seven pages at once.

Recommended:

1. Platform Hub
2. one verified high-usage platform detail page
3. one second platform with materially different workflow
4. QA / mobile / SEO / relation validation
5. expand to remaining accepted platforms

Exact first platform is decided from current verified Firm mappings at implementation time, not from this document.

---

# 12. Acceptance

Platform detail implementation must preserve:

- Master boundary
- Diagnosis boundary
- Affiliate boundary
- Firm × Platform evidence boundary
- Unknown status
- current Production regression

Final architecture status:

`PLATFORM_DETAIL_CONTENT_CONTRACT_CONFIRMED`
