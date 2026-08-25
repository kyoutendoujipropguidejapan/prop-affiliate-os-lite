# RETROSPECTIVE TRIPLE FACT CHECK AUDIT

更新日：2026-08-26 JST
Status：APPROVED AUDIT PROGRAM / NO PRODUCTION CHANGE
Scope：既存公開物・既存制作物・既存Canonical候補

## 0. Purpose

2026-08-26以前に作成・公開したコンテンツにも、FACT CHECK STANDARD v1の最低3回ルールを遡及適用する。

新規制作物だけを厳格化し、既存公開物を旧基準のまま放置しない。

## 1. Audit Priority

### P0 — Current Public Production

最優先。

対象：
- Home
- Diagnosis周辺の説明
- Firm/Plan表示
- FAQ
- 価格
- Coupon
- Campaign
- Affiliate CTA近傍の条件表示
- 日本利用可否・日本語対応
- Daily Loss / Max Loss / DD
- payout条件
- service nature / disclaimer

高リスクFactから先に実施する。

### P1 — Active Commercial Content

- 現行キャンペーン
- 現行クーポン
- 現行Affiliate特典
- 現在配信中の記事・投稿からの購入導線

期限・対象者・割引率・併用可否を重点確認。

### P2 — Published Firm / Platform / Payout / Comparison Content

- Firm解説
- Platform解説
- Payout解説
- 比較記事
- FAQ記事
- 初心者ガイドのFact部分

### P3 — Published Editorial / Case Study / B2B

- ニュース
- レビュー
- ケーススタディ
- B2B資料

意見とFactを分離して検証する。

### P4 — Internal / Draft Assets

- GitHub Handoff docs
- 未公開spec
- Evidence候補
- 過去Master/Artifact

Public Truthへ再利用する前に3回チェックへ移行する。

## 2. Triple Check Contract

各Factごとに最低：

1. Check 1：一次情報確認
2. Check 2：別公式導線/規約/FAQ/checkout/direct contact等で独立再照合
3. Check 3：修正・再公開直前のfresh recheck

同一ページを3回読むだけでは原則3回と数えない。

## 3. Existing Public Fact Status

遡及監査が未完了の既存Factは、直ちに誤り扱いにはしない。

ただし監査状態を以下で管理する：

- `LEGACY_UNAUDITED`
- `CHECK1_PASS`
- `CHECK2_PASS`
- `CHECK3_PASS`
- `TRIPLE_VERIFIED`
- `VERIFIED_WITH_CAUTION`
- `CONFLICT`
- `STALE`
- `CORRECTION_REQUIRED`
- `HOLD`

既存公開Factを、過去に1回確認済みだったという理由だけで`TRIPLE_VERIFIED`へ昇格しない。

## 4. Immediate Correction Rule

遡及監査中に以下を発見した場合：

- 失格条件の誤表示
- 価格/割引/期限の誤表示
- 日本利用可否の誤表示
- payout条件の誤表示
- service nature / regulatory statusの重大誤認
- expired campaignをcurrent表示

Statusを`CORRECTION_REQUIRED`または`HOLD`にし、Production reconciliation後の最小修正候補へ上げる。

多数決で押し切らない。

## 5. Current Known P0 Signals

Production reconciliation後に優先再監査する既知項目：

- Fintokei 速攻プロ current new-purchase cohort
- The5ers Futures Day Trade 25K price
- Blueberry Futures Accelerated base prices
- Hantec Instant Lite HOLD/source state
- FTM Instant Pro conflicting Daily DD representations
- Funded7 One Phase / Instant conflicts
- FundedElite Flash base vs customizable options
- Fundora active campaign state
- Fintokei Academy benefit conditions

この一覧は確定Fact一覧ではなく、監査優先Signal一覧。

## 6. Publication / Correction Gate

既存公開Factの修正時も：

- check count >= 3
- unresolved high-risk conflict = 0
- scope / cohort / locale確定
- effective period確認
- compliance gate PASS
- human approval when HOLD/C2/C3

未達なら`FACT_CHECK_HOLD`。

## 7. Audit Recording Minimum

各監査対象で最低保存：

- claim_id
- page/asset
- claim text/value
- scope
- Check 1 source + checked_at
- Check 2 source + checked_at
- Check 3 source + checked_at
- conflict notes
- final status
- correction required yes/no
- evidence ids where available

## 8. Work Boundary

内部Git認証復旧までは、Productionコード修正はしない。

Chat/GitHub Handoff側では：

- 公開面のSignal抽出
- 公式Source再確認
- audit packet作成
- correction candidate整理

まで進める。

認証復旧後：

1. Current Production reconciliation
2. P0 public audit
3. correction candidate最小patch
4. fresh Check 3
5. QA
6. publish approval

## 9. Completion Definition

完了条件：

- Current Productionの高リスクFact 100%がTriple Verified / Verified With Caution / HOLDのいずれかに分類
- Active commercial Fact 100%分類
- Firm/Plan/FAQのFactが順次分類
- `LEGACY_UNAUDITED`を最終的に0へ近づける

一括で速度優先の雑な監査はしない。高リスク・公開中・収益導線の順で処理する。

Final Status：
`RETROSPECTIVE_TRIPLE_FACT_CHECK_AUDIT_ACTIVE`
