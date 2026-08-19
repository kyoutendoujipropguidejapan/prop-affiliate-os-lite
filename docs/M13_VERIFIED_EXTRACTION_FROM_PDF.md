# M13｜GitHubへのMaster／成果物同期設計｜検証済み抽出

更新日：2026-08-20 JST
Source：回収PDF 20ページ
Source SHA-256：`84ba35a65f7cfcbd3ce46d27f7d7542e1da8e8df2539f93bc4e45f8dc7828af9`
状態：VERIFIED EXTRACTION / 元M13 Artifactそのものではない

## 結論

M13は、Excel Masterをビジネス値・運用判断の最上位正本として維持し、GitHubには人間承認済み・範囲付きの機械可読snapshotと仕様・Evidence・履歴を置く二層Canonical設計である。

GitHubはExcel Masterの編集代替ではない。WorkはGitHub Canonical Snapshotをread-onlyで参照し、Work→GitHub Canonicalの自動逆流、GitHub→本番の自動公開、監視→Masterの自動反映を禁止する。

## 主要安全原則

- 正本性はファイル名の新しさではなく、stable path / master_release_id / hash / verified_at / effective period / Source Priority / human approval / Git履歴で判定する。
- Excel Master = Layer A / Business Canonical。
- GitHub approved snapshot = Layer B / Runtime Canonical Snapshot。
- GeneratedはCanonicalから再生成可能にし、手編集しない。
- EvidenceはURLだけでなく、evidence_id / 引用範囲 / 取得日時 / plan・variant scope / Source Priority / page hashを保持する。
- Workは実装・preview・QAの担当であり、Firm / Plan / SourceHealthの唯一正本にならない。
- 本番公開はM08 QAと人間承認後の別タスク。

## M13が推奨するLayer B最小構成

- `data/canonical/master-release-manifest.yaml`
- `data/canonical/firm-catalog.json`
- `data/canonical/plan-catalog.csv`
- `data/canonical/diagnosis-eligibility.json`
- `data/canonical/source-health.json`
- `data/canonical/monitor-sources.csv`
- P1として `offer-status.yaml`

M13はJSON/CSV/YAMLを用途別に使い分ける。DiagnosisLogicV2全体はGitHubへ複製せず、version/hash/read-only参照だけを残す。

## Variant / SourceHealthの重要原則

M13は単純なfirm/plan-level Booleanだけで診断可否を決める設計を避ける。

候補可否は `PlanVariant + scope + approval` から派生させる。

共通Fieldとして、

- firm_id / plan_id / variant_id
- status
- verified_at
- effective_from / effective_to
- supersedes
- source_priority
- source_evidence_ids
- human approval（承認者・時刻・scopeを含む）

を重視する。

## Fintokei｜速攻プロ

限定Variantとして扱うための固定条件：

- 2026-07-15以降
- new purchase only
- Legacy Variantを別variant_idで保持
- 人間承認（承認者 / 承認時刻 / approval_scope）
- 複数の公式Evidence
- Workがscopeを評価できなければBlock

M13内の例は `APPROVED_CURRENT_SCOPE` / `ELIGIBLE_CURRENT_SCOPE` を示すが、これは形式例であり実際のBlock解除指示ではない。条件が1つでも欠ければ `BLOCKED_SOURCE_REVIEW`。

## HOLD 5件

以下は `CONFLICT / BLOCKED_SOURCE_CONFLICT` 継続：

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

単一ソース、単一ページ、ファイル更新だけで解除しない。

## Work同期フロー

`公式一次情報・運営判断 → Excel Master → 人間review/export → GitHub approved snapshot + manifest + evidence ref → PR/hash照合 → Work preview(read-only) → M08 QA/fresh render → 人間承認 → 別タスクで公開`

逆方向の自動writeは禁止。

## Archive / Backup

- 旧recordは削除せず `supersedes` で追跡。
- Master releaseはrelease ID/hash/manifestを残す。
- GitHub Canonical Snapshotはcommit/tagで固定し、main直接pushではなくPR reviewを前提にする。
- EvidenceはCookie/認証情報/PIIを含めない。

## M13からM16へ引き継ぐべき必須契約

1. `variant_id` とscopeをfirst-classで扱う。
2. human approvalを単独Booleanだけにしない。
3. `source_priority` と `source_evidence_ids` を条件値のprovenanceとして保持する。
4. SourceHealthからdiagnosis可否は派生させ、単純Booleanだけで安全判定を完結させない。
5. Workはapproved snapshotのみread-only参照。
6. GitHub snapshot mergeと本番公開を分離する。
7. Fintokei限定VariantとHOLD 5件はfail-safeでBlock側へ倒す。

## 注意

本ファイルは回収PDFからの検証済み実装用抽出であり、元M13 Markdown Artifactそのものではない。元ArtifactがGitHubへ同期される場合は別ファイルとして扱い、混同しない。
