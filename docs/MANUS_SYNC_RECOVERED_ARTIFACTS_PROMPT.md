# MANUS_SYNC_RECOVERED_ARTIFACTS_PROMPT

更新日：2026-08-19 JST
用途：Work復活前に、Manus側で回収済みの6 ArtifactをGitHubへ安全に同期するための実行指示。

---

GitHub Repository：
`kyoutendoujipropguidejapan/prop-affiliate-os-lite`

M01〜M16 Artifact回収・照合で「回収済み・GitHub未同期」と確認した既存成果物6件を、**再作成せず、元ファイル内容を維持したままGitHubへ同期してください。**

## 同期対象と保存先

1. M07最終統合仕様
   - `docs/M07_FINAL_INTEGRATION_SPEC.md`
2. M14 全70 FAQ判定 + UPDATE_REQUIRED 10件差し替え本文
   - `docs/M14_FAQ_FINAL_AUDIT.md`
3. M15 `monitor_sources.json` Draft
   - `monitoring/monitor_sources.json`
4. M15 JSON Schema
   - `schemas/monitor_sources.schema.json`
5. M16 Runtime Snapshot仕様書（回収済み成果物内にSchema草案を含む）
   - `docs/M16_RUNTIME_SNAPSHOT_SPEC.md`
6. M13 GitHubへのMaster／成果物同期設計全文
   - `docs/M13_MASTER_GITHUB_SYNC_DESIGN.md`

M16について、個別Schema JSONファイルが元Artifactとして存在しない場合は新規生成しないでください。仕様書内Schema草案をそのまま保存してください。

## 最重要ルール

- 元Artifactを要約版へ置換しない
- 内容を最新化しない
- 不足部分を想像で補完しない
- 既存ファイルが同じpathに存在する場合は上書きせず差分報告する
- Masterを変更しない
- SourceHealthを変更しない
- DiagnosisLogicV2を変更しない
- Workを変更しない
- サイトコードを変更しない
- 公開しない
- 監視を開始しない
- Cronを開始しない
- Issue自動作成を開始しない

## 同期前安全確認

### Fintokei速攻プロ

回収Artifact内で次の5条件が維持されていることを確認：

- `effective_from = 2026-07-15`
- 新規購入口座限定
- 旧口座分離
- Evidence保持
- 人間承認

条件が欠けている場合、元ファイルを修正せず「差分あり」と報告してください。

### HOLD 5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

Block継続と整合していることを確認してください。M15/M16では可能なら次の意味が維持されているか確認：

- `resolution_mode = human_only`
- `auto_unblock_allowed = false`
- `top3_blocked = true`

### M15

次を確認：

- status = `DRAFT_NOT_ACTIVE`
- Primary 5
- Shadow 4
- 合計9 URL
- Master / SourceHealth / Diagnosis / Work / siteへの自動反映禁止

## 同期手順

1. GitHub最新treeを取得
2. 対象pathが未使用か確認
3. 元ファイル全文を読み込む
4. 安全条件を照合
5. 6 Artifactを指定pathへ同期
6. 各ファイルをGitHubから再Fetch
7. 非空・切断なし・内容一致を確認
8. commit SHA / blob SHAを記録
9. `docs/ARTIFACT_SYNC_STATUS.md` を `SYNCED_VERIFIED` 相当に更新
10. `docs/PROGRESS.md` を「回収済み・GitHub同期済み」に更新
11. `docs/IMPLEMENTATION_READINESS.md` のGateを再判定

## Readiness再判定ルール

同期と再Fetch確認がすべてPASSした場合のみ再判定してください。

- Work監査：GO維持
- P0実装：M07同期・整合PASSならGO候補
- FAQ統合：M14同期・整合PASSならGO候補
- 監視Dry Run：M15同期だけでは開始しない。Preflight + 人間承認までCONDITIONAL/NO-GO
- Runtime Snapshot実装：M16同期・仕様確認後にCONDITIONAL GO候補
- 本番公開：M08完走 + BLOCKER/CRITICAL=0 + 390px fresh render + 人間承認までNO-GO

## 最終報告

以下を簡潔に報告してください。

- 同期した6ファイルpath
- 各commit/blob SHA
- 内容一致確認 PASS/FAIL
- Fintokei 5条件 PASS/FAIL
- HOLD 5件整合 PASS/FAIL
- M15 `DRAFT_NOT_ACTIVE` PASS/FAIL
- 重複・矛盾
- 更新後Readiness

確認質問は不要です。元Artifactが実在するものだけ同期してください。

---
