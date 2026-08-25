# PLATFORM ARCHITECTURE DECISION — MT4 / MT5

更新日：2026-08-26 JST
Status：APPROVED BY CENTRAL COMMAND
Production code changes：NONE

## Decision

将来のTrading Platform canonical registryへ次を正式追加する。

- `mt5` → `/platforms/mt5/`
- `mt4` → `/platforms/mt4/`

これによりcanonical platform familyは9 entityとする。

1. mt5
2. mt4
3. tradelocker
4. ctrader
5. match-trader
6. dxtrade
7. blackarrow
8. quantower
9. volumetrica

## Reason

MT4 / MT5は既存のプロップファーム比較・取引環境説明・Firm × Platform mappingで重要な取引プラットフォームであり、Display Stringだけに残すと将来のPlatform Hub / Detail / cross-link構造に欠落が生じるため。

## Boundaries

- `planCatalog.platforms` は引き続きprotected display-string layer。今回のArchitecture DecisionだけでMasterを書き換えない。
- canonical entity追加はFirm × Platform relationの自動生成を意味しない。
- MT4/MT5を利用するFirmはCurrent Production / official evidenceで個別確認する。
- Firm-level mappingを全Planへ自動展開しない。
- Platform availabilityとJapan eligibilityを混同しない。
- MetaQuotesの一般機能をFirm固有で有効な機能として断定しない。
- Platform利用が利益、合格、出金、約定品質を保証するような表現は禁止。

## Implementation timing

Firm Detail foundationと初回Waveの安定後にPlatform Pilotを開始する。今回の決定だけでpublic route、sitemap、navigation、GA4 eventを追加しない。

Final Status：

`MT4_MT5_CANONICAL_SCOPE_APPROVED`
