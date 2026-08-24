# Work Data Patch Result 2026-08-24

確認日：2026-08-24 JST
対象：未公開Work（Graphic COMPLETE後）
正本：`docs/WORK_DATA_PATCH_SPEC_2026-08-24.md`
判定：**Data Patch Verification = PASS**

## 0. 実施境界

- 公式再調査：なし
- グラフィック変更：なし
- Version保存：なし
- commit：なし
- push：なし
- publish：なし
- 本番Version 80：変更なし

## 1. 変更ファイル

今回のデータパッチで変更：

- `app/master-data.json`
- `tests/master-v2-2-p0.test.mjs`
- `tests/firm-plan-selector.test.mjs`
- `tests/rendered-html.test.mjs`
- `tests/seo-required-integration.test.mjs`

既存の未公開Graphic差分は変更せず維持。

## 2. Actual counts

| 項目 | Actual |
|---|---:|
| Firm | 14 |
| PlanCatalog | 72 |
| Current | 67 |
| Legacy / ended | 4 |
| Listed-only | 1 |
| Diagnosis rows | 64 |
| Block | 5 |
| SourceHealth | 16 |

## 3. Blue Guardian

新規Plan ID：

- P070：Blue Guardian `1ステップ Nano`
- P071：Blue Guardian `2ステップ Nano`
- P072：Blue Guardian `BNPL（合格後払い）`

P070〜P072は未使用を確認して採番。

- 3件とも初回パッチではDiagnosis非対象
- P072の競合値は一本化せず保持
- PriceOffersへの追加なし

既存Plan：

- P042 `3ステップ`：Legacy化 / Diagnosis行CV2-041除外
- P045 `1ステップ Crypto`：listed-only / Diagnosis対象外維持
- P046 `1ステップ Pro`：Legacy / Diagnosis対象外維持

公開表示構造（未公開Work）：

- Current = 8
- 確認中 = 1
- Legacy = 2

## 4. SourceHealth

- SH003：Hantec Instant Lite → `RESOLVED`
- SH015：Blue Guardian 3 Step → `RESOLVED_TO_LEGACY`
- SH016：Blue Guardian BNPL conflict → `要確認`

SourceHealth actual = 16。

## 5. Hantec Trader Instant Lite / P028

反映済み：

- Daily Loss = 3%
- Standard Max Loss = 5%
- Max Loss Add-on = 6%
- SH003 = RESOLVED
- `blockTop3 = false`
- confidence = 55を維持（仕様どおり勝手に再計算しない）

Block総数は6 → 5。

## 6. 残るBlock 5

1. Fintokei｜速攻プロ
2. Funded7｜1フェーズ
3. Funded7｜インスタント
4. Funded Trader Markets｜インスタント Pro
5. FundedElite｜Flash Activation

## 7. Protected hash

Before / After一致：

- DiagnosisLogicV2：`c0b52a8153c0be5c6e8e18f66ccc3b2348fa431dcb505a729767e19baed56f21`
- `integrated-tools.js`：`39b152e17889cbb7634062e369e3814300407de167ecfca70379910b76073169`
- GA4 / `site-events.js`：`9b878d2243e35fa7b87653ea5319184f9f745b56abf27a254f2314660e593c34`
- Sitemap：`f692026d220b5915beca858112823d718921c78456f4eeee1533705a646af971`
- Learning graphic：`f3f268dddc857b3f5fb04aab0b090878ccbd49144431d06d09d931a3f652ddca`
- Diagnosis graphic：`3accbb665d363575ae29273c227a51b1f0003a23f5063a34bf1f0ea4b4454bed`
- Firm comparison：`9ebb89afa9e92160cbcbb8419bc8cd2bd5e5847b7da9e1b356d02e4bae8e6afb`
- Selector graphic：`652f8960105286139e86eb05bd56f643b06b11b1546ff9b924d2e3118ed3ef20`

## 8. Verification

- Regression：48/48 PASS
- Production build：PASS
- lint：error 0 / existing `no-img-element` warning 1
- `git diff --check`：PASS
- DiagnosisLogicV2：差分なし
- GA4 / Sitemap / Graphic：差分なし

Cloud Browser fresh：

- Blue Guardian → Plan一覧 → P070詳細：PASS
- Current / 確認中 / Legacy分離：PASS
- Hantec → Instant Lite詳細：PASS
- Diagnosis Q1〜Q7完走：Top3 3件表示
- 残るBlock 5 / P042 / P070〜P072のTop3混入：0
- 画像欠損：0
- 横overflow：0
- サイト由来console error：0
- browser extension由来ログ24件は分離済み
- 390px実画面：既知NOT_EXECUTABLEのため再試行なし

## 9. Gate

- Data Patch Verification：**PASS**
- 新規BLOCKER：0
- 新規CRITICAL：0
- 未公開Work：実装・検証完了
- Production：Version 80のまま
- Version保存 / commit / push / publish：未実施

## 10. 次工程

次は新規データ調査ではなく、**未公開Work全体（Graphic + Data Patch）のRelease Candidate Gate**。

390px実画面は現環境でNOT_EXECUTABLEの既知Cautionとして扱い、同じ手段で再試行しない。

公開前に確認する場合は、今回変更したBlue Guardian / Hantec / DiagnosisとGraphic既存4点の統合回帰だけを対象にし、仕様追加は行わない。
