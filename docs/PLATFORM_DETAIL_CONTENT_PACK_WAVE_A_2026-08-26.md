# PLATFORM DETAIL CONTENT PACK — WAVE A

更新日：2026-08-26 JST
Status：CONTENT READY / NOT PRODUCTION IMPLEMENTED
対象：MetaTrader 5 / MetaTrader 4 / TradeLocker / cTrader

Firm-specific mappingは含めない。公開実装はPlatform PhaseまでHOLD。

---

# 1. MetaTrader 5

Route：`/platforms/mt5/`

## Intro

MetaTrader 5（MT5）は、MetaQuotesが提供する取引プラットフォームです。デスクトップ、Web、iOS、Android向けの利用方法が案内されており、チャート分析、注文、ポジション管理などを行えます。ただし、プロップファームで利用する場合、対応銘柄やEAの可否、市場データ、注文条件などはFirmごとに異なるため、MT5という名前だけで利用条件を判断しないことが重要です。

## Beginner summary

最初に見るのは次の4点です。

- Desktop / Web / Mobileのどれを使うか
- 注文とchart操作に慣れているか
- Market Depth等の高度機能が必要か
- Firm側でEA / copy / symbols等に制限がないか

## General features

公式情報で確認できる一般仕様：

- Desktop / Web / iOS / Android
- netting / hedging position accounting
- Market Depth
- multiple order types
- DesktopのMQL5 / Expert Advisor environment

## Caution

`MT5に機能がある = そのFirmで利用可能`ではない。

Firm-specific evidenceが必要：EA、copy、symbols、server、market data、execution、weekend/news rule等。

## Disclaimer

`MetaTrader 5の一般機能と、各プロップファームで実際に利用できる機能・銘柄・注文環境・口座仕様は異なる場合があります。利用前に各ファームの最新条件をご確認ください。`

---

# 2. MetaTrader 4

Route：`/platforms/mt4/`

## Intro

MetaTrader 4（MT4）は、MetaQuotesが提供する取引プラットフォームです。デスクトップ、Web、iOS、Androidでの利用方法が案内され、チャート分析、注文、ポジション管理、MQL4を使ったExpert Advisorなどの機能があります。プロップファームでの採用状況や利用可能機能はFirmごとに異なるため、現行口座で本当にMT4を選べるかを個別に確認する必要があります。

## Beginner summary

- Desktop / Web / Mobileのどれで使うか
- MT4に慣れているか
- EAを使う場合はFirm ruleを確認
- MT4対応が現行Planでも続いているか確認

## General features

公式情報で確認できる一般仕様：

- Desktop / Web / iOS / Android
- chart / technical analysis
- market / pending order management
- MQL4 / Expert Advisor environment on desktop
- Web one-click trading等

## Caution

MT4は歴史の長いPlatformだが、「古いから悪い」「MT5より劣る」等の一律評価は行わない。

## Disclaimer

`MetaTrader 4の一般機能と、各プロップファームで実際に利用できる機能・銘柄・注文環境・口座仕様は異なる場合があります。利用前に各ファームの最新条件をご確認ください。`

---

# 3. TradeLocker

Route：`/platforms/tradelocker/`

## Intro

TradeLockerは、チャート分析・注文・ポジション管理などを一つの画面で行える取引プラットフォームです。公式情報ではWeb、iOS、Android、Desktop向けの利用方法が案内されています。TradingView charting integrationも特徴の一つですが、実際に利用できる銘柄、注文設定、口座権限、市場データなどはFirmや口座条件によって異なります。

## Beginner summary

- 普段のchart操作に近いか
- Web / Mobile / Desktopのどれを使うか
- Platform demoとFirmのfree trialを混同しない
- Firm側のsymbols / order permissionを確認

## General features

公式Research Packで確認済み：

- Web / iOS / Android / Desktop
- TradingView charting integration
- drawing tools / indicators
- platform demo environment

## Caution

TradeLocker自身とBroker / Prop Firmの役割を分離する。Deposit / payout / account rulesはFirm側の領域。

## Disclaimer

`TradeLockerは取引プラットフォームであり、各プロップファームの口座条件、出金条件、資金管理、利用可能機能を決定する主体ではありません。利用可能な機能や銘柄等は、利用するファームや口座によって異なる場合があります。`

---

# 4. cTrader

Route：`/platforms/ctrader/`

## Intro

cTraderは、Web・モバイル・デスクトップ系のアプリから利用できる取引プラットフォームです。公式Documentationでは、チャート上からの注文・ポジション管理、Market / Limit / Stop / Stop Limitなどの注文、複数タイプのDepth of Market（DOM）などが案内されています。ただし、実際の市場データや注文条件、口座権限は利用するFirmによって異なります。

## Beginner summary

- Web / Mobile / Desktopのどれを使うか
- DOMが必要か
- chartからのorder managementに慣れているか
- Firm側のmarket data / execution条件を確認

## General features

公式Research Packで確認済み：

- Web / iOS / Android / Desktop family
- Market / Limit / Stop / Stop Limit
- chart上のposition / order management
- Standard / Price / VWAP DOM
- Japanese documentation availability at vendor level

## Caution

Japanese documentationがあることと、Firmが日本語Supportを提供することは別。

## Disclaimer

`cTraderの一般的な機能と、各プロップファームで実際に利用できる機能・銘柄・市場データ・約定条件等は同一とは限りません。利用前に各ファームの最新の取引環境と口座条件をご確認ください。`

---

Final Status：
`PLATFORM_WAVE_A_CONTENT_READY_NOT_IMPLEMENTED`
