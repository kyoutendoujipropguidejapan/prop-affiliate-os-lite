# INTEGRATION_ROADMAP_2026-08-26

用途：既存Productionへ新成果物を安全に統合するための総合ロードマップ。

## 1. Current Principle

既存Productionを作り直さない。
既存成果物を最大限再利用する。
新機能は独立Release Trainで段階導入する。

最終構造：

Current Production
→ Firm Detail
→ Platform
→ Payout
→ Firm × Platform × Payout cross-linking

## 2. Immediate Blocker Track

新機能より先に以下を完了する。

1. `git.chatgpt-team.site` authentication recovery
2. Evidence accepted local commit remote確定
3. Fundora accepted local commit remote確定
4. Fundora campaign Production handling
5. Current Production reconciliation
6. clean baseline確定

このTrackが完了するまで新しいProduction実装を開始しない。

## 3. Firm Detail Track

Phase FD0：Chat/GitHub handoff specification（完了）

- Compliance Baseline
- Content Contract
- Fundora/Fintokei Pilot Spec
- 14 Firm Rollout Matrix

Phase FD1：Pilot implementation

- `/firms/fundora/`
- `/firms/fintokei/`

Phase FD2：Pilot QA

- regression
- build/lint
- compliance
- SEO
- 390px
- actual iPhone

Phase FD3：Wave rollout

- Wave 1 → QA
- Wave 2 → QA
- Wave 3 → QA

## 4. Platform Track

Firm Detail安定後に開始。

将来対象：

- `/platforms/`
- `/platforms/compare/`
- `/platforms/tradelocker/`
- `/platforms/ctrader/`
- `/platforms/match-trader/`
- `/platforms/dxtrade/`
- `/platforms/blackarrow/`
- `/platforms/quantower/`
- `/platforms/volumetrica/`

Canonical Platform：

- tradelocker
- ctrader
- match-trader
- dxtrade
- blackarrow
- quantower
- volumetrica

既存 `planCatalog.platforms` はDisplay String Layerとして保護。

Platform Registry / Firm × Platformは別Layer。

Firm Detail内でPlatform Registryを先行再構築しない。

## 5. Payout Track

Source Archive不足中はProduction実装をHOLDする。

不足Source：

- P00R-PROP-PAYOUT-JOURNEY-source.zip
- P01-PROP-PAYOUT-METHODS-source.zip
- P10-PAYOUT-ROUTE-DB-source.zip

Status：`SOURCE_REQUIRED`

Source到着前：

- Route DB生成禁止
- Web代替禁止
- Summaryからrecord生成禁止
- descriptorからrecord生成禁止
- Production skeleton先行追加も原則行わない

Source到着後：

1. Source verification
2. R1 Data Pack
3. Data Acceptance
4. Payout integration OFF
5. QA
6. Feature ON decision

将来Route例：

- `/payout/`
- `/payout/methods/`
- `/payout/routes/`
- `/payout/providers/{provider}/`

## 6. Cross-Link Track

Firm / Platform / Payoutが独立安定後に接続する。

Entity relations：

- Firm → Plan
- Firm → Platform
- Firm → Payout Method
- Firm → Payout Provider
- Firm → Payout Route
- Platform → Firms
- Provider → Firms / Routes

Affiliate情報をEntity mappingやsearch orderへ影響させない。

## 7. Protected Boundaries

保護対象：

- DiagnosisLogicV2
- 7問 / 質問順
- score / eligibility / ranking
- Masterの意味・境界
- Affiliate / Commission / Coupon / Priceの診断非介入
- existing GA4 initialization
- Unknown preservation
- Conflict preservation

## 8. Compliance

全Trackで `COMPLIANCE_BASELINE_V1_2026-08-26.md` を共通Gateとして使用する。

免責は後付けではなく、Disclosure / Fact separation / Status / Claim / Analyticsまで含めた設計要件とする。

## 9. Release Principle

Firm / Platform / Payoutを同時に大規模公開しない。

原則：

1 module
→ QA
→ release
→ stability check
→ next module

問題発生時にModule単位でrollback可能な状態を維持する。

## 10. Current Next Action

Production実装前に必要な設計はFirm Detail Pilotまで準備済み。

次のProduction作業は、Immediate Blocker Track完了後のFirm Detail Pilotのみ。

Platformはその後。
PayoutはSource到着後。
