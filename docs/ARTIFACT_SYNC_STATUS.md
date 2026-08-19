# ARTIFACT_SYNC_STATUS

更新日：2026-08-19 JST
対象：プロップファームの歩き方
目的：Manus側で回収できた既存成果物と、GitHub上で実体確認できる正本を混同しないための同期待ち台帳。

## 現在の結論

M01〜M16の回収・照合により、これまで「完了記録はあるが詳細実体が未確認」だった重要Artifactのうち、実装前優先度が高い6成果物は **Manus側で回収済み**。

ユーザー報告では2026-08-19に6ファイルを個別添付済み。ファイル名は下記のとおり。ただし、このChatGPTセッションのファイル検索では現時点で6実体ファイル本文をまだ読み取れていないため、内容照合・GitHub同期・SHA確認は未実施。

**状態：USER_REPORTED_ATTACHED_PENDING_INGEST_AND_SYNC**

## 回収済み6成果物（ユーザー報告の実ファイル名）

### P0

1. M07｜`M07_integrated_work_implementation_spec.md`
2. M14｜`M14_firm_faq_primary_source_final_check.md`

### P1

3. M15｜`monitor_sources.json`
4. M15｜`monitor_sources.schema.json`
5. M16｜`M16_minimum_runtime_snapshot_spec.md`
6. M13｜`M13_github_master_artifact_sync_design.md`

M16は仕様書内にSchema草案を含むが、個別Schema JSON実体は元Artifactとして回収されていない。存在しないSchemaを再生成して「回収Artifact」と扱わない。

ユーザー報告では、6件とも非空・基本的な切断なし・元内容未改変・指定安全条件トークンあり・差分なし。ただしGitHub Canonical昇格前にChatGPT側で再確認する。

## GitHub昇格条件

各Artifactは、次を満たした場合のみGitHub上の読める正本候補へ昇格する。

1. このセッションで実ファイル本文を読み取れる状態にする
2. 内容を全文確認する
3. 既存GitHub成果物と重複・矛盾を照合する
4. Fintokei速攻プロの安全条件を確認する
5. HOLD 5件のBlock継続条件を確認する
6. M15は `DRAFT_NOT_ACTIVE` を確認する
7. 自動公開・自動Master更新等の禁止条件を確認する
8. 適切な保存先と名称を確定する
9. GitHub同期後に再Fetchし、内容とSHAを確認する
10. `PROGRESS.md` / `IMPLEMENTATION_READINESS.md` を同期済み状態へ更新する

## 推奨GitHub保存先

- `docs/M07_FINAL_INTEGRATION_SPEC.md`
- `docs/M14_FAQ_FINAL_AUDIT.md`
- `monitoring/monitor_sources.json`
- `schemas/monitor_sources.schema.json`
- `docs/M16_RUNTIME_SNAPSHOT_SPEC.md`
- `docs/M13_MASTER_GITHUB_SYNC_DESIGN.md`

元ファイル名は必要に応じて本文またはSync Logに残し、内容は改変しない。

## 安全条件

### Fintokei｜速攻プロ

以下をVariant単位で保持できない限りBlock継続。

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

### M15

- `DRAFT_NOT_ACTIVE` 維持
- Primary 5 / Shadow 4 / 合計9 URL
- 監視開始禁止
- Cron開始禁止
- 自動Issue作成禁止
- Master / SourceHealth / Diagnosis / Work / siteへの自動反映禁止

## Readinessへの影響

ユーザー報告で実ファイル名まで確定したことは前進だが、ChatGPT側の全文読取とGitHub同期が未完了のため現行Gateはまだ変更しない。

- Work監査：GO
- P0実装：CONDITIONAL GO
- FAQ統合：CONDITIONAL GO
- 監視Dry Run：NO-GO
- Runtime Snapshot実装：NO-GO
- 本番公開：NO-GO

実ファイル全文確認・GitHub同期・再Fetch/SHA検証後にGateを再判定する。

## 次のアクション

6ファイルがこのセッションで読み取れるようになり次第、**全文確認 → 既存GitHubとの照合 → 安全条件検証 → GitHub同期 → 再Fetch/SHA確認 → Readiness再判定** の順で進める。

不足内容をPROGRESS要約から再生成して、回収Artifactと同一扱いしない。
