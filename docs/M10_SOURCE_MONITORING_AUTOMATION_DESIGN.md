# M10｜公式ソース監視 自動化技術設計

更新日：2026-08-16
対象：プロップファームの歩き方
前提：M05 Source Monitoring Spec / M06 SourceHealth / Master v2.2

## 0. 目的

14社の公式情報確認を、毎回の全ページ再調査から次の流れへ移行する。

`公式URL監視 → 差分取得 → ノイズ除去 → 意味差分分類 → SourceHealth照合 → 人間承認 → 正本更新候補`

**変更検知からサイト公開までを自動化しない。**

初期MVPでは「変更候補を見つけて証拠を残す」ところまでを自動化し、正本反映と公開は人間確認を必須とする。

---

# 1. 推奨アーキテクチャ

## GitHub

役割：履歴と正本候補の保存。

保存するもの：

- 監視URL一覧
- 監視設定
- 取得Snapshotのメタデータ
- 意味差分イベント
- 人間承認結果
- SourceHealth更新候補
- 実装コード
- テスト

GitHubを「いつ、何が、なぜ変わったか」の監査ログにする。

## Replit

役割：将来のFetcher / Parser / Diff Workerの実行環境候補。

- HTTP取得
- HTML正規化
- Content extraction
- hash比較
- Diff作成
- ルールベース分類
- 結果の一時保存

無料/低コスト運用を優先し、常時稼働が必要な構成にしない。

## ChatGPT

役割：意味差分の確認・Source Priority判断・SourceHealth判断・公開文案。

機械差分だけでは判断しにくい、

- 数値変更の意味
- 旧新ルール
- プラン違い
- FAQ更新遅延
- 公式ソース競合

を人間と一緒に判定する。

## Work

役割：承認された正本をサイトへ反映。

監視WorkerからWorkへ直接書き込まない。

---

# 2. データフロー

1. `monitor_sources` から対象URL選択
2. HTTP fetch
3. raw response metadata保存
4. main content抽出
5. normalize
6. normalized hash計算
7. 前回hashと比較
8. 変更なし →終了
9. 変更あり → textual diff作成
10. noise filter
11. semantic candidate抽出
12. change type分類
13. severity評価
14. SourceHealth関連確認
15. `change_event`保存
16. 人間確認キューへ
17. 承認/却下/継続確認
18. 承認済みのみMaster/SourceHealth更新候補へ
19. Work反映は別工程

---

# 3. 推奨データ構造

## monitor_sources

```text
source_id
firm_id
firm_name
url
source_type
source_priority
watch_category
frequency
critical_keywords
ignore_patterns
sourcehealth_ids
active
last_checked_at
last_success_at
last_hash
```

## source_snapshots

```text
snapshot_id
source_id
checked_at
http_status
final_url
etag
last_modified
content_hash
normalized_hash
content_length
extractor_version
raw_storage_ref
normalized_storage_ref
```

raw全文を無期限でGitHubへ大量Commitする必要はない。MVPでは意味差分に必要な抜粋とhashを中心に保持する。

## change_events

```text
change_id
source_id
detected_at
previous_snapshot_id
current_snapshot_id
change_type
severity
changed_fields
old_value
new_value
context_excerpt
source_priority
sourcehealth_ids
confidence
status
reviewer
reviewed_at
review_note
```

status候補：

- NEW
- NOISE
- NEEDS_CROSSCHECK
- CONFLICT
- CONFIRMED
- REJECTED
- CHANGELOGGED
- READY_FOR_WORK

---

# 4. Change Type

- PLAN_CHANGE
- RULE_CHANGE
- PRICE_CHANGE
- CAMPAIGN_CHANGE
- ELIGIBILITY_CHANGE
- PLATFORM_CHANGE
- PAYOUT_CHANGE
- KYC_CHANGE
- AFFILIATE_CHANGE
- SOURCE_CLARIFICATION
- CONTENT_ONLY
- UNKNOWN

`CONTENT_ONLY` はSEO文章変更、デザイン文言、並び替え等でルール意味差分がないもの。

---

# 5. 正規化

HTMLそのまま比較は禁止。

除外候補：

- script
- style
- cookie banner
- nav/footerの定型文
- tracking query
- session ID
- timestamps
- random DOM ids
- A/B test attributes
- social counters
- unrelated testimonial rotation

