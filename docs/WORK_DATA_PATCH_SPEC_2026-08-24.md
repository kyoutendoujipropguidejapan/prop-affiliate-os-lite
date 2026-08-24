# Work Data Patch Spec 2026-08-24

確認日：2026-08-24 JST
対象：現在の未公開Work（Graphic COMPLETE後）
目的：Workに再調査をさせず、Chat / GitHubで確定した最小データ差分だけを実装する。
位置づけ：**このファイル単体を実装正本として使用できる self-contained canonical spec**。

## 0. 実行原則

- 本番 Version 80 は変更しない。
- 未公開WorkのGraphic Style Refinement済み4画像・配置・CSSは変更しない。
- Master / SourceHealth / Diagnosis data の最小差分だけを対象にする。
- DiagnosisLogicV2は変更禁止。
- Diagnosis 7問 / 質問順は変更禁止。
- Version保存 / commit / push / publishは明示承認まで禁止。
- 公式サイト再調査は禁止。この仕様の値を正本として使う。
- 不足値を 0 / false / 推測値で補完しない。
- 既存IDへ衝突する場合は上書きせず停止して報告する。

背景資料として以下がGitHubに存在するが、**実装のために別途取得する必要はない**。本ファイルの内容だけで実行する。

- `docs/SOURCEHEALTH_RECHECK_2026-08-24.md`
- `docs/BLUE_GUARDIAN_MASTER_PATCH_SPEC_2026-08-24.md`
- `docs/HANTEC_INSTANT_LITE_PATCH_SPEC_2026-08-24.md`
- `docs/BLOCK_REVIEW_FINAL_2026-08-24.md`

## 1. 実装前に1回だけ確認すること

現在の未公開Workで次だけ確認する。

1. Firm = 14
2. PlanCatalog = 69
3. Diagnosis rows = 65
4. Block = 6
5. P001〜P069が既存で、P070 / P071 / P072が未使用か
6. P042 = Blue Guardian 3 Step
7. P045 = Blue Guardian 1 Step Crypto
8. P046 = Blue Guardian 1 Step Pro
9. P028 = Hantec Trader Instant Lite
10. DiagnosisLogicV2 / Graphic 4画像 / GA4 / Sitemap のpatch前hashを記録

この前提と違う場合、件数合わせやID推測をせず停止して差分を報告する。

## 2. Blue Guardian P042 / 3 Step

P042を削除せずLegacy化する。

- plan/status：current / 販売中扱い → Legacy / 旧モデル
- public表示：現行プランと同列にせずLegacy後段へ分離
- Diagnosis：対象 → 対象外
- DiagnosisPlanCurrentのP042対応行（現行想定CV2-041）を削除 / 除外
- 既存rules値はhistorical / legacy表示用に保持
- General Information / checkout残存とdedicated rules Legacyの不整合履歴をSourceHealthへ追加

専用公式ページが `3 Step Rules (Legacy Model)` と明示しているため、販売導線にvariationが残ることだけを理由にcurrentへ戻さない。

## 3. Blue Guardian 新規Catalog 3モデル

P070 / P071 / P072が空いていれば以下で使用する。

- P070 = Blue Guardian 1 Step Nano
- P071 = Blue Guardian 2 Step Nano
- P072 = Blue Guardian BNPL

衝突時は別IDを勝手に採番せず停止して報告する。

### 3.1 P070 1 Step Nano

- Firm = Blue Guardian / PF010
- official_name = `1 Step Nano`
- public_name = `1ステップ Nano`
- status = Active
- diagnosis = 対象外（初回パッチ）
- type = 1ステップ
- Profit Target = 10%
- Daily Loss = 4%
- Daily reset = 5:00 PM EST
- Max Loss = 6%
- DD type = Trailing
- DD basis = Highest Watermark Closing Trade / highest recorded closed balance
- DD lock = 初期残高に対して6%利益到達後、starting balanceでlock + 1% withdrawal buffer
- Evaluation min days = 0
- Funded min days = 5 profitable days
- profitable day = 0.5%以上の利益日
- Consistency = 50% Challenge + Funded
- Profit Split = 85% default
- Profit Split add-on = 100%
- Payout = every 7 days
- first_payout専用列 = 明示ソース不足なら推測で7日を入れない
- Payout processing = within 24 business hours
- Minimum withdrawal = Crypto $100 / Rise $500
- News = Challenge Allowed / Funded high-impact + FOMC 前後5分のOpen / Close制限
- Weekend = Yes
- Overnight = Yes
- Scalping = minimum 2 minutes
- EA = Yes
- Copy Trading = 本人が法的に所有する自己口座間のみ
- Platforms = MT5 / Match-Trader / TradeLocker
- KYC = Funded first payout申請前
- Japan = restricted-country listに日本なしを根拠に利用可。明示Allowed文ではない旨をnote保持
- source/data status = VERIFIED_WITH_CAUTION

