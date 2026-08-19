# M13 ↔ M16 Cross-check

更新日：2026-08-20 JST
対象：M13 GitHub/Master同期設計 と M16 最小Runtime Snapshot仕様
状態：RECONCILIATION_REQUIRED / Runtime実装はまだNO-GO

## 結論

M13とM16は大原則では一致する。

一致事項：

- Excel Masterが上位正本
- GitHub側は承認済みsnapshot配布層
- Work / Replitはread-only片方向
- GitHub mergeと本番公開は別
- DiagnosisLogicV2を複製・変更しない
- Affiliate / Commission / Coupon / Priceを診断採点へ混ぜない
- Fintokei速攻プロは2026-07-15以降・新規購入・Legacy分離・Evidence・人間承認が揃わなければBlock
- HOLD 5件は自動解除しない
- rollback / supersedes / hash / human reviewを使う

ただし、M16は作成時にM13全文を直接読めていなかったため、実装契約には複数の差がある。Runtime実装前に解消が必要。

## C01｜保存パス / Layer Bの名前

M13：`data/canonical/*` をLayer B Runtime Canonical Snapshotとして提案。

M16：`runtime/*` をapproved distribution snapshotとして提案。

同じ責務を2箇所に複製すると二重正本になるため、両方を同時にCanonicalとして実装しない。

**現時点の扱い：未決定。Work P0ではどちらも新規実装しない。**

## C02｜Plan Variant

M13：`plan_id + variant_id + scope + effective period` を明示。FintokeiはLegacy/currentを別variant_idで保持。

M16：`plans.json` Schemaにvariant_idがなく、Fintokei具体例だけ `variant` objectを持つ。一方、diagnosis candidate Schemaは `additionalProperties:false` のため具体例とSchemaが矛盾する。

**推奨契約：M13のvariant_id/scopeモデルを採用してからM16 Schema vNextを作る。**

## C03｜Human approval

M13：human approvalは単独Boolean禁止。承認者・承認時刻・approval scopeとセット。

M16：manifest / source_healthでは `human_approved` Booleanが中心。

**推奨契約：M16 vNextではstructured approval objectを採用し、必要ならBooleanは派生値にする。**

## C04｜Provenance / Evidence

M13：条件値に `source_priority` と `source_evidence_ids` を必須化し、URLだけではなく引用範囲・snapshot/hashへ紐づける。

M16：主に `source_refs` を使用し、priority/evidence IDの強制が弱い。

**推奨契約：M13のprovenanceを優先し、M16のsource_refsは補助リンク扱い。**

## C05｜SourceHealth → Diagnosis

M13：単純な `top3_block=false` のようなBooleanだけで安全判定しない。Variant/scope/approvalから `diagnosis_policy` を派生。

M16：`top3_blocked` BooleanをSourceHealth / Candidateに保持。

Boolean自体はcache/派生値として利用可能だが、正本判断の唯一入力にしない。

**推奨契約：CanonicalはM13型のscope-aware policy、Runtimeでは派生 `top3_blocked` を持ってよい。**

## C06｜Monitor Source実行状態

M13：monitoringは仕様・dry run・change classificationを分離し、Cron/自動公開を含めない。

M15：`DRAFT_NOT_ACTIVE`。

M16：Runtime SnapshotがAPPROVEDでもMonitor実行開始は別承認と説明するが、Runtime用Schemaではtop-level execution gateが弱い。

**推奨契約：Snapshot approvalとMonitor execution approvalを別Field/別manifestで分離する。**

## C07｜File formats

M13：用途別にJSON/CSV/YAMLを使う。

M16：最小RuntimeをJSON中心に統一。

これは安全性上の必須衝突ではない。将来の実装コスト・diff可読性を見て決める。

## C08｜SourceHealth ID

M15/M16：`SH_FINTOKEI_SWIFT` 等のlogical labelを使用。

Master：`SH001`, `SH003`, `SH008`, `SH012` 等のCanonical ID。

M13はstable IDとEvidence参照を重視するがmapping形式は未固定。

**実装前にCanonical ID / logical tag mapping contractを決める。**

## Work復活時への影響

### Work Day0監査

GO。M13/M16のRuntime naming差は、未公開Work作業版の監査を妨げない。

### M07 P0実装

CONDITIONAL GO。P0はMaster v2.2/M07/M14/既存Workを基準に行い、M13/M16 Runtime層を新規実装しない。

### FAQ統合

CONDITIONAL GO。M13/M16差とは独立。

### Runtime Snapshot実装

NO-GO。C01〜C08のうち最低C01〜C06/C08をcontract decisionとして確定してからvNext Schemaを作る。

### Monitoring Dry Run

NO-GO。M15はDRAFT_NOT_ACTIVEのまま。SourceHealth ID mapping・Preflight・人間承認後のみ。

## 明日のWorkに対する停止条件

WorkはDay0/P0作業中に以下をしない：

- `data/canonical/*` または `runtime/*` を新しい正本として勝手に生成しない
- M13/M16のpath差を独自判断で統合しない
- Fintokeiをfirm-level Booleanで解除しない
- HOLD 5件を解除しない
- Work fixtureをGitHub canonicalへ逆流させない
- Runtime設計未決定を理由に既存Master/Work値を推測補完しない

## 将来の統合案（提案・未承認）

最小の統合方向は、**M13の意味契約を優先し、M16の小さいJSON配布設計をvNextとして合わせる**こと。

具体的には：

- variant_id / scope / effective periodを追加
- structured human approval
- source_priority + source_evidence_ids
- scope-aware diagnosis_policyをCanonicalに保持
- top3_blockedは派生値
- monitor execution gateをsnapshot approvalから分離
- logical SourceHealth tag → Canonical ID mappingを明示

この統合案はまだ実装・承認していない。
