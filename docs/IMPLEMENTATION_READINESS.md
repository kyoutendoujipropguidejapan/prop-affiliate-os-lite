# IMPLEMENTATION_READINESS

更新日：2026-08-20 JST
対象：プロップファームの歩き方
目的：Work復活後の実装・監視・公開Gateを一意にする。

## 0. 現在の判定

- Work監査開始：**GO / 完了**
- M07 P0-01〜P0-03：**PASS（Work報告ベース）**
- M07 P0-04〜P0-05：**GO**
- M14 FAQ統合：**CONDITIONAL GO**
- 監視Dry Run開始：**NO-GO**
- Runtime Snapshot実装：**NO-GO**
- 本番公開：**NO-GO**

重要更新：2026-08-20、WorkでDay0監査後にP0-01〜P0-03を実装。Work報告では14社 / PlanCatalog 69 / Diagnosis行65 / SourceHealth 14、FundingPips 5プラン、Block 6件を確認し、既存24回帰 + P0専用5 = 29/29 PASS、build PASS、lint error 0。本番公開・Version保存は未実施。

---

## 1. P0-01〜P0-03 実装結果（Work報告）

変更ファイル：

- `app/master-data.json`
- `scripts/sync-master-v2-2.mjs`
- `scripts/sync-master-v2-2.sh`
- `tests/master-v2-2-p0.test.mjs`
- `tests/rendered-html.test.mjs`
- `package.json`

データ実数：

- Firm = 14
- PlanCatalog = 69
- Diagnosis data rows = 65
- SourceHealth = 14
- FundingPips = 5 plans
- SH011〜SH014 = synced

Block 6件：

- Fintokei｜速攻プロ
- Funded7｜1フェーズ
- Funded7｜インスタント
- Funded Trader Markets｜インスタント Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

Work報告では全件 `blockTop3:true` / Conflict / confidence 55。FTM Instant Proは監査用データ行として保持するが診断結果候補へ復活させない。

SuperFunded：

- 1ステップ = Trailing / 最低3日
- 2ステップ = 最低各フェーズ4日

保護確認：

- DiagnosisLogicV2差分なし
- 7問 / 質問順差分なし
- 診断runtime変更なし
- Affiliate / commission / coupon / priceを採点へ混入させない
- price/coupon fixture未変更
- `data/canonical/*` / `runtime/*` / monitoring未作成
- 本番Version 78未公開

検証：

- 既存回帰 24/24 PASS
- P0専用 5/5 PASS
- 合計 29/29 PASS
- build PASS
- lint error 0（既存img warning 1）
- 新規BLOCKER / CRITICALなし

注意：上記はWorkからの実装報告を記録したもので、GitHub上のWorkコード実体をこの文書が独立再検証したことを意味しない。

---

## 2. 次の実装Gate｜P0-04〜P0-05

### P0-04｜390px mobile UX

GO。

目的：CSSテストだけでなく、fresh 390px実画面で以下を確認する。

- horizontal scrollなし
- CTA見切れなし
- 文字・カード・detailsのクリップなし
- 主要導線が1画面で競合しない
- 既存基礎講座01→05→診断を壊さない

本番公開はまだ禁止。

### P0-05｜段階表示 / Firm-first

GO。

目標：

`14社一覧 → 選択した会社のプラン一覧 → 必要なプランだけ詳細`

14社一覧で69プラン詳細を初期展開しない。

Firm detail冒頭の基本順：

- 特徴
- 日本語対応
- 無料トライアル
- 取引環境
- 注意点
- プラン一覧

その後、選択プランだけ詳細。

DiagnosisLogicV2 / SourceHealth / price / coupon / GA4 / FAQの全面改修はこの単位で触らない。

P0-04〜05完了条件：

- fresh 390px証跡
- firm-first表示
- no horizontal overflow
- 29 tests以上を維持
- build / lint PASS
- HOLD 5 + Fintokei Block維持
- DiagnosisLogicV2差分なし

---

## 3. 絶対保護条件

### Fintokei｜速攻プロ

Variant単位でのみ扱う。

- `effective_from = 2026-07-15`
- `new_purchase_only = true`
- legacy account separation required
- Evidence required
- human approval required

購入日・旧口座・scopeを安全に区別できない場合はTop3 Block継続。

### HOLD 5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

共通：

- human-only resolution
- auto unblock禁止
- Top3 Block継続
- FAQ schemaへ入れない
- 診断Top3根拠へ使わない

### Diagnosis

- DiagnosisLogicV2を不用意に変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0/falseで代用しない
- Conflictを自動Verified化しない

---

## 4. FAQ Gate

M14 FAQ統合は **CONDITIONAL GO** のまま。

GO昇格条件：

- M11と現行WorkのQ ID照合
- UPDATE_REQUIRED 10件だけ差し替え
- PASS_WITH_CAUTIONの注記 / 再確認条件維持
- HOLD 5件をschema化しない
- Fintokei限定Variant FAQを確定schema化しない

P0-04〜05完了後に着手する。

---

## 5. 監視Dry Run Gate

現時点：**NO-GO**

未完了：

1. `sourcehealth_ids` Canonical mapping contract
2. Preflight全PASS
3. HTTP/Baseline/failure handling実装確認
4. 人間がACTIVE化を明示承認

`DRAFT_NOT_ACTIVE` のままでは監視開始しない。

---

## 6. Runtime Snapshot Gate

現時点：**NO-GO**

M13/M16大原則は一致するが、R01〜R08のcontract decision未確定。

Work P0では `data/canonical/*` / `runtime/*` を新しい正本として生成しない。

---

## 7. 公開Gate

本番公開はM08完走までNO-GO。

必要条件：

- M08 Full Regression
- BLOCKER = 0
- CRITICAL = 0
- fresh 390px render
- DiagnosisLogicV2不変
- HOLD 5件Top3除外
- Fintokei Variant誤適用なし
- Official / Affiliate link分離
- GA4破損・二重発火なし
- 人間の明示公開承認

---

## 8. 最短経路

1. P0-04｜fresh 390px mobile UX
2. P0-05｜Firm-first段階表示
3. P0-06〜P0-08｜Firm detail / 7問診断 / なぜこの3つ
4. M14 FAQ統合
5. 価格境界 / GA4修正
6. SEO必要分統合
7. M08 Full Regression
8. fresh 390px最終確認
9. Go / No-Go
10. 公開は別承認
