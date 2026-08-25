# FIRM DETAIL PROGRAM INDEX

Date: 2026-08-26 JST
Status: ACTIVE HANDOFF INDEX
Production code changes: NONE

Purpose: Single reading order for Work/Codex/AI before any Firm-detail implementation.

---

# Read order

1. `docs/CURRENT_STATE.md`
   - Handoff snapshot only. Reconcile with actual current Production before implementation.

2. `docs/COMPLIANCE_BASELINE_V1_2026-08-26.md`
   - Shared compliance/disclosure/claims/privacy baseline.

3. `docs/FIRM_DETAIL_CONTENT_CONTRACT_2026-08-26.md`
   - Shared Firm-detail information architecture and data boundaries.

4. `docs/M11_FIRM_FAQ_CONTENT_PACK.md`
   - Existing 14-Firm FAQ content source.

5. `docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md`
   - Verified implementation extraction and FAQ PASS/CAUTION/UPDATE/HOLD decisions.

6. `docs/FIRM_DETAIL_PILOT_IMPLEMENTATION_SPEC_2026-08-26.md`
   - Fundora + Fintokei pilot implementation spec.

7. `docs/FIRM_DETAIL_RELEASE_GATE_V1_2026-08-26.md`
   - Mandatory QA/compliance/release gate.

8. `docs/FIRM_DETAIL_WAVE1_CONTENT_SPEC_2026-08-26.md`
   - FTM / Blueberry Futures / Trading Cult Pro / SuperFunded.

9. `docs/FIRM_DETAIL_WAVE2_WAVE3_PREP_2026-08-26.md`
   - Remaining Firm pre-implementation preparation.

10. `docs/FIRM_DETAIL_ROLLOUT_MATRIX_2026-08-26.md`
    - Rollout sequencing.

11. `docs/FIRM_PLATFORM_PAYOUT_ENTITY_LINKING_CONTRACT_2026-08-26.md`
    - Future Firm ↔ Platform ↔ Payout relation contract.

12. `docs/INTEGRATION_ROADMAP_2026-08-26.md`
    - Broader integration order after Firm detail foundation.

---

# Current implementation policy

Do not implement all 14 Firm pages in one release.

Required progression:

1. Reconcile actual current Production.
2. Complete pending accepted release work first.
3. Implement Fundora + Fintokei pilot only.
4. Run full release gate.
5. Accept/reject pilot.
6. Implement Wave 1 only after pilot acceptance.
7. Re-read current Production and primary evidence before each later wave.

---

# Non-negotiable boundaries

Do not change merely for Firm-detail rollout:

- DiagnosisLogicV2
- 7 questions/order
- score
- eligibility
- ranking
- master-data structure
- affiliate influence on diagnosis/ranking
- GA4 initialization
- payout real-data source gate
- Platform mappings not yet verified

Do not infer missing values for visual completeness.

---

# Compliance rule

Every Firm page must pass the shared release gate.

Commercial disclosure, fact/opinion separation, claim control, current-status labeling, privacy, and service-nature accuracy are release requirements, not optional editorial polish.

---

# Future architecture

Firm pages become the primary entity hub.

Later:

Firm ↔ Trading Platform ↔ Payout

Relations are added only through separately accepted registries/mappings and must not be flattened into the existing Production Master for convenience.

---

# Stop rule

If Work finds a mismatch between this Handoff and current Production, current Production/newer accepted evidence wins unless Central Command explicitly decides otherwise.

Return unresolved conflicts rather than guessing.

Status:

`FIRM_DETAIL_PROGRAM_HANDOFF_READY`
