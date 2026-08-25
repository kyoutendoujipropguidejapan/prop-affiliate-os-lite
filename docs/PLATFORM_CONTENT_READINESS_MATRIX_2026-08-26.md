# PLATFORM CONTENT READINESS MATRIX

更新日：2026-08-26 JST
Status：PLANNING / CONTENT READINESS
Production code changes：NONE

Purpose：将来のPlatform Hub / Platform Detail実装に向けて、9 canonical platformのContent / Evidence / Firm Mapping / Production readinessを分離して管理する。

## 1. Readiness definitions

- `CONTENT_RESEARCH_READY`：公式一次情報Research Packがあり、一般説明候補を作成可能
- `FIRM_MAPPING_PENDING`：Current Production reconciliation後にFirm × Platform mapping確認が必要
- `IMPLEMENTATION_HOLD`：Firm Detail foundationより前にはProduction実装しない
- `PREPUBLICATION_RECHECK`：公開直前にvendor / Japan-specific scope等のfresh再確認が必要

## 2. Matrix

| Platform | Canonical ID | Content Research | Firm × Platform Mapping | Route | Production |
|---|---|---|---|---|---|
| MetaTrader 5 | mt5 | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| MetaTrader 4 | mt4 | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| TradeLocker | tradelocker | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| cTrader | ctrader | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| Match-Trader | match-trader | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| DXtrade | dxtrade | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| Blackarrow | blackarrow | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| Quantower | quantower | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| Volumetrica | volumetrica | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |

## 3. Confirmed shared rules

- `planCatalog.platforms` はDisplay String Layerとして保護
- Platform RegistryをMasterへflattenしない
- Firm × Platform relationはEvidence確認後のみ
- general platform capability ≠ Firm-enabled capability
- Unknownをunsupportedへ変換しない
- Platform availability ≠ Japan eligibility
- Japanese UI/documentation ≠ Firm Japanese support
- Vendor marketing claimsを本サイトの比較評価へそのまま変換しない
- EA / algorithmic / copy機能はVendor-level capabilityとFirm permissionを分離する

## 4. Canonical scope decision

Central CommandによりMT5 / MT4の追加を承認済み。

Canonical IDs：
- mt5
- mt4
- tradelocker
- ctrader
- match-trader
- dxtrade
- blackarrow
- quantower
- volumetrica

Decision record：
`docs/PLATFORM_ARCHITECTURE_DECISION_MT4_MT5_2026-08-26.md`

## 5. Research Pack status

全9 Platformで公式一次情報ベースのResearch Pack作成済み。

- `PLATFORM_RESEARCH_FACT_PACK_MT5_2026-08-26.md`
- `PLATFORM_RESEARCH_FACT_PACK_MT4_2026-08-26.md`
- `PLATFORM_RESEARCH_FACT_PACK_TRADELOCKER_2026-08-26.md`
- `PLATFORM_RESEARCH_FACT_PACK_CTRADER_2026-08-26.md`
- `PLATFORM_RESEARCH_FACT_PACK_MATCH_TRADER_2026-08-26.md`
- `PLATFORM_RESEARCH_FACT_PACK_DXTRADE_2026-08-26.md`
- `PLATFORM_RESEARCH_FACT_PACK_BLACKARROW_2026-08-26.md`
- `PLATFORM_RESEARCH_FACT_PACK_QUANTOWER_2026-08-26.md`
- `PLATFORM_RESEARCH_FACT_PACK_VOLUMETRICA_2026-08-26.md`

## 6. Initial pilot candidates

Content research自体は9 PlatformすべてREADY。

Pilot実装順はCurrent Production reconciliation後に以下を確認して決定する：
- current Firm usage breadth
- verified Firm mappings
- user value
- content differentiation
- route conflict
- mobile QA cost

Current implementation principle：
1. `/platforms/` Hub
2. verified usage breadthが高い1 page
3. workflowが異なる2 page目
4. QA
5. incremental rollout

MT5を必ずPilot 1にするとは固定しない。Current Truthを優先する。

## 7. Prepublication recheck

公開前には各Research Packの`PREPUBLICATION_RECHECK`項目と、Firm-specific mappingを再確認する。

特に：
- Match-Trader Japanese language exposure
- DXtrade enabled widgets / delivery type
- BlackArrow asset / connection scope
- Quantower license / connection scope
- Volumetrica server-side feature rollout
- MT4 / MT5 Firm-level EA / copy permission

## 8. Work boundary

Research preparationは完了。

Platform Registry / public routes / sitemap / navigation / GA4のProduction実装はFirm Detail foundation後までHOLD。

Final Status：
`ALL_9_PLATFORM_CONTENT_RESEARCH_READY_IMPLEMENTATION_HOLD`
