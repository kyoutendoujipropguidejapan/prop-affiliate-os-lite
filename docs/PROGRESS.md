# プロップファームの歩き方｜進捗

更新日：2026-08-24 JST

## 完了

- M01〜M16：完了記録あり
- Work Day0監査：完了
- M07 P0-01〜P0-08：実装・検証完了
- M14 FAQ統合：完了
- 価格境界修正：完了
- GA4整理：完了 / 実送信のみCaution
- SEO必要分統合：完了
- ER-01 remediation：完了
- M08 Full Regression：PASS_WITH_CAUTION
- Firm → Plan Selector：実装・検証完了
- Version 80：本番公開済み
- Graphic Style Refinement：COMPLETE / PASS_WITH_CAUTION
- SourceHealth recheck：COMPLETE
- Blue Guardian / Hantec patch spec：COMPLETE
- Block Review Final：COMPLETE
- Work Data Patch：**PASS**

---

## 本番

- Production = **Version 80**
- Firm 14社
- V80公開時PlanCatalog = 69
- Firm → Plan → Detail 3段階Selector公開済み
- 今回のGraphic / Data Patchはまだ未公開

---

## 未公開Work：Graphic

4点を都会・日常・プロップファーム / トレード文脈へ差し替え済み。

- learning-path.webp
- diagnosis-flow.webp
- firm-compare.webp
- selector-flow.webp

Graphic単体検証：

- 1363px fresh PASS
- regression 46/46 PASS
- build PASS
- lint error 0 / existing warning 1
- git diff --check PASS
- BLOCKER 0 / CRITICAL 0
- 390px fresh：NOT_EXECUTABLE

判定：**Graphic Style Refinement = PASS_WITH_CAUTION**

---

## 未公開Work：Data Patch

正本：`docs/WORK_DATA_PATCH_SPEC_2026-08-24.md`
結果：`docs/WORK_DATA_PATCH_RESULT_2026-08-24.md`

判定：**Data Patch Verification = PASS**

Actual：

- Firm 14
- PlanCatalog 72
- Current 67
- Legacy / ended 4
- Listed-only 1
- Diagnosis rows 64
- Block 5
- SourceHealth 16

Blue Guardian：

- P042 3 Step → Legacy / Diagnosis除外
- P070 1 Step Nano → Active / Diagnosis未接続
- P071 2 Step Nano → Active / Diagnosis未接続
- P072 BNPL → Active WITH_CAUTION / Diagnosis未接続
- P045 Crypto → listed-only / HOLD維持
- P046 1 Step Pro → Legacy維持

Hantec：

- P028 Instant Lite → Daily3 / Max5 / Add-on6
- SH003 → RESOLVED
- blockTop3 = false
- confidence 55維持

SourceHealth：

- SH003 RESOLVED
- SH015 BG 3 Step RESOLVED_TO_LEGACY
- SH016 BG BNPL 要確認

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
- git diff --check PASS
- Cloud Browser：Blue Guardian / Hantec / Diagnosis PASS
- Block 5 / P042 / P070-P072 Top3混入 0
- site console error 0
- protected hash不変
- 新規BLOCKER 0 / CRITICAL 0

---

## 現在のGate

### Production

- Version 80
- 今回差分未公開

### Unpublished Work

- Graphic = COMPLETE
- Data Patch = PASS
- Integrated state = **READY_FOR_RELEASE_CANDIDATE_GATE**
- 390px fresh = NOT_EXECUTABLE
- Version保存 = 未実施
- Work commit / push = 未実施
- publish = 未実施

### Monitoring / Runtime

- Monitoring Dry Run = NO-GO
- Runtime Snapshot = NO-GO

---

## 次

新規調査や機能追加は一旦止める。

未公開Work全体（Graphic + Data Patch）をRelease Candidateとして固定し、以下だけ行う。

1. 最終差分確認
2. 統合回帰
3. Blue Guardian / Hantec / Diagnosis / Graphicのfresh確認
4. protected hash再確認
5. 新規BLOCKER / CRITICAL 0確認

390px実画面は現環境でNOT_EXECUTABLEの既知Cautionとして扱い、同じ確認を繰り返さない。

上記がPASSならRelease判断へ進む。
