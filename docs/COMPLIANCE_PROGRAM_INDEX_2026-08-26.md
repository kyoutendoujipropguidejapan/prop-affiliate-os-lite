# COMPLIANCE PROGRAM INDEX

更新日：2026-08-26 JST
Status：MANDATORY HANDOFF INDEX
Production code changes：NONE

今後のFirm / Platform / Payout / Campaign / Coupon / Review / Case Study公開作業では、Complianceを後付けにせず次の順で参照する。

## 1. Core

1. `COMPLIANCE_BASELINE_V1_2026-08-26.md`
2. `JAPAN_COMPLIANCE_OFFICIAL_SOURCE_PACK_2026-08-26.md`
3. `COMPLIANCE_ESCALATION_MATRIX_2026-08-26.md`
4. `COMPLIANCE_COPY_LIBRARY_V1_2026-08-26.md`
5. `SITE_WIDE_DISCLOSURE_ARCHITECTURE_2026-08-26.md`

## 2. Firm Detail

6. `FIRM_DETAIL_RELEASE_GATE_V1_2026-08-26.md`
7. `FIRM_DETAIL_CONTENT_READINESS_MATRIX_2026-08-26.md`
8. `FIRM_DETAIL_PREPUBLICATION_VERIFICATION_QUEUE_2026-08-26.md`

## 3. Platform

9. `PLATFORM_PREPUBLICATION_COMPLIANCE_GATE_2026-08-26.md`
10. `PLATFORM_COMPARISON_TAXONOMY_2026-08-26.md`

## 4. Payout

Payout public data is SOURCE_REQUIRED / HOLD. Generic disclaimer designは既存Contractを参照するが、実Route / Firm relationをweb代替sourceから作らない。

## 5. Mandatory stop conditions

次を検知したら通常公開フローを停止する：

- regulatory/legal status断定が必要
- FSA等のwarning signal
- scam/fraud/payout refusal allegation
- security/personal-data incident
- Firm TermsとDirect Contactの重大Conflict
- siteがuser funds / KYC / bank / wallet dataを扱う新機能
- provided/sponsored relationshipを開示できない
- unsupported superiority / guarantee claimを削れない

Return status：
`COMPLIANCE_HOLD`

## 6. Guiding rule

`免責があるから強い表現をしてよい` とは扱わない。

まず本文・CTA・Data / Evidenceを安全にし、その上でDisclosure / Disclaimerを配置する。

Final Status：
`COMPLIANCE_GOVERNANCE_INDEX_CONFIRMED`
