# PLATFORM RESEARCH FACT PACK — Volumetrica

更新日：2026-08-26 JST
Status：CONTENT_RESEARCH_READY
Production code changes：NONE

## 1. Canonical

- Platform name：Volumetrica
- Canonical ID：`volumetrica`
- Future route：`/platforms/volumetrica/`

## 2. Official-source facts

Volumetrica公式Help Centerで確認できる一般仕様：

- Volumetrica WebにはChart / DOM / Time & Sales / Trading / Trade Copier等のカテゴリがある。
- chartからのtrading、Market / Limit / Stop order、OCO strategy、Chart DOMが案内されている。
- DOMではBid / Ask sideのlimit orderを価格帯ごとに表示する機能が説明されている。
- Volume / Delta / Volume Profile等のvolume-analysis oriented indicatorsが提供されている。
- 2026 Web changelogではmobile向け改善やTrade Copier enhancements等が継続して更新されている。
- 公式changelog自身が、一部機能はserver-side rollout状況により一部Propで未提供の場合があると注意している。

## 3. Official references

- https://help.volumetricatrading.com/en/support/solutions/204000012774
- https://help.volumetricatrading.com/en/support/solutions/articles/204000014274-trading-from-the-chart
- https://help.volumetricatrading.com/en/support/solutions/articles/204000014436-vertical-dom
- https://help.volumetricatrading.com/en/support/solutions/articles/204000038567-volumetrica-web-changelog

## 4. Public-page safe angle

- Volumetricaとは何か
- Web trading workflow
- Chart / DOM / Time & Salesの役割
- volume / delta oriented analysis
- Prop Firmごとにserver-side feature rolloutが異なり得ること

## 5. Firm-specific caution

Firm × Platform Evidenceなしに断定しない：

- data feed
- market depth / entitlement
- trade copier availability
- breakeven / trailing stop availability
- OCO behavior
- supported symbols
- Mini / Micro cross-trading configuration
- Firm-specific rollout version

## 6. Compliance

一般Platform機能を全Prop Firmで有効と断定しない。特に公式changelogでserver-side rollout差が明示されているため、Firm-specific statusを別Evidenceで扱う。

Required disclaimer concept：

`Volumetricaの機能は接続先やプロップファーム側の設定・提供バージョンによって異なる場合があります。特に注文機能やTrade Copier等は、各ファームでの利用可否を個別にご確認ください。`

## 7. Readiness

- General official research：READY
- Firm-specific rollout variance：HIGH CAUTION
- Firm × Volumetrica mapping：PENDING CURRENT PRODUCTION RECONCILIATION
- Production implementation：HOLD UNTIL PLATFORM PHASE

Final Status：
`VOLUMETRICA_CONTENT_RESEARCH_READY`
