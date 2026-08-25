# PLATFORM RESEARCH FACT PACK — MetaTrader 4

更新日：2026-08-26 JST
Status：CONTENT_RESEARCH_READY
Production code changes：NONE

## 1. Canonical

- Platform name：MetaTrader 4
- Canonical ID：`mt4`
- Future route：`/platforms/mt4/`
- Vendor：MetaQuotes

## 2. Official-source facts

MetaQuotes公式情報で確認できる一般仕様：

- Desktop / Web / iOS / Androidの利用形態がある。
- Web platformはブラウザから利用できる。
- MobileはiOS / Androidに対応する。
- Desktopはtechnical analysis、trade operations、open position / pending order管理、MQL4によるExpert Advisor・custom indicator・script開発、strategy testingをサポートする。
- Web platformはone-click trading、trade history、technical indicators、real-time quotes等を備える。
- Mobileは主要な注文、チャート、technical analysis、trade history等を提供する。

## 3. Official references

- https://www.metatrader4.com/en
- https://www.metatrader4.com/en/trading-platform
- https://www.metatrader4.com/en/trading-platform/web-trading
- https://www.metatrader4.com/en/mobile-trading
- https://www.metatrader4.com/en/trading-platform/help

## 4. Public-page safe angle

初心者向けには次を中心に説明する。

- MT4とは何か
- Desktop / Web / Mobileの違い
- 注文・チャート・technical analysisの基本
- EA / MQL4は主にDesktop側の概念として説明
- MT4は現在も一部のFirm / providerで使われる可能性があるが、Firmごとの採用状況は別Evidenceで確認する
- MT4一般仕様とFirm固有仕様を分離

## 5. Firm-specific caution

次はFirm × Platform Evidenceなしに断定しない。

- 利用可能銘柄
- server / connection
- order / execution configuration
- EA可否
- copy trading可否
- news / weekend等のFirm rule
- latency / execution quality

## 6. Compliance

禁止：

- MT4だから約定が速い／安全／有利という一般化
- MT4対応だから日本から利用可能という推論
- Platform一般機能を各Firmで利用可能と断定
- Platform利用が利益・合格・出金を保証する表現

Required disclaimer concept：

`MetaTrader 4の一般機能と、各プロップファームで実際に利用できる機能・銘柄・注文環境・口座仕様は異なる場合があります。利用前に各ファームの最新条件をご確認ください。`

## 7. Readiness

- General official research：READY
- Japan-specific vendor UI/documentation scope：PREPUBLICATION_RECHECK
- Firm × MT4 mapping：PENDING CURRENT PRODUCTION RECONCILIATION
- Production implementation：HOLD UNTIL PLATFORM PHASE

Final Status：

`MT4_CONTENT_RESEARCH_READY`
