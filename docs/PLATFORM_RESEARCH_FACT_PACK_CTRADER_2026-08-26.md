# PLATFORM RESEARCH FACT PACK — CTRADER

確認日：2026-08-26 JST
Status：RESEARCH_VALIDATED_NOT_PRODUCTION_CANONICAL
Production code changes：NONE

Purpose：将来の `/platforms/ctrader/` 個別ページに使える公式一次情報のResearch Packを作る。Firm固有設定とは分離し、Production Canonicalへの自動反映はしない。

## 1. Official-source findings

### Web access
cTrader公式HelpはcTrader Webをfully functional web versionとして案内し、manual trading / charting機能を提供するとしている。

確認できる主な対応OS / browser例：
- Windows
- macOS
- Chrome OS
- Linux Ubuntu
- Chrome / Firefox / Edge / Safari等

Source：
- https://help.ctrader.com/ctrader-web/

公開時はSystem Requirementsが変更され得るため、細かなversionは固定資産化せずlast checkedを表示する。

## 2. Mobile / desktop family

cTrader公式HelpではWebに加え、Mobile iOS / Android、Windows / Mac系アプリのDocumentationが提供されている。

公式Helpの日本語ページも存在する。

Sources：
- https://help.ctrader.com/trading-with-ctrader/ja/
- https://help.ctrader.com/ctrader-mobile-ios/ja/charting/charts/
- https://help.ctrader.com/ctrader-mobile-android/ja/charting/charts/

注意：日本語Documentationがあることと、各Prop Firmの日本語Supportがあることは別。

## 3. Order types

cTrader Mobile公式Helpで確認できるstandard order types：
- Market
- Limit
- Stop
- Stop Limit

Source：
- https://help.ctrader.com/ctrader-mobile-ios/trade/orders/

Firm側の口座権限・symbol・execution条件と混同しない。

## 4. Charts / position management

公式Helpで確認できる内容：
- open positions / pending orders / SL / TPをchart上に表示
- chartからposition / pending order等を操作できる機能
- indicators / drawing objects
- mobile chartに関するperformance limitationの注記

Sources：
- https://help.ctrader.com/ctrader-mobile-ios/charting/charts/
- https://help.ctrader.com/ctrader-mobile-android/charting/charts/

## 5. Depth of Market (DOM)

cTrader公式Helpでは3種類のDOMを案内：
- Standard DOM
- Price DOM
- VWAP DOM

Price DOM / VWAP DOMでは、公式Help上、注文操作に関する機能も案内されている。

Source：
- https://help.ctrader.com/trading-with-ctrader/depth-of-market/

注意：市場データの深度・提供内容・利用可能性はFirm/Broker側の条件やData Entitlementの影響を受け得るため、Platform一般仕様とFirm固有表示を分離する。

## 6. Interface / Active Symbol Panel

cTrader Web公式HelpではActive Symbol Panelから、order entry、standard DOM、market hours等へアクセスする構成が案内されている。

Source：
- https://help.ctrader.com/ctrader-web/interface/active-symbol-panel/

## 7. Safe beginner-facing summary candidate

公開候補文：

`cTraderは、Web・モバイル・デスクトップ系のアプリから利用できる取引プラットフォームで、チャート上からの注文・ポジション管理や複数の注文方式、Depth of Market（DOM）などの機能が公式に案内されています。ただし、利用できる銘柄、市場データ、注文条件、口座権限などは利用するプロップファームや口座条件によって異なる場合があります。`

## 8. Performance-claim boundary

cTrader公式ページにperformance wordingが存在しても、本サイトでは独立検証なしに以下へ強めない：
- 約定が最速
- latencyが最低
- 他Platformより高速
- slippageが少ない
- 安全性が高い

Vendor marketing claimと、本サイトの比較評価は別。

## 9. Firm-specific boundary

Firm × Platform evidenceが必要：
- symbols
- market data depth
- DOM availability / data quality
- leverage
- order permissions
- server / connection
- execution configuration
- account permissions
- copy / automation constraints

## 10. Compliance copy

`cTraderの一般的な機能と、各プロップファームで実際に利用できる機能・銘柄・市場データ・約定条件等は同一とは限りません。利用前に各ファームの最新の取引環境と口座条件をご確認ください。`

## 11. SEO draft

Route候補：
`/platforms/ctrader/`

Title候補：
`cTraderとは？プロップファームで使う前に知りたい特徴・注文・DOM`

H1候補：
`cTraderとは？プロップファーム利用前に確認したい取引環境`

Meta候補：
`cTraderのWeb・モバイル環境、注文タイプ、チャート、Depth of Market（DOM）と、プロップファームごとに確認したい違いを初心者向けに整理します。`

## 12. Production readiness

Content research：READY_WITH_CAUTION
Firm mapping：PENDING_CURRENT_PRODUCTION_RECONCILIATION
Route：NOT_IMPLEMENTED
Canonical：NOT_CREATED
Sitemap：NOT_ADDED
GA4：NOT_ADDED

Final Research Status：
`CTRADER_CONTENT_RESEARCH_READY`
