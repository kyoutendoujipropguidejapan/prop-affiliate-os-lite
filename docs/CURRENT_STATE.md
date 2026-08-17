# CURRENT_STATE

確認基準日：2026-08-17 JST

## 本番

- 公開サイト：`https://kyouten-prop-guide.utsr.chatgpt.site`
- 本番：Version 78
- 本番は不用意に変更しない

## Work

最新把握ではWorkは利用上限により一時停止中。

Work復活までは、調査・仕様・UX・QA・SEO・GitHub整理を進め、実装差分を小さくしておく。

Work復活時は最初に `docs/IMPLEMENTATION_READINESS.md` と `docs/WORK_RESTART_PROMPT.md` を確認し、コードを書く前に未公開作業版を監査する。

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

Excel Masterがデータ・診断・SourceHealthの上位正本。GitHubの要約文だけでMasterを上書きしない。

## 進捗

M01〜M16は完了記録あり。詳細は `docs/PROGRESS.md`。

ただし、完了記録とGitHub上の実体ファイルは一致しない。

GitHubに主要実体があるもの：

- M08 QA
- M09 SEO原稿
- M10監視技術設計
- M11 14社FAQ原稿
- M12 Dry Run URLセット

M07 / M13 / M14 / M15 / M16等は詳細成果物がGitHubで確認できない部分があるため、`docs/IMPLEMENTATION_READINESS.md` のArtifact Existence Gateを適用する。

## ファーム/プラン

- 14社
- v2.0監査カタログ：69レコード
- 現行プランファミリー：65
- 現行確認済：59
- 公式情報競合で診断Top3保留：6（Master v2.2基準）
- Legacy/販売終了：3
- 一覧掲載のみ・詳細未確定：1

M06以降、Fintokei速攻プロは2026-07-15以降の新規購入Variantに限り条件付き解除候補。旧口座との分離、Evidence、人間承認を保持できない場合はBlock継続。

Block継続5件：

- Funded7 1フェーズ
- Funded7 Instant
- Funded Trader Markets Instant Pro
- Hantec Trader Instant Lite
- FundedElite Flash Activation

自動unblock禁止。

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

FAQは後段。M11原稿を基礎とするが、M14でPASS 32 / PASS_WITH_CAUTION 23 / UPDATE_REQUIRED 10 / HOLD 5に再分類済み。M14差し替え全文がないUPDATE_REQUIRED項目は公開前に回収または再照合する。

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

FundingPips紹介条件はSH011の公式表示差を維持し、診断採点には使用しない。

## GitHub

`kyoutendoujipropguidejapan/prop-affiliate-os-lite`

AIエージェント向けハンドオフ基盤。

推奨読み順：

1. README
2. AGENTS
3. CURRENT_STATE
4. PROGRESS
5. IMPLEMENTATION_READINESS
6. タスク別実体ファイル
7. Work時はWORK_RESTART_PROMPT

現時点ではWork本体コードの同期はまだ行っていない。

## 監視 / Runtime

M10/M12はGitHubに実体あり。
M15 `monitor_sources` とM16 Runtime Snapshotは仕様完了記録があるが、実JSON / Schema実体はGitHub未確認。

- 監視Dry RunはM15実体同期＋Preflight＋人間承認まで開始しない
- Runtime SnapshotはAPPROVEDのみWork/Replit利用可能という設計を維持
- Master / SourceHealth / Diagnosis / Work / siteへの自動反映禁止

## OSS事前調査

- shadcn/ui：UI部品の部分流用候補
- Formity：診断UXの参考
- TanStack Table：将来のフィルタ/Faceting候補
- openstatusHQ/data-table-filters：高度な検索時だけ検討
- Payload：将来の管理画面候補

現時点では新規依存を入れること自体を目的にしない。
