# CURRENT_STATE

確認基準日：2026-08-14〜15 JST

## 本番

- 公開サイト：`https://kyouten-prop-guide.utsr.chatgpt.site`
- 本番：Version 78
- 本番は不用意に変更しない

## Work

Workは利用上限に達しており、一時停止中。

Work復活までは、調査・仕様・UX・QA・SEO・GitHub整理を進め、実装差分を小さくしておく。

## 最新データ/UX正本

最新Master：`Prop_Firm_Master_v2_2_Final_UX_Copy.xlsx`

主要シート：

- PlanCatalogV2
- PlanCoverage
- DiagnosisPlanCurrent
- DiagnosisLogicV2
- SourceHealth
- Coupons
- PriceOffers
- UXJourney
- PageUXSpec
- CuriosityCopy
- UXCopyFinal
- FirmUXCopy
- FirmPlanFlow
- MicrocopyRules
- UXMeasurement
- UXBacklog

## ファーム/プラン

- 14社
- v2.0監査カタログ：69レコード
- 現行プランファミリー：65
- 現行確認済：59
- 公式情報競合で診断Top3保留：6
- Legacy/販売終了：3
- 一覧掲載のみ・詳細未確定：1

## 公開設計

### 基本構造

ファーム一覧
↓
そのファームのプラン一覧
↓
必要なプランだけ詳細

内部ではプラン単位で精密管理するが、公開画面で65件の詳細カードを連続表示しない。

### ファーム詳細の冒頭

- 特徴
- 日本語対応
- 無料トライアル
- 取引環境
- 注意点
- プラン一覧

その後、必要なプランのみ展開する。

## 基礎講座

一本道を維持：

1. プロップファームって何？
2. いきなり購入しなくていい
3. まず確認する3つ
4. 失格しやすいルールを知る
5. 自分に合う候補を探す
6. 30秒診断へ

トップの基本思想：`初めてでも、基礎から順番に。`

## UX

中心思想：

`見やすい → 少し分かる → 次が気になる → 自分で進みたくなる`

- 1画面1テーマ
- Primary CTAは原則1つ
- Secondaryは弱くする
- CTA前に次に得られることを予告
- ページ末尾を行き止まりにしない
- 価格/クーポンを途中で主役にしない

## 診断

診断はプラン単位。

- DiagnosisPlanCurrent：現行候補母集団
- DiagnosisLogicV2：採点ロジック
- Top3はファーム＋プラン名
- 理由2点＋注意1点
- 「品質順位」ではなく「あなたとの相性」

Affiliate、コミッション、クーポン、価格は採点に使用禁止。

## 価格/クーポン

割引適用後金額は公開しない。

公開では：

`コード｜効果｜対象｜期限`

を中心にする。

価格3区分は初期折りたたみ。

## FundingPips

現行5プランを監査済み：

- 1 Step Flex
- 2 Step Standard
- 2 Step Pro
- 2 Step Flex
- Zero

無料Trial：2 Step Standard / 2 Step Pro。

公開では5プランをファーム単位で集約する。

## 主な競合/確認中

SourceHealthを正本とする。特に：

- Fintokei 速攻プロ
- Funded7 1フェーズ
- Funded7 Instant
- FTM Instant Pro
- Hantec Instant Lite
- FundedElite Flash Activation

などは公式情報の競合を勝手に解消しない。

## GitHub

`kyoutendoujipropguidejapan/prop-affiliate-os-lite`

2026-08-15からAIエージェント向けハンドオフ基盤として整備開始。

現時点ではWork本体コードの同期はまだ行っていない。

## OSS事前調査

- shadcn/ui：UI部品の部分流用候補
- Formity：診断UXの参考
- TanStack Table：将来のフィルタ/Faceting候補
- openstatusHQ/data-table-filters：高度な検索時だけ検討
- Payload：将来の管理画面候補

現時点では新規依存を入れること自体を目的にしない。
