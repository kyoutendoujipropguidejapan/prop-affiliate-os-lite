# Work Data Patch Spec 2026-08-24

確認日：2026-08-24 JST
対象：現在の未公開Work（Graphic COMPLETE後）
目的：Workに再調査をさせず、Chat / GitHubで確定した最小データ差分だけを実装する。

## 0. 前提

- 本番 Version 80 は変更しない
- 未公開WorkにはGraphic Style Refinement済み4画像がある
- Graphic実装・配置・CSSは変更しない
- Master / SourceHealth / Diagnosisのデータ差分だけを対象にする
- DiagnosisLogicV2は変更禁止
- Version保存 / commit / publishは明示承認まで禁止

参照正本：

1. `docs/SOURCEHEALTH_RECHECK_2026-08-24.md`
2. `docs/BLUE_GUARDIAN_MASTER_PATCH_SPEC_2026-08-24.md`
3. `docs/HANTEC_INSTANT_LITE_PATCH_SPEC_2026-08-24.md`
4. `docs/BLOCK_REVIEW_FINAL_2026-08-24.md`

Workで公式サイト再調査を行わない。上記4文書と現在のMaster / app dataを照合して実装する。

## 1. Blue Guardian P042

- P042 / 3 Step：販売中/current → Legacy
- public表示は旧モデルとして後段へ分離
- Diagnosis対象 → 対象外
- DiagnosisPlanCurrentの対応行（現CV2-041）を除外
- 既存historical rulesは削除せずLegacy情報として保持
- General Information / checkout残存 vs dedicated rules LegacyのSourceHealth履歴を追加

## 2. Blue Guardian 新規Catalog 3モデル

既存Plan ID衝突を1回だけ確認する。P070 / P071 / P072が空いていれば使用。衝突時は勝手に上書きせず停止して報告。

### 1 Step Nano

- status：Active
- diagnosis：対象外（初回）
- type：1ステップ
- PT 10%
- Daily 4%
- Max 6%
- DD Trailing / highest closed balance / 6%利益でstarting balance lock + 1% buffer
- Evaluation min days 0
- Funded min 5 profitable days（各0.5%以上）
- Consistency 50% Challenge + Funded
- Profit Split 85% / optional 100% add-on
- Payout every 7 days
- News Challenge allowed / Funded high-impact・FOMC ±5分制限
- Weekend / Overnight Yes
- EA Yes
- Copy own legally-owned accounts only
- Platform MT5 / Match-Trader / TradeLocker
- Daily DD本文のExample 3に3%誤記があるため `VERIFIED_WITH_CAUTION`。canonicalは4%

### 2 Step Nano

- status：Active
- diagnosis：対象外（初回）
- type：2ステップ
- PT 8% / 5%
- Daily 3%
- Max 10%
- DD Static
- Min days 0（Evaluation / Funded）
- Consistency 50% Funded only
- Profit Split 80%
- Payout 14 days
- Payout cap 2% initial balance / cycle
- News Challenge allowed / Funded high-impact・FOMC ±5分制限
- Weekend / Overnight Yes
- EA Yes
- Copy own legally-owned accounts only
- Platform MT5 / Match-Trader / TradeLocker
- Example 3にDaily4%誤記があるため `VERIFIED_WITH_CAUTION`。canonicalは3%

### BNPL

- status：Active WITH_CAUTION
- diagnosis：対象外（初回）
- type：1ステップ系 / BNPL固有
- PT 4%
- Daily 4%
- Max 8%
- DD Trailing
- Evaluation min days 0
- Funded min 5 profitable days（各0.5%以上）
- Consistency 20% Funded
- Payout：Instant after consistency + min days
- Guardian Shield funded：open loss 1%でauto-close
- News Challenge allowed / Funded high-impact ±5分制限
- Weekend / Overnight Yes
- EA Yes
- Copy own legally-owned accounts only
- Platform MT5 / Match-Trader / TradeLocker
- Profit Split：専用ページQuick Overview 85% / 詳細節80%のConflictを保持。確定数値をDiagnosisへ渡さない
- Price / account_sizesは今回PriceOffersへ追加しない

