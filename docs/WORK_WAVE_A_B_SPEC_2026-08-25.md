# Work Wave A+B Spec 2026-08-25

確認日：2026-08-25 JST
対象：Production Version 81 から分岐する未公開Work
目的：公開後に確認できた価格穴を解消し、Historical VOC Evidenceに基づく6-route Home Pain Routerを最小差分で追加する。SEO技術確認も同一セッションで行うが、大規模なSEO copy変更はしない。

## 0. 絶対原則

- Production Version 81を直接変更しない
- 未公開Workでのみ作業
- 新規調査禁止。本仕様を正本とする
- Version保存 / commit / push / publish禁止
- DiagnosisLogicV2 / 7問 / scoring変更禁止
- Affiliate / coupon / priceをDiagnosisへ接続禁止
- Graphic 4点変更禁止
- Firm / Plan追加禁止
- Current / Legacy / listed-only / Block判定変更禁止
- base price / official campaign / personal couponを分離
- 既存URL / canonical / redirectを壊さない
- 390px実画面は既知NOT_EXECUTABLEなら再試行しない。CSS/DOMで回帰確認する

---

# Phase A｜Price P0 patch

## A1 The5ers Futures｜Day Trade

現在publicの「価格を確認中」を解消。

Canonical：

- 25K = $59
- Activation fee = None
- note：公式ページに3rd payoutでrefundとの記載

実装：

- status：確認中 → 確認済み
- public：`25K $59`
- activation：`なし`
- note：`3回目のPayoutで返金と公式記載。購入前に現行購入画面を確認。`
- 50K等はscale表示からpurchase entry priceを推測しない
- affiliate / couponは既存commercial layerを維持

Official source：
`https://www.the5ers.com/futures/`

## A2 Blueberry Futures｜Accelerated

Standard evaluation base price：

- 25K = $129
- 50K = $184
- 100K = $276
- 150K = $454

実装：

- status：確認中 → 確認済み
- 4サイズのstandard base priceを表示
- 60% discount後価格をbase priceへ混ぜない
- campaign / affiliate codeは既存campaign layerを維持
- 自動割引計算を追加しない

Official source：
`https://help.blueberryfutures.com/en/articles/11196037-what-are-your-prices-for-evaluations`

補助：
`https://help.blueberryfutures.com/en/articles/12921219-accelerated-account-specs-rules-targets`

## Phase A期待値

- Price pending count：2 → 0
- Firm = 14
- PlanCatalog = 72
- Diagnosis = 64
- Block = 5
- SourceHealth = 16

---

# Phase B｜Evidence-backed Home Pain Router

正本：

- `docs/HISTORICAL_VOC_EVIDENCE_CODING_2026-08-25.md`
- `docs/HOME_PAIN_ROUTER_SPEC_2026-08-25.md`
- `docs/HOME_PAIN_ROUTER_ROUTE_MAP_2026-08-25.md`

X事前検証は不要。6つはSTRONG evidence routeとして採用。

## B1 Hero

現行ブランド思想を維持しつつ、Firm / 商品起点ではなくDecision Routerへ寄せる。

H1：
`どのプロップファームを選ぶかの前に、失格・出金・信頼性を確認しよう。`

Sub：
`今の悩みから必要な情報だけ確認して、自分に合う候補まで順番に進めます。`

Primary CTA：
`今の悩みから見る`

Secondary CTA：
`30秒診断へ`

HeroでFirm名 / price / campaignを主役にしない。

## B2 「あなたは今どこ？」6 cards

順序固定：

### R01
Heading：`初めてで、何から見ればいいか分からない`
Sub：`仕組み・失格ルール・出金・選び方を順番に確認します。`
Link：`/beginner-guide`

### R02
Heading：`失格ルールが複雑で、どこで失格するのか不安`
Sub：`Daily Loss・Max Loss・DD・禁止事項を先に整理します。`
Link：`/daily-loss-vs-max-loss`

### R03
Heading：`利益はあるけど、出金条件やKYCが不安`
Sub：`出金日・Consistency・Profitable Days・KYCを確認します。`
Link：`/first-payout-checklist`

### R05
Heading：`日本から本当に使えるか、日本語で困らないか確認したい`
Sub：`日本居住者利用可否・日本語UI・サポート・KYCを分けて確認します。`
Link：`/japanese-support-prop-firms`

