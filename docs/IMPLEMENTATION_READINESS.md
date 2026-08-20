# IMPLEMENTATION_READINESS

更新日：2026-08-20 JST
対象：プロップファームの歩き方
目的：Work復活後の実装・監視・公開Gateを一意にする。

## 0. 現在の判定

- Work監査開始：**GO / 完了**
- M07 P0-01〜P0-03：**PASS（Work報告ベース）**
- M07 P0-05 Firm-first段階表示：**PASS（Work報告ベース）**
- M07 P0-04 390px Mobile UX：**PASS_WITH_CAUTION / fresh 390px証跡未取得**
- M07 P0-06〜P0-08：**390px証跡取得後にGO判定**
- M14 FAQ統合：**CONDITIONAL GO**
- 監視Dry Run開始：**NO-GO**
- Runtime Snapshot実装：**NO-GO**
- 本番公開：**NO-GO**

重要更新：P0-04〜05の実装報告では14社Firm-first、69プラン初期閉鎖、会社→プラン一覧→詳細の3段階表示、Block 6件の公開向け「公式情報を確認中」表示、29/29 tests、build PASS、lint error 0、新規BLOCKER/CRITICALなしを確認。ただしCloud Browserが1363px固定で、fresh 390px実画面証跡だけ未取得。

---

## 1. P0-01〜P0-03 実装結果

Work報告ベースでPASS。

- Firm = 14
- PlanCatalog = 69
- Diagnosis data rows = 65
- SourceHealth = 14
- FundingPips = 5 plans
- SH011〜SH014 synced
- Block 6件維持
- SuperFunded 1ステップ = Trailing / 最低3日
- SuperFunded 2ステップ = 最低各フェーズ4日
- DiagnosisLogicV2差分なし
- Affiliate / commission / coupon / priceの採点混入なし
- 29/29 tests PASS
- build PASS
- lint error 0
- 本番Version 78未公開

## 2. P0-05｜Firm-first段階表示

**PASS（Work報告ベース）**

確認済み：

- 14社を会社単位で初期表示
- 全69プラン詳細は初期状態で閉じる
- 会社 → プラン一覧 → 詳細の3段階表示
- FundingPips検索で1社・5プラン
- HOLD 5件 + Fintokei速攻プロ = 計6件を「公式情報を確認中」として区別
- `SourceHealth` / `Conflict` / `Block Top3` / confidence等の内部語を公開UIへ出さない
- DiagnosisLogicV2 / 質問 / 採点 / GA4 / price / couponは変更なし
- 29/29 tests PASS
- build PASS
- lint error 0
- git diff --check PASS

## 3. P0-04｜390px Mobile UX

**PASS_WITH_CAUTION**

CSS / 構造テストと1363px fresh renderでは問題なし。ただし、M07/M08の受入条件は「fresh 390px実画面」での確認を要求するため、まだ完全PASSへ昇格しない。

未完了は1点のみ：

- current worktreeを390px viewportでfresh renderし、トップ / Firm一覧 / Firm内プラン一覧 / Plan詳細について、横スクロール・CTA見切れ・文字切れ・details clip・ボタン競合がないことを実画面証跡で確認する。

### 390px証跡の取得方針

Cloud Browser UIがviewport変更を提供しない場合、Work環境内で既存のheadless browser / browser test capabilityが利用可能なら、それを使って `390x844` 前後のviewportを明示指定してcurrent worktreeをrenderする。

- 新規OSS / 新規browser依存を追加しない
- 本番を公開しない
- Version保存しない
- verification-onlyで実行
- screenshotまたは同等のfresh render evidenceを残す

既存環境で390px viewport render自体が技術的に不可能な場合は、その制約を明示し、P0-04はPASS_WITH_CAUTIONのまま公開Gateまで持ち越す。CSSテストだけで完全PASSにはしない。

## 4. 次の実装Gate

P0-06〜P0-08へ進む前に、まず390px fresh render verificationを1回だけ試す。

390pxで問題がなければP0-04をPASSへ昇格し、次に：

- P0-06｜共通Firm detail
- P0-07｜7問診断の現行Logic維持・候補整合
- P0-08｜「なぜこの3つ？」結果説明

へ進む。

390pxで修正が必要なら、その修正だけを行い、再render後にP0-04を閉じる。

---

## 5. 絶対保護条件

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

共通：human-only resolution / auto unblock禁止 / Top3 Block継続 / FAQ schemaへ入れない / 診断Top3根拠へ使わない。

### Diagnosis

- DiagnosisLogicV2を変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0/falseで代用しない
- Conflictを自動Verified化しない

---

## 6. FAQ / Monitoring / Runtime / Publish Gate

### FAQ

M14 FAQ統合：**CONDITIONAL GO**。

### Monitoring

**NO-GO**。M15は `DRAFT_NOT_ACTIVE` 維持。

### Runtime Snapshot

**NO-GO**。M13/M16 contract未確定。

### Publish

**NO-GO**。M08 Full Regression、BLOCKER=0、CRITICAL=0、fresh 390px最終確認、GA4確認、人間承認が必要。

---

## 7. 最短経路

1. P0-04 fresh 390px verification-only
2. P0-04 PASSへ昇格
3. P0-06〜P0-08
4. M14 FAQ統合
5. 価格境界 / GA4修正
6. SEO必要分統合
7. M08 Full Regression
8. fresh 390px最終確認
9. Go / No-Go
10. 公開は別承認
