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
- SEO必要分統合 ✅（Work報告ベース）
- 追加SEO完成原稿5本 ✅
- SEO内部リンク／Metadata Guardrail設計 ✅

P0-04｜390px Mobile UX は **PASS_WITH_CAUTION**。既存環境で390px fresh renderが技術的に取得できず、公開GateまでCautionを持ち越す。

GA4はコード・VM検証でPASS。Cloud Browserが計測スクリプトを `ERR_BLOCKED_BY_CLIENT` で遮断したため、実送信確認のみ公開Gateへ持ち越す。

Readiness Gate正本：`docs/IMPLEMENTATION_READINESS.md`
Artifact台帳：`docs/ARTIFACT_SYNC_STATUS.md`

---

## Work最新状態

- Firm = 14
- PlanCatalog = 69
- Diagnosis rows = 65
- SourceHealth = 14
- FundingPips = 5 plans
- Block 6件維持
- DiagnosisLogicV2 / 7問 / 質問順差分なし
- Firm-first：会社 → プラン一覧 → 詳細
- M14 FAQ：14社 / 70件
- 割引後価格自動表示 = 0
- Official 175 / Affiliate CTA 21、分類違反0
- Sitemap = 22 URL
- SEO Title / Meta / H1 / canonical / internal 404 重大異常なし
- SEO統合後 41/41 tests PASS
- build PASS
- lint error 0 / existing warning 1
- git diff --check PASS
- Version保存 / checkpoint / 本番公開なし

---

## M08 Full Regression 初回

QA正本：`docs/M08_QA_REGRESSION_SPEC.md`

確認SHA：`2bd92e1f1fb77df93fd1fd41735521f0c51fe0cc`

ER-01でCRITICALを検出し、正本のFAIL時停止ルールに従って中断。

### 集計

- M08総Test数 = 98
- 実行済み = 1
- PASS = 0
- FAIL = 1
- NOT_EXECUTABLE = 0
- 停止により未実施 = 97
- BLOCKER = 0
- CRITICAL = 1
- MAJOR = 0
- MINOR = 0
- FAIL Test ID = `ER-01`

### ER-01

存在しないURLへの直接アクセス。

期待：HTTP 404 + 基礎講座 / 診断への復帰導線。

実結果：

- HTTP 404
- Content-Type `text/plain`
- body `Not found`
- 基礎講座CTAなし
- 診断CTAなし
- 再現例 `/__m08_missing__`

原因候補：カスタム404不在でAssets側標準404へ委譲。

停止前の基盤検証：

- automated regression 41/41 PASS
- build PASS
- lint error 0 / existing warning 1
- git diff --check PASS
- QA前後 tracked diff SHA一致
- untracked file SHA一致
- コード変更 0

判定：

- M08 Full Regression = **FAIL**
- 本番公開 = **NO-GO**

---

## 現在のGate

- Day0監査：完了
- P0-01〜03：PASS
- P0-04：PASS_WITH_CAUTION
- P0-05：PASS
- P0-06〜08：PASS
- M14 FAQ統合：PASS
- 価格境界：PASS
- GA4：PASS_WITH_CAUTION
- SEO必要分統合：PASS
- M08 Full Regression：**FAIL / ER-01 CRITICAL**
- ER-01 remediation：**GO**
- 監視Dry Run：NO-GO
- Runtime Snapshot：NO-GO
- 本番公開：NO-GO

## 次

最優先：**ER-01のみ修正**。

受入条件：

- 未知URLはHTTP 404を維持
- サイトトーンに沿う404 UI
- 基礎講座CTA
- 30秒診断CTA
- 404から価格 / Coupon / Affiliateを主導線にしない
- 404をindex対象化しない
- 正常URL / sitemap / canonicalを壊さない

修正後にER-01 targeted verificationを実施する。

その後、コード変更が入るため **M08 Full Regressionは98件を先頭から再実行**する。前回の未実施97件へ途中再開しない。

公開・Version保存はまだ行わない。
