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
- M07 P0-01〜P0-03 実装・検証 ✅
- M07 P0-05 Firm-first段階表示 ✅
- M07 P0-06〜P0-08 実装・検証 ✅
- M14 FAQ統合 ✅
- 価格境界修正 ✅
- GA4整理 ✅ / 実送信のみCaution
- SEO必要分統合 ✅
- ER-01 remediation ✅
- M08 Full Regression再実行 ✅ / PASS_WITH_CAUTION

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
- SEO重大異常なし
- Version保存 / checkpoint / 本番公開なし

---

## ER-01 remediation

PASS。

- unknown HTML navigation = HTTP 404
- Content-Type = HTML
- 専用404 UI
- 基礎講座CTA / 30秒診断CTA / Home link
- noindex,nofollow
- canonicalなし
- Sitemap非掲載
- static asset 404 / normal responseへ干渉なし
- targeted 1/1 PASS
- regression 42/42 PASS
- build PASS
- lint error 0
- git diff --check PASS

---

## M08 Full Regression 再実行

QA正本：`docs/M08_QA_REGRESSION_SPEC.md`
SHA：`2bd92e1f1fb77df93fd1fd41735521f0c51fe0cc`

ER-01修正後のWorkをQA-onlyで先頭から再検証。

### 件数

正本本文の一意なTest IDは106件：

- SM〜GA = 98
- ER = 8
- 合計 = 106

106件すべて判定。

### 集計

- PASS = 83
- FAIL = 0
- NOT_EXECUTABLE = 23
- BLOCKER = 0
- CRITICAL = 0
- MAJOR = 0
- MINOR = 0

NOT_EXECUTABLE：`SM-02`, `SM-10`, `MB-01`〜`MB-12`, `GA-01`〜`GA-09`。

SM〜GAの98件のみでは PASS 75 / FAIL 0 / NOT_EXECUTABLE 23。
ER-01〜ER-08は8/8 PASS。

### 主な確認

- Beginner 01→05→Diagnosis：PASS
- Firm 14社 / Plan 69 / FundingPips 5 / Firm→Plan→Detail：PASS
- Diagnosis 7問 / Top3 / 理由2＋注意1 / 相性表示：PASS
- DiagnosisLogicV2 hash一致
- SourceHealth 14 / Block 6件Top3除外
- Fintokei速攻プロは安全側Block維持
- Price / Coupon：PASS
- Official 175 / Affiliate CTA 21：PASS
- SEO Sitemap 22 / title / meta / H1 / canonical / robots / internal 404：PASS
- ER-01〜ER-08：PASS
- regression 42/42 PASS
- build PASS
- lint error 0 / existing warning 1
- git diff --check PASS
- QAによるソース変更 0

### 残るCaution

1. **390px fresh実画面**
   - Cloud Browserは1363px固定でviewport変更不可
   - mobile CSS / DOM系自動検証はPASS
   - 未確認のためPASSにはしない

2. **GA4実送信**
   - 静的 / VM検証PASS
   - ID 1 / loader 1 / init 1 / listener 1 / 1click=1event
   - diagnosis_completeに生回答なし
   - Cloud Browserでは `ERR_BLOCKED_BY_CLIENT` のため実送信未確認

判定：

- M08 Full Regression = **PASS_WITH_CAUTION**
- 本番公開判定 = **CONDITIONAL GO**

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
- ER-01 remediation：PASS
- M08 Full Regression：PASS_WITH_CAUTION
- 本番公開：CONDITIONAL GO
- 監視Dry Run：NO-GO
- Runtime Snapshot：NO-GO

## 次

**Release Candidate Final Verification**。

残る2点だけ確認する：

1. 390px fresh実画面 / 実機
2. GA4実送信

両方問題なければ公開GO候補。問題があればSeverity判定して停止し、勝手に修正しない。

本番公開・Version保存・checkpointは別承認まで実施しない。
