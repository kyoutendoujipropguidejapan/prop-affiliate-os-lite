# CURRENT_STATE

確認基準日：2026-08-25 JST

## 本番

- 公開サイト：`https://kyouten-prop-guide.utsr.chatgpt.site`
- Production：**Version 80**
- V80で Firm → Plan → Detail の3段階Selectorを公開済み
- 今回のGraphic + Data Patch Release Candidateはまだ未公開

## 作業分担

- Chat：公式調査、SourceHealth判定、仕様、文言、Master更新案、Work用差分指示
- GitHub：正本、判断根拠、進捗、引き継ぎ、変更履歴
- Work：最小差分実装、tests / build / lint、Cloud Browser、Version保存 / 公開

Workに重複調査や仕様再設計をさせず、Chat / GitHubで判断を固めてから最小差分だけ渡す。

## 未公開Work最新状態

現在の未公開Workは **Release Candidateとして固定済み**。

正本：

- `docs/WORK_DATA_PATCH_SPEC_2026-08-24.md`
- `docs/WORK_DATA_PATCH_RESULT_2026-08-24.md`
- `docs/RELEASE_CANDIDATE_FINAL_2026-08-25.md`

### Graphic

- 都会・日常・プロップファーム / トレード文脈の線画4点
- `learning-path.webp`
- `diagnosis-flow.webp`
- `firm-compare.webp`
- `selector-flow.webp`
- 4/4読込、960×640、ratio正常
- Graphic変更は固定済み

### Data Patch actual

- Firm = 14
- PlanCatalog = 72
- current = 67
- legacy / ended = 4
- listed-only = 1
- Diagnosis rows = 64
- SourceHealth = 16
- Block = 5

Blue Guardian：

- P042 3 Step → Legacy / Diagnosis除外
- P070 1 Step Nano → Active / Diagnosis未接続
- P071 2 Step Nano → Active / Diagnosis未接続
- P072 BNPL → Active WITH_CAUTION / Diagnosis未接続
- P045 1 Step Crypto → listed-only / HOLD維持
- P046 1 Step Pro → Legacy維持
- 未公開Work表示：Active 8 / 確認中1 / Legacy 2

Hantec Trader：

- P028 Instant Lite → Daily 3% / Max 5% / Add-on 6%
- SH003 RESOLVED
- blockTop3 = false

SourceHealth：

- SH003 = RESOLVED
- SH015 = Blue Guardian 3 Step RESOLVED_TO_LEGACY
- SH016 = Blue Guardian BNPL 要確認

残るBlock 5：

1. Fintokei｜速攻プロ
2. Funded7｜1フェーズ
3. Funded7｜Instant
4. Funded Trader Markets｜Instant Pro
5. FundedElite｜Flash Activation

## Release Candidate Final Verification

判定：**PASS_WITH_CAUTION**

- 差分fingerprint：`83a32d0118ced8415e323e5fb3580ebb39d6b066c6242f68a6bbd6eb7deac910`
- fingerprint Before / After一致
- QAによるソース変更0
- 想定外差分0
- Regression 48/48 PASS
- Build PASS
- Lint error 0 / existing warning 1
- git diff --check PASS
- Blue Guardian fresh PASS
- Hantec fresh PASS
- Diagnosis fresh PASS
- Graphic fresh PASS
- site console error 0
- 新規BLOCKER 0 / CRITICAL 0

Protected hashは検証前後一致：Master / DiagnosisLogicV2 / GA4 / Sitemap / Graphic 4点。

### Caution

390px実画面 = **NOT_EXECUTABLE**。

現環境の既知制約。これが唯一のCaution。

## Diagnosis絶対保護

- DiagnosisLogicV2を変更しない
- 7問 / 質問順を変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0 / falseで代用しない
- Conflictを自動Verified化しない
- 新規Planを件数合わせ目的でDiagnosisへ接続しない

## Monitoring / Runtime

- Monitoring Dry Run = NO-GO
- Runtime Snapshot = NO-GO
- Master / SourceHealth / Diagnosis / siteへの自動反映禁止

## 現在のGate

- Production = Version 80
- Release Candidate Final Verification = **PASS_WITH_CAUTION**
- Caution = 390px実画面NOT_EXECUTABLEのみ
- Version保存 = 未実施
- Work commit / push = 未実施
- publish = 未実施

## 次

新規調査・仕様変更・機能追加は行わない。

Release承認後は **Version保存 → Production publish** だけを実施する。

公開後はProduction URLを実iPhoneで確認できるため、390pxをpost-release限定確認として実施する。重大なモバイル崩れがある場合はVersion 80をrollback候補とする。
