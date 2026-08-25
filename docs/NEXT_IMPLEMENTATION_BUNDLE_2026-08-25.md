# Next Implementation Bundle 2026-08-25

確認日：2026-08-25 JST
対象：Production Version 81 から分岐する次回未公開Work

## 実装bundle

次回Workでは以下を1つの未公開bundleとして扱う。

1. `docs/WORK_WAVE_A_B_SPEC_2026-08-25.md`
   - Price P0：The5ers Futures / Blueberry Futures
   - Evidence-backed Home Pain Router 6 routes
   - SEO technical P0 audit

2. `docs/FINTOKEI_ACADEMY_POINT_STAGE_LP_SPEC_2026-08-25.md`
   - Fintokei Point Stage news article
   - Academy-first導線
   - 50%OFF特典は最新App表示確認付き
   - Academy CTA 3点
   - Fintokei本体AffiliateはAcademy後段
   - Academy XP / Main Point Stage XP分離
   - Point Stage / Scaling Dojo分離

## 実装順

Phase A：Price P0
↓
Phase B：Home Pain Router
↓
Phase C：SEO technical audit
↓
Phase D：Fintokei Academy × Point Stage article
↓
Fresh regression / build / lint / diff / render
↓
停止

## Phase D route

推奨：`/articles/fintokei-academy-point-stage`

既存Article routing patternへ合わせる。

Home全文掲載は禁止。Homeの `最新の変更 / 学ぶ` から記事へ内部リンクを追加する。

新規route architectureを作り直さない。

## Phase D fresh check

- Article HTTP / render正常
- H1 1件
- canonical self
- Article / Breadcrumb structured dataがvisible contentと整合
- Header imageがある場合欠損0
- Academy CTA 3箇所
- iPhone / Androidリンク正常
- Fintokei本体Affiliate CTAはAcademy説明より後段
- PR明示あり
- 新Special = 未解放 / countdownのscope保持
- 50%OFF = App最新条件確認のcaution保持
- Academy XPとMain XPを合算していない
- Point StageとScaling Dojoを混同していない
- Diagnosis / Firm rankingへdiscountを接続していない
- internal links正常
- sitemapへ新規Articleを追加する場合canonicalと一致

## Release protection

- Version保存しない
- publishしない
- V81を変更しない
- 既存Graphic 4点変更しない
- DiagnosisLogicV2変更しない
- GA4 existing event変更しない

最終判定：
`Next Implementation Verification = PASS / PASS_WITH_CAUTION / FAIL`

公開直前にはFintokei Academy 50%OFFとMyFintokei新Specialの状態だけfresh確認する。未解放から解放済みへ変わっていた場合は記事の時制だけ正しく更新し、条件を推測しない。