Caution：同一専用記事の本文 / Quick Overview / Example 1/2はDaily 4%だがExample 3に3%誤記がある。canonicalは4%。3%を採用しない。

Profit Splitの率85%を採用し、記事内の算術誤り例は根拠にしない。

### 3.2 P071 2 Step Nano

- Firm = Blue Guardian / PF010
- official_name = `2 Step Nano`
- public_name = `2ステップ Nano`
- status = Active
- diagnosis = 対象外（初回パッチ）
- type = 2ステップ
- Profit Target = 8% / 5%
- Daily Loss = 3%
- Daily reset = 5:00 PM EST
- Max Loss = 10%
- DD type = Static
- Evaluation min days = 0
- Funded min days = 0
- Consistency = 50% Funded only
- Profit Split = 80%
- Payout = every 14 days
- first_payout専用列 = 明示ソース不足なら推測で14日を入れない
- Payout processing = within 24 business hours
- Minimum withdrawal = Crypto $100 / Rise $500
- Payout cap = 1 cycleあたり初期残高の2%
- News = Challenge Allowed / Funded high-impact + FOMC 前後5分のOpen / Close制限
- Weekend = Yes
- Overnight = Yes
- Scalping = minimum 2 minutes
- EA = Yes
- Copy Trading = 本人が法的に所有する自己口座間のみ
- Platforms = MT5 / Match-Trader / TradeLocker
- KYC = Funded first payout申請前
- Japan = restricted-country listに日本なしを根拠に利用可。明示Allowed文ではない旨をnote保持
- source/data status = VERIFIED_WITH_CAUTION

Caution：同一専用記事の正式本文 / Quick Overview / Example 1/2はDaily 3%だがExample 3に4%誤記がある。canonicalは3%。4%を採用しない。

Profit Splitの率80%を採用し、記事内の算術不整合例は根拠にしない。

### 3.3 P072 Buy Now Pay Later (BNPL)

- Firm = Blue Guardian / PF010
- official_name = `Buy Now Pay Later (BNPL)`
- public_name = `BNPL（合格後払い）`
- status = Active WITH_CAUTION
- diagnosis = 対象外（初回パッチ）
- type = 1ステップ系 / BNPL固有
- Profit Target = 4%
- Daily Loss = 4%
- Daily reset = 5:00 PM EST
- Max Loss = 8%
- DD type = Trailing
- DD basis = highest closed balance / HWM。ただし専用記事の該当段落に別プラン名誤記があるためCAUTION
- Evaluation min days = 0
- Funded min days = 5 profitable days
- profitable day = 0.5%以上の利益日
- Consistency = 20% Funded
- Payout = Instant after consistency + minimum profitable days
- Payout processing = within 24 business hours
- Minimum withdrawal = Crypto $100 / Rise $500
- Profit Split = **CONFLICT / 要確認**。Quick Overview 85% / 詳細Rewards節80%を一本化しない
- Profit Split add-on = 90%
- News = Challenge Allowed / Funded high-impact 前後5分制限
- Weekend = Yes
- Overnight = Yes
- Scalping = minimum 2 minutes
- EA = Yes
- Copy Trading = 本人が法的に所有する自己口座間のみ
- Guardian Shield = Funded only / open loss 1%でauto-close
- withdrawal buffer = 8%利益到達でDD lock後、初期残高1% buffer
- Platforms = MT5 / Match-Trader / TradeLocker
- KYC = Funded first payout申請前
- Japan = restricted-country listに日本なしを根拠に利用可。明示Allowed文ではない旨をnote保持
- source/data status = VERIFIED_WITH_CAUTION / CONFLICT
- Price / account_sizes = 今回PriceOffersへ追加しない。推測補完しない

BNPL SourceHealthに保持する競合：

1. Profit Split：85% vs 80%
2. DD説明段落に別プラン名誤記
3. Entry cost：$5 / $10表示差
4. Account sizes：Helpとlanding pageの範囲差

