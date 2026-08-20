# IMPLEMENTATION_READINESS

更新日：2026-08-20 JST
対象：プロップファームの歩き方
目的：Work復活後の実装・監視・公開Gateを一意にする。

## 0. 現在の判定

- Work Day0監査：**完了**
- M07 P0-01〜P0-03：**PASS（Work報告ベース）**
- M07 P0-04 390px Mobile UX：**PASS_WITH_CAUTION**
- M07 P0-05 Firm-first：**PASS（Work報告ベース）**
- M07 P0-06〜P0-08：**PASS（Work報告ベース）**
- M14 FAQ統合：**GO**
- 価格境界 / GA4修正：**FAQ統合後**
- SEO統合：**その後**
- 監視Dry Run：**NO-GO**
- Runtime Snapshot：**NO-GO**
- 本番公開：**NO-GO**

P0-04のCautionは、既存環境に390px fresh render可能なbrowser binary / viewport変更機能がないため公開Gateまで持ち越す。

---

## 1. P0-01〜P0-03

Work報告ベースでPASS。

- Firm = 14
- PlanCatalog = 69
- Diagnosis rows = 65
- SourceHealth = 14
- FundingPips = 5 plans
- SH011〜SH014 synced
- Block 6件維持
- SuperFunded 1-Step = Trailing / min 3 days
- SuperFunded 2-Step = min 4 days each phase
- DiagnosisLogicV2差分なし
- Affiliate / commission / coupon / priceの診断採点混入なし
- 29/29 tests PASS
- build PASS
- lint error 0

## 2. P0-04 / P0-05

### P0-04

**PASS_WITH_CAUTION**。

- 390px CSS / 構造テスト：PASS
- Cloud Browser fresh render：1363x936でPASS
- Playwright packageはあるがbrowser binaryなし
- OS browserなし / CDP未稼働 / Cloud Browser viewport固定
- 390px実画面証跡のみ未取得

### P0-05

**PASS**。

- 14社を会社単位で初期表示
- 69プランは初期閉鎖
- 会社 → プラン一覧 → 詳細の3段階
- HOLD 5 + Fintokei速攻プロを「公式情報を確認中」として区別
- 内部用語を公開UIへ出さない

## 3. P0-06〜P0-08

**PASS（Work報告ベース）**。

変更ファイル：

- `app/route.ts`
- `public/integrated-tools.js`
- `public/home-integrated.css`
- `tests/rendered-html.test.mjs`

確認済み：

- 14社Firm detailの冒頭順を統一：特徴 → 日本語対応 → 無料トライアル → 取引環境 → 注意点 → プラン一覧
- Firm-first 3段階表示維持
- 69プラン初期閉鎖
- 7問 / 質問順 / DiagnosisLogicV2差分なし
- Diagnosis候補65件維持
- Unknownはnull扱い。0 / falseとして確定評価しない
- 結果冒頭に「なぜ、この3つが候補になったのか。」
- 各候補：あなたとの相性 → 理由2点 → 注意1点 → 詳細を見る
- 品質ランキング表現 / 内部用語なし
- Block 6件は実診断Top3へ混入なし
- 30/30 tests PASS
- build PASS
- lint error 0（既存warning 1）
- git diff --check PASS
- 新規BLOCKER / CRITICALなし
- Version保存 / 本番公開なし

Fresh renderはCloud Browser 1363x936で、14社 / 69プラン / 初期展開0 / Firm→Plan→Detail / Top3理由表示を確認。390px Cautionは継続。

---

## 4. 次のGate｜M14 FAQ統合

**GO**。

正本：

- `docs/M11_FIRM_FAQ_CONTENT_PACK.md`
- `docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md`

M14判定：PASS 32 / PASS_WITH_CAUTION 23 / UPDATE_REQUIRED 10 / HOLD 5。

実装ルール：

- PASS：M11を基本維持
- PASS_WITH_CAUTION：注記 / 公開前再確認条件を維持
- UPDATE_REQUIRED：M14 U01〜U10の差し替え本文を使用
- HOLD：確定FAQ schemaへ入れない
- Fintokei速攻プロ限定Variant FAQはschema化しない
- Coupon / Referral / Eligibility / SourceHealth conflict / Legacy / Campaign / locale価格差など変動性が高いFAQは原則schema化しない
- 画面に実際に表示するQ&Aだけschema化する
- FAQ schemaと可視本文を完全一致させる

HOLD 5：

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

---

## 5. 絶対保護

### Fintokei｜速攻プロ

- effective_from = 2026-07-15
- new purchase only
- legacy separation
- Evidence
- human approval

現行Workでは条件付き解除せずTop3 Block継続。

### Diagnosis

- DiagnosisLogicV2を変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0/falseで代用しない
- Conflictを自動Verified化しない

---

## 6. Monitoring / Runtime / Publish

### Monitoring

**NO-GO**。M15 `DRAFT_NOT_ACTIVE` 維持。SourceHealth ID mapping / Preflight / human approval未完了。

### Runtime Snapshot

**NO-GO**。M13/M16 contract未確定。Work P0で `data/canonical/*` / `runtime/*` を作らない。

### Publish

**NO-GO**。

公開前に必要：

- M14 FAQ統合PASS
- 価格境界修正
- GA4重複 / Official-Affiliate誤分類 / diagnosis_complete raw answer送信の修正
- 必要SEO統合
- M08 Full Regression
- BLOCKER = 0
- CRITICAL = 0
- P0-04 390px Cautionの明示再評価
- 人間の公開承認

---

## 7. 最短経路

1. M14 FAQ統合
2. 価格境界 / GA4修正
3. SEO必要分統合
4. M08 Full Regression
5. 390px Caution再評価
6. Go / No-Go
7. 公開は別承認
