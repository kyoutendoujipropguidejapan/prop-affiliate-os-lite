# M15_INGEST_VALIDATION

更新日：2026-08-19 JST
対象：`monitor_sources.json`
Source SHA-256：`c481efa8997694971e52350d1ff4e9a3c620ad002d3d19faef5b2afe57efc8fc`
GitHub blob SHA：`ec92a4798dd8cccd06dd4dff199fbda1fd9441a7`
状態：**INGESTED_VERIFIED_SYNCED_DRAFT**

## 1. 受領・同期確認

- JSON構文：PASS
- sources：9件
- Primary：DR01〜DR05の5件
- Shadow：DR06〜DR09の4件
- M12の9 URLとの完全一致：PASS
- status：`DRAFT_NOT_ACTIVE`
- activation_phase：`not_started`
- Primary 5：`enabled=true`
- Shadow 4：`enabled=false` / `phase_2`
- GitHub `monitoring/monitor_sources.json` へ元内容を改変せず同期
- GitHub blob SHAはローカル元ファイルから計算したGit blob SHAと一致

## 2. 安全フラグ

全体Safety Policy：

- `master_auto_update_allowed=false`
- `sourcehealth_auto_update_allowed=false`
- `diagnosis_auto_update_allowed=false`
- `work_auto_apply_allowed=false`
- `site_auto_publish_allowed=false`
- `conflict_resolution_default=human_only`
- `sourcehealth_resolution_requires_crosscheck=true`
- `human_review_default=true`

全9 sourceで：

- `human_review_required=true`
- `auto_publish_allowed=false`
- `sourcehealth_resolution_mode=human_only`
- `auto_unblock_allowed=false`

よって、受領Draft自体からMaster / SourceHealth / Diagnosis / Work / siteへ自動反映する設計にはなっていない。

## 3. Fintokei速攻プロVariant保護

DR01で以下を確認。

- `effective_from=2026-07-15`
- `new_purchase_only=true`
- `legacy_account_separation_required=true`
- `evidence_required=true`
- `human_approval_required=true`
- 条件判定不能時はBlock継続というnotesあり

M07 / M12 / M14の安全条件と整合。

## 4. M12整合

M12のDry Run URLセットと比較し、DR01〜DR09のURL、Primary/Shadow区分、優先度、主要watch対象は整合した。

特に：

- DR01：effective date / legacy-new split
- DR02：country set diff
- DR03：FundingPips model / eligibility / coupon wording
- DR04：promotion validityを掲載だけで有効判定しない
- DR05/DR06：Hantec Instant Lite cross-check
- DR07：FTM Instant Pro 3% / no daily DD conflict
- DR08/DR09：The5ers Futures EN/JP locale cross-check

を保持している。

## 5. Activation前に解決・確認すべき点

### A. SourceHealth IDの参照整合

このDraftの `sourcehealth_ids` には、MasterのCanonical IDとは異なる意味ラベルが含まれる。

代表例：

- DR01：`SH_FINTOKEI_SWIFT`（Master canonicalは `SH001`）
- DR05/DR06：`SH_HANTEC_INSTANT_LITE`（canonicalは `SH003`）
- DR07：`SH_FTM_INSTANT_PRO`（canonicalは `SH012`）
- DR08/DR09：`SH_THE5ERS_FUTURES_LOCALE`（canonicalは `SH008`）

DR03は `SH011` と意味ラベル `SH_FUNDINGPIPS_ELIGIBILITY` を併記している。
DR02 / DR04も意味ラベルを使用している。

このfieldがCanonical SourceHealthへのforeign keyなのか、monitoring側のlogical tagを許すfieldなのかをSchemaで確定するまで、SourceHealth連携はACTIVE化しない。

**元Artifactは改変しない。** Schema確認後、必要なら新しい修正版として別version化する。

### B. Global activation gate

Primary 5は `enabled=true` だが、全体は `status=DRAFT_NOT_ACTIVE` / `activation_phase=not_started`。

Runnerは必ずglobal statusをsource-level `enabled` より先に評価する必要がある。Schema / Runtime仕様 / runner contractでこのprecedenceを確認するまでHTTP fetchやCronを開始しない。

### C. 自動Issue / Cronの明示flag

今回のJSONには自動Issue作成やCron開始を許可するflag自体は定義されていない。M15成果物の非実行方針上は問題ないが、将来runnerが実装される際は「未定義=許可」と解釈しないこと。

## 6. Readiness判定

- M15 JSON Artifactの回収：GO
- GitHub同期：GO / 完了
- Dry Run設定内容の基本整合：PASS_WITH_CAUTION
- 監視Dry Run開始：**NO-GO**

NO-GO理由：

1. `monitor_sources.schema.json` の本文確認・同期前
2. SourceHealth ID fieldの意味と参照整合をSchemaで確認する必要あり
3. global DRAFT gate precedenceをSchema / runner contractで確認する必要あり
4. Preflight全PASS・人間のACTIVE化承認前

## 7. 次

次に `monitor_sources.schema.json` を全文確認し、

- sourcehealth_idsの制約
- status / enabled / activation_phaseの条件
- Variant必須条件
- Primary/Shadow条件
- safety flags
- URL / source_id uniqueness

を検証する。

Schema確認後も、明示的な人間承認がない限り監視を開始しない。
