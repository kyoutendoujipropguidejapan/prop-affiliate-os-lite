# プロップファームの歩き方｜進捗

更新日：2026-08-20

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
- 追加SEO完成原稿5本 ✅
- SEO内部リンク／Metadata Guardrail設計 ✅

P0-04｜390px Mobile UX は **PASS_WITH_CAUTION**。既存環境で390px fresh renderが技術的に取得できず、公開GateまでCautionを持ち越す。

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

### Verification

- 30/30 tests PASS
- build PASS
- lint error 0 / existing warning 1
- git diff --check PASS
- 新規BLOCKER / CRITICALなし
- Version保存 / 本番公開なし
- Cloud Browser fresh render = 1363x936。390px Caution継続

---

## M14 FAQ

M14最終判定：

- PASS 32
- PASS_WITH_CAUTION 23
- UPDATE_REQUIRED 10
- HOLD 5

実装正本：

- `docs/M11_FIRM_FAQ_CONTENT_PACK.md`
- `docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md`

次はM11と現行WorkのQ IDを照合し、M14に従ってFAQを統合する。

- UPDATE_REQUIREDはU01〜U10差し替え本文を使用
- HOLD 5件はschema化しない
- Fintokei限定Variant FAQはschema化しない
- Coupon / Referral / Eligibility / SourceHealth conflict / Legacy / Campaign / locale差など変動性が高いFAQは原則schema化しない
- 可視Q&AとFAQ schemaを一致させる

---

## 安全条件

### Fintokei｜速攻プロ

- 2026-07-15以降
- new purchase only
- 旧口座分離
- Evidence
- human approval
- 現行WorkではTop3 Block継続

### HOLD 5

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

Top3 Block継続 / FAQ schemaへ使わない / 自動解除禁止。

---

## 現在のGate

- Day0監査：完了
- P0-01〜03：PASS
- P0-04：PASS_WITH_CAUTION
- P0-05：PASS
- P0-06〜08：PASS
- M14 FAQ統合：GO
- 監視Dry Run：NO-GO
- Runtime Snapshot：NO-GO
- 本番公開：NO-GO

## 次

最優先：**M14 FAQ統合のみ**をWorkで実装・検証する。

その後、価格境界 / GA4 → SEO必要分 → M08 Full Regression → 公開Gate。

公開・Version保存はまだ行わない。
