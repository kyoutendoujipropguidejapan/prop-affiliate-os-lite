# ARTIFACT_SYNC_STATUS

更新日：2026-08-18 JST
対象：プロップファームの歩き方
目的：Manus側で回収できた既存成果物と、GitHub上で実体確認できる正本を混同しないための同期待ち台帳。

## 現在の結論

M01〜M16の回収・照合により、これまで「完了記録はあるが詳細実体が未確認」だった重要Artifactのうち、実装前優先度が高い6成果物は **ローカル回収済み**。

ただし、2026-08-18時点ではGitHubへ未同期のため、GitHub上のCanonical Artifactへはまだ昇格していない。

**状態：RECOVERED_LOCAL_NOT_SYNCED**

## 回収済み6成果物

### P0

1. M07｜M01〜M06統合・Work最終実装仕様
2. M14｜全70 FAQ判定 + UPDATE_REQUIRED 10件の差し替え本文

### P1

3. M15｜`monitor_sources.json` Draft
4. M15｜JSON Schema
5. M16｜最小Runtime Snapshot仕様（各Schemaを含む回収成果物）
6. M13｜GitHubへのMaster／成果物同期設計全文

## GitHub昇格条件

各Artifactは、次を満たした場合のみGitHub上の読める正本候補へ昇格する。

1. 実ファイルを受領する
2. 内容を全文確認する
3. 既存GitHub成果物と重複・矛盾を照合する
4. Fintokei速攻プロの安全条件を確認する
5. HOLD 5件のBlock継続条件を確認する
6. M15は `DRAFT_NOT_ACTIVE` を確認する
7. 自動公開・自動Master更新等の禁止条件を確認する
8. 適切な保存先と名称を確定する
9. GitHub同期後に再Fetchし、内容とSHAを確認する
10. `PROGRESS.md` / `IMPLEMENTATION_READINESS.md` を同期済み状態へ更新する

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
- 監視開始禁止
- Cron開始禁止
- 自動Issue作成禁止
- Master / SourceHealth / Diagnosis / Work / siteへの自動反映禁止

## Readinessへの影響

回収できたこと自体は前進だが、GitHub未同期のため現行Gateはまだ変更しない。

- Work監査：GO
- P0実装：CONDITIONAL GO
- FAQ統合：CONDITIONAL GO
- 監視Dry Run：NO-GO
- Runtime Snapshot実装：NO-GO
- 本番公開：NO-GO

実ファイル同期と再検証後にGateを再判定する。

## 次のアクション

回収した6成果物の実ファイルを受領し、**1ファイルずつ内容確認 → 既存GitHubとの照合 → 安全条件検証 → 同期** の順で進める。

不足内容をPROGRESS要約から再生成して、回収Artifactと同一扱いしない。
