# WORK_RESTART_DAY0_CHECKLIST

更新日：2026-08-19 JST
対象：2026-08-20 午後のWork復活に向けた初動チェック

## 0. 目的

Work復活直後に、既存成果を作り直したり、未同期Artifactを推測補完したり、本番へ先に触れたりせず、安全に未公開作業版の監査から再開する。

## 1. Workを開く前に確認

GitHub：`kyoutendoujipropguidejapan/prop-affiliate-os-lite`

読む順番：

1. `README.md`
2. `AGENTS.md`
3. `docs/CURRENT_STATE.md`
4. `docs/PROGRESS.md`
5. `docs/IMPLEMENTATION_READINESS.md`
6. `docs/ARTIFACT_SYNC_STATUS.md`
7. `docs/WORK_RESTART_PROMPT.md`
8. この `docs/WORK_RESTART_DAY0_CHECKLIST.md`

## 2. Work復活前に同期しておきたい回収済みArtifact

現在はManus側で回収済み・GitHub未同期。

推奨保存先：

- `docs/M07_FINAL_INTEGRATION_SPEC.md`
- `docs/M14_FAQ_FINAL_AUDIT.md`
- `monitoring/monitor_sources.json`
- `schemas/monitor_sources.schema.json`
- `docs/M16_RUNTIME_SNAPSHOT_SPEC.md`
- `docs/M13_MASTER_GITHUB_SYNC_DESIGN.md`

M16は仕様書内にSchema草案を含み、個別Schema JSON実体が回収されていないため、存在しないSchemaファイルを新規生成して「回収Artifact」と扱わない。

## 3. Artifact同期後の必須再確認

- M07：P0実装順・変更禁止・既存成果再利用・公開禁止がM08/WORK_RESTARTと矛盾しない
- M14：70 FAQ判定、UPDATE_REQUIRED 10件、HOLD 5件が完全に読める
- M15：`DRAFT_NOT_ACTIVE`、Primary 5 / Shadow 4、合計9 URL、安全フラグ保持
- M16：Excel Master上位正本、APPROVED Runtimeのみ利用、Work/Replit片方向
- M13：二層Canonical、version / approval / archive / Work同期方針がM16と一致

### Fintokei速攻プロ

以下をVariant単位で保持できない場合はBlock継続。

- `effective_from = 2026-07-15`
- 新規購入口座限定
- 旧口座分離
- Evidence保持
- 人間承認

### HOLD 5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

共通：

- `resolution_mode = human_only`
- `auto_unblock_allowed = false`
- `top3_blocked = true`
- 確定FAQ schema・診断Top3根拠に使用しない

## 4. Work復活直後の最初の1ターン

`docs/WORK_RESTART_PROMPT.md` を使用。

最初はコードを書かない。

Workに報告させる内容：

1. 現在の未公開作業版の状態
2. Master v2.2との差分
3. M07 P0との適合/不足
4. M14 FAQ反映状況
5. 使用技術・依存
6. 採用/不採用するOSS
7. 最小実装プラン
8. 絶対に変更しない箇所

人間確認後にのみP0実装へ進む。

## 5. P0実装順

原則：M07同期済み最終仕様を優先し、M07が未同期なら `WORK_RESTART_PROMPT + PROGRESS + Master v2.2` をfallback contractとする。

実装時も以下を保持：

- ファーム一覧 → プラン一覧 → 必要な詳細だけ
- 14社一覧にプラン詳細カードを大量表示しない
- 価格/クーポンを主役にしない
- 基礎講座01→05→30秒診断の一本道を壊さない
- DiagnosisLogicV2を変更しない
- Affiliate / commission / coupon / priceを診断採点に使わない
- Official linkとAffiliate CTAを分離
- SourceHealth競合を勝手に解消しない

## 6. FAQ統合

M14同期済みの場合：

- PASS：実装候補
- PASS_WITH_CAUTION：注記込みで実装候補
- UPDATE_REQUIRED：M14差し替え本文を使用
- HOLD：確定FAQ schemaに入れない

M14未同期の場合、M11原稿のUPDATE_REQUIRED該当箇所をそのまま公開しない。

## 7. 実装後QA

唯一のQA正本：`docs/M08_QA_REGRESSION_SPEC.md`

順番：

1. Smoke
2. P0 Acceptance
3. Full Regression
4. Diagnosis / SourceHealth / SEO / GA4 / Link / Error
5. 390px fresh render
6. BLOCKER / CRITICAL = 0確認

BLOCKERまたはCRITICALが1件でも残ればNo-Go。

## 8. 公開Gate

公開条件：

- M08完走
- BLOCKER / CRITICAL = 0
- 390px fresh render確認
- DiagnosisLogicV2不変
- Fintokei境界安全
- HOLD 5件Top3不可
- FAQ schema整合
- Official/Affiliate link分離
- GA4二重発火なし
- 人間承認

公開は別ターン・別承認。Work復活＝公開許可ではない。

## 9. 明日のDay0判定

- Work監査：GO
- P0実装：回収済みM07のGitHub同期後に再判定
- FAQ統合：M14実体同期後に再判定
- 監視Dry Run：M15同期 + Preflight + 人間承認までNO-GO
- Runtime実装：M16実体同期までNO-GO
- 本番公開：M08 PASS + 人間承認までNO-GO
