# PLATFORM PILOT PREIMPLEMENTATION SPEC

更新日：2026-08-26 JST
Status：PREIMPLEMENTATION_ONLY
Production code changes：NONE

Purpose：Firm Detail rollout後にPlatform Pilotへ移行する際、Workに設計判断を残さないための事前仕様。現時点では実装開始しない。

## 1. Entry Gate

Platform Pilotは以下完了後のみ開始：
- Git/internal auth blocker解消
- pending accepted commits処理完了
- Current Production reconciliation PASS
- Fundora/Fintokei Firm Detail Pilot PASS
- Firm Detail rolloutの少なくとも初回Wave安定
- Master / Diagnosis / GA4 protected state確認
- 9 platform canonical scope確認

MT4 / MT5 scopeはCentral Command承認済み：
`docs/PLATFORM_ARCHITECTURE_DECISION_MT4_MT5_2026-08-26.md`

## 2. Pilot scope

最小構成：
- `/platforms/` Hub
- 1 platform detail route
- 1 second platform detail route（workflow差を検証するため）
- Platform → verified Firm relation display
- disclaimer / verification status
- SEO / mobile / regression tests

初回から9 platformすべてを実装しない。

## 3. Candidate content

公式一次情報Research Pack作成済み：
- MetaTrader 5
- MetaTrader 4
- TradeLocker
- cTrader
- Match-Trader
- DXtrade
- BlackArrow
- Quantower
- Volumetrica

全9 Platformでgeneral content researchはREADY。

Pilot 1 / Pilot 2はCurrent Production reconciliation後のverified Firm mappingと利用価値で決定する。Research完了順や好みだけで自動選定しない。

## 4. Data boundary

New Platform RegistryはMasterと分離。

Required conceptual layers：
- Platform Registry
- Platform Variant（必要時）
- Firm × Platform Relation
- Connection
- Execution
- Market Data
- Data Entitlement

ただしPilotでは将来要件だけのために全Layerを過剰実装しない。

## 5. Firm relation boundary

Firm一覧に出せるのはCurrent Production / official Evidenceで確認済みmappingのみ。

禁止：
- plan display stringだけから複雑なconnection仕様を推測
- catalog外Firm追加
- Program mappingの推測
- platform一般機能をFirm固有機能として表示
- Vendor-level EA / copy / DOM capabilityをFirm permissionとして扱う

## 6. Page structure

Hub：
1. Platformとは
2. Platformを比較する時に見るポイント
3. Verified platform cards
4. Firmによって違う点
5. Beginner glossary
6. related Firm pages
7. disclaimer / checked date

Detail：
`PLATFORM_DETAIL_CONTENT_CONTRACT_2026-08-26.md` に従う。

## 7. Compliance

- vendor marketing wordingを本サイト評価へ昇格しない
- performance / latency / execution superiorityをEvidenceなしで比較しない
- Platform自体が利益・合格・出金を保証するような表現禁止
- Japan availabilityとFirm eligibilityを混同しない
- Firm-specific execution / market-dataを一般仕様と分離
- EA / algorithmic / copy機能の可否はFirm ruleを別確認
- Platform vendorとBroker / Prop Firm / Exchange / Liquidity Providerの役割を混同しない

## 8. SEO

Pilot public前：no index / sitemap非掲載を許容。

Publish Gate後：
- unique title
- unique meta
- self canonical
- one H1
- Hub/detail internal linking
- duplicate content check

## 9. Analytics

将来候補：
- platform_view
- platform_compare
- platform_firm_matrix_open

Pilot実装時も既存GA4 dispatcher以外を使用しない。

## 10. Test requirements

- registry schema/type validation
- 9 canonical IDs validation
- unknown preservation
- Firm mapping allow-list behavior
- route render
- self canonical
- no catalog-outside Firm leakage
- no Diagnosis impact
- no Master mutation
- no Affiliate ranking impact
- no PII analytics
- 390px no overflow

## 11. Rollout

P0：Hub + detail 1 + detail 2 OFF / preview
P1：QA
P2：Platform Pilot publish
P3：stability observation
P4：remaining detail rollout preparation
P5：incremental expansion

## 12. Stop conditions

- canonical scope unexpectedly differs from approved 9 IDs
- current Firm mapping cannot be verified
- Master rewrite becomes necessary
- Diagnosis changes become necessary
- content requires unsupported performance claim
- route conflict
- mobile overflow not resolved without large refactor

Final preimplementation status：
`PLATFORM_PILOT_SPEC_PREPARED_ALL_9_RESEARCH_READY_NOT_AUTHORIZED_TO_IMPLEMENT`
