# IMPLEMENTATION_READINESS

更新日：2026-08-21 JST
対象：プロップファームの歩き方
目的：Work復活後の実装・監視・公開Gateを一意にする。

## 0. 現在の判定

- Work Day0監査：**完了**
- M07 P0-01〜P0-03：**PASS（Work報告ベース）**
- M07 P0-04 390px Mobile UX：**PASS_WITH_CAUTION**
- M07 P0-05 Firm-first：**PASS（Work報告ベース）**
- M07 P0-06〜P0-08：**PASS（Work報告ベース）**
- M14 FAQ統合：**PASS（Work報告ベース）**
- 価格境界 / GA4修正：**GO**
- SEO統合：**価格境界 / GA4後**
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

- 14社Firm detail：特徴 → 日本語対応 → 無料トライアル → 取引環境 → 注意点 → プラン一覧
- Firm-first 3段階表示維持
- 69プラン初期閉鎖
- 7問 / 質問順 / DiagnosisLogicV2差分なし
- Diagnosis候補65件維持
- Unknownはnull扱い
- 「なぜ、この3つが候補になったのか。」表示
- 各候補：あなたとの相性 → 理由2点 → 注意1点 → 詳細を見る
- Block 6件はTop3混入なし
- 30/30 tests PASS
- build PASS
- lint error 0（既存warning 1）
- git diff --check PASS

## 4. M14 FAQ統合

**PASS（Work報告ベース）**。

Work報告：

- 14社 / 70 FAQ統合
- PASS 32
- PASS_WITH_CAUTION 23
- UPDATE_REQUIRED 10（U01〜U10適用）
- HOLD 5（確認中表示を維持）
- FAQ全件を初期閉鎖
- HOLD / Coupon / 限定Variant等をFAQ構造化データから除外
- 70件すべての判定を個別固定する回帰テスト追加
- 33/33 tests PASS
- build PASS
- lint error 0
- Version保存 / 本番公開 / checkpoint作成なし

FAQ schemaは、表示Q&Aと一致させ、HOLD / Coupon / Fintokei限定Variant等の変動性・競合性が高い項目を除外する方針を維持。

## 5. 次のGate｜価格境界 / GA4

**GO**。

Day0監査で残った主な修正対象：

### 価格境界

- 割引後金額の自動計算表示を削除
- Price / Couponを診断採点へ接続しない
- Coupon表示は code / effect / eligibility / expiry を基本とする
- 最終価格は購入前に公式購入画面で確認する導線へ
- 既存price / coupon正本値を不用意に変更しない

### GA4

- GA4 IDは維持
- inline初期化と `site-events.js` の二重初期化 / 二重発火を解消
- React側Analyticsとsite-events.jsの同一クリック二重処理を解消
- Official linkをAffiliate eventとして誤分類しない
- `diagnosis_complete`で回答の生値を送らない
- 既存イベントを不用意に削除しない
- 新イベント追加は必要最小限。既存との重複を避ける

この単位ではSEO本文、Runtime、monitoring、本番公開には進まない。

## 6. 絶対保護

### Fintokei｜速攻プロ

- effective_from = 2026-07-15
- new purchase only
- legacy separation
- Evidence
- human approval

現行Workでは条件付き解除せずTop3 Block継続。

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

## 7. Monitoring / Runtime / Publish

### Monitoring

**NO-GO**。M15 `DRAFT_NOT_ACTIVE` 維持。

### Runtime Snapshot

**NO-GO**。M13/M16 contract未確定。

### Publish

**NO-GO**。

公開前に必要：

- 価格境界 / GA4 PASS
- 必要SEO統合
- M08 Full Regression
- BLOCKER = 0
- CRITICAL = 0
- P0-04 390px Cautionの明示再評価
- 人間の公開承認

## 8. 最短経路

1. 価格境界 / GA4修正
2. SEO必要分統合
3. M08 Full Regression
4. 390px Caution再評価
5. Go / No-Go
6. 公開は別承認
