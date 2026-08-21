# プロップファームの歩き方｜進捗

更新日：2026-08-22

## 完了

- M01｜公開サイト・モバイルUX総監査 ✅
- M02｜診断7問UX監査 ✅
- M03｜SEO・検索流入設計 ✅
- M04｜14社ファーム詳細ページのSEO/UX設計 ✅
- M05｜公式ソース監視設計 ✅
- M06｜SourceHealth競合6件の再調査 ✅
- M07｜M01〜M06統合・Work実装仕様確定 ✅
- M08｜実装前QA・回帰テスト仕様 ✅
- M09｜SEO記事・ルール解説の完成原稿 ✅
- M10｜公式ソース監視の自動化技術設計 ✅
- M11｜14社ファーム詳細FAQ完成原稿 ✅
- M12｜監視Dry Run用URLセット確定 ✅
- M13｜GitHubへのMaster／成果物同期設計 ✅
- M14｜14社FAQの公式一次情報最終チェック ✅
- M15｜M12 Dry Run用 monitor_sources 設定ファイル案 ✅
- M16｜最小Runtime Snapshot仕様確定 ✅
- 実装前Readiness Gate ✅
- M01〜M16 Artifact回収・照合 ✅
- M13↔M16 cross-check ✅
- Work Day0監査 ✅
- M07 P0-01〜P0-03 実装・検証 ✅（Work報告ベース）
- M07 P0-05 Firm-first段階表示 ✅（Work報告ベース）
- M07 P0-06〜P0-08 実装・検証 ✅（Work報告ベース）
- M14 FAQ統合 ✅（Work報告ベース）
- 価格境界修正 ✅（Work報告ベース）
- GA4整理 ✅ / 実送信のみCaution（Work報告ベース）
- 追加SEO完成原稿5本 ✅
- SEO内部リンク／Metadata Guardrail設計 ✅

P0-04｜390px Mobile UX は **PASS_WITH_CAUTION**。既存環境で390px fresh renderが技術的に取得できず、公開GateまでCautionを持ち越す。

GA4はコード・VM検証でPASS。Cloud Browserが計測スクリプトを `ERR_BLOCKED_BY_CLIENT` で遮断したため、実送信確認のみ公開Gateへ持ち越す。

Readiness Gate正本：`docs/IMPLEMENTATION_READINESS.md`
Artifact台帳：`docs/ARTIFACT_SYNC_STATUS.md`

---

## Work最新状態

### データ / Diagnosis

- Firm = 14
- PlanCatalog = 69
- Diagnosis rows = 65
- SourceHealth = 14
- FundingPips = 5 plans
- Block 6件維持
- DiagnosisLogicV2 / 7問 / 質問順差分なし
- Unknownはnull扱い
- commercial dataを診断採点へ混ぜない

### Firm-first / Firm detail

- 14社を会社単位で初期表示
- 69プラン初期閉鎖
- 会社 → プラン一覧 → 詳細の3段階
- Firm detail冒頭：特徴 → 日本語対応 → 無料トライアル → 取引環境 → 注意点 → プラン一覧
- HOLD 5 + Fintokei速攻プロを「公式情報を確認中」として区別

### Diagnosis result

- 「なぜ、この3つが候補になったのか。」を表示
- 各候補：あなたとの相性 → 理由2点 → 注意1点 → 詳細を見る
- 品質ランキング表現 / 内部用語なし
- Block 6件のTop3混入なし

### M14 FAQ統合

- 14社 / 70 FAQ
- PASS 32
- PASS_WITH_CAUTION 23
- UPDATE_REQUIRED 10（U01〜U10）
- HOLD 5
- FAQ全件初期閉鎖
- HOLD / Coupon / 限定Variant等をFAQ schemaから除外

### 価格境界

- 割引後価格の自動計算 / 表示 = 0件
- 公式キャンペーン7件 + Coupon 13件
- code / effect / eligibility / expiry の4項目表示
- 全カードで購入前の公式購入画面による最終価格確認を案内
- 3価格セクション初期折りたたみ維持
- Price / Coupon正本hash不変

### GA4

- GA4 ID = `G-L4DRJ0FQPN` のみ
- 初期化責務 = `public/site-events.js` 1箇所
- inline初期化 / React click listener撤去
- Official 175 / Affiliate CTA 21 を自動検証、分類違反0
- diagnosis_complete payload = completed / result_count / eligible_count / excluded_count のみ
- 生回答 / Top firm / Top plan送信なし
- beginner_course_start / next / complete、diagnosis_start / complete維持
- 新規イベント追加なし
- VM検証：初期化1回 / listener 1個 / 1click = 1event
- Cloud Browserで実送信のみ未確認

### Verification

- 36/36 tests PASS
- build PASS
- lint error 0 / existing warning 1
- git diff --check PASS
- DiagnosisLogicV2保護区間hash不変
- Block 6件Top3不可
- 新規BLOCKER = 0
- 新規CRITICAL = 0
- Version保存 / 本番公開 / checkpoint作成なし

---

## 現在のGate

- Day0監査：完了
- P0-01〜03：PASS
- P0-04：PASS_WITH_CAUTION
- P0-05：PASS
- P0-06〜08：PASS
- M14 FAQ統合：PASS
- 価格境界：PASS
- GA4：PASS_WITH_CAUTION（実送信のみ未確認）
- SEO必要分統合：GO
- M08 Full Regression：SEO後
- 監視Dry Run：NO-GO
- Runtime Snapshot：NO-GO
- 本番公開：NO-GO

## 次

最優先：**SEO必要分統合のみ**をWorkで実装・検証する。

その後、M08 Full Regression → 390px / GA4 Caution再評価 → Go / No-Go → 公開は別承認。
