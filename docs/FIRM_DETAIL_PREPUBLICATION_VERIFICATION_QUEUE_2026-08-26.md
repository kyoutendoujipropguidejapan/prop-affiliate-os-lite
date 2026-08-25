# FIRM_DETAIL_PREPUBLICATION_VERIFICATION_QUEUE

更新日：2026-08-26 JST
目的：Firm個別ページの実装・公開直前に必要な再確認を、Firmごとではなく確認テーマごとにまとめる。

## 0. 基本方針

- このQueueはChat / evidence deskで先に消化し、Workに調査判断を残さない。
- 公式一次情報を優先し、Direct Contactは補助Evidenceとして扱う。
- 不明項目は不明のまま。
- HOLD解除は人間承認を必要とする。
- Affiliate / Coupon / Campaignは事実確認や診断順位へ影響させない。

## P0｜Pilot前に必須

### Fundora

- 日本居住者Eligibilityの最新公式確認
- 現行Plan名称と主要ルールの最新性
- 現行Campaignの開始・終了・対象・併用不可条件
- サービス性質の公式表現（demo / learning / evaluation等）
- Official URL / Affiliate DeepLinkの分離

### Fintokei

- 日本居住者Eligibility
- 現行Plan一覧
- 速攻プロ：2026-07-15以降の新規購入口座と旧口座の条件差
- Academy導線の現行性
- Academy XPとFintokei本体制度の分離
- 日本語サイト / Helpの範囲
- Official URL / Affiliate URL分離

## P1｜Wave 1前

### SuperFunded

- 現行Plan一覧
- assessment / funded stageの時間制限
- inactivity条件
- Platform
- Coupon / Campaign current status

### Blueberry Futures

- Ascent = EOD / Accelerated = Trailingの現行公式確認
- 25K / 50K / 100K / 150K base price
- Campaign priceとBase Priceの分離
- 日本語Helpの範囲
- CFD側Blueberry Fundedとのブランド分離

### Trading Cult Pro

- 現行Prop model
- ArenaとTrading Cult Proのアカウント・サービス境界
- Coupon / Referralの現行対象・期限
- Platform
- 日本Eligibility

### The5ers

- 現行Program selector
- 対象市場
- Program names
- 日本語ページ / Helpの範囲
- Program固有Rules

## P2｜Wave 2前

### Hantec Trader

- Current ProductionでP028 Instant LiteがAccepted状態であること
- Daily 3% / Standard Max 5% / Add-on 6%の現行性
- SH003 RESOLVEDが最新であること
- 日本語範囲

注意：M14旧HOLDをCurrent Truthより優先しない。

### Blue Guardian

- P070 / P071のActive状態
- P072 BNPLのWITH_CAUTION状態
- P045 Crypto listed-only / HOLD
- P042 / P046 Legacy状態
- 日本Eligibility

### Blueberry Funded

- Instant Access系の現行Plan名称
- Rules / loss / payout条件のPlan差
- 日本語範囲
- Futuresとのブランド境界

### The5ers Futures

- Day Trade / Swing現行Rules
- M14 U10のmidnight balance/equity 4%ルール
- Day Trade 25K $59
- Activation fee None
- 他account size price

## P3｜Wave 3前

### Funded Trader Markets

- Instant Proの未解決項目
- 現行日本語対応範囲
- evaluation / Instant Planの分類
- Support / KYC / Eligibility
- 過去security incidentを掲載する場合の最新事実確認

### FundingPips

- SH011
- Affiliate Help概要と詳細tier
- Coupon購入画面
- 日本Eligibility
- 現行Plan / Platform

### Funded7

- 1フェーズ未解決項目
- Instant未解決項目
- PAYG current rules
- Coupon / Campaign対象
- 日本Eligibility

### FundedElite

- Flash Activation未解決項目
- 現行Plan
- 日本Eligibility
- service nature / rules

## Cross-Firm P0

公開するFirmすべてで必須：

- official service name
- Japan eligibility
- current plan names
- Japanese support scope
- official information URL
- affiliate URL if present
- service nature wording
- last checked date

## Cross-Firm Compliance P0

- PR disclosure
- affiliate relationship disclosure
- sponsored/provided account disclosure where applicable
- no guaranteed profit / payout / passing claims
- no unsupported No.1 / safest / fastest claims
- eligibility != regulatory authorization
- official fact != reviewer opinion
- unknown != unsupported
- campaign != base price
- ended != active

## Verification Output Contract

各確認結果は最低限次を返す：

- Firm
- Claim / field
- Source type
- Source URL or evidence pointer
- verified_at
- status: VERIFIED / CONDITIONAL / UNVERIFIED / CONFLICT
- publication: PUBLIC / PUBLIC_WITH_CAUTION / HOLD
- notes

このQueueが未消化でも、未確認部分をHOLD / unknownとして分離できる場合はFirmページ全体を自動HOLDしない。
