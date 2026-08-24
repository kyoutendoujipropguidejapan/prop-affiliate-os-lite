# Blue Guardian Master Patch Spec 2026-08-24

確認日：2026-08-24 JST
Firm：PF010 / Blue Guardian / CFD
目的：Master v2.2 の Blue Guardian 現行モデルを、公式一次情報に基づき次回最小データパッチへ落とすための確定仕様。

重要：この文書だけで Master / Diagnosis / 公開データを自動更新しない。Workへ渡す前の正本候補。DiagnosisLogicV2は変更禁止。

## 0. 結論

### 次回パッチで実施候補

1. P042 Blue Guardian 3 Step：current → Legacy
2. P042をDiagnosisPlanCurrentから除外
3. 1 Step Nanoを新規Active catalog追加
4. 2 Step Nanoを新規Active catalog追加
5. BNPLを新規Active catalog追加
6. 新規3モデルは初回パッチではDiagnosisへ接続しない
7. P045 1 Step Cryptoはlisted-only / HOLD維持
8. P046 1 Step ProはLegacy維持

Plan IDは既存P001-P069と衝突しないことをWorkで確認したうえで、空きがなければ P070 / P071 / P072 を候補とする。ID衝突時は推測で上書きしない。

## 1. 公式モデル状態

Blue Guardian公式Account Modelsには現在、Instant Standard / Instant Starter / 1 Step Standard / 1 Step Pro (Legacy) / 2 Step Standard / 2 Step Pro / 3 Step (Legacy) / BNPL / 1 Step Nano / 2 Step Nano が掲載されている。

- 3 Step：Legacy
- 1 Step Pro：Legacy
- 1 Step Nano：現行専用ルールあり
- 2 Step Nano：現行専用ルールあり
- BNPL：現行専用ルールあり
- 1 Step Crypto：General Informationには残るが専用現行ルール記事は確認できないためlisted-only / HOLD維持

## 2. 共通Firmレベル

### platforms

公式Platform Rules：

- MetaTrader 5 (MT5)
- Match-Trader
- TradeLocker

US clientのみMT5制限がある。日本向けはこの制限記載に該当しない。

### age_requirement

18歳以上。

### restricted_countries / japan_eligibility

公式General Informationの制限国一覧に日本は含まれない。

公開/DB表現：

- japan_eligibility = Yes（restricted list基準の推定）
- evidence_note = 「日本を明示的にAllowedと書いた文ではなく、現行Restricted Countries一覧に日本がないことを根拠とする」

制限国一覧の変更時は再確認する。

### kyc

- Instant Starter：KYC不要
- それ以外のInstant / Funded：最初のPayout申請前にKYC

Nano / BNPLは funded account移行後、first payout前KYCとして扱う。

### general permissions

Nano / BNPL専用ページ共通：

- EA：Allowed
- Copy Trading：本人が法的に所有する自己口座間のみAllowed
- Overnight：Allowed
- Weekend：Allowed
- Tick scalping：最低保有2分
- News：ChallengeはAllowed、Fundedはhigh-impact/FOMC前後5分のOpen/Closeを制限

## 3. 1 Step Nano

### catalog status

- official_name = 1 Step Nano
- public_name = 1ステップ Nano
- type = 1ステップ
- plan_status = active candidate
- diagnosis_status = excluded at first patch

### RulesSchema mapping

- profit_target = 10% / Phase 1
- daily_loss = 4% of initial balance
- daily_reset = 5:00 PM EST
- daily_calc = reset時のBalance / Equityの高い方から、初期残高の4%固定額を差し引く
- max_loss = 6%
- dd_type = trailing
- dd_basis = Highest Watermark Closing Trade / highest recorded closed balance
- dd_lock = initial balanceに対して6%利益到達後、starting balanceでlock + 1% withdrawal buffer
- min_trading_days = Evaluation 0 / Funded 5 profitable days
- profitable_day_definition = fundedで0.5%以上の利益日
- consistency_rule = 50%（Challenge + Funded）
- payout_frequency = every 7 days
- first_payout = 専用記事では「Every 7 days」とあるが、first payoutを別記した明示文は未確認。7日周期として保持し、first_payout専用列がある場合は推測で埋めない
- payout_processing = within 24 business hours
- minimum_withdrawal = Crypto $100 / Rise $500
- profit_split = 85% default
- profit_split_addon = 100% add-on
- news_trading = Challenge Allowed / Funded high-impact + FOMC ±5分制限
- weekend_holding = Yes
- overnight_holding = Yes
- scalping = minimum 2 minutes
- ea = Yes
- copy_trading = own legally-owned accounts only
- platforms = MT5 / Match-Trader / TradeLocker
- kyc = first payout before request on Funded
- japan_eligibility = Yes by restricted-country-list inference