BNPLはcatalogには追加するがDiagnosisへ接続しない。

## 4. Blue Guardian P045 / P046

### P045 1 Step Crypto

- listed-only維持
- HOLD維持
- dedicated current rules article未確認
- Diagnosis除外維持
- 不足値を推測しない

### P046 1 Step Pro

- Legacy維持
- Diagnosis除外維持
- 現行プランへ戻さない

## 5. Hantec P028 Instant Lite

SH003は現行専用HelpによりRESOLVEDとして処理する。旧Conflictは履歴として削除しない。

### 5.1 P028 PlanCatalog patch

維持：

- Plan ID = P028
- Firm ID = PF006
- type = インスタント
- status = 販売中
- Profit Target = なし
- Daily Loss = 3%
- Free Trial = なし
- Japan = 既存値維持

更新：

- Max Loss = `5%（Max Loss +1% Add-on時6%）`
- DD = `Closed Balance Trailing → +5%利益到達後Starting BalanceでLock`
- Start/evaluation min days = なし
- Payout eligibility = `各Payout cycle 5 profitable days（各日0.5%以上）`
- Consistency = 20%（Add-on 25%）
- First payout = 初回tradeから14日後（Weekly Payout Add-on 7日）
- Profit Split = 80%（95% Add-on）
- News = high-impact / red-folder event 前後3分はOpen / Close不可（Add-onで許可可）
- Weekend = No（Add-onで許可可）
- Maximum Open Risk = starting balanceの1%
- EA / Robots = No
- Mandatory Buffer = first 3% profit non-withdrawable
- minimum withdrawal request = $20（既存schemaに列がある場合のみ）
- inactivity = 30 days（既存schemaに列がある場合のみ）
- data status = Verified / old SH003 resolved
- caution = Standard Max Loss 5%、+1% Add-on時6%。旧版6→7表記は履歴のみ

`No minimum trading days` と `Payout cycleごと5 profitable days` は別スコープ。公開では `開始までの最低取引日数なし / 出金cycleでは5 profitable days` と分ける。

### 5.2 P028 Diagnosis row patch

対象：P028対応行（現行想定CV2-027）。IDが異なる場合はPlan ID P028で照合する。

- daily_loss = 3%
- daily_loss_numeric = 3.0
- max_loss = 5%
- max_loss_numeric = 5.0
- dd_type = Trailing
- min_trading_days = 開始条件なし。Payout conditionは別noteで5 profitable days
- payout = 14日 / 80%
- news = Restricted
- weekend = No
- status = Verified / Resolved
- Block Top3 = No
- source = dedicated Instant Lite Help
- caution = Max Loss +1% Add-on時6%。旧版SH003は解消履歴として保持
- confidence = **Workで勝手に94へ上げない**。既存Confidence契約でVerified行に使う明示ルールがある場合のみそのルールを適用。ルールが不明なら既存値を保持して報告

DiagnosisLogicV2は変更しない。

### 5.3 SH003

- status = RESOLVED
- resolution = `2026-08-20更新のdedicated Instant Lite HelpでStandard 5% / Add-on 6%に収束`
- historical conflict = 旧Helpの7%（standard 6%）表示を履歴として保持
- 旧値を現行へ戻さない

Hantec unblockはcandidateへ適用して回帰する。P028変更に起因するtargeted / regression failureがあればBlock変更だけを勝手に別プランへ波及させず、FAILとして報告する。

## 6. 維持Block 5

以下は変更しない。

1. Fintokei｜速攻プロ
   - 2026-07-15以降新規購入：PT6 / Daily2 / Overall3 / Min3
   - 旧購入：別世代（Daily3 / Overall6 / Min5等）
   - Runtimeが購入日 / generationを安全判定できないためKEEP_BLOCK

2. Funded7｜1フェーズ
   - FAQ / comparison：Daily4 / Max8 / Split80
   - 商品ページ：Daily5 / Max10 / Split50
   - scoring-critical公式内ConflictのためKEEP_BLOCK

3. Funded7｜Instant
   - FAQ / comparison：Max6またはtier依存
   - 商品ページ：Max10
   - OREF tier mapping未確定のためKEEP_BLOCK

4. Funded Trader Markets｜Instant Pro
   - 詳細FAQ / matrix：Daily DD 3%
   - 公式紹介コピーにno Daily Drawdown Limitが残る
   - 失格条件の公式内ConflictのためKEEP_BLOCK

