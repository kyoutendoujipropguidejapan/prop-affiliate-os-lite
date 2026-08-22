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
- ER-01 remediation：**PASS（Work報告ベース）**
- M08 Full Regression：**PASS_WITH_CAUTION**
- 本番公開判定：**CONDITIONAL GO**
- 監視Dry Run：**NO-GO**
- Runtime Snapshot：**NO-GO**

公開Gateへ持ち越すCautionは2件だけ：

1. 390px fresh実画面証跡未取得
2. GA4実送信未確認（Cloud Browserで `ERR_BLOCKED_BY_CLIENT`。静的/VM検証はPASS）

本番公開・Version保存・checkpoint作成はまだ行わない。

---

## 1. 実装済み基盤

Work報告ベース：

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
- Result「なぜ、この3つが候補になったのか。」＋理由2点＋注意1点＋「あなたとの相性」
- M14 FAQ = 14社 / 70件
- PASS 32 / PASS_WITH_CAUTION 23 / UPDATE_REQUIRED 10 / HOLD 5
- HOLD / Coupon / 限定Variant等をFAQ schemaから除外
- 割引後価格自動計算 / 表示 = 0
- Official / Affiliate link separation維持
- Sitemap = 22 URL
- SEO重複 / canonical / internal 404重大異常なし

---

## 2. ER-01 remediation

**PASS**。

変更：

- `worker/index.ts`
- `er-01-remediation.test.mjs`

確認：

- unknown HTML navigation = HTTP 404維持
- Content-Type = `text/html; charset=utf-8`
- 専用404 UI
- Primary CTA = `/beginner-guide`「基礎講座へ戻る」
- Secondary CTA = `/#diagnosis`「30秒診断を始める」
- Home linkあり
- `noindex,nofollow`
- canonicalなし
- Sitemap 22 URL維持 / 404 URL非掲載
- static asset 404 / 正常レスポンスへ干渉しない
- targeted 1/1 PASS
- regression 42/42 PASS
- build PASS
- lint error 0（既存warning 1）
- git diff --check PASS

---

## 3. M08 Full Regression 再実行結果

唯一のQA正本：`docs/M08_QA_REGRESSION_SPEC.md`
確認SHA：`2bd92e1f1fb77df93fd1fd41735521f0c51fe0cc`

ER-01修正後のWorkを対象にQA-onlyで先頭から再検証。

### Test ID件数

正本本文を一意なTest IDで採番すると106件：

- SM〜GA = 98
- ER-01〜ER-08 = 8
- 合計 = 106

従来の「98件」はER群を除いた件数として扱い、実際のFull RegressionではERを省略せず106件すべて判定した。

### 集計

- 総Test ID = 106
- PASS = 83
- FAIL = 0
- NOT_EXECUTABLE = 23
- BLOCKER = 0
- CRITICAL = 0
- MAJOR = 0
- MINOR = 0

NOT_EXECUTABLE：

- `SM-02`
- `SM-10`
- `MB-01`〜`MB-12`
- `GA-01`〜`GA-09`

SM〜GAの98件だけでは PASS 75 / FAIL 0 / NOT_EXECUTABLE 23。
ER-01〜ER-08は8/8 PASS。

### 主なPASS

- ER-01 = 404 status / HTML UI / beginner+diagnosis CTA / noindex / canonicalなし
- Beginner 01→02→03→04→05→Diagnosis 実クリック完走
- Firm 14社 / Plan 69 / FundingPips 5 / Firm→Plan→Detail正常
- Diagnosis 7問 / Top3 / 理由2＋注意1 / 相性表示 / back/reload正常
- DiagnosisLogicV2 hash一致
- SourceHealth 14 / Block 6件Top3除外
- Fintokei速攻プロはRuntime条件評価不能のため安全側Block維持
- Price / Coupon境界PASS
- Official 175 / Affiliate CTA 21、分類違反0
- SEO Sitemap 22/22、title/meta/H1/canonical/robots/internal 404 PASS
- Error / Empty ER-01〜ER-08 PASS
- regression 42/42 PASS
- build PASS
- lint error 0（既存warning 1）
- git diff --check PASS
- QAによるソース差分 0

### Caution / NOT_EXECUTABLE

#### 390px

Cloud Browserは1363px固定でviewport変更不可。390px fresh renderは未確認。
モバイルCSS / 単一カラム / 折返し / 404 CTA縦配置の自動検証はPASS。
未確認のためPASSには上げない。

#### GA4

静的/VM検証はPASS：

- GA4 ID `G-L4DRJ0FQPN` のみ
- loader 1
- 初期化責務 1
- click listener 1
- VMで1 click = 1 event
- Beginner / Diagnosis event定義維持
- `diagnosis_complete` payload = `completed / result_count / eligible_count / excluded_count` のみ

Cloud Browserでは `site-events.js` が `ERR_BLOCKED_BY_CLIENT` となるため実送信は未確認。

### 判定

- M08 Full Regression：**PASS_WITH_CAUTION**
- 本番公開判定：**CONDITIONAL GO**

条件：公開Gateで390px fresh実画面確認とGA4実送信確認を行う。

---

## 4. 絶対保護

### Fintokei｜速攻プロ

- `effective_from = 2026-07-15`
- new purchase only
- legacy separation
- Evidence
- human approval
- 現行Runtimeでは条件判定不能なのでTop3 Block継続

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

---

## 5. Monitoring / Runtime

### Monitoring

**NO-GO**。M15 `DRAFT_NOT_ACTIVE` 維持。

### Runtime Snapshot

**NO-GO**。M13/M16 contract未確定。

---

## 6. 次のGate｜Release Candidate Final Verification

M08でBLOCKER / CRITICAL = 0になったため、次は新機能実装ではなく残る2 Cautionだけを確認する。

1. 390px fresh実画面 / 実機確認
2. GA4実送信確認

この2件が問題なく確認できれば、本番公開判定をGOへ上げられる候補になる。

このGateでもコード・データ変更は原則行わない。問題を検出した場合はSeverityを判定し、勝手に修正せず停止する。

公開・Version保存・checkpoint作成は人間の明示承認後に別工程で行う。
