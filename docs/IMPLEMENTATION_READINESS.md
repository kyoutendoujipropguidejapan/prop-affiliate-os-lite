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
- M08 Full Regression：**FAIL / ER-01 CRITICAL**
- ER-01 remediation：**GO**
- 監視Dry Run：**NO-GO**
- Runtime Snapshot：**NO-GO**
- 本番公開：**NO-GO**

公開Gateへ持ち越す既知Cautionは2件：

1. 390px fresh実画面証跡未取得
2. GA4実送信未確認（Cloud Browserで計測スクリプトがERR_BLOCKED_BY_CLIENT。コード/VM検証はPASS）

加えて、M08でER-01 CRITICALを検出したため、現時点では公開不可。

---

## 1. 実装済み基盤

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
- 割引後価格の自動計算 / 表示 = 0件
- Official / Affiliate link separation維持
- SEO Sitemap = 22 URL
- SEO必要分統合後 41/41 tests PASS
- build PASS / lint error 0 / git diff --check PASS

## 2. P0-04｜390px Mobile UX

**PASS_WITH_CAUTION**。

- 390px向けCSS / 構造テスト：PASS
- Cloud Browser fresh render：1363x936でPASS
- Playwright packageはあるがbrowser binaryなし
- OS browserなし / CDP未稼働 / Cloud Browser viewport固定
- 390px実画面証跡のみ未取得

公開Gateで再評価する。

## 3. GA4

**PASS_WITH_CAUTION**。

- GA4 ID = `G-L4DRJ0FQPN`
- 初期化責務 = `public/site-events.js` 1箇所
- inline初期化 / React click listener撤去
- Official 175 / Affiliate CTA 21 を自動検証、分類違反0
- `diagnosis_complete` payload = completed / result_count / eligible_count / excluded_count のみ
- 生回答 / Top firm / Top plan送信なし
- VM検証：初期化1回 / listener 1個 / 1click = 1event
- Cloud Browserで実送信のみ未確認

## 4. SEO必要分統合

**PASS**。

- M09 / M09B / Internal Link Map のGitHub blob SHA一致を確認後に実装
- 重複ページ 0
- Sitemap 22 URL
- Title重複 0
- Meta重複 0
- H1異常 0
- canonical誤り 0
- 内部404 0
- Beginner 01→05→Diagnosis維持
- HOLD / Conflictを確定例に使用しない
- Affiliate URLを情報源に使用しない
- Price / CouponをTitle / Metaの主役にしない

## 5. M08 Full Regression 初回結果

QA正本：`docs/M08_QA_REGRESSION_SPEC.md`

確認SHA：`2bd92e1f1fb77df93fd1fd41735521f0c51fe0cc`

WorkはER-01でCRITICALを検出し、M08のFAIL時停止ルールに従ってFull Regressionを中断。

集計：

- M08総Test数 = 98
- 実行済みM08 Test ID = 1
- PASS = 0
- FAIL = 1
- NOT_EXECUTABLE = 0
- 未実施 = 97
- BLOCKER = 0
- CRITICAL = 1
- MAJOR = 0
- MINOR = 0
- FAIL Test ID = `ER-01`

### ER-01

条件：存在しないURLへ直接アクセス。

期待：404に加えて、基礎講座・診断への復帰導線が表示される。

実結果：

- HTTP status = 404
- Content-Type = text/plain
- body = `Not found`
- 基礎講座CTAなし
- 診断CTAなし
- 再現例 = `/__m08_missing__`

原因候補：カスタム404実装がなく、未知ルートがAssets側の標準404へ委譲されている。

停止前の基盤検証：

- automated regression = 41/41 PASS
- build PASS
- lint error 0（既存warning 1）
- git diff --check PASS
- QA開始前後のtracked diff SHA一致
- untracked file SHA一致
- コード変更 0
- Version保存 / checkpoint / publish なし

M08 Full Regression判定：**FAIL**

本番公開判定：**NO-GO**

## 6. 次のGate｜ER-01 remediation

**GO**。

次の変更はER-01解消に必要な最小範囲だけに限定する。

受入条件：

- 未知URLがHTTP 404を維持する
- `text/plain Not found`ではなく既存サイトトーンに沿う404 UIを返す
- 基礎講座への復帰CTAを表示する
- 30秒診断への復帰CTAを表示する
- 404から価格 / Coupon / Affiliateを主導線にしない
- noindex相当の安全な扱いを維持し、404ページをindex対象化しない
- 既存の正常URL / sitemap / canonicalを壊さない
- DiagnosisLogicV2 / Block 6 / SourceHealth / FAQ / price / GA4 / SEO記事本文を変更しない

ER-01修正後は、ER-01 targeted verificationだけで公開判定に進まない。

**コード変更が入るため、M08 Full Regressionは98件を先頭から再実行する。前回の未実施97件へ途中再開しない。**

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

ER-01修正 → targeted verification → M08 Full Regressionを最初から再実行 → BLOCKER / CRITICAL = 0 → 390px / GA4 Caution再評価 → 人間の明示公開承認、の順でのみ進む。

## 9. 最短経路

1. ER-01のみ修正
2. ER-01 targeted verification
3. M08 Full Regressionを98件先頭から再実行
4. 390px / GA4 Caution再評価
5. 最終Go / No-Go
6. 公開は別承認
