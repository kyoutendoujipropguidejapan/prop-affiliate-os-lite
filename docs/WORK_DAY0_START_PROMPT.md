# WORK_DAY0_START_PROMPT

更新日：2026-08-20 JST
用途：Work復活直後に最初に貼る監査開始プロンプト。

---

「プロップファームの歩き方」の続きです。

既存成果を作り直さず、現在の未公開作業版の続きから再開してください。**最初のターンではコード変更も公開もしないでください。**

本番はVersion 78です。

最初にGitHub Repository：
`kyoutendoujipropguidejapan/prop-affiliate-os-lite`

を確認し、必ず次の順番で読んでください。

1. `README.md`
2. `AGENTS.md`
3. `docs/CURRENT_STATE.md`
4. `docs/PROGRESS.md`
5. `docs/IMPLEMENTATION_READINESS.md`
6. `docs/ARTIFACT_SYNC_STATUS.md`
7. `docs/M13_M16_CROSSCHECK.md`
8. `docs/WORK_RESTART_PROMPT.md`
9. `docs/WORK_RESTART_DAY0_CHECKLIST.md`
10. `docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md`

## Artifact Existence Gate

M07 / M14 / M16 / M13は回収PDF本文をChatGPTで全文確認済みです。検証済み抽出・cross-checkはGitHubにあります。

M15 JSON / Schemaは元Artifactを改変せずGitHub同期済みです。

ただし回収PDFからの検証済み抽出を、元Markdown Artifactそのものと混同しないでください。

## 上位正本

データ・診断・SourceHealthの上位正本は最新Master v2.2です。

主要シート：

- PlanCatalogV2
- PlanCoverage
- DiagnosisPlanCurrent
- DiagnosisLogicV2
- SourceHealth
- Coupons
- PriceOffers
- UXJourney
- PageUXSpec
- CuriosityCopy
- UXCopyFinal
- FirmUXCopy
- FirmPlanFlow
- MicrocopyRules
- UXMeasurement
- UXBacklog

GitHub要約やWork fixtureだけでExcel Masterの値を上書きしないでください。

## 今回の重要なRuntime境界

M13とM16は大原則では一致していますが、Runtime Snapshotの実装契約はまだNO-GOです。

未決定事項：

- M13 `data/canonical/*` とM16 `runtime/*` の唯一のLayer B path
- `variant_id + scope` 契約
- structured human approval
- `source_priority + source_evidence_ids`
- scope-aware diagnosis policyと派生`top3_blocked`
- Monitor execution approval
- SourceHealth logical tag ↔ Canonical ID mapping

**Day0監査とM07 P0では、`data/canonical/*` / `runtime/*` を新しい正本として生成・統合しないでください。**

Runtime契約未決定を理由にMasterや既存Work値を推測補完しないでください。

## 絶対に変更しないもの

最初の監査ターンでは以下を変更禁止：

- DiagnosisLogicV2
- SourceHealthの競合状態
- 既存GA4 ID
- 基礎講座の既存URL
- クーポン条件
- 価格正本
- Official link / Affiliate CTAの役割分離
- 本番Version 78
- 公開状態
- 監視の`DRAFT_NOT_ACTIVE`

## Fintokei速攻プロ

Block解除候補はVariant単位で次を安全に保持できる場合のみです。

- `effective_from = 2026-07-15`
- 新規購入口座限定
- 旧口座分離
- Evidence保持
- 人間承認

購入日・旧口座・scopeを安全に評価できない場合はBlock継続です。

単純にfirm/plan-levelのBooleanだけで解除しないでください。

## HOLD / Block継続5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

共通：

- human-only resolution
- auto unblock禁止
- Top3 Block継続
- 確定FAQ schemaへ使用しない
- 診断Top3根拠へ使用しない

## 公開UIの基本構造

`ファーム一覧 → ファーム内プラン一覧 → 必要なプランだけ詳細`

14社一覧に全プラン詳細カードを大量表示しないでください。

ファーム詳細冒頭：

- 特徴
- 日本語対応
- 無料トライアル
- 取引環境
- 注意点
- プラン一覧

その後必要なプランのみ展開。

## 基礎講座

既存の一本道を維持：

01 プロップファームって何？
→ 02 いきなり購入しなくていい
→ 03 まず確認する3つ
→ 04 失格しやすいルールを知る
→ 05 自分に合う候補を探す
→ 30秒診断

## 診断

- DiagnosisPlanCurrentを候補母集団として使う
- DiagnosisLogicV2は変更禁止
- Affiliate / commission / coupon / priceを採点へ入れない
- Block対象はTop3から除外
- 結果は「なぜこの3つ？」から始める
- 各候補：あなたとの相性 / 理由2点 / 注意1点 / 詳細を見る

## FAQ

M11原稿を基礎とし、M14判定を優先。

- PASS：実装候補
- PASS_WITH_CAUTION：注記・公開前再確認込み実装候補
- UPDATE_REQUIRED：`docs/M14_VERIFIED_EXTRACTION_FROM_PDF.md` の差し替え本文を使用
- HOLD：確定FAQ schemaへ入れない

不要なFAQ全文改稿はしないでください。

## SEO

完成原稿：

- `docs/M09_SEO_CONTENT_PACK.md`
- `docs/M09B_SEO_CONTENT_PACK_2.md`

内部リンク：

- `docs/SEO_INTERNAL_LINK_MAP.md`

価格・割引・Affiliateを記事の主役にしないでください。

## 最初の返答でやること

**まだ実装しないでください。**

以下だけ報告してください。

1. 現在の未公開作業版の状態
2. 本番Version 78との差分
3. Master v2.2との差分
4. M07 P0仕様の適合 / 不足
5. M14 FAQ判定の反映状況
6. Fintokei / HOLD 5件の現行表現可否
7. 使用技術 / 依存
8. 採用 / 不採用するOSSと理由
9. 既存実装を維持する箇所
10. 最小P0実装プラン
11. GA4イベントの既存/追加候補重複
12. 現時点のBLOCKER / CRITICAL候補
13. Runtime/monitoringを今回触らず分離できるか

最後に、

**P0実装開始：GO / CONDITIONAL GO / NO-GO**

を1つだけ判定してください。

私が確認するまでコード変更・公開は行わないでください。

---
