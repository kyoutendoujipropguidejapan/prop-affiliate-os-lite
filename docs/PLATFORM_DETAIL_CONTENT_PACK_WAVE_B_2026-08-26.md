# PLATFORM DETAIL CONTENT PACK — WAVE B

更新日：2026-08-26 JST
Status：CONTENT READY / NOT PRODUCTION IMPLEMENTED
対象：Match-Trader / DXtrade / BlackArrow / Quantower / Volumetrica

Firm-specific mappingは含めない。公開実装はPlatform PhaseまでHOLD。

---

# 1. Match-Trader

Route：`/platforms/match-trader/`

## Intro

Match-Traderは、Match-Trade Technologiesが提供する取引プラットフォームです。公式DocumentationではWeb、mobile、desktop application構成、market watch、chart、order management、trade history等が案内されています。Prop向けsolutionも存在しますが、Platform一般機能と各Firmでのchallenge設定や利用条件は分けて確認する必要があります。

## Beginner summary

- Web / Mobile / Desktopの利用形態
- chart / order workflow
- Japanese表示が実際のFirm環境で提供されるか
- Prop dashboardとFirm ruleを混同しない

## General features

公式Research Packで確認済み：
- web / mobile / desktop
- PWA-oriented access
- chart / market watch / order management
- TradingView chart integration
- vendor-level Japanese translation capability

## Caution

Vendor-level Japanese対応とFirm日本語Supportは別。

## Disclaimer

`Match-Traderの一般機能と、各プロップファームで実際に有効な機能・表示言語・注文条件・口座仕様は異なる場合があります。利用前に各ファームの最新条件をご確認ください。`

---

# 2. DXtrade

Route：`/platforms/dxtrade/`

## Intro

DXtradeは、Devexpertsが提供するwhite-label型の取引プラットフォームです。公式情報ではWeb trading interface、iOS / Android mobile delivery、customizable layout、Trading Journal、Trading Dashboard、charting等が案内されています。導入事業者側で構成を調整できるため、同じDXtradeでもFirmごとに見える機能や注文条件が異なる可能性があります。

## Beginner summary

- Web / Mobileの提供形態
- Firm独自layout / widgetの有無
- market data / executionがどこから提供されるか
- DXtrade一般仕様とFirm固有仕様を分ける

## General features

公式Research Packで確認済み：
- web trading
- iOS / Android mobile options
- customizable layouts
- journal / dashboard / charting
- TradingView integration option

## Caution

White-label configuration差が大きい。Vendor導入事例のperformance claimを一般化しない。

## Disclaimer

`DXtradeは導入事業者ごとに構成や有効機能を調整できるため、一般的なDXtradeの説明と、各プロップファームで実際に利用できる機能・注文条件・取引環境は一致しない場合があります。`

---

# 3. BlackArrow

Route：`/platforms/blackarrow/`

## Intro

BlackArrowはNelogica Softwareが提供する取引プラットフォームで、公式情報ではBrokerやExchangeそのものではなくtechnology serviceとして説明されています。Windows、Mac、Web、Mobileでの利用、charting、indicators、simulation、OCO、AutoBreakeven、Trailing Stop等が案内されています。接続先のBrokerやProp Firmによって市場データや利用機能は異なります。

## Beginner summary

- PlatformとFirm / Brokerの役割を分ける
- Futures / Equities等の対象assetを接続先ごとに確認
- simulationと実際のchallenge環境を混同しない
- order / risk toolsがFirm環境で有効か確認

## General features

公式Research Packで確認済み：
- Windows / Mac / Web / Mobile
- charting / indicators / price alerts
- simulator
- OCO / AutoBreakeven / Trailing Stop
- Prop Trading integration offering

## Caution

Vendorのexecution-speed等のmarketing wordingは独立検証値として扱わない。

## Disclaimer

`BlackArrowは取引プラットフォームであり、実際の取引条件・市場データ・注文機能・リスク設定は接続先のブローカーやプロップファームによって異なる場合があります。`

---

# 4. Quantower

Route：`/platforms/quantower/`

## Intro

Quantowerは、Windows向けのmulti-connect型取引プラットフォームです。公式情報では複数のBroker、Exchange、Data Feedへの接続、Chart、DOM Trader、Time & Sales、Volume Profile、Cluster Chart、VWAP等の分析機能が案内されています。利用できる機能は接続先やLicenseによって異なるため、Prop Firmで使う場合はFirm側の対応範囲を別に確認する必要があります。

## Beginner summary

- Windows desktop中心で使うか
- DOM / order-flow分析が必要か
- 接続先Data Feedを確認
- Free / Paid機能差を確認

## General features

公式Research Packで確認済み：
- Windows 10/11 64-bit
- multi-connect
- chart / DOM / Time & Sales
- volume / order-flow analytics
- free / paid feature scope

## Caution

Platform機能、License、Connectionの3つを分けて説明する。

## Disclaimer

`Quantowerで利用できる接続先・市場データ・注文機能・分析機能は、ライセンスや接続先によって異なる場合があります。プロップファームでの利用条件は各ファームの最新情報をご確認ください。`

---

# 5. Volumetrica

Route：`/platforms/volumetrica/`

## Intro

Volumetricaは、Chart、DOM、Time & Sales、volume / delta系分析などを扱う取引プラットフォームです。公式Help CenterではWeb trading、Market / Limit / Stop order、OCO、Chart DOM、Trade Copier等が案内されています。一方、公式changelogでも一部機能はProp Firm側のserver rollout状況により提供時期が異なる場合があると説明されているため、Firmごとの確認が特に重要です。

## Beginner summary

- Chart / DOM / Time & Salesの役割
- volume / delta分析が必要か
- market-data entitlementを確認
- Firm側のversion / rollout差を確認

## General features

公式Research Packで確認済み：
- Web Chart / DOM / Time & Sales
- Market / Limit / Stop order
- OCO / Chart DOM
- Trade Copier category
- volume / delta indicators

## Caution

Firm-specific server-side rollout差を最優先注意として表示する。

## Disclaimer

`Volumetricaの機能は接続先やプロップファーム側の設定・提供バージョンによって異なる場合があります。特に注文機能やTrade Copier等は、各ファームでの利用可否を個別にご確認ください。`

---

Final Status：
`PLATFORM_WAVE_B_CONTENT_READY_NOT_IMPLEMENTED`
