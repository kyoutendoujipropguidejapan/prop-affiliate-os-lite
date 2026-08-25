# FIRM_DETAIL_CONTENT_READINESS_MATRIX

更新日：2026-08-26 JST
位置づけ：Firm個別ページ横展開前のContent Readiness判定。Productionコードは変更しない。

## 0. 判定原則

このMatrixは、GitHub HandoffのM11/M14だけで公開可否を決めない。

優先順位：

1. 現在のProduction Current Truth
2. 公式一次情報の最新確認
3. Accepted Work Result / SourceHealth resolution
4. M14 verified extraction
5. M11 content base
6. Historical notes

M14が古いHOLDを含み、その後Accepted Workで解決済みの場合は、古いHOLDを機械的に復活させない。ただしCurrent Truthとの照合は公開前に必須。

## 1. Readiness enum

- `PILOT_READY`：Pilot実装候補。既存Contentを主に再利用可能。
- `READY_WITH_CAUTION`：公開候補だが、公開前に限定項目の再確認が必要。
- `READY_WITH_CURRENT_OVERRIDE`：M14より新しいAccepted Current Truthがあり、Current Truthを優先して実装する。
- `PARTIAL_HOLD`：Firmページ自体は作成可能だが、特定Plan / FAQ / ClaimをHOLDのまま分離する。
- `HOLD_PAGE`：ページ全体を公開すべきでない状態。現時点では該当なし。

## 2. 14社 Matrix

| Firm | Firm ID | Readiness | そのまま再利用できる主資産 | 公開前再確認 | HOLD / 非公開 | 主なCompliance注意 |
|---|---|---|---|---|---|---|
| Fintokei | PF001 | PILOT_READY / PARTIAL_HOLD | M11、M14 U01、Academy accepted content | 日本Eligibility、日本語範囲、Academy導線、現行Plan名称 | 速攻プロ限定Variantの扱いを一般化しない。旧口座条件と分離 | Academy利用必須の誤認禁止。PR/Official CTA分離。速攻プロの購入時期差を明示 |
| Funded7 | PF002 | PARTIAL_HOLD | M11 Q1/Q4、M14 U02 | 現行Plan一覧、Coupon対象、Eligibility | 1フェーズ / Instantの未解決項目を確定表示しない | HOLDを診断・FAQ schema・推奨表現へ使わない |
| Fundora | PF003 | PILOT_READY | M11、M14判定、既存Campaign accepted implementation | 現行Plan、Eligibility、Campaign終了状態 | CampaignをBase Priceへ混ぜない | Demo/learning/evaluation service natureを維持。利益・資金提供保証表現禁止 |
| Funded Trader Markets | PF004 | PARTIAL_HOLD | M11 Q1/Q3/Q4/Q5 | 日本語範囲、現行Plan、Support | Instant Proの未解決項目 | Instant / evaluationを混同しない。セキュリティ事案を扱う場合は事実と推測を分離 |
| The5ers | PF005 | READY_WITH_CAUTION | M11 base + M14 U03/U04 | 現行Program selector、対象市場、日本語範囲 | 古いProgram名称の断定 | CFD/Futures等の対象市場を混同しない。Programごとの条件差を維持 |
| Hantec Trader | PF006 | READY_WITH_CURRENT_OVERRIDE | Current StateのInstant Lite resolution、M11 base | Current ProductionのP028/SH003状態、日本語範囲 | M14旧Q2 HOLDをそのまま復活させない | M14より新しいAccepted Current Truthを優先。Standard/Add-on条件を混同しない |
| SuperFunded | PF007 | READY_WITH_CAUTION | M11 + M14 U05 | 現行Plan、Platform、Coupon | 変動Campaignの恒久化禁止 | 時間制限なしと不活動条件を別概念として表示。PR導線明示 |
| Blueberry Futures | PF008 | READY_WITH_CAUTION | M11 + M14 U06/U07、Current price confirmation | Ascent/Accelerated現行Rules、価格、Campaign status | 60% campaign priceをbaseへ混ぜない | Futures productとCFD sister brandを混同しない。DD方式をPlan別に表示 |
| Trading Cult Pro | PF009 | READY_WITH_CAUTION | M11 + M14 U08 | 現行models、Arenaとのアカウント関係、Coupon/Referral | 期限不明Couponの確定表示 | Trading Cult ProとArenaのサービス境界を明示。Tournamentと通常Prop商品を混同しない |
| Blue Guardian | PF010 | READY_WITH_CAUTION | Current State Plan grouping、M11/M14 caution | P070/P071/P072 status、P045 HOLD、現行Platform | P045 Cryptoはlisted-only/HOLD。Legacy P042/P046をCurrent扱いしない | Active / caution / legacy / listed-onlyのStatusを明確化 |
| Blueberry Funded | PF011 | READY_WITH_CAUTION | M11 + M14 U09 | Instant Access現行Rules、日本語範囲 | 旧Planと現行Planの混同禁止 | CFDとBlueberry Futuresを別Firm/商品体系として扱う |
| FundedElite | PF012 | PARTIAL_HOLD | M11 Q1/Q2/Q4/Q5 | 現行Plan、Eligibility、日本語範囲 | Flash Activation未解決項目 | HOLDを推奨材料へ利用しない。曖昧なサービス性質を断定しない |
| The5ers Futures | PF013 | READY_WITH_CAUTION | M11 + M14 U10、Day Trade 25K価格確認 | 現行Day Trade/Swing価格・Rules | 未反映価格をProduction確定値として扱わない | Futures/CFDのThe5ersを混同しない。PriceとActivation feeを別表示 |
| FundingPips | PF014 | READY_WITH_CAUTION | M11/M14 | SH011、Affiliate Help、Coupon購入画面、Eligibility | 未確認tier/特典の断定 | Affiliate Helpの概要と詳細tierを混同しない。Couponを診断へ影響させない |

