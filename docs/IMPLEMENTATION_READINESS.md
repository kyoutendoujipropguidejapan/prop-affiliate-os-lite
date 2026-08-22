# IMPLEMENTATION_READINESS

更新日：2026-08-22 JST
対象：プロップファームの歩き方
目的：Work復活後の実装・監視・公開Gateを一意にする。

## 0. 現在の判定

- Work Day0監査：**完了**
- M07 P0-01〜P0-03：**PASS（Work報告ベース）**
- M07 P0-04 390px Mobile UX：**PASS_WITH_CAUTION**
- M07 P0-05 Firm-first：**PASS（Work報告ベース）**
- M07 P0-06〜P0-08：**PASS（Work報告ベース）**
- M14 FAQ統合：**PASS（Work報告ベース）**
- 価格境界：**PASS（Work報告ベース）**
- GA4整理：**PASS_WITH_CAUTION（実送信のみ未確認）**
- SEO必要分統合：**PASS（Work報告ベース）**
- M08 Full Regression：**GO**
- 監視Dry Run：**NO-GO**
- Runtime Snapshot：**NO-GO**
- 本番公開：**NO-GO**

公開Gateへ持ち越すCautionは2件：

1. 390px fresh実画面証跡未取得
2. GA4実送信未確認（Cloud Browserで計測スクリプトがERR_BLOCKED_BY_CLIENT。コード/VM検証はPASS）

---

## 1. P0 / FAQ 実装済み状態

Work報告ベースで以下を維持：

- Firm = 14
- PlanCatalog = 69
- Diagnosis rows = 65
- SourceHealth = 14
- FundingPips = 5 plans
- Block 6件維持
- 69プラン初期閉鎖
- Firm-first：会社 → プラン一覧 → 詳細
- Firm detail：特徴 → 日本語対応 → 無料トライアル → 取引環境 → 注意点 → プラン一覧
- 7問 / 質問順 / DiagnosisLogicV2差分なし
- Unknownはnull扱い
- 「なぜ、この3つが候補になったのか。」表示
- 各候補：あなたとの相性 → 理由2点 → 注意1点 → 詳細を見る
- M14 FAQ 14社 / 70件統合
- PASS 32 / PASS_WITH_CAUTION 23 / UPDATE_REQUIRED 10 / HOLD 5
- HOLD / Coupon / 限定Variant等をFAQ schemaから除外

## 2. P0-04｜390px Mobile UX

**PASS_WITH_CAUTION**。

- 390px向けCSS / 構造テスト：PASS
- Cloud Browser fresh render：1363x936でPASS
- Playwright packageはあるがbrowser binaryなし
- OS browserなし / CDP未稼働 / Cloud Browser viewport固定
- 390px実画面証跡のみ未取得

本番公開Gateで再評価する。

## 3. 価格境界

**PASS（Work報告ベース）**。

- 割引後価格の自動計算 / 表示 = 0件
- 公式キャンペーン7件 + Coupon 13件を code / effect / eligibility / expiry の4項目で表示
- 全カードに「購入前に公式購入画面で最終価格を確認してください。」
- 3価格セクションは初期折りたたみ維持
- Price / Coupon正本はタスク前後でhash不変
- Price / CouponをDiagnosisへ接続していない

## 4. GA4整理

**PASS_WITH_CAUTION（Work報告ベース）**。

- GA4 ID = `G-L4DRJ0FQPN` のみ
- GA4初期化責務 = `public/site-events.js` の1箇所
- inline初期化とReact側click listener撤去
- `data-track-firm`単独でAffiliate判定しない
- Official 175 links / Affiliate conversion CTA 21 linksを自動検証し、分類違反0
- `diagnosis_complete` payloadは `completed / result_count / eligible_count / excluded_count` のみ
- 回答コード / 生回答 / Top firm / Top planを送信しない
- `beginner_course_start / next / complete`、`diagnosis_start / complete`を維持
- 新規イベント追加なし
- VM検証で初期化1回 / listener 1個 / 1click = 1event

Caution：Cloud Browserでは計測スクリプトが `ERR_BLOCKED_BY_CLIENT` となり、GA4の実送信だけ未確認。本番公開Gateで可能なら実機・通常ブラウザで確認する。

## 5. SEO必要分統合

**PASS（Work報告ベース）**。

正本3件のGitHub blob SHA一致を確認してから統合：

