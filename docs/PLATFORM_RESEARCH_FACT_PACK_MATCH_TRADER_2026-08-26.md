# PLATFORM RESEARCH FACT PACK — Match-Trader

更新日：2026-08-26 JST
Status：CONTENT_RESEARCH_READY
Production code changes：NONE

## 1. Canonical

- Platform name：Match-Trader
- Canonical ID：`match-trader`
- Future route：`/platforms/match-trader/`
- Vendor：Match-Trade Technologies

## 2. Official-source facts

公式Documentation / product informationで確認できる一般仕様：

- Web / mobile / desktop application構成として案内されている。
- Platform overviewではmarket watch、chart workspace、order management、basic / advanced order options、account information、open positions、trade history等が説明されている。
- PWA technologyを使ったmobile-focused accessが案内されている。
- 2026 release notesではJapaneseを含む複数言語のtranslation engine追加が案内されている。
- TradingView chart integrationがrelease notesで確認できる。
- Prop向けsolution / dashboardが別系統で存在し、通常のgeneral platform説明とProp Firm固有設定を分離する必要がある。

## 3. Official references

- https://docs.match-trade.com/docs-category/match-trader/
- https://docs.match-trade.com/docs/match-trader-platform-overview/
- https://docs.match-trade.com/docs/match-trader-trading-platform/
- https://docs.match-trade.com/docs/release-notes-match-trader/
- https://match-trade.com/products/

## 4. Public-page safe angle

- Match-Traderとは何か
- Web / mobile / desktop workflow
- chart / market watch / order managementの基本
- PWA型accessの考え方
- Japanese language capabilityはvendor-levelで説明し、各Firmでの表示範囲を別確認
- Prop-specific dashboard / rule configurationと一般Platform機能を分離

## 5. Firm-specific caution

Firm × Platform Evidenceなしに断定しない：

- symbols
- leverage / swap / commission
- order / execution configuration
- TradingView availability
- copy trading availability
- Japanese UI exposure
- Prop dashboard features
- payout / challenge configuration
- server / connection

## 6. Compliance

Vendorの「high-tech」「best experience」等のmarketing wordingを本サイト評価へ変換しない。

Required disclaimer concept：

`Match-Traderの一般機能と、各プロップファームで実際に有効な機能・表示言語・注文条件・口座仕様は異なる場合があります。利用前に各ファームの最新条件をご確認ください。`

## 7. Readiness

- General official research：READY
- Japanese vendor-language capability：VERIFIED_VENDOR_LEVEL / FIRM_LEVEL_RECHECK
- Firm × Match-Trader mapping：PENDING CURRENT PRODUCTION RECONCILIATION
- Production implementation：HOLD UNTIL PLATFORM PHASE

Final Status：
`MATCH_TRADER_CONTENT_RESEARCH_READY`
