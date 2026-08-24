# CURRENT_STATE

確認基準日：2026-08-24 JST

## 本番

- 公開サイト：`https://kyouten-prop-guide.utsr.chatgpt.site`
- 本番：**Version 80**
- V80で Firm → Plan → Detail の3段階Selectorを公開済み
- 14社Firm紹介 / 69プラン一言紹介を公開済み
- 現在の未公開Workにあるグラフィック4点は、まだ本番へ未反映
- 本番は不用意に変更しない

## Work

Workは利用可能。

役割分担：

- Chat：調査、SourceHealth判定、仕様、文言、Master更新案、Work用差分指示
- GitHub：正本、判断根拠、進捗、引き継ぎ、変更履歴
- Work：最小差分実装、tests / build / lint、Cloud Browser表示確認、Version保存 / 公開

Workに重複調査や仕様再設計をさせず、Chat / GitHubで判断を固めてから最小差分だけ渡す。

## 未公開Graphic Work

Graphic Style Refinement：**PASS_WITH_CAUTION / implementation COMPLETE**

4点を都会・日常・プロップファーム / トレード文脈の線画へ差し替え済み：

- `learning-path.webp`
- `diagnosis-flow.webp`
- `firm-compare.webp`
- `selector-flow.webp`

仕様：

- 960×640 WebP
- 白背景 / ネイビー線 / 淡いブルー / 控えめなティール
- 山、登山、冒険、順位、価格、クーポン、実在Firmロゴなし
- 既存配置、lazy load、CTA、導線は維持

検証：

- 1363px fresh PASS
- 46/46 regression PASS
- build PASS
- lint error 0 / existing warning 1
- git diff --check PASS
- DiagnosisLogicV2 / Master / GA4 / Sitemap hash不変
- BLOCKER 0 / CRITICAL 0
- 390px fresh実画面：環境上 NOT_EXECUTABLE

Graphicはこれ以上機能追加せず固定する。

## 最新データ / UX正本

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

## ファーム / プラン（現行Master基準）

- Firm = 14
- PlanCatalog = 69
- current plan families = 65
- current verified = 59
- official conflict / Top3保留 = 6
- legacy / ended = 3
- listed-only / detail未確定 = 1
- Diagnosis rows = 65
- SourceHealth = 14
- Block = 6

現行Block 6：

- Fintokei｜速攻プロ
- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

自動unblock禁止。

## SourceHealth再評価 2026-08-24

判断記録：`docs/SOURCEHEALTH_RECHECK_2026-08-24.md`

現在のレビュー結論：

### Block継続

- Fintokei｜速攻プロ：2026-07-15以降の新規購入Variantは確認できるが、現Runtimeで購入日を安全に判定できない
- Funded7｜1フェーズ：公式内Conflict継続
- Funded7｜Instant：公式内Conflict継続
- Funded Trader Markets｜Instant Pro：Daily DD公式内Conflict継続
- FundedElite｜Flash Activation：standard / custom / marketing条件の分離確認不足

### 解除候補

- Hantec Trader｜Instant Lite：標準 Max Loss 5%、Add-on +1%として整理可能。Master反映 + 回帰後にBlock解除候補

### Blue Guardian

- 1 Step Crypto：listed-only / HOLD / Diagnosis除外継続
- 1 Step Pro：Legacy継続
- 3 Step：現行公式専用ページがLegacy。**current → legacy変更候補 / Diagnosis除外候補**
- 1 Step Nano：Active catalog追加候補 / 初回Diagnosis未接続
- 2 Step Nano：Active catalog追加候補 / 初回Diagnosis未接続
- BNPL：Active catalog追加候補 / 初回Diagnosis未接続

3 StepのLegacy不整合は次回データパッチ最優先。

## 次回パッチの件数見込み

Blue Guardian 3 StepをLegacy化し、Nano 2件 + BNPLをcatalogへ追加する場合：

- PlanCatalog：69 → **72**
- current plan families：65 → **67**（65 - 1 + 3）
- legacy / ended：3 → **4**
- listed-only：1維持

新規3モデルを初回Diagnosisへ接続しない場合：

- Diagnosis rows：65 → **64**（3 Step除外）

Hantec Instant Liteを回帰後にunblockした場合：

- Block：6 → **5**

Blue Guardian 3 StepはLegacy除外であり、Block追加とは数えない。

SourceHealthへ3 StepのLegacy不整合を追加する場合：

- SourceHealth：14 → **15**

件数を65へ合わせる目的でNano / BNPLをDiagnosisへ早期接続しない。

## 公開設計

基本構造：

ファーム一覧
↓
そのファームのプラン一覧
↓
必要なプランだけ詳細

V80で公開済み。

Firm / Plan Selectorは「会社から探す」、Diagnosisは「条件から探す」と役割を分離する。

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
- 価格 / クーポンを途中で主役にしない

## Diagnosis絶対保護

- DiagnosisLogicV2を変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0 / falseで代用しない
- Conflictを自動Verified化しない
- 新規PlanはMaster必須フィールドの完全Mapping前にDiagnosisへ接続しない

## 価格 / クーポン

割引適用後金額は公開しない。

公開では：

`コード｜効果｜対象｜期限`

を中心にする。

価格3区分は初期折りたたみ。

## GitHub

Repository：`kyoutendoujipropguidejapan/prop-affiliate-os-lite`

推奨読み順：

1. README
2. AGENTS
3. CURRENT_STATE
4. PROGRESS
5. IMPLEMENTATION_READINESS
6. `SOURCEHEALTH_RECHECK_2026-08-24.md`
7. タスク別実体ファイル

## 次のGate

Workへまだデータ更新を渡さない。

Chat / GitHub側で次を確定する：

1. Blue Guardian 1 Step Nano / 2 Step Nano / BNPLのMaster必須フィールド
2. 日本居住者Eligibility
3. platform
4. news trading
5. weekend holding
6. payout timing / first payout
7. consistency
8. drawdown type / calculation timing
9. source URLs / checked_at
10. Hantec Instant Lite Add-onの正確な表現

確定後、Workには調査をさせず**最小データ差分仕様だけ**渡す。

Graphicの本番反映とSourceHealth / Master更新は別Gateで扱い、混ぜない。
