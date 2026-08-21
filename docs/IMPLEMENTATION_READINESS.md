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
- SEO必要分統合：**GO**
- M08 Full Regression：**SEO統合後**
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

変更ファイル：

- `app/route.ts`
- `public/home-integrated.css`

確認済み：

- 割引後価格の自動計算 / 表示 = 0件
- 公式キャンペーン7件 + Coupon 13件を code / effect / eligibility / expiry の4項目で表示
- 全カードに「購入前に公式購入画面で最終価格を確認してください。」
- 3価格セクションは初期折りたたみ維持
- Price / Coupon正本はタスク前後でhash不変
- Price / CouponをDiagnosisへ接続していない

## 4. GA4整理

**PASS_WITH_CAUTION（Work報告ベース）**。

変更ファイル：

- `app/layout.tsx`
- `app/analytics.tsx`
- `public/site-events.js`
- `public/integrated-tools.js`
- `app/diagnosis.tsx`

確認済み：

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

## 5. Verification latest

Work報告：

- tests = 36/36 PASS
- build PASS
- lint error 0（既存warning 1）
- git diff --check PASS
- DiagnosisLogicV2保護区間hash不変
- Block 6件Top3不可
- Diagnosis rows 65 / SourceHealth 14 / 7問・質問順維持
- 新規BLOCKER = 0
- 新規CRITICAL = 0
- Version保存 / 本番公開 / checkpoint作成なし

## 6. 次のGate｜SEO必要分統合

**GO**。

正本：

- `docs/M09_SEO_CONTENT_PACK.md`
- `docs/M09B_SEO_CONTENT_PACK_2.md`
- `docs/SEO_INTERNAL_LINK_MAP.md`

方針：

- 完成原稿を不用意にリライトしない
- 既存ページ・記事と重複する場合は重複作成しない
- Title / Meta / Canonical / internal linksの重複を防ぐ
- 初心者導線を優先し、price / coupon / affiliateをSEO本文の主役にしない
- 動的なFirm/Plan数値は現在のMaster/Workと整合しない限り新たに断定しない
- DiagnosisLogicV2 / Block / SourceHealth / FAQ / GA4 / price boundaryは変更しない
- 本番公開・Version保存はまだしない

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

公開前に必要：

- SEO必要分統合PASS
- M08 Full Regression
- BLOCKER = 0
- CRITICAL = 0
- 390px Caution再評価
- GA4実送信Caution再評価
- 人間の公開承認

## 9. 最短経路

1. SEO必要分統合
2. M08 Full Regression
3. 390px / GA4 Caution再評価
4. Go / No-Go
5. 公開は別承認
