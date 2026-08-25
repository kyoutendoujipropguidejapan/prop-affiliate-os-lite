# Home Pain Router Route Map 2026-08-25

確認日：2026-08-25 JST
対象：`HOME_PAIN_ROUTER_SPEC_2026-08-25.md` の6 primary routes
目的：新規ページを急増させず、既存URLを最大限使ってPain Routerを実装可能な状態にする。

## 0. 原則

- 既存URL / canonicalを壊さない
- redirect変更なし
- 新規Hubは必要になってからadditiveに追加
- Router初版は既存Guideへ送る
- 価格 / couponへ直接送らない
- DiagnosisLogicV2変更なし

---

## R01 はじめて

表示：`初めてで、何から見ればいいか分からない`

Primary URL：`/beginner-guide`

内部Journey：

- `/beginner-guide/what-is-a-prop-firm`
- `/beginner-guide/no-need-to-buy-yet`
- `/beginner-guide/three-things-to-check`
- `/beginner-guide/rules-that-cause-disqualification`
- `/beginner-guide/find-your-fit`
- Diagnosis

状態：EXISTING / READY

---

## R02 失格ルールが不安

表示：`失格ルールが複雑で、どこで失格するのか不安`

Primary URL：`/daily-loss-vs-max-loss`

Related：

- `/fixed-vs-trailing-drawdown`
- `/articles/news-trading-rules`
- `/articles/weekend-holding-rules`
- `/articles/minimum-trading-days`

状態：EXISTING / READY

改善：Primary articleから上記関連Guideへの文脈内部リンクを強化。

---

## R03 出金・KYCが不安

表示：`利益はあるけど、出金条件やKYCが不安`

Primary URL：`/first-payout-checklist`

Related：

- `/prop-firm-payout-comparison`
- Firm / Plan DetailのPayout fields

状態：EXISTING / READY

将来：Payout Evidence Hub追加後にPrimary route再評価。

---

## R04 どの形式が合うか分からない

表示：`1-Step・2-Step・Instantのどれが自分向きか分からない`

Primary URL：`/one-step-two-step-instant`

Next：Diagnosis

状態：EXISTING / READY

---

## R05 日本から使えるか確認したい

表示：`日本から本当に使えるか、日本語で困らないか確認したい`

Primary URL：`/japanese-support-prop-firms`

Next：Firm → Plan Detail

状態：EXISTING / READY

注意：ページ本文で以下を分離：

- 日本居住者利用可否
- 日本語サイト
- 日本語管理画面
- 日本語FAQ
- 日本語Support
- KYC / payoutのJapan-specific evidence

---

## R06 情報が古くないか確認したい

表示：`前に見た情報が古くないか、今のルールを確認したい`

専用URL：現時点では未確定。

Initial fallback：Home内の `最新の変更 / Rule Change` section anchor。

実装時に現在のDOM anchorが存在しなければ、既存Homeへ安定ID（例：`latest-changes`）だけ追加してカードをそこへ送る。

新規ページは初版では作らない。

状態：FALLBACK_READY / DOM ID要確認

将来候補：`/changes/` または `/latest-changes/` は、Change Log Data Layerが十分蓄積してから作る。

---

# 初版実装可否

- R01 READY
- R02 READY
- R03 READY
- R04 READY
- R05 READY
- R06 DOM anchor確認のみ

新規コンテンツページを作らずに6 routesの初版を実装可能。

---

# GA4

初版では新規eventを増やさない。

理由：

- 現行GA4 event architectureを保護
- Router導入とanalytics変更を同一patchに混ぜない
- GA4接続後、landing page / page path / flowを見て必要性を判断

将来 `pain_route_click` を追加する場合は別Gate。

---

# 実装順

1. V81後Price P0 patch完了
2. R06のHome DOM anchor確認
3. 6 card + Hero CTA + minimal CSS
4. Existing regression
5. 390px CSS/DOM assurance
6. fresh render
7. Version保存 / publishは別承認

Status：ROUTE_MAP_READY