正規化：

- whitespace collapse
- Unicode normalization
- smart quote統一
- currency/percent周辺の空白統一
- hidden text除外
- navigation重複除外

ただし数値、日付、％、プラン名、国名、platform名は消さない。

---

# 6. Critical Token検出

優先的に意味差分候補へ上げる語群。

## Risk / Rule

- daily loss
- daily drawdown
- maximum loss
- max loss
- drawdown
- static
- trailing
- end of day
- EOD
- consistency
- risk per trade
- lot

## Evaluation

- profit target
- minimum trading days
- maximum trading days
- phase

## Trading permission

- news trading
- weekend holding
- EA
- expert advisor
- copy trading
- prohibited

## Payout

- payout
- reward
- profit split
- withdrawal
- minimum profit
- consistency

## Eligibility

- restricted countries
- prohibited countries
- residents
- Japan
- KYC
- age

## Platform

- MT5
- MT4
- cTrader
- Match-Trader
- TradeLocker

## Commercial

- price
- discount
- coupon
- promotion
- affiliate
- referral

日本語公式ページの場合は対応日本語語彙も辞書へ追加する。

---

# 7. 数値差分の優先度

数値変更は全文差分より先に構造抽出する。

例：

```text
Daily Loss: 5% → 4%
Max Loss: 10% → 8%
Profit Target: 8% → 10%
Profit Split: 80% → 90%
Minimum Days: 3 → 1
```

以下は原則CRITICAL候補：

- Daily Loss
- Max Loss
- DD方式
- Profit Target
- Minimum Days
- Payout条件
- Profit Split
- Restricted Countries
- Japan eligibility
- KYC
- News/Weekend禁止

価格・Campaignは重要だが診断ロジックへ直接入れない。

---

# 8. Noise Filter

## 自動NOISE候補

- footer copyright年
- Cookie文言
- social follower count
- testimonial順序
- unrelated blog一覧更新
-画像URL hash変更のみ
- CSS class変更のみ
- Tracking parameter

## 人間確認へ残す

- 数値が1文字でも変わった
- `allowed` ↔ `prohibited`
- `static` ↔ `trailing`
- country list追加削除
- plan name追加削除
- platform追加削除
- payout cadence変更
- Effective date追加
- grandfathering表現

---

# 9. Source Priority Gate

Source Priority：

A1 Terms / formal Rules
A2 Help / Support
A3 FAQ
A4 Product / Pricing
A5 official email / partner material
B1 official SNS
C1 user evidence
D1 third party

判断ルール：

- A4変更だけでA1/A2と矛盾 → `NEEDS_CROSSCHECK`
- A1とA2が一致 → `CONFIRMED`候補
- A1/A2が不一致 → `CONFLICT`
- SNSだけでルール変更 → Master変更不可
- campaignは公式campaign/product pageで確認可能なら別扱い

---

# 10. SourceHealth接続

既存SourceHealth IDが紐づくURLで変更が出た場合、通常Changeより優先する。

処理：

1. 既存Conflict内容取得
2. 新Snapshotが競合のどちら側を支持するか
3. もう一方の公式Sourceも再取得
4. 2つ以上整合するか
5. effective date確認
6. variant/phase/account size確認
7. 解消可否を人間判断

1ページの更新だけでBlock解除しない。

---

# 11. Fintokei速攻プロ 特別ルール

M06結論を保持。

Block解除候補条件：

```text
effective_from >= 2026-07-15
new_purchase_only = true
legacy_account_separated = true
human_approved = true
```

監視で新情報が出ても、購入日境界を消さない。

旧口座の扱いが不明になった場合は安全側へ戻し、Block継続候補にする。

---

# 12. 通知設計

初期MVPでは「すべて通知」しない。

## 即時確認候補

- ELIGIBILITY_CHANGE
- RULE_CHANGEでrisk項目
- PAYOUT_CHANGE
- SourceHealth関連
- plan終了/新規追加

## 日次まとめ候補

- PRICE_CHANGE
- CAMPAIGN_CHANGE
- AFFILIATE_CHANGE

## 通知不要

- NOISE
- CONTENT_ONLY（重大意味差分なし）

通知には必ず：