### R04
Heading：`1-Step・2-Step・Instantのどれが自分向きか分からない`
Sub：`早さだけでなく、利益目標とDDの余裕から違いを確認します。`
Link：`/one-step-two-step-instant`

### R06
Heading：`前に見た情報が古くないか、今のルールを確認したい`
Sub：`現在ルール・旧モデル・公式情報差・変更履歴を分けて確認します。`
Link：Home内 `最新の変更 / Rule Change` section anchor

R06実装：
- 既存anchorがあれば再利用
- なければHome内の該当sectionに安定ID `latest-changes` を追加
- 新規pageは作らない

Card CTA：`確認する`

## B3 UI原則

- 6 cards
- Mobile 1 column
- Desktopは視認性優先の2〜3列
- 1 card = 1 pain
- Firm logo / price / couponをcard内に出さない
- 赤い警告UIを乱用しない
- 恐怖喚起より「整理できる」トーン
- 既存Graphicを移動・差替えしない
- Homeの既存順序を以下に寄せる：
  1 Hero
  2 Pain Router
  3 失格 / 出金 / 信頼性
  4 Beginner 5 Steps
  5 Evidenceの見方
  6 30秒Diagnosis
  7 Firm → Plan Selector
  8 最新の変更
  9 学ぶ / Guides
  10 Price / Campaign / Coupon

既存sectionを大量削除しない。必要な場合は並び・見出しの最小変更のみ。

## B4 Evidence section

既存表示を壊さない範囲で、見出し/説明を整理できる場合のみ最小対応。

見出し候補：
`「確認済み」の意味も、分けて表示します。`

Public label候補：
- 公式確認済み
- 公式情報を確認中
- 公式内で情報差あり
- 旧モデル
- 日本人利用報告あり
- 出金Evidenceあり

禁止：
- Internal Confidence %
- SourceHealth
- Block Top3
- Affiliate関係をEvidence評価へ反映
- Payout Evidenceを将来Payout保証として表現

## B5 GA4

初版で新規event追加禁止。

- existing `beginner_course_*`
- existing `diagnosis_start / diagnosis_complete`

を保護。

`pain_route_click` は別Gate。今回追加しない。

---

# Phase C｜SEO technical P0 audit only

大幅なtitle/meta変更を行わない。

Google Search Console現状：

- sitemap 22 URLs
- HomeはSubmitted and indexed
- 優先7記事はURL Inspection時点で `URL is unknown to Google`
- live on-page auditで critical / high / medium = 0
- News / Weekend / Minimum Trading Days等にthin-content low issueあり

今回Workが行うのは技術確認のみ：

- sitemap current URLs 200
- canonical self-consistent
- robots indexability
- title duplicate 0
- meta description duplicate 0
- H1 exactly 1 / indexable page
- internal broken link / 404 = 0
- structured dataとvisible content整合
- current/verified date矛盾0
- Hero/Pain Routerから既存Guideへの内部リンクが正常

記事の大規模リライトは今回しない。

---

# Fresh verification

最低限：

1. Price pending = 0
2. The5ers Futures 25K $59 / activationなし
3. Blueberry Futures 25K129 / 50K184 / 100K276 / 150K454
4. discount / campaign混入なし
5. Home 6 cards全表示
6. 6 card link正常
7. R06 latest-changes anchor正常
8. Beginner CTA正常
9. Diagnosis start→Q1〜Q7→Top3正常
10. BG/Hantec selector/detail smoke
11. Firm14 / Plan72 / Diagnosis64 / Block5 / SourceHealth16
12. P042 / P070-P072 Top3混入0
13. Graphic4/4読込 / hash不変
14. DiagnosisLogicV2 hash不変
15. GA4 hash不変
16. Sitemap/canonical regression
17. 390px CSS/DOM horizontal overflow 0
18. normal desktop fresh render
19. site console error 0
20. existing regression PASS
21. build PASS
22. lint error 0（existing warningは分離）
23. git diff --check PASS
24. 新規BLOCKER / CRITICAL = 0

## Expected judgement

`Wave A+B Verification = PASS / PASS_WITH_CAUTION / FAIL`

390px実画面が既知NOT_EXECUTABLEのみならPASS_WITH_CAUTION可。

Version保存 / commit / push / publishは行わず、最終報告で停止。