- `docs/M09_SEO_CONTENT_PACK.md` = `8a57ce6ba1edf24b0142cf711e6abe2b08d672e6`
- `docs/M09B_SEO_CONTENT_PACK_2.md` = `e91b7a51d45eaa3b03421f3e4478ab561cb8d4f1`
- `docs/SEO_INTERNAL_LINK_MAP.md` = `6eed1a9db8243314b221f31279c5d4b7225406e8`

最終10テーマ / slug：

- 最大DD：`/daily-loss-vs-max-loss`（既存・導線更新）
- Static / Trailing / EOD：`/fixed-vs-trailing-drawdown`（既存統合ページ維持）
- 失格しやすいルール：`/beginner-guide/rules-that-cause-disqualification`（既存・関連記事追加）
- 無料トライアル：`/articles/prop-firm-free-trial`（新規）
- ニュース取引：`/articles/news-trading-rules`（新規）
- 週末持ち越し：`/articles/weekend-holding-rules`（新規）
- 最低取引日数：`/articles/minimum-trading-days`（新規）
- 出金条件：`/first-payout-checklist`（既存・導線更新）

確認済み：

- duplicate article = 0
- Sitemap 18 → 22 URL（新規4記事のみ追加）
- Title duplicate = 0
- Meta description duplicate = 0
- H1 = index対象各URL 1件
- canonical error = 0
- internal 404 = 0
- Firm detail関連記事 = 14社すべて1〜3本 / 最大3本
- HOLD / Conflictプランを関連記事根拠から除外
- Affiliate URLの情報源利用 = 0
- Price / CouponをTitle/Metaの主役にしたページ = 0
- Beginner 01→05→Diagnosis維持
- DiagnosisLogicV2 hash一致 / Block 6件維持
- tests = 41/41 PASS
- build PASS
- lint error 0（既存image warning 1）
- git diff --check PASS
- 新規BLOCKER / CRITICAL = 0

## 6. 次のGate｜M08 Full Regression

**GO**。

唯一のQA正本：`docs/M08_QA_REGRESSION_SPEC.md`

実行順はM08に従う：

1. Build / lint / automated tests
2. Smoke
3. 390px mobile
4. Beginner 01〜05
5. Firm → Plan → Detail
6. Diagnosis Q1〜Q7 / Result
7. SourceHealth Block matrix
8. Fintokei variant/date boundary
9. Price / Coupon
10. Official / Affiliate links
11. SEO head / sitemap / robots
12. GA4
13. 404 / empty / direct URL
14. 390px最終fresh render
15. Go / No-Go

ただし現在のWork契約ではFintokei速攻プロはVariant条件を安全に判定できないため、**M08 FK-02/FK-03で条件付き解除を実装してPASSさせようとしない**。現行方針どおり、条件保持不可 / scope判定不可ならBlock継続を正解とする。

公開候補判定の絶対条件：

- BLOCKER = 0
- CRITICAL = 0
- DiagnosisLogicV2不変
- Affiliate / commission / coupon / priceを診断採点に使用しない
- HOLD 5 + Fintokei速攻プロの計6件をTop3から除外
- Official / Affiliate link separation維持
- Beginner既存URL維持
- SEO重大異常なし
- Build / regression / lint PASS

390px fresh実画面とGA4実送信は環境制約のため未確認。M08で再試行し、取得不能ならCautionとして明示して最終Go/No-Goを分ける。

## 7. 絶対保護

### Fintokei｜速攻プロ

- effective_from = 2026-07-15
- new purchase only
- legacy separation
- Evidence
- human approval
- 現行Workでは条件付き解除せずTop3 Block継続

### HOLD 5

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

Top3 Block継続 / FAQ schemaへ使わない / 自動解除禁止。

### Diagnosis

- DiagnosisLogicV2を変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0/falseで代用しない
- Conflictを自動Verified化しない

## 8. Monitoring / Runtime / Publish

### Monitoring

**NO-GO**。M15 `DRAFT_NOT_ACTIVE` 維持。

### Runtime Snapshot

**NO-GO**。M13/M16 contract未確定。

### Publish

**NO-GO**。

M08 Full Regression完了後に、BLOCKER / CRITICALと2件のCautionを明示したうえで最終Go/No-Goを判定し、人間の明示公開承認があって初めて公開へ進む。

## 9. 最短経路

1. M08 Full Regression
2. 390px / GA4 Caution再評価
3. 最終Go / No-Go
4. 公開は別承認