- Firm
- Source
- detected_at
- old → new
- context
- Source Priority
- SourceHealth関係
- 人間に何を確認してほしいか

を含める。

---

# 13. 実行頻度MVP

M05のSource Monitoring Specを正本とする。

技術側の基本：

- 日次：Campaign / Price / plan availability
- 週次：Rules / FAQ / Payout / Platform
- 月次：Eligibility / KYC / Legal

SourceHealth関連は週次を基本に、公式変更を検知したら関連Sourceを同時再確認する。

全URLを毎時監視しない。

---

# 14. Failure Handling

## HTTP error

- 429 → retry/backoff
- 403 → Browser必要フラグ、無限retryしない
- 404 → SOURCE_REMOVED候補、人間確認
- 5xx → 次回再試行
- redirect → final URL記録

## Parser failure

前回Snapshotを上書きしない。

`PARSER_FAILED`として保存し、変更扱いにしない。

## Site redesign

normalized contentが極端に変化した場合、RULE_CHANGEではなく`PARSER_REVIEW`へ。

---

# 15. Security / Safety

- login必須/private portalを無理にスクレイピングしない
- passwords/API keysをRepoに保存しない
- robots/利用条件へ配慮
- 高頻度アクセス禁止
- third party contentを正本に昇格しない
- HTMLをそのまま実行しない
- fetched contentはuntrusted inputとして扱う

---

# 16. GitHub出力案

MVPでは変更イベントごとに大量Commitしない。

推奨：

```text
data/monitor_sources.json
state/source_state.json
changes/YYYY-MM/change_<id>.json
```

重大変更のみGitHub Issue候補：

Title例：

`[RULE_CHANGE][Fintokei] Swift Daily Loss candidate change`

Issue body：Source / old / new / evidence / priority / SourceHealth / review checklist。

ただしIssue自動作成も初期はdry-run確認後に有効化する。

---

# 17. 段階導入

## Phase A｜Dry Run

5 URL程度。

対象例：

- ルール
- Restricted Countries
- Campaign
- SourceHealth関連2件

2週間程度、検知精度を確認。

## Phase B｜14社最小監視セット

M05で定義した最小URLへ拡張。

## Phase C｜通知

CRITICAL候補のみ通知。

## Phase D｜SourceHealth workflow

競合関連を自動でcross-check queueへ。

## Phase E｜Work handoff

CONFIRMEDイベントからWork更新候補を生成。

**サイト自動公開はPhase Eでも行わない。**

---

# 18. テスト

必須：

- same HTML → no change
- footer year only → NOISE
- Daily Loss 5→4 → RULE_CHANGE/CRITICAL
- discount 30→40 → CAMPAIGN/PRICE
- Japan removed from restricted list → ELIGIBILITY_CHANGE
- static→trailing → RULE_CHANGE/CRITICAL
- 404 → source review
- A4 only change vs A1 conflict → NEEDS_CROSSCHECK
- SourceHealth page change → cross-check required
- Fintokei effective date condition lost → Block release不可

---

# 19. MVP実装範囲

最初の実装はここまでで十分。

1. monitor_sources読込
2. fetch
3. normalize
4. hash compare
5. diff
6. keyword/numeric extraction
7. change type分類
8. JSON event保存
9. dry-run report

LLM自動判定、GitHub Issue自動作成、通知、自動Master更新は後段。

---

# 20. M10受入条件

- M05監視仕様を技術実装へ変換できる
- HTML差分と意味差分を分離
- Source Priority gateがある
- SourceHealthを自動解消しない
- 人間承認が必須
- Fintokei条件付き解除を保持
- 失敗時に前回正本を破壊しない
- 低頻度/低コストMVPから開始できる
- Work/サイトへ直接書き込まない
- 将来Replit/GitHubへ実装可能なデータ構造を持つ

---

# 21. 実装開始時プロンプト

ReplitまたはCodexで実装する場合：

「`docs/M10_SOURCE_MONITORING_AUTOMATION_DESIGN.md` を正本として、まずPhase A Dry RunのMVPだけを実装してください。サイト更新、Master自動更新、通知、自動Issue作成はまだ実装しないでください。対象URLは5件以下。fetch→normalize→hash→diff→分類→JSON保存まで。テストを先に作り、SourceHealth関連とFintokei条件付き解除を安全側に扱ってください。」
