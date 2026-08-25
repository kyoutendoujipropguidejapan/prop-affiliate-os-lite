# PLATFORM CONTENT READINESS MATRIX

更新日：2026-08-26 JST
Status：PLANNING / CONTENT READINESS
Production code changes：NONE

Purpose：将来のPlatform Hub / Platform Detail実装に向けて、9 canonical platformのContent / Evidence / Firm Mapping / Production readinessを分離して管理する。

## 1. Readiness definitions

- `CONTENT_RESEARCH_READY`：公式一次情報Research Packがあり、一般説明候補を作成可能
- `CONTRACT_ONLY`：共通Content Contractのみ。個別公式Research未完了
- `FIRM_MAPPING_PENDING`：Current Production reconciliation後にFirm × Platform mapping確認が必要
- `IMPLEMENTATION_HOLD`：Firm Detail Pilotより前にはProduction実装しない
- `PREPUBLICATION_RECHECK`：公開直前にvendor / Japan-specific scope等のfresh再確認が必要

## 2. Matrix

| Platform | Canonical ID | Content Research | Firm × Platform Mapping | Route | Production |
|---|---|---|---|---|---|
| MetaTrader 5 | mt5 | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| MetaTrader 4 | mt4 | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| TradeLocker | tradelocker | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| cTrader | ctrader | CONTENT_RESEARCH_READY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| Match-Trader | match-trader | CONTRACT_ONLY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| DXtrade | dxtrade | CONTRACT_ONLY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| Blackarrow | blackarrow | CONTRACT_ONLY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| Quantower | quantower | CONTRACT_ONLY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |
| Volumetrica | volumetrica | CONTRACT_ONLY | FIRM_MAPPING_PENDING | planned | IMPLEMENTATION_HOLD |

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

## 5. Initial pilot candidates

Content面ではMT5 / MT4 / TradeLocker / cTraderが先行準備済み。

ただし実装順は、Current Production reconciliation後に以下を確認して決定する：
- current Firm usage breadth
- verified Firm mappings
- user value
- content differentiation
- route conflict
- mobile QA cost

Current recommendation：
1. `/platforms/` Hub
2. verified usage breadthが高い1 page
3. workflowが異なる2 page目
4. QA
5. remaining platform rollout

MT5を必ずPilot 1にするとはこの段階では固定しない。Firm mappingのCurrent Truthを優先する。

## 6. Remaining research queue

次の公式一次情報Research Packを順次作成する：
- Match-Trader
- DXtrade
- Blackarrow
- Quantower
- Volumetrica

Research完了前に本文を推測生成しない。

## 7. Work boundary

Research PackはChat / Evidence preparationで進めてよい。

Platform Registry / public routes / sitemap / navigation / GA4のProduction実装はFirm Detail foundation後までHOLD。

Final Status：
`PLATFORM_CONTENT_PREP_CONTINUES_9_PLATFORM_SCOPE_CONFIRMED`
