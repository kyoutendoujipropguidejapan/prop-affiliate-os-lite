# SourceHealth Recheck 2026-08-24

確認日：2026-08-24 JST
対象：SourceHealth / 確認中プラン / Blue Guardian 現行モデル再整理
位置づけ：**Master / Diagnosis 更新前の承認用判断記録**。この文書だけで Master や公開データを自動更新しない。

## 0. 結論

次回の最小データパッチは、以下を基準にする。

### 維持

- Fintokei｜速攻プロ：購入日VariantをRuntimeで安全に判定できないため **Block継続**
- Funded7｜1フェーズ：公式内Conflict継続のため **Block継続**
- Funded7｜Instant：公式内Conflict継続のため **Block継続**
- Funded Trader Markets｜Instant Pro：Daily DDの公式内Conflict継続のため **Block継続**
- FundedElite｜Flash Activation：標準条件とマーケティング / custom条件の分離確認が不足するため **Block継続**
- Blue Guardian｜1 Step Crypto：存在は確認できるが専用ルール未確認のため **listed-only / diagnosis除外継続**
- Blue Guardian｜1 Step Pro：**Legacy継続**

### 変更候補 / Patch Ready

- Hantec Trader｜Instant Lite：**SH003 RESOLVED_FOR_PATCH**。2026-08-20更新の専用HelpでStandard Max Loss 5%、+1% Add-on時6%に収束。旧6→7表示は履歴として保持し、回帰後にBlock解除候補
- Blue Guardian｜3 Step：現行公式専用ページでは Legacy と明示。**current → legacy変更候補**、Diagnosisから除外候補
- Blue Guardian｜1 Step Nano：**新規Active catalog追加候補**。初回はDiagnosis未接続
- Blue Guardian｜2 Step Nano：**新規Active catalog追加候補**。初回はDiagnosis未接続
- Blue Guardian｜BNPL：**新規Active catalog追加候補（CAUTION）**。専用ページ内Profit Split等の不整合をSourceHealthで保持し、Diagnosis未接続

詳細仕様：

- `docs/BLUE_GUARDIAN_MASTER_PATCH_SPEC_2026-08-24.md`
- `docs/HANTEC_INSTANT_LITE_PATCH_SPEC_2026-08-24.md`

## 1. Blue Guardian 重要Gate

### 3 Step

現行Masterでは current / Diagnosis対象だが、現行公式専用ページでは Legacy 扱い。

安全側の判断：

1. 3 StepをLegacyへ移す
2. Diagnosisから除外する
3. LegacyとしてFirm詳細の後段に残す場合は「旧モデル」表示
4. SourceHealthへ「General Information / checkout残存 vs dedicated rules Legacy」の履歴を追加

販売導線に残っていることだけを理由に current へ戻さない。

### Nano / BNPL

- 1 Step Nano：Active catalog追加候補、Diagnosis初回未接続
- 2 Step Nano：Active catalog追加候補、Diagnosis初回未接続
- BNPL：Active catalog追加候補。ただし専用ページ内のProfit Split 85% / 80%等をCAUTIONとして保持し、Diagnosis初回未接続
- 1 Step Crypto：listed-only / HOLD / Diagnosis除外継続
- 1 Step Pro：Legacy継続

全フィールド詳細はBlue Guardian patch specを参照。

## 2. Hantec Instant Lite SH003再判定

Master v2.2のP028は、旧取得時点で「本文Max Loss 5% / Add-on欄がstandard 6%を示唆」のためConflict / Blockだった。

2026-08-20更新の現行専用Instant Lite Helpでは：

- Daily Loss 3%
- Max Total Loss 5%
- Max Loss +1% Add-on = 6%（standard 5%）
- Consistency 20%
- Payout cycle 5 profitable days（各日0.5%以上）
- First payout 14日
- Standard split 80%

へ収束。

旧Helpキャッシュには「7%（standard 6%）」版が残るため、その履歴は削除しない。ただし現行値としては採用しない。

判定：

- SH003 = RESOLVED_FOR_PATCH
- P028 Max Loss canonical = 5%
- Add-on = 6%
- Diagnosis Block解除 = READY_FOR_REVIEW
- Work回帰成功後にBlock解除確定候補

「No minimum trading days」と「Payout cycleごと5 profitable days」はスコープが異なるため、公開では `開始条件なし / 出金cycleでは5 profitable days` と分ける。

## 3. 既存確認中項目