5. FundedElite｜Flash Activation
   - Base：PT6 / Daily3 / Total6 / Split80 / Payout14d
   - marketing/custom：target as low as2 / up to95 / instant payout等
   - variant / add-on mapping未完成のためKEEP_BLOCK

件数合わせを目的に解除しない。

## 7. SourceHealth patch

既存SourceHealth schema / IDを尊重し、列やIDを推測で上書きしない。

最低限：

1. SH003：既存行をRESOLVED化しhistorical conflict保持
2. Blue Guardian 3 Step Legacy mismatch：新規履歴行を追加
   - dedicated rules Legacyをcurrent判定の優先根拠とする
   - P042はDiagnosis除外
3. Blue Guardian BNPL conflict：新規行を追加
   - Profit Split 85 / 80、DD段落誤記、price / size表示差
   - catalog Active WITH_CAUTION
   - Diagnosis除外

1 Step Nano / 2 Step NanoのExample typoは、既存schemaでSourceHealth rowを増やす必要がなければPlan note / cautionで保持してよい。

現在SourceHealthが14行で、次の空きIDがSH015 / SH016なら利用可。空きでなければ勝手に上書きせず、既存採番規則に従える場合のみ次IDを使う。判断不能なら停止して報告。

## 8. 期待件数

前提がSection 1と一致する場合の基本見込み：

- Firm = 14
- PlanCatalog = 72
- current families = 67
- legacy / ended = 4
- listed-only = 1
- Diagnosis rows = 64
- Block = 5

SourceHealthは既存SH003を更新し、BG 3 Step / BNPLを2行新規追加できる構造なら 14 → 16 が見込み。ただしhidden row /別採番があればactualを優先し、件数を無理に合わせない。

Blue Guardian 3 StepはLegacy除外でありBlock追加とは数えない。

新規Nano / BNPLをDiagnosisへ早期接続して64を65へ戻さない。

## 9. 変更禁止

- Graphic 4画像 / 配置 / CSS
- DiagnosisLogicV2
- Diagnosis 7問 / 質問順
- GA4
- Sitemap
- SEO記事本文
- Price / Coupon canonical
- Affiliate link architecture
- FAQ schema
- 404
- Monitoring / Runtime

## 10. 実装後テスト

パッチ実装後だけ実行する。

1. Firm 14維持
2. PlanCatalog 72
3. current 67 / legacy-ended 4 / listed-only 1（現行分類契約と一致する場合）
4. BG P042 3 Step = Legacy / Diagnosis非対象
5. BG P070 1 Step Nano = Active / Diagnosis非対象
6. BG P071 2 Step Nano = Active / Diagnosis非対象
7. BG P072 BNPL = Active WITH_CAUTION / Diagnosis非対象
8. BG P045 Crypto = HOLD/listed-only、P046 1 Step Pro = Legacy維持
9. Hantec P028 = Daily3 / Max5 / Add-on6 / SH003 RESOLVED / Block解除candidate
10. 残るBlock 5がTop3へ出ない
11. Diagnosis rows = 64見込み
12. DiagnosisLogicV2 hash不変
13. Graphic 4画像hash不変
14. GA4 hash不変
15. Sitemap hash不変
16. 既存regression PASS
17. build PASS
18. lint error 0
19. git diff --check PASS
20. Cloud Browser fresh：Blue Guardian Firm→Plan→Detail、Hantec Firm→Plan→Detail、Diagnosisを1回完走
21. console error 0（browser extension由来ノイズは分離報告）

390px実画面は既知のNOT_EXECUTABLEなので再試行しない。

## 11. 最終報告

必ず以下を報告する。

- 変更ファイル
- actual Firm / PlanCatalog / current / legacy-ended / listed-only / Diagnosis / Block / SourceHealth件数
- P070 / P071 / P072採番可否
- SourceHealth追加 / resolved一覧
- BG P042 Legacy化確認
- BG Nano / BNPLがDiagnosis未接続であること
- Hantec SH003 RESOLVED / Block解除結果
- 残るBlock 5
- protected hash before/after
- tests / build / lint / diff / browser
- 新規BLOCKER / CRITICAL

判定：`Data Patch Verification = PASS / PASS_WITH_CAUTION / FAIL`

**Version保存 / commit / push / publishは行わない。**
