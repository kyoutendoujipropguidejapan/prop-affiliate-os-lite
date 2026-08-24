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

### 変更候補

- Hantec Trader｜Instant Lite：旧Conflictは解消候補。標準 Max Loss 5%、Add-on +1% を別条件として保持し、**レビュー / 回帰後にBlock解除候補**
- Blue Guardian｜3 Step：現行公式専用ページでは Legacy と明示。**current → legacy変更候補**、Diagnosisから除外候補
- Blue Guardian｜1 Step Nano：**新規Active catalog追加候補**。Diagnosisは必要項目の完全Mappingまで接続しない
- Blue Guardian｜2 Step Nano：**新規Active catalog追加候補**。Diagnosisは必要項目の完全Mappingまで接続しない
- Blue Guardian｜BNPL：**新規Active catalog追加候補**。Diagnosisは必要項目の完全Mappingまで接続しない

## 1. 重要Gate

### Blue Guardian 3 Step

現行Masterでは current / Diagnosis対象だが、現行公式専用ページでは Legacy 扱い。

これは公開候補母集団に直接影響するため、次回データパッチの最優先。

**安全側の判断：**

1. 3 StepをLegacyへ移す
2. Diagnosisから除外する
3. LegacyとしてFirm詳細の後段に残す場合は「旧モデル」表示にする
4. SourceHealthへ「General Information / checkout残存 vs dedicated rules Legacy」の履歴を追加する

販売導線に残っていることだけを理由に current へ戻さない。

## 2. Blue Guardian 再構成案

### Active / catalog追加候補

#### 1 Step Nano

公式専用ルール記事あり。

- 現行Masterには未登録
- Active catalog追加候補
- 方式：1ステップ
- Diagnosis：初回追加時は除外

理由：Diagnosisへ接続する前に、Masterが要求する全 scoring fields、Eligibility、platform、news、weekend、payout等の完全Mappingを確認する。

#### 2 Step Nano

公式専用ルール記事あり。

- 現行Masterには未登録
- Active catalog追加候補
- 方式：2ステップ
- Diagnosis：初回追加時は除外

#### BNPL

公式専用ルール記事あり。

- 現行Masterには未登録
- Active catalog追加候補
- 方式：1ステップ系 / BNPL固有モデル
- Diagnosis：初回追加時は除外

名称を通常1 Stepへ吸収せず、公式モデル名を保持する。

### listed-only / HOLD

#### 1 Step Crypto

- General Information上の存在確認あり
- 専用現行ルール記事未確認
- current rulesを確定できない

**判定：listed-only / HOLD / Diagnosis除外継続**

### Legacy

#### 3 Step

**Legacy化候補。Diagnosis除外。**

#### 1 Step Pro

現行MasterのLegacy扱いを維持。

## 3. 既存確認中項目

| 対象 | 判定 | 次回パッチ |
|---|---|---|
| Fintokei 速攻プロ | KEEP_BLOCK | 2026-07-15以降新規購入Variantの世代情報は保持。現Runtimeでは自動解除しない |
| Funded7 1フェーズ | KEEP_BLOCK | 値を一本化しない。公式確定回答または表示収束まで待つ |
| Funded7 Instant | KEEP_BLOCK | Max Loss 6/8/10履歴を消さずConflict維持 |
| FTM Instant Pro | KEEP_BLOCK | Daily DDなし / 3%のConflict維持 |
| Hantec Instant Lite | RESOLVED_CANDIDATE | Standard 5% と Add-on +1% を別フィールド / 注記で保持。回帰後にunblock候補 |
| FundedElite Flash Activation | KEEP_BLOCK | standard FAQとcustom / marketing訴求を分離できるまでBlock |
| Blue Guardian 1 Step Crypto | KEEP_HOLD | listed-only / diagnosis除外 |
| Blue Guardian 3 Step | LEGACY_CANDIDATE | currentからLegacyへ。Diagnosis除外 |
| Blue Guardian 1 Step Pro | KEEP_LEGACY | 変更不要 |
| Blue Guardian 1 Step Nano | ADD_ACTIVE_CANDIDATE | catalog追加。Diagnosis未接続 |
| Blue Guardian 2 Step Nano | ADD_ACTIVE_CANDIDATE | catalog追加。Diagnosis未接続 |
| Blue Guardian BNPL | ADD_ACTIVE_CANDIDATE | catalog追加。Diagnosis未接続 |

