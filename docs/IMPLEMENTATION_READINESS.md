# IMPLEMENTATION_READINESS

更新日：2026-08-20 JST
対象：プロップファームの歩き方
目的：Work復活後の実装・監視・公開Gateを一意にする。

## 0. 現在の判定

- Work監査開始：**GO / 完了**
- M07 P0-01〜P0-03：**PASS（Work報告ベース）**
- M07 P0-05 Firm-first段階表示：**PASS（Work報告ベース）**
- M07 P0-04 390px Mobile UX：**PASS_WITH_CAUTION / fresh 390px実画面証跡未取得**
- M07 P0-06〜P0-08：**GO**
- M14 FAQ統合：**CONDITIONAL GO**
- 監視Dry Run開始：**NO-GO**
- Runtime Snapshot実装：**NO-GO**
- 本番公開：**NO-GO**

重要更新：2026-08-20、Work環境で390px fresh renderを再試行したが、既存Playwrightは利用可能でもChromium/Firefox/WebKit本体が未配置、OSブラウザなし、既存CDP未稼働、Cloud Browserは1363x936固定でviewport変更不可だった。新規browser dependencyは追加せず終了し、P0-04はPASS_WITH_CAUTIONのまま保持する。CSS/構造テスト、29/29 tests、build、lintはPASS。本番公開・Version保存は未実施。

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

### 実施済み

- 390px向けCSS / 構造テスト：PASS
- Cloud Browser fresh render：PASS、ただし1363x936固定
- 29/29 tests：PASS
- build：PASS
- lint：0 errors（既存img warning 1）
- 修正ファイルなし

### 390px fresh renderが未取得の理由

- Playwright package：利用可能
- Chromium / Firefox / WebKit browser binary：未配置
- OS既存browser：なし
- CDP接続先：未稼働
- Cloud Browser：viewport変更機能なし、1363x936固定

新規OSS / browser dependencyを追加しない方針を守り、390px verificationはここで停止。

### Gate扱い

P0-04をFAILにはしないが、CSSテストだけで完全PASSにも上げない。

この技術制約はP0-06〜08の実装を止めない。ただし**本番公開Gateには未解消事項として残す**。公開前に390px実機または390px指定可能なfresh browser evidenceを取得できる場合は再確認する。

---

## 4. 次の実装Gate｜P0-06〜P0-08

**GO**

390px verificationは環境制約で追加試行しても改善しないため、P0-04をPASS_WITH_CAUTIONのまま持ち越し、次の機能実装へ進む。

### P0-06｜共通Firm detail

目標：Firm detail冒頭を共通順序にする。

- 特徴
- 日本語対応
- 無料トライアル
- 取引環境
- 注意点
- プラン一覧

その後に選択プラン詳細。

### P0-07｜7問診断

- 現行7問UI / 質問順 / DiagnosisLogicV2を変更しない
- DiagnosisPlanCurrent / current candidate dataを使う
- Block 6件はTop3不可
- Affiliate / commission / coupon / priceを採点へ入れない

### P0-08｜「なぜこの3つ？」

結果冒頭に理由説明を追加。

各候補：

- あなたとの相性
- 理由2点
- 注意1点
- 詳細を見る

人気順・おすすめ順位のような表現にしない。

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

**NO-GO**。M08 Full Regression、BLOCKER=0、CRITICAL=0、GA4確認、人間承認が必要。390px fresh実画面証跡は未取得のため、公開判断時に明示的に再評価する。

---

## 7. 最短経路

1. P0-06〜P0-08
2. M14 FAQ統合
3. 価格境界 / GA4修正
4. SEO必要分統合
5. M08 Full Regression
6. 390px fresh evidenceを再取得可能なら実施
7. Go / No-Go
8. 公開は別承認
