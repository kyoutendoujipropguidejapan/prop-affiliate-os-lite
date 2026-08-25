# PLATFORM RESEARCH FACT PACK — MetaTrader 5

更新日：2026-08-26 JST
Status：CONTENT_RESEARCH_READY
Production code changes：NONE

## 1. Canonical

- Platform name：MetaTrader 5
- Canonical ID：`mt5`
- Future route：`/platforms/mt5/`
- Vendor：MetaQuotes

## 2. Official-source facts

MetaQuotes公式情報で確認できる一般仕様：

- Desktop / Web / iOS / Androidの提供がある。
- Web platformはブラウザから利用できる。
- MobileはiOS / Androidに対応する。
- MT5はnetting / hedgingの2つのposition accounting systemをサポートする。
- Market Depthを備える。
- DesktopではMQL5によるalgorithmic trading / Expert Advisor環境を持つ。
- Web / Mobile / Desktopの利用可能機能は同一とは限らないため、surface別に説明する。

## 3. Official references

- https://www.metatrader5.com/en/trading-platform
- https://www.metatrader5.com/en/trading-platform/web-trading
- https://www.metatrader5.com/en/mobile-trading
- https://www.metatrader5.com/en/download

## 4. Public-page safe angle

初心者向けには次を中心に説明する。

- MT5とは何か
- Desktop / Web / Mobileの違い
- 注文・チャート・Market Depthの基本
- EA / MQL5は主にDesktop側の概念として説明
- Firmによってsymbols / server / permissions / execution / market dataが異なること
- MT5一般仕様とFirm固有仕様を分離

## 5. Firm-specific caution

次はFirm × Platform Evidenceなしに断定しない。

- 利用可能銘柄
- server / connection
- order / execution configuration
- EA可否
- copy trading可否
- news / weekend等のFirm rule
- DOM / data entitlement
- latency / execution quality

## 6. Compliance

禁止：

- MT5だから約定が速い／安全／有利という一般化
- MT5対応だから日本から利用可能という推論
- Platform一般機能を各Firmで利用可能と断定
- Platform利用が利益・合格・出金を保証する表現

Required disclaimer concept：

`MetaTrader 5の一般機能と、各プロップファームで実際に利用できる機能・銘柄・注文環境・口座仕様は異なる場合があります。利用前に各ファームの最新条件をご確認ください。`

## 7. Readiness

- General official research：READY
- Japan-specific vendor UI/documentation scope：PREPUBLICATION_RECHECK
- Firm × MT5 mapping：PENDING CURRENT PRODUCTION RECONCILIATION
- Production implementation：HOLD UNTIL PLATFORM PHASE

Final Status：

`MT5_CONTENT_RESEARCH_READY`