## 4. 件数への影響見込み

現行基準：

- PlanCatalog = 69
- current plan families = 65
- legacy / ended = 3
- listed-only = 1
- Diagnosis rows = 65
- SourceHealth = 14
- Block = 6

Blue Guardian 3 StepをLegacyへ移し、Nano 2件 + BNPLをcatalogへ追加した場合の**catalog上の見込み**：

- PlanCatalog = 72
- current plan families = 67（65 - 1 + 3）
- legacy / ended = 4
- listed-only = 1

ただし新規3モデルを初回パッチでDiagnosisへ接続しない場合：

- Diagnosis rows = 64（現65から3 Stepを除外）

Hantec Instant LiteのBlock解除を同時承認した場合：

- Block = 5

Blue Guardian 3 StepはLegacy除外であり「Block追加」とは数えない。

SourceHealthは、3 StepのLegacy不整合を新規履歴として追加する場合：

- SourceHealth = 15

※ 件数を65へ合わせるためだけに新規Nano / BNPLをDiagnosisへ早期接続しない。

## 5. 次回Master更新の推奨順

1. Blue Guardian 3 StepをLegacyへ変更
2. 3 StepをDiagnosisから除外
3. Blue Guardian 1 Step Nano / 2 Step Nano / BNPLをcatalogへ新規追加
4. 3モデルは `diagnosis_eligible = false` 相当で開始
5. 1 Step Cryptoはlisted-only維持
6. 1 Step ProはLegacy維持
7. Hantec Instant Liteの標準 / Add-on表現を整理
8. Hantec unblockは回帰テスト成功後に確定
9. 他の既存ConflictはBlock維持
10. DiagnosisLogicV2自体は変更しない

## 6. Workへ渡す前の追加確認

Chat / GitHub側で以下を確定してからWorkへ渡す。

- Blue Guardian Nano / BNPLの全Master必須フィールド
- 日本居住者Eligibility
- platform
- news trading
- weekend holding
- payout timing / first payout
- consistency
- drawdown type / calculation timing
- source URLs / checked_at
- Hantec Instant Lite Add-onの正確な表現

不足項目を0 / falseで補完しない。

## 7. 公式参照URL（再確認対象）

Blue Guardian：

- `https://help.blueguardian.com/en/articles/16444654-1-step-nano-rules`
- `https://help.blueguardian.com/en/articles/16445450-2-step-nano-rules`
- `https://help.blueguardian.com/en/articles/15859899-buy-now-pay-later-bnpl-rules`
- `https://help.blueguardian.com/en/articles/14062468-3-step-rules-legacy-model`
- `https://help.blueguardian.com/en/articles/15618204-general-information-rules`

Hantec Trader：

- `https://help.htrader.hmarkets.com/en/support/solutions/articles/158000445802-instant-lite`

Funded7：

- `https://funded7.com/faq/one-phase-challenge/`
- `https://funded7.com/faq/instant-funding-challenge/`

FundedElite：

- `https://www.fundedelite.com/challenges/flash-activation`

## 8. Status

- Graphic: COMPLETE
- SourceHealth recheck: REVIEWED / PATCH_SPEC_READY
- Master update: NOT_STARTED
- Diagnosis data update: NOT_STARTED
- DiagnosisLogicV2 update: PROHIBITED / NOT_REQUIRED
- Work implementation: NOT_STARTED

次工程は、Chat側でBlue Guardian Nano / BNPLのMaster必須フィールドを埋め、Workへ渡す**最小データ差分仕様**を完成させること。
