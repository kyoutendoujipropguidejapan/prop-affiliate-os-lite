# CURRENT_STATE

確認基準日：2026-08-24 JST

## 本番

- 公開サイト：`https://kyouten-prop-guide.utsr.chatgpt.site`
- Production：**Version 80**
- V80で Firm → Plan → Detail の3段階Selectorを公開済み
- 本番データはまだ旧公開状態。今回のGraphic / Data Patchは未公開
- 本番は不用意に変更しない

## 作業分担

- Chat：公式調査、SourceHealth判定、仕様、文言、Master更新案、Work用差分指示
- GitHub：正本、判断根拠、進捗、引き継ぎ、変更履歴
- Work：最小差分実装、tests / build / lint、Cloud Browser、Version保存 / 公開

Workに重複調査や仕様再設計をさせず、Chat / GitHubで判断を固めてから最小差分だけ渡す。

## 未公開Work最新状態

### Graphic

Graphic Style Refinement：**COMPLETE / PASS_WITH_CAUTION**

4点を都会・日常・プロップファーム / トレード文脈の線画へ差し替え済み：

- `learning-path.webp`
- `diagnosis-flow.webp`
- `firm-compare.webp`
- `selector-flow.webp`

- 1363px fresh PASS
- 46/46 regression PASS（Graphic単体時）
- build PASS
- lint error 0 / existing warning 1
- 390px fresh実画面：環境上 NOT_EXECUTABLE

Graphicは固定。追加機能・追加画像は行わない。

### Data Patch

正本：`docs/WORK_DATA_PATCH_SPEC_2026-08-24.md`
結果：`docs/WORK_DATA_PATCH_RESULT_2026-08-24.md`

**Data Patch Verification = PASS**

未公開Work actual：

- Firm = 14
- PlanCatalog = 72
- current = 67
- legacy / ended = 4
- listed-only = 1
- Diagnosis rows = 64
- SourceHealth = 16
- Block = 5

変更：

- Blue Guardian P042 3 Step → Legacy / Diagnosis除外
- P070 1 Step Nano → Active catalog追加 / Diagnosis未接続
- P071 2 Step Nano → Active catalog追加 / Diagnosis未接続
- P072 BNPL → Active WITH_CAUTION catalog追加 / Diagnosis未接続
- P045 1 Step Crypto → listed-only / HOLD維持
- P046 1 Step Pro → Legacy維持
- Hantec P028 Instant Lite → SH003 RESOLVED / Standard Max Loss 5% / Add-on 6% / Block解除

SourceHealth：

- SH003 = RESOLVED
- SH015 = Blue Guardian 3 Step `RESOLVED_TO_LEGACY`
- SH016 = Blue Guardian BNPL conflict `要確認`

残るBlock 5：

1. Fintokei｜速攻プロ
2. Funded7｜1フェーズ
3. Funded7｜Instant
4. Funded Trader Markets｜Instant Pro
5. FundedElite｜Flash Activation

検証：

- regression 48/48 PASS
- Production build PASS
- lint error 0 / existing warning 1
- `git diff --check` PASS
- Cloud Browser Blue Guardian / Hantec / Diagnosis PASS
- Block 5 / P042 / P070-P072 Top3混入 0
- site console error 0
- 新規BLOCKER 0 / CRITICAL 0

Protected hashはBefore / After一致：DiagnosisLogicV2 / integrated-tools.js / GA4 / Sitemap / Graphic 4点。

## 重要な正本

データパッチ判断：

- `docs/SOURCEHEALTH_RECHECK_2026-08-24.md`
- `docs/BLUE_GUARDIAN_MASTER_PATCH_SPEC_2026-08-24.md`
- `docs/HANTEC_INSTANT_LITE_PATCH_SPEC_2026-08-24.md`
- `docs/BLOCK_REVIEW_FINAL_2026-08-24.md`
- `docs/WORK_DATA_PATCH_SPEC_2026-08-24.md`
- `docs/WORK_DATA_PATCH_RESULT_2026-08-24.md`

Excel Master：`Prop_Firm_Master_v2_2_Final_UX_Copy.xlsx`

注意：今回Workで変更したのは `app/master-data.json`。Excel Masterそのものの同期更新は別Gateとし、GitHub要約だけでExcel Masterを上書きしない。

## Diagnosis絶対保護

- DiagnosisLogicV2を変更しない
- 7問 / 質問順を変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0 / falseで代用しない
- Conflictを自動Verified化しない
- 新規Planを件数合わせのためDiagnosisへ接続しない

## 公開設計

ファーム一覧
↓
そのファームのプラン一覧
↓
必要なプランだけ詳細

Firm Selectorは「会社から探す」、Diagnosisは「条件から探す」。Price / Couponは後段。

## 基礎講座

1. プロップファームって何？
2. いきなり購入しなくていい
3. まず確認する3つ
4. 失格しやすいルールを知る
5. 自分に合う候補を探す
6. 30秒診断へ

基本思想：`初めてでも、基礎から順番に。`

## Monitoring / Runtime

- Monitoring Dry Run = NO-GO
- Runtime Snapshot = NO-GO
- Master / SourceHealth / Diagnosis / siteへの自動反映禁止

## 現在のGate

- Production = Version 80
- Graphic implementation = COMPLETE
- Data Patch Verification = PASS
- 未公開Work統合状態 = READY_FOR_RELEASE_CANDIDATE_GATE
- 390px fresh = NOT_EXECUTABLE（既知Caution）
- Version保存 / Work commit / push / publish = 未実施

## 次

新規調査・機能追加は行わない。

次工程は、未公開Work全体（Graphic + Data Patch）をRelease Candidateとして固定し、最小統合回帰 / 最終差分確認を行うこと。

390px実画面は現環境で実行不能のため同じ方法を繰り返さない。Cautionを明示したうえでRelease判断する。
