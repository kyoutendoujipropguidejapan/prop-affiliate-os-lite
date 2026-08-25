# PLATFORM RESEARCH FACT PACK — TRADELOCKER

確認日：2026-08-26 JST
Status：RESEARCH_VALIDATED_NOT_PRODUCTION_CANONICAL
Production code changes：NONE

Purpose：将来の `/platforms/tradelocker/` 個別ページに使える公式一次情報のResearch Packを作る。Firm固有設定とは分離し、Production Canonicalへの自動反映はしない。

## 1. Official-source findings

### Platform nature
TradeLocker公式Helpは、TradeLockerをbroker / prop firmではなくtrading platformとして明確に区別している。

TradeLocker側：
- trading interface
- charting environment
- execution tools
- trading workflows

Broker / Prop Firm側：
- trading accounts
- funds
- deposits / withdrawals
- trade execution
- account permissions

Source：
- https://support.tradelocker.com/en/articles/14597099-what-is-tradelocker

この分離はFirmページ・Platformページ・PayoutページのCompliance Boundaryとして重要。

## 2. Device / access availability

公式Helpで確認できる利用形態：
- Web application
- iOS app
- Android app
- Desktop application

Android appは公式Help上、Android 12以上をサポートすると案内されている。古いAndroidではmobile web browser利用が案内されている。

Source：
- https://support.tradelocker.com/en/articles/13673068-mobile-app

公開時はOS要件が変わり得るため、固定仕様として永続化せずlast checkedを付ける。

## 3. Charting

TradeLocker公式サイトはTradingView charting統合を案内。

確認できる項目：
- TradingView charting integration
- 50+ drawing tools
- 100+ indicators
- browser / desktop / tablet / mobileでのchart access案内

Source：
- https://tradelocker.com/platform/charting/

注意：
- これを「すべてのProp Firmで全機能が使える」とは表現しない。
- Firm / account permission / configuration差を別Layerで扱う。

## 4. Demo environment

TradeLocker公式Helpではplatformを試せるfree demo environmentを案内している。

Source：
- https://support.tradelocker.com/en/articles/14597099-what-is-tradelocker

これはTradeLocker自体のdemoであり、特定Prop Firmのfree trialやchallengeとは別物。

## 5. Safe beginner-facing summary candidate

公開候補文：

`TradeLockerは、チャート分析・注文・ポジション管理などを一つの画面で行える取引プラットフォームです。Web、モバイル、デスクトップ向けの利用方法が案内されています。ただし、利用できる銘柄・注文設定・口座権限・市場データなどは、利用するプロップファームや口座条件によって異なる場合があります。`

## 6. Firm-specific boundary

TradeLocker一般仕様とFirm固有仕様を混ぜない。

Firm × Platform evidenceが必要な候補：
- available symbols
- leverage
- order permissions
- account permissions
- market data
- execution configuration
- copy functionality
- server / connection
- add-ons / risk controls

## 7. Prohibited claims

Evidenceなしで以下を使用しない：
- 最速
- 最も安定
- MT5より優れている
- 約定が速い
- スリッページが少ない
- 初心者に最適
- Prop Firm向けNo.1

## 8. Compliance copy

必須注意：

`TradeLockerは取引プラットフォームであり、各プロップファームの口座条件、出金条件、資金管理、利用可能機能を決定する主体ではありません。利用可能な機能や銘柄等は、利用するファームや口座によって異なる場合があります。`

## 9. SEO draft

Route候補：
`/platforms/tradelocker/`

Title候補：
`TradeLockerとは？プロップファームで使う前に知りたい特徴と確認ポイント`

H1候補：
`TradeLockerとは？プロップファーム利用前に確認したい取引環境`

Meta候補：
`TradeLockerの基本的な特徴、Web・モバイル・デスクトップでの利用、チャート環境、プロップファームごとに異なる確認ポイントを初心者向けに整理します。`

## 10. Production readiness

Content research：READY_WITH_CAUTION
Firm mapping：PENDING_CURRENT_PRODUCTION_RECONCILIATION
Route：NOT_IMPLEMENTED
Canonical：NOT_CREATED
Sitemap：NOT_ADDED
GA4：NOT_ADDED

Final Research Status：
`TRADELOCKER_CONTENT_RESEARCH_READY`
