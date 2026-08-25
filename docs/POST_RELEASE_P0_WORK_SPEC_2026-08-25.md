# Post-release P0 Work Spec 2026-08-25

確認日：2026-08-25 JST
対象：Production Version 81 から分岐する未公開Work
目的：V81公開後に確認できた価格穴とpublic status整合だけを最小patchし、SEOの安全な技術確認を行う。

## 0. 原則

- Version 81本番は直接変更しない
- 未公開Workで実装・検証する
- DiagnosisLogicV2 / 7問 / scoring / Block 5は変更しない
- Graphic 4点は変更しない
- 新規Firm / Plan追加なし
- Affiliate / coupon / campaignをranking / diagnosisへ接続しない
- base price / campaign / personal couponを分離する
- Version保存 / publishは明示承認まで禁止
- 公式再調査は行わない。この仕様の値を正本として使う

## 1. PriceOffers：The5ers Futures Day Trade

現在publicの「価格を確認中」を解消する。

公式確認値：

- Plan：The5ers Futures｜Day Trade
- Account Size：25K
- Base Price：$59
- Activation fee：None
- Note：公式ページにRefunded on 3rd payoutと記載

実装：

- status：確認中 → 確認済み
- public表示：`25K $59`
- Activation fee：`なし`
- note：`3回目のPayoutで返金と公式記載。購入前に現行購入画面を確認。`
- 50Kはscale表に出るが、購入entry priceとして推測しない
- affiliate link / coupon条件は既存の別レイヤーを維持

公式URL：
`https://www.the5ers.com/futures/`

## 2. PriceOffers：Blueberry Futures Accelerated

現在publicの「価格を確認中」を解消する。

Standard evaluation base price：

- 25K：$129
- 50K：$184
- 100K：$276
- 150K：$454

実装：

- status：確認中 → 確認済み
- 4サイズのstandard base priceを表示
- 60% discount後価格はbase priceへ混ぜない
- FUTURES60等のcampaign / affiliate codeは既存campaignレイヤーのまま
- 自動で割引後価格を計算しない

公式URL：
`https://help.blueberryfutures.com/en/articles/11196037-what-are-your-prices-for-evaluations`

補助URL：
`https://help.blueberryfutures.com/en/articles/12921219-accelerated-account-specs-rules-targets`

## 3. Public SourceHealth / 確認中一覧 fresh audit

V81 actual canonical：

- PlanCatalog 72
- Current 67
- Legacy / ended 4
- Listed-only 1
- Diagnosis 64
- Block 5
- SourceHealth 16

Fresh renderでpublicの「確認中」一覧とFirm詳細を確認する。

重点：

### Hantec Instant Lite

期待：

- Daily 3%
- Standard Max 5%
- Add-on 6%
- SH003 RESOLVED
- 旧 `本文5% / Add-on記載は標準6%を示唆` 表現がpublicに残っていない
- 診断Top3 Blockではない

### Blue Guardian 3 Step

期待：

- Legacy表示
- Currentに混入しない
- Diagnosisへ混入しない

### Blue Guardian Nano / BNPL

期待：

- P070 / P071 Active catalog
- P072 Active WITH_CAUTION
- 3件ともDiagnosis未接続
- BNPL Profit Split conflictを勝手に一本化しない

### SourceHealth summary

- resolved itemを「現在確認中」として古いまま表示しない
- historyとcurrent cautionを分ける
- 件数は16 canonicalと整合するか、publicがcurrent-onlyならそのcontractに従う

差異があれば、表示レイヤーのみ最小修正。Master canonicalを再解釈しない。

## 4. SEO technical P0 audit

この段階ではGA4 / GSC実データなしでtitleを大幅変更しない。

確認のみ：

- sitemap current URLs all 200
- canonical self-consistent
- robots indexability
- title duplicate 0
- meta description duplicate 0
- H1 exactly 1 / indexable page
- internal 404 = 0
- structured data visible contentと一致
- updated / verified dateの表示がV81の内容と矛盾しない
- article → related rule article → diagnosis の内部リンクが切れていない

重点記事：

- `/one-step-two-step-instant`
- `/daily-loss-vs-max-loss`
- `/fixed-vs-trailing-drawdown`
- `/articles/news-trading-rules`
- `/articles/weekend-holding-rules`
- `/articles/minimum-trading-days`
- `/first-payout-checklist`

## 5. SEO copy候補は実装せずレポートのみ

GSC / GA4データ取得前なので、以下は変更しないで候補として報告する。

Home title candidate：
`プロップファーム比較【2026年】14社72プラン｜ルール・出金・30秒診断`

Home meta candidate：
`日本から使えるプロップファーム14社・72プランを、日次損失・最大損失・出金・ニュース取引などのルールから比較。7問の30秒診断で条件に合う候補を3つまで絞れます。`

実装はSearch Consoleのquery / impressions / CTRを確認後。

## 6. 検証

最低限：

1. Firm 14
2. PlanCatalog 72
3. Diagnosis 64
4. Block 5
5. SourceHealth 16
6. Price pending count：2 → 0
7. The5ers Futures Day Trade：25K $59
8. Blueberry Futures Accelerated：4サイズstandard price
9. discount計算 / campaign混入なし
10. Hantec current表示正常
11. BG 3 Step Legacy正常
12. BG Nano / BNPL Diagnosis混入0
13. DiagnosisLogicV2 hash不変
14. Graphic 4点hash不変
15. GA4 hash不変
16. sitemap / canonical / structured data regression
17. existing regression PASS
18. build PASS
19. lint error 0
20. git diff --check PASS
21. site console error 0

390px実画面は別human check。Work環境で既知NOT_EXECUTABLEなら再試行しない。

## 7. 最終報告

- 変更ファイル
- Price pending actual count
- The5ers Futures price表示
- Blueberry Futures Accelerated 4サイズ表示
- SourceHealth public整合結果
- Hantec / BG fresh結果
- technical SEO audit結果
- title / meta候補（未実装であること）
- protected hash
- tests / build / lint / diff
- 新規BLOCKER / CRITICAL

判定：`Post-release P0 Verification = PASS / PASS_WITH_CAUTION / FAIL`

Version保存 / publishは行わない。
