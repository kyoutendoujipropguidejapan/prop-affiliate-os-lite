# PLATFORM CONTENT READINESS MATRIX

更新日：2026-08-26 JST
Status：PLANNING / CONTENT READINESS
Production code changes：NONE

Purpose：将来のPlatform Hub / Platform Detail実装に向けて、7 canonical platformのContent / Evidence / Firm Mapping / Production readinessを分離して管理する。

## 1. Readiness definitions

- `CONTENT_RESEARCH_READY`：公式一次情報Research Packがあり、一般説明候補を作成可能
- `CONTRACT_ONLY`：共通Content Contractのみ。個別公式Research未完了
- `FIRM_MAPPING_PENDING`：Current Production reconciliation後にFirm × Platform mapping確認が必要
- `IMPLEMENTATION_HOLD`：Firm Detail Pilotより前にはProduction実装しない
- `SCOPE_DECISION_REQUIRED`：Canonical Registryへの追加・除外などArchitecture判断が必要

## 2. Matrix

| Platform | Canonical ID | Content Research | Firm × Platform Mapping | Route | Production |
|---|---|---|---|---|---|
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

## 4. Initial pilot candidates

Content面ではTradeLocker / cTraderが先行準備済み。

ただし実装順は、Current Production reconciliation後に以下を確認して決定する：
- current Firm usage breadth
- verified Firm mappings
- user value
- content differentiation
- route conflict
- mobile QA cost

Current recommendation：
1. `/platforms/` Hub
2. TradeLocker or cTrader one page
3. materially different second page
4. QA
5. remaining platform rollout

## 5. Important architecture gap discovered

Current canonical platform list contains:
- tradelocker
- ctrader
- match-trader
- dxtrade
- blackarrow
- quantower
- volumetrica

しかし既存Master / project usageではMT5が取引環境として重要なDisplay String / selection contextで扱われている。

MT5を将来のPlatform Registry / Platform Detailのcanonical entityへ追加するかは、この文書では決定しない。

Status：
`MT5_SCOPE_DECISION_REQUIRED`

理由：
- canonical list変更はArchitecture Decision
- route `/platforms/mt5/` の新設可否に影響
- Firm × Platform mapping範囲に影響
- comparison taxonomyに影響
- current preferred platform contextとの整合に影響

## 6. Work boundary

MT5 scope決定前でもTradeLocker / cTraderのResearch Pack作成は可能。

ただしPlatform Registry実装開始前にはMT5 scopeを中央判断で確定する。

Final Status：
`PLATFORM_CONTENT_PREP_CONTINUES_MT5_DECISION_PENDING`