### Source caution

同じ1 Step NanoページのDaily DD本文・Quick Overview・Example 1/2は4%だが、Example 3に「3%」という不整合文がある。

判断：

- daily_loss canonical = 4%
- source_status = VERIFIED_WITH_CAUTION
- SourceHealthへ軽微な本文内不整合として記録候補
- 3%を自動採用しない

Profit Splitの本文は85%で一貫するが、$5,000例のFirm receives $700は算術誤り（本来$750）。率の値は85%を採用し、例示計算は根拠に使わない。

## 4. 2 Step Nano

### catalog status

- official_name = 2 Step Nano
- public_name = 2ステップ Nano
- type = 2ステップ
- plan_status = active candidate
- diagnosis_status = excluded at first patch

### RulesSchema mapping

- profit_target = 8% / 5%
- daily_loss = 3% of initial balance
- daily_reset = 5:00 PM EST
- daily_calc = reset時のBalance / Equityの高い方から、初期残高の3%固定額を差し引く
- max_loss = 10%
- dd_type = static
- min_trading_days = Evaluation 0 / Funded 0
- consistency_rule = 50% Funded only
- payout_frequency = every 14 days
- first_payout = 専用記事でfirst payoutを別記した明示文は未確認。14日周期として保持し、first_payout専用列は推測で埋めない
- payout_processing = within 24 business hours
- minimum_withdrawal = Crypto $100 / Rise $500
- payout_cap = 1 cycleあたり初期残高の2%
- profit_split = 80%
- news_trading = Challenge Allowed / Funded high-impact + FOMC ±5分制限
- weekend_holding = Yes
- overnight_holding = Yes
- scalping = minimum 2 minutes
- ea = Yes
- copy_trading = own legally-owned accounts only
- platforms = MT5 / Match-Trader / TradeLocker
- kyc = first payout before request on Funded
- japan_eligibility = Yes by restricted-country-list inference

### Source caution

同じ2 Step Nanoページは正式本文・Quick Overview・Example 1/2でDaily DD 3%だが、Example 3に4%という不整合文がある。

判断：

- daily_loss canonical = 3%
- source_status = VERIFIED_WITH_CAUTION
- 4%例文を自動採用しない

Profit Splitは80%と明記されるが、$5,000例の「Trader $4,050 / Firm $1,000」は算術不整合。率80%を採用し、例示金額を根拠に使わない。

## 5. BNPL

### catalog status

- official_name = Buy Now Pay Later (BNPL)
- public_name = BNPL（合格後払い）
- type = 1ステップ系 / BNPL固有
- plan_status = active candidate
- diagnosis_status = excluded at first patch

通常1 Step Standardへ統合せず独立モデルとして保持する。

### RulesSchema mapping

- profit_target = 4% / Phase 1
- daily_loss = 4% of initial balance
- daily_reset = 5:00 PM EST
- max_loss = 8%
- dd_type = trailing
- dd_basis = highest closed balance / HWM と読む記述あり。ただし該当段落に「On 2 step pro accounts」という誤記があるため計算基準はCAUTION
- min_trading_days = Evaluation 0 / Funded 5
- consistency_rule = 20% Funded
- payout_frequency = Instant payout after consistency + minimum trading days
- payout_processing = within 24 business hours
- minimum_withdrawal = Crypto $100 / Rise $500
- profit_split = CONFLICT：Quick Overview 85% / 詳細Rewards節 80%
- profit_split_addon = 90%
- news_trading = Challenge Allowed / Funded high-impact ±5分制限
- weekend_holding = Yes
- overnight_holding = Yes
- scalping = minimum 2 minutes
- ea = Yes
- copy_trading = own legally-owned accounts only
- guardian_shield = Funded only / 1% floating loss auto-close
- withdrawal_buffer = 8%利益到達でDD lock後、初期残高1% buffer
- platforms = MT5 / Match-Trader / TradeLocker
- kyc = first payout before request on Funded
- japan_eligibility = Yes by restricted-country-list inference

### BNPL SourceHealth

BNPLはActive catalog追加自体は可能だが、以下をSourceHealthに残す。

1. Profit Split：同一専用ページ内 85% vs 80%
2. DD説明：BNPL記事内に「On 2 step pro accounts」という誤記
3. Entry cost：Helpはstart $10、BNPL landing pageはheroで$5表記と$10表記が混在
4. Account sizes：HelpのActivation Fee表は5K/10K/25K/50K/100K/200K、landing pageは10K〜400Kと案内。モデル固有の全サイズ確定にはcheckout再確認が必要

したがって：

