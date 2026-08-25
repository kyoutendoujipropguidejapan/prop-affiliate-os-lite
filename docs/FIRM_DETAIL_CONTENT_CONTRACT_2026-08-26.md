# FIRM_DETAIL_CONTENT_CONTRACT

更新日：2026-08-26 JST
用途：Firm個別ページを14社へ横展開する際の共通Content Contract。

## 1. 目的

Firm個別ページを広告LPではなく、そのFirmについて最終確認するためのEntity Hubとして設計する。

主導線：

初心者講座 → 30秒診断 → 比較 → Firm個別ページ → 公式確認 → 必要に応じてAffiliate CTA

価格・Campaign・Couponはページの主役にしない。

## 2. URL Contract

Hub：`/firms/`

Firm：`/firms/{firm-slug}/`

Slugは安定IDとして扱い、Campaign名や一時的なブランド表記変更を入れない。

## 3. Section Order

Firm個別ページは原則以下の順序を維持する。

1. Breadcrumb / H1
2. Firm Snapshot
3. まず確認する3点
4. このFirmの特徴
5. 現行プラン
6. 主要ルール
7. 取引Platform
8. 日本から利用する際の確認事項
9. Payout
10. FAQ
11. 関連ガイド
12. Price / Campaign / Coupon
13. Official / Affiliate CTA
14. 情報確認状況
15. Disclosure / Disclaimer

## 4. Firm Snapshot Contract

表示候補：

- firm_id
- firm_name
- japan_eligibility_status
- japanese_language_status
- evaluation_type_summary
- platform_display
- current_plan_count
- last_checked_at

StatusはCOMPLIANCE_BASELINE_V1の表示規則に従う。

Unknownをunsupportedとして表示しない。

## 5. First Three Checks

### ルール

優先：

- Daily Loss
- Max Loss
- DD方式
- Minimum Trading Days
- 禁止取引

### 入口

存在する場合のみ：

- Free Trial
- Academy
- low-cost entry
- demo / practice environment

存在しないFirmへ疑似的な入口を作らない。

### 取引環境

- current display platform
- mobile / web等、確認済み情報
- Firm固有仕様とPlatform一般仕様を分離

## 6. Plan Contract

Production PlanCatalogを再利用する。

新PlanをContent側で生成しない。

表示Group：

- Current
- Condition / Checking
- Legacy / Ended
- Listed-only / HOLD（必要時は明確に区別）

HOLD PlanをCurrentと同じ見た目・導線で扱わない。

Diagnosis接続状態と公開掲載状態を混同しない。

## 7. Rule Contract

主要RuleはProduction canonical / verified sourceから取得する。

優先項目：

- Profit Target
- Daily Loss
- Max Loss
- Drawdown method
- Minimum Trading Days
- News Trading
- Weekend Holding
- Consistency
- Payout conditions（確認済み範囲のみ）

Conflict / Unknownは断定しない。

## 8. Platform Contract

Phase 1では既存 `planCatalog.platforms` Display String Layerを使用可能。

Platform RegistryがProductionへ入るまでは、Firm Detail側で独自Platform DBを作らない。

将来：

`Firm → Firm × Platform → /platforms/{platform}/`

リンク先未公開時はリンクを出さない。

## 9. Japan Section Contract

表示候補：

- Japan eligibility
- Japanese website / help
- KYC availability
- Support language
- Japan-specific caution

Japan eligibility と regulatory status を分離する。

## 10. Payout Contract

P00R / P01 / P10 Source不足中は、確認済みFirm固有情報だけを表示する。

禁止：

- Payout Route DBの推測
- Providerの推測
- Summaryから実Routeを生成
- Web代替でR1 Dataを埋める

将来：

Firm → Method → Provider → Route

## 11. FAQ Contract

M11を本文Baseとし、M14判定を適用する。

- PASS：基本維持
- PASS_WITH_CAUTION：注意条件を保持
- UPDATE_REQUIRED：M14差し替え本文を使用
- HOLD：確定値へ変更しない。Schema対象外

各社最大5問。
本文とFAQの重複を増やさない。

## 12. Price / Campaign / Coupon Contract

3レイヤー分離：

- Base Price
- Official Campaign
- Personal Coupon

Campaign終了後はEnded / historyへ移し、Base priceへ混ぜない。

価格や割引を診断順位へ影響させない。

## 13. CTA Contract

Official CTA：通常公式URL。

例：`公式情報を確認する`

Affiliate CTA：conversion用Affiliate URL。

例：`PR｜公式サイトを見る`

Affiliate CTA付近にDisclosureを表示する。

## 14. SEO Contract

各Firm：

- unique title
- unique meta description
- unique H1
- self canonical
- duplicate firm slug禁止

標準Title型：

`{Firm}とは？プラン・ルール・日本語対応を初心者向けに整理`

標準H1型：

`{Firm}を使う前に確認したいプラン・ルール・取引環境`

ランキング型・根拠なし最上級表現へ寄せない。

## 15. Structured Data

FAQ schemaはM14安全ルールを適用。

Firm / Organization等のschemaを追加する場合も、Production上の実表示・公式性質・確認済み情報と一致させる。

AffiliateやCoupon情報をSEO canonical decisionへ混ぜない。

## 16. Compliance Contract

`COMPLIANCE_BASELINE_V1_2026-08-26.md` を必須参照。

最低限：

- commercial disclosure
- fact/opinion separation
- service nature protection
- last checked
- unsupported claim control
- disclaimer

## 17. Data Boundary

保護：

- app/master-data.json
- DiagnosisLogicV2
- score
- eligibility
- ranking
- Affiliate / Commission / Coupon / Price logic

Firm Detailは表示・導線Layerとして既存Canonicalを読む。
Content Contractを理由にMasterをflatten / rebuildしない。

## 18. Future Connection Contract

将来Entity Graph：

- Firm → Plan
- Firm → Platform
- Firm → Payout Method
- Firm → Payout Provider
- Firm → Article
- Firm → Campaign
- Firm → Evidence status

Firm DetailをEntity Hubとするが、未実装RegistryをFirm Detail内で先行再構築しない。

## 19. Minimum Acceptance

Firmページ1件ごとに：

- source Firm ID一致
- Current / HOLD / Legacy混同0
- Unknown誤変換0
- Affiliate / Official CTA分離
- Disclosure表示
- Last checked表示
- FAQ M11/M14整合
- unique title/meta/H1
- Diagnosisへの影響0
- Masterへの予期せぬ変更0
- 390px horizontal overflow 0

以上を満たして初めて横展開対象とする。
