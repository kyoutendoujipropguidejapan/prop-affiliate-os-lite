# Post-release Gap Audit 2026-08-25

確認日：2026-08-25 JST
対象：Production Version 81
目的：価格未確認・確認中情報・検索流入上の穴を、公開後の改善候補として整理する。

## 0. 結論

Version 81の機能 / Data Patch / Graphicは公開済み。次工程は新規機能追加より、以下の穴埋めを優先する。

1. 価格確認中2件の解消
2. public側の「確認中」表示と最新SourceHealthの整合再確認
3. broad SEO（プロップファーム 比較 / おすすめ / 価格）の弱さを、ルール・失格・出金・方式比較のlong-tail clusterで補強
4. GA4 / Search Console実データが取れ次第、閲覧数・CTR・流入queryベースで優先順位を更新

## 1. 価格確認中2件

### The5ers Futures｜Day Trade

公式Futuresページで現行Day Tradeの25K evaluation priceを確認。

- Account Size：25K
- Price：$59
- Activation fee：None
- refunded on 3rd payout の記載あり
- one-time fee / no monthly fees

公式：
- https://www.the5ers.com/futures/

公開PriceOffers候補：
- status：CONFIRMED
- display：`25K $59`
- note：`3回目のPayoutで返金と公式記載。購入前に現行画面を再確認。`

50Kはscale表に出るが、今回確認できた購入entry priceとしては25K $59をcanonicalにする。50Kを購入価格として推測しない。

### Blueberry Futures｜Accelerated

公式HelpのEvaluation Pricesでstandard priceを確認。

Accelerated / Trailing Drawdown：

- 25K：$129
- 50K：$184
- 100K：$276
- 150K：$454

公式Helpでは60% discount後の参考価格も併記されるが、canonical base priceはstandard priceを採用する。

公式：
- https://help.blueberryfutures.com/en/articles/11196037-what-are-your-prices-for-evaluations
- https://help.blueberryfutures.com/en/articles/12921219-accelerated-account-specs-rules-targets

公開PriceOffers候補：
- status：CONFIRMED
- base_price：25K $129 / 50K $184 / 100K $276 / 150K $454
- campaign priceはPriceOffersのbaseへ混ぜない
- 既存FUTURES60等のcampaign / affiliate条件は別レイヤー維持

## 2. ルール / SourceHealthの穴

Version 81 data canonical：

- PlanCatalog 72
- Current 67
- Legacy / ended 4
- listed-only 1
- Diagnosis 64
- Block 5
- SourceHealth 16

残るBlock：

1. Fintokei 速攻プロ
2. Funded7 1フェーズ
3. Funded7 Instant
4. FTM Instant Pro
5. FundedElite Flash Activation

維持方針：

- 公式内Conflictが解消しない限りBlock解除しない
- 数値を一本化するために古い履歴を削除しない
- Blue Guardian 1 Step Cryptoはlisted-only / HOLD
- Blue Guardian BNPLはActive WITH_CAUTION / Diagnosis未接続

公開側の「確認中情報一覧」は、V81のSourceHealth 16と整合するかを次Workでfresh確認する。特にHantec Instant Liteが旧Conflict表示のまま残っていないか、BG 3 Stepがcurrent扱いで残っていないかを確認する。

## 3. SEO現状スナップショット

2026-08-25の公開検索スナップショットでは、broad query：

- `プロップファーム`
- `プロップファーム 比較`
- `プロップファーム クーポン`
- `プロップファーム 出金`
- `プロップファーム 失格`

で競合の比較 / ranking / beginner guideが強く、当サイトhomeは上位結果として安定表示を確認できない。

一方、long-tail：

- `プロップファーム 1ステップ 2ステップ 違い`

では当サイト `/one-step-two-step-instant` の検索結果露出を確認できた。

判断：

- broad head keywordだけを追うより、既存の「ルール-first」方針でlong-tail clusterを強化する
- rankingサイトを模倣せず、`失格しないためのルール理解`、`DDの違い`、`出金条件`、`評価方式`、`Firm → Plan`で差別化する

## 4. SEO優先cluster

P0：既存記事を強化

- `/one-step-two-step-instant`
- `/daily-loss-vs-max-loss`
- `/fixed-vs-trailing-drawdown`
- `/articles/news-trading-rules`
- `/articles/weekend-holding-rules`
- `/articles/minimum-trading-days`
- `/first-payout-checklist`

各記事に以下を追加 / 確認：

- title先頭にprimary queryを自然に置く
- 100〜160字で検索意図へ即答するintro
- 関連Firm / Planへの内部リンク
- beginner guideへの上流リンク
- diagnosisへの下流CTA
- visible FAQとschemaの一致
- last updated / verified date

P1：価格intent

- 価格ページ / sectionを `プロップファーム 価格 比較` intentへ寄せる
- base price / campaign / personal couponを明確に分離
- canonical priceを自動割引計算しない
- `確認中`が解消した2件を反映

P1：Firm query

専門Manusサイトとのcannibalizationを避けるため、main site側で14社full reviewを量産しない。

main siteは：

- Firmカード
- Plan selector
- rule summary
- official source
- specialist pageがある場合はそこへ自然に接続

に留め、検索意図の重複を監査してから個別firm SEOを増やす。

## 5. CTR改善候補

現在Home titleはブランド名始まりで、broad queryとの一致が弱い可能性がある。

A/B候補：

`プロップファーム比較【2026年】14社72プラン｜ルール・出金・30秒診断` 

ただしtitle変更はSearch Consoleのquery / CTRを見てから実装する。データ無しで即変更しない。

Meta description候補：

`日本から使えるプロップファーム14社・72プランを、日次損失・最大損失・出金・ニュース取引などのルールから比較。7問の30秒診断で条件に合う候補を3つまで絞れます。`

## 6. Analytics / Search Console Gate

実閲覧数 / landing page / query / CTR / positionを使ったブラッシュアップには、GA4 / Google Search Consoleの実データが必要。

取得したい指標：

- 直近28日 / 7日
- pageviews / users / engaged sessions
- landing page別流入
- organic query / clicks / impressions / CTR / avg position
- beginner 01→05→diagnosis transition
- diagnosis_start / diagnosis_complete
- Firm selector open率
- price / coupon section到達率

データが接続できるまでは、public search snapshotを仮シグナルとして使い、実閲覧数とは呼ばない。

## 7. Workへ渡す前の最小patch候補

Analytics確認前に安全に実施可能：

1. The5ers Futures Day Tradeの価格確認中を25K $59へ更新
2. Blueberry Futures Acceleratedをstandard price 4サイズへ更新
3. SourceHealth public listがV81 stateと一致するかfresh確認
4. Hantec old conflict / BG 3 Step old current表示が残る場合のみ表示修正
5. Sitemap / canonical / structured data / internal 404 regression

Analytics取得後：

6. title / meta改善
7. internal link優先順位変更
8. high-impression low-CTR記事のsnippet改善
9. high-view low-diagnosis-completeページのCTA改善

## 8. Status

- V81 Production：COMPLETE
- Price recheck：2件CONFIRMED
- Remaining rule conflicts：5 Block + BG Crypto HOLD + BNPL CAUTION
- SEO public snapshot：COMPLETE
- GA4 / GSC behavioral analysis：PENDING DATA ACCESS
- Work patch：NOT_STARTED