新規3モデルは、未確認フィールドを0 / falseで埋めない。

## 3. Blue Guardian P045 / P046

- P045 1 Step Crypto：listed-only / HOLD / Diagnosis除外維持
- P046 1 Step Pro：Legacy / Diagnosis除外維持

## 4. Hantec P028 Instant Lite

SH003をResolved履歴へ移す。

P028：

- Daily = 3%
- Max = 5%
- Max Loss Add-on = +1% → 6%
- DD = Closed Balance Trailing → +5%利益でStarting Balance Lock
- Payout cycle = 5 profitable days（各0.5%以上）
- Start/evaluation min days = なし
- Consistency = 20%（Add-on 25%）
- First payout = 14 days（Weekly add-on 7 days）
- Split = 80%（95% add-on）
- News = high-impact ±3分Open/Close不可（add-on可）
- Weekend = No（add-on可）
- Open Risk = 1%
- EA / Robots = No
- Buffer = first 3% profit non-withdrawable
- data status = Verified / old SH003 resolved

Diagnosis対応行：

- Max numeric = 5.0
- Daily numeric = 3.0
- status Conflict → Verified/Resolved
- Block Top3 Yes → No
- confidenceは既存Confidence契約に従う。件数合わせや推測で値を上げない

旧Helpの6→7表示はhistorical conflictとして保持し、現行値へ戻さない。

## 5. 維持Block 5

変更しない：

- Fintokei 速攻プロ
- Funded7 1フェーズ
- Funded7 Instant
- FTM Instant Pro
- FundedElite Flash Activation

理由は `docs/BLOCK_REVIEW_FINAL_2026-08-24.md` を正本とする。

## 6. 期待件数

データ構造上の重複や既存hidden rowがないことを確認した上で、基本見込み：

- Firm = 14
- PlanCatalog = 72
- current families = 67
- legacy / ended = 4
- listed-only = 1
- Diagnosis rows = 64
- Block = 5

SourceHealthの総行数は、Resolved履歴を含める設計と新規BG conflict採番により変動可能。件数を先に固定せず、追加・解消の履歴が欠落していないことを優先する。

## 7. 変更禁止

- Graphic 4画像 / 配置 / CSS
- DiagnosisLogicV2
- Diagnosis 7問 / 質問順
- GA4
- Sitemap
- SEO記事本文
- Price / Coupon canonical
- Affiliate link architecture
- FAQ schema（今回データ差分でHOLDをschema化しない）
- 404
- Monitoring / Runtime

## 8. 最小テスト

実装後のみ実行：

1. Firm 14維持
2. PlanCatalog 72見込み
3. BG 3 Step = Legacy / Diagnosis非対象
4. BG 1 Step Nano / 2 Step Nano / BNPL = catalog表示・Diagnosis非対象
5. BG 1 Step Crypto HOLD / 1 Step Pro Legacy維持
6. Hantec Instant Lite = Max5 / Add-on6 / Block解除
7. 残るBlock 5がTop3に出ない
8. DiagnosisLogicV2 hash不変
9. Graphic files hash不変
10. 既存regression PASS
11. build PASS
12. lint error 0
13. git diff --check PASS
14. Cloud Browser fresh：Blue Guardian / Hantec Firm→Plan→Detail、診断1回

390px実画面は既知のNOT_EXECUTABLEなので再試行しない。

## 9. 最終報告

- 変更ファイル
- actual PlanCatalog / current / legacy / listed-only / Diagnosis / Block件数
- 新規Plan ID
- SourceHealth追加 / resolved一覧
- BG 3 StepのLegacy化確認
- BG Nano / BNPLがDiagnosis未接続であること
- Hantec SH003解消 / unblock確認
- 残るBlock 5
- protected hash結果
- tests / build / lint / diff
- BLOCKER / CRITICAL

判定：`Data Patch Verification = PASS / PASS_WITH_CAUTION / FAIL`

Version保存 / commit / publishは行わない。