- BNPL catalog = ADD_ACTIVE_WITH_CAUTION
- diagnosis = excluded
- price = public確定値として自動使用しない
- profit_split = 要確認として公開表示するか、公開詳細で率表示を保留

## 6. account_sizes / price

RulesSchema上は account_sizes / price があるが、今回の3モデルでは公式ページの抽出表示がモデル選択タブと価格表を完全に一対一で結び付けない。

### Nano

Checkoutの個別商品ページで1 Step Nano / 2 Step Nano variationは5K / 10K / 50K / 100Kで確認できる。一方、25K / 200K / 300K / 400Kは今回の証跡でモデル別variationを完全確認できていない。

### BNPL

専用HelpのActivation Fee表とlanding pageのサイズ説明に差がある。

判断：

- 初回Master patchで account_sizes / price を推測補完しない
- 現行PlanCatalogV2がサイズ・価格を診断必須にしていない場合、要確認で追加可
- PriceOffersへは別Gateでcheckout証跡が揃ってから追加

## 7. Blue Guardian 3 Step

P042：

- current official dedicated page title = 3 Step Rules (Legacy Model)
- PlanCatalogV2：販売中 → Legacyへ変更
- Diagnosis状態：診断対象（ANY時） → 対象外
- DiagnosisPlanCurrent：CV2-041を削除候補
- 既存ルール値はhistorical/legacy表示用に保持してよい
- SourceHealth：General Information / checkout残存とdedicated rules Legacyの不整合履歴を追加

販売導線に古いvariationが残ることだけでcurrentへ戻さない。

## 8. 1 Step Crypto / 1 Step Pro

### P045 1 Step Crypto

- General Information掲載あり
- dedicated current rules article未確認
- listed-only / HOLD維持
- Diagnosisへ入れない

### P046 1 Step Pro

- dedicated pageがLegacy Model
- Legacy維持
- Diagnosisへ入れない

## 9. Diagnosis影響

初回最小パッチでは：

- P042 / CV2-041 3 StepをDiagnosisから除外
- Nano / BNPLはDiagnosisへ追加しない
- DiagnosisLogicV2は不変

Diagnosis rows見込み：65 → 64

Hantec Instant Liteのunblockは別Gateなので、このBlue Guardianパッチと同時に数を調整する目的で接続しない。

## 10. PlanCatalog件数見込み

現行：69

- P042は削除せずLegacy化：件数変化なし
- Nano 2件 + BNPL 1件追加：+3

見込み：72

分類見込み：

- current families = 67（65 - 3 Step 1 + 新規3）
- legacy / ended = 4
- listed-only = 1

## 11. SourceHealth追加候補

既存SourceHealth番号はWork / Masterで空きを確認して採番する。番号を推測で上書きしない。

追加候補：

A. Blue Guardian 3 Step Legacy mismatch（高）
B. Blue Guardian BNPL profit split / price / account-size inconsistency（高）
C. 1 Step Nano article internal typo（中〜低）
D. 2 Step Nano article internal typo（中〜低）

診断へ影響するA/Bを優先し、C/DはNotesレベルでも可。

## 12. 公式一次情報

- Account Models: https://help.blueguardian.com/en/collections/18967956-account-models
- 1 Step Nano: https://help.blueguardian.com/en/articles/16444654-1-step-nano-rules
- 2 Step Nano: https://help.blueguardian.com/en/articles/16445450-2-step-nano-rules
- BNPL: https://help.blueguardian.com/en/articles/15859899-buy-now-pay-later-bnpl-rules
- 3 Step Legacy: https://help.blueguardian.com/en/articles/14062468-3-step-rules-legacy-model
- General Information: https://help.blueguardian.com/en/articles/15618204-general-information-rules
- Platform Rules: https://help.blueguardian.com/en/articles/9661525-platform-rules
- Payout: https://help.blueguardian.com/en/articles/9660857-how-do-payouts-work
- Official CFD page: https://blueguardian.com/forex
- Checkout: https://checkout.blueguardian.com/

## 13. Workへ渡す最小差分

まだWork実装は開始しない。

次にChat側でHantec Instant Liteを同じ粒度で確定した後、Blue Guardian + Hantecを一つの最小データパッチとしてWorkへ渡すのが効率的。

Workに調査はさせず、実装内容は：

- exact row/value patch
- SourceHealth row追加/更新
- Diagnosis row削除/Block解除候補の反映
- counts更新
- regression/build/lint/diff

のみに限定する。

## Status

- Blue Guardian source research: COMPLETE
- Master field mapping: COMPLETE_WITH_CAUTION
- Blue Guardian patch spec: READY_FOR_REVIEW
- Master write: NOT_STARTED
- Diagnosis write: NOT_STARTED
- Work implementation: NOT_STARTED