| 対象 | 判定 | 次回パッチ |
|---|---|---|
| Fintokei 速攻プロ | KEEP_BLOCK | 2026-07-15以降新規購入Variantの世代情報は保持。現Runtimeでは自動解除しない |
| Funded7 1フェーズ | KEEP_BLOCK | 値を一本化しない。公式確定回答または表示収束まで待つ |
| Funded7 Instant | KEEP_BLOCK | Max Loss 6/8/10履歴を消さずConflict維持 |
| FTM Instant Pro | KEEP_BLOCK | Daily DDなし / 3%のConflict維持 |
| Hantec Instant Lite | RESOLVED_FOR_PATCH | Standard 5% / Add-on 6%。回帰後unblock候補 |
| FundedElite Flash Activation | KEEP_BLOCK | standard FAQとcustom / marketing訴求を分離できるまでBlock |
| Blue Guardian 1 Step Crypto | KEEP_HOLD | listed-only / diagnosis除外 |
| Blue Guardian 3 Step | LEGACY_CANDIDATE | currentからLegacyへ。Diagnosis除外 |
| Blue Guardian 1 Step Pro | KEEP_LEGACY | 変更不要 |
| Blue Guardian 1 Step Nano | ADD_ACTIVE_CANDIDATE | catalog追加。Diagnosis未接続 |
| Blue Guardian 2 Step Nano | ADD_ACTIVE_CANDIDATE | catalog追加。Diagnosis未接続 |
| Blue Guardian BNPL | ADD_ACTIVE_WITH_CAUTION | catalog追加。Diagnosis未接続。Split等はSourceHealth保持 |

## 4. 件数への影響見込み

現行基準：

- PlanCatalog = 69
- current plan families = 65
- legacy / ended = 3
- listed-only = 1
- Diagnosis rows = 65
- SourceHealth = 14
- Block = 6

Blue Guardian 3 StepをLegacyへ移し、Nano 2件 + BNPLをcatalogへ追加した場合：

- PlanCatalog = 72
- current plan families = 67（65 - 1 + 3）
- legacy / ended = 4
- listed-only = 1
- Diagnosis rows = 64（新規3モデルを初回Diagnosisへ接続しないため）

Hantec Instant LiteのBlock解除を同時承認した場合：

- Block = 5

Blue Guardian 3 StepはLegacy除外でありBlock追加とは数えない。

SourceHealth件数は、解消履歴を行として保持するか、新規Blue Guardian conflictを何件の独立行にするかで変わるため、件数合わせを目的に固定しない。

## 5. 次回Master更新の推奨順

1. Blue Guardian 3 StepをLegacyへ変更
2. 3 StepをDiagnosisから除外
3. Blue Guardian 1 Step Nano / 2 Step Nano / BNPLをcatalogへ新規追加
4. 新規3モデルはDiagnosis未接続
5. 1 Step Cryptoはlisted-only維持
6. 1 Step ProはLegacy維持
7. Hantec Instant LiteをStandard Max5% / Add-on6%へ整理
8. SH003をResolved履歴へ
9. Hantec Block解除は回帰成功を条件に反映
10. 他の既存ConflictはBlock維持
11. DiagnosisLogicV2は変更しない

## 6. 公式参照URL

Blue Guardian：

- `https://help.blueguardian.com/en/articles/16444654-1-step-nano-rules`
- `https://help.blueguardian.com/en/articles/16445450-2-step-nano-rules`
- `https://help.blueguardian.com/en/articles/15859899-buy-now-pay-later-bnpl-rules`
- `https://help.blueguardian.com/en/articles/14062468-3-step-rules-legacy-model`
- `https://help.blueguardian.com/en/articles/15618204-general-information-rules`

Hantec Trader：

- `https://help.htrader.hmarkets.com/en/support/solutions/articles/158000445802-instant-lite`
- `https://htrader.hmarkets.com/programs/instant-lite/`

Funded7：

- `https://funded7.com/faq/one-phase-challenge/`
- `https://funded7.com/faq/instant-funding-challenge/`

FundedElite：

- `https://www.fundedelite.com/challenges/flash-activation`

## 7. Status

- Graphic: COMPLETE
- Blue Guardian patch spec: READY_FOR_REVIEW
- Hantec Instant Lite patch spec: READY_FOR_REVIEW
- SourceHealth recheck: PATCH_SPEC_READY
- Master update: NOT_STARTED
- Diagnosis data update: NOT_STARTED
- DiagnosisLogicV2 update: PROHIBITED / NOT_REQUIRED
- Work implementation: NOT_STARTED

次工程は、残るKEEP_BLOCK項目をChat側で最終確認し、変更不要を確定したうえで、Blue Guardian + Hantecの**最小Work実装指示**を作ること。