## 3. Pilot Gate

最初のPilotは変えない。

1. Fundora
2. Fintokei

理由：

- Fundora：比較的シンプルな構成＋Campaign分離を検証できる
- Fintokei：複数Plan、Academy、限定Variant、旧口座差を含む複雑系を検証できる

2社がPASSするまで残りFirmを一括実装しない。

## 4. Pilot後の暫定Rollout順

Pilot PASS後、再確認コストとHOLD密度を考慮し、以下を暫定順とする。

### Wave 1

- SuperFunded
- Blueberry Futures
- Trading Cult Pro
- The5ers

### Wave 2

- Hantec Trader
- Blue Guardian
- Blueberry Funded
- The5ers Futures

### Wave 3

- Funded Trader Markets
- FundingPips
- Funded7
- FundedElite

Wave 3はHOLD / Affiliate-detail / Eligibility再確認が多いため後段。

## 5. Page Completion != Claim Completion

Firmページは、全項目が確定するまで作れないわけではない。

安全な実装：

- 確認済み：表示
- 条件付き：caution表示
- 不明：unknown表示
- HOLD：非断定 / schema除外 / Diagnosis非利用
- Legacy：Currentから分離

ページ完成のために不足情報を推測しない。

## 6. Compliance Gate

全Firm共通：

- Affiliate / Sponsor / Provided Accountの関係を必要箇所で開示
- Official URLとAffiliate CTAを分離
- `日本から利用可能` と `日本の規制当局による登録・認可` を同義にしない
- 利益、合格、出金、資金提供を保証しない
- unsupported superiority claimを使わない
- current / campaign / coupon / legacyを分離
- last checkedを表示
- reviewer opinionとofficial factを分離
- FAQ schemaは画面表示本文と一致し、HOLD/変動項目を原則除外
- PII/KYC/bank/wallet detailsをGA4へ送らない

## 7. Work使用前の最終確認

各Firmの実装開始直前に、Current Productionとの差分を再照合する。

このMatrixはImplementation Planning正本であり、将来の公式変更を固定する資料ではない。
