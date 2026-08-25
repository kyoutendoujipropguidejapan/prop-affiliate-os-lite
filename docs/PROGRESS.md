# プロップファームの歩き方｜進捗

更新日：2026-08-25 JST

## 完了

- M01〜M16：完了記録あり
- Work Day0監査：完了
- M07 P0-01〜P0-08：実装・検証完了
- M14 FAQ統合：完了
- 価格境界修正：完了
- GA4整理：完了 / 実送信のみ既存Caution履歴あり
- SEO必要分統合：完了
- ER-01 remediation：完了
- M08 Full Regression：PASS_WITH_CAUTION
- Firm → Plan Selector：実装・検証完了
- Version 80：本番公開済み
- Graphic Style Refinement：COMPLETE
- SourceHealth recheck：COMPLETE
- Blue Guardian / Hantec patch spec：COMPLETE
- Block Review Final：COMPLETE
- Work Data Patch：PASS
- Graphic + Data Patch Release Candidate Final Verification：**PASS_WITH_CAUTION**

## Production

- Version 80
- 今回のRelease Candidateは未公開

## Release Candidate actual

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
- SH003 RESOLVED
- blockTop3 = false

残るBlock 5：

1. Fintokei｜速攻プロ
2. Funded7｜1フェーズ
3. Funded7｜Instant
4. Funded Trader Markets｜Instant Pro
5. FundedElite｜Flash Activation

## Final Verification

- 差分fingerprint：`83a32d0118ced8415e323e5fb3580ebb39d6b066c6242f68a6bbd6eb7deac910`
- Before / After一致
- QA source changes 0
- 想定外差分0
- regression 48/48 PASS
- build PASS
- lint error 0 / existing warning 1
- git diff --check PASS
- Blue Guardian fresh PASS
- Hantec fresh PASS
- Diagnosis fresh PASS
- Graphic 4/4 fresh PASS
- site console error 0
- protected hash不変
- 新規BLOCKER 0
- 新規CRITICAL 0

判定：**Release Candidate Final Verification = PASS_WITH_CAUTION**

唯一のCaution：

- 390px fresh実画面 = NOT_EXECUTABLE

同じ環境での再試行はしない。

## Current Gate

- Graphic = COMPLETE
- Data Patch = PASS
- Release Candidate = FROZEN
- Final Verification = PASS_WITH_CAUTION
- Version保存 = 未実施
- Work commit / push = 未実施
- publish = 未実施
- Production = Version 80

## 次

新規調査・仕様変更・追加実装を行わない。

Release承認後は **Version保存 → Production publish** のみ。

公開後にProduction URLを実iPhoneで390px確認し、重大な崩れがあればVersion 80をrollback候補とする。

詳細：`docs/RELEASE_CANDIDATE_FINAL_2026-08-25.md`
