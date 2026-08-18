# プロップファームの歩き方｜進捗

更新日：2026-08-18

## 完了

- M01｜公開サイト・モバイルUX総監査 ✅
- M02｜診断7問UX監査 ✅
- M03｜SEO・検索流入設計 ✅
- M04｜14社ファーム詳細ページのSEO/UX設計 ✅
- M05｜公式ソース監視設計 ✅
- M06｜SourceHealth競合6件の再調査 ✅
- M07｜M01〜M06統合・Work実装仕様確定 ✅
- M08｜実装前QA・回帰テスト仕様 ✅
- M09｜SEO記事・ルール解説の完成原稿 ✅
- M10｜公式ソース監視の自動化技術設計 ✅
- M11｜14社ファーム詳細FAQ完成原稿 ✅
- M12｜監視Dry Run用URLセット確定 ✅
- M13｜GitHubへのMaster／成果物同期設計 ✅
- M14｜14社FAQの公式一次情報最終チェック ✅
- M15｜M12 Dry Run用 monitor_sources 設定ファイル案 ✅
- M16｜最小Runtime Snapshot仕様確定 ✅
- 実装前Readiness Gate v1 ✅
- M01〜M16 Artifact回収・照合 ✅
- 追加SEO完成原稿5本 ✅
- SEO内部リンク／Metadata Guardrail設計 ✅

Readiness Gate正本：`docs/IMPLEMENTATION_READINESS.md`
Artifact同期待ち台帳：`docs/ARTIFACT_SYNC_STATUS.md`

---

## GitHub上のArtifact状態

### 実体確認済み

- `docs/M08_QA_REGRESSION_SPEC.md`
- `docs/M09_SEO_CONTENT_PACK.md`
- `docs/M09B_SEO_CONTENT_PACK_2.md`
- `docs/M10_SOURCE_MONITORING_AUTOMATION_DESIGN.md`
- `docs/M11_FIRM_FAQ_CONTENT_PACK.md`
- `docs/M12_DRY_RUN_SOURCE_SET.md`
- `docs/SEO_INTERNAL_LINK_MAP.md`
- `docs/WORK_RESTART_PROMPT.md`
- `docs/IMPLEMENTATION_READINESS.md`
- `docs/ARTIFACT_SYNC_STATUS.md`

### Manus側で回収済み・GitHub未同期

P0：

1. M07最終統合仕様
2. M14 全70 FAQ判定 + UPDATE_REQUIRED 10件の差し替え本文

P1：

3. M15 `monitor_sources.json` Draft
4. M15 JSON Schema
5. M16 Runtime Snapshot仕様書 / 各Schema
6. M13 GitHub同期設計全文

これらは **RECOVERED_LOCAL_NOT_SYNCED**。GitHubへ実ファイル同期・再検証するまで、GitHub上のCanonical Artifactとして扱わない。

M01〜M06の詳細報告は、必要になった時だけ実体の有無を確認する。既存正本から不要に再生成しない。

---

## 重要な安全条件

### Fintokei｜速攻プロ

Block解除候補はVariant単位で次を保持できる場合のみ。

- `effective_from = 2026-07-15`
- `new_purchase_only = true`
- 旧口座分離
- Evidence保持
- human approval

条件を安全に評価できない場合はBlock継続。

### HOLD / Block継続 5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

共通：

- `resolution_mode = human_only`
- `auto_unblock_allowed = false`
- `top3_blocked = true`
- 確定値・FAQ schema・診断Top3根拠に使用しない

回収したM07/M13/M14/M15/M16 Artifactでも、この安全条件が整合していると報告済み。GitHub同期時に再確認する。

---

## M08

`docs/M08_QA_REGRESSION_SPEC.md` をWork向けQAの唯一の正本とする。

BLOCKERまたはCRITICALが1件でも残る場合はNo-Go。

## M09 / M09B

`docs/M09_SEO_CONTENT_PACK.md`

- 最大DD
- Static DD
- Trailing DD
- EOD DD
- 失格しやすいルール

`docs/M09B_SEO_CONTENT_PACK_2.md`

- 無料トライアル
- ニュース取引
- 週末持ち越し
- 最低取引日数
- 出金条件

合計10本の初心者向け完成原稿。動的な各社数値は一般論として断定せず、公開前Fact-check Gateを通す。

内部リンク・Title/Meta/Canonicalの重複防止は `docs/SEO_INTERNAL_LINK_MAP.md` を使用する。

## M10 / M12 / M15

監視設計：

`公式URL → normalize → diff → noise filter → semantic candidate → SourceHealth cross-check → human review`

- M12：Primary 5 + Shadow 4 URL実体あり
- M15：`monitor_sources.json` Draft / SchemaをManus側で回収済み
- M15 status：`DRAFT_NOT_ACTIVE`
- まだGitHub未同期

**M15実体同期＋Preflight＋人間承認までDry Runは開始しない。**

Master / SourceHealth / Diagnosis / Work / siteへの自動反映は禁止。

## M11 / M14

M11で14社70 FAQを作成。M14で公式一次情報により最終照合。

- PASS 32
- PASS_WITH_CAUTION 23
- UPDATE_REQUIRED 10
- HOLD 5

M14の全70判定とUPDATE_REQUIRED 10件の差し替え本文はManus側で回収済み。ただしGitHub未同期のため、差し替え実体を同期・照合するまでUPDATE_REQUIRED 10件をM11のまま公開しない。

## M13 / M16

二層Canonical設計：

- Excel Master = 編集・監査用上位正本
- GitHub Runtime Snapshot = 人間承認済み機械可読配布層
- Work / Replitへ片方向handoff

M13設計全文、M16 Runtime Snapshot仕様 / SchemaはManus側で回収済み。ただしGitHub未同期。

**Runtime実装はM16実体同期まで開始しない。APPROVED以外を本番データとして使わない。**

Affiliate / commission / coupon / priceは診断採点データへ混ぜない。

---

## Readiness Gate v1 結論

Artifact回収後も、GitHub未同期のためGateはまだ据え置く。

- Work監査開始：GO
- P0実装：CONDITIONAL GO
- FAQ統合：CONDITIONAL GO
- 監視Dry Run：NO-GO
- Runtime Snapshot実装：NO-GO
- 本番公開：M08 PASS + 人間承認までNO-GO

次のGate更新条件：回収済み6 Artifactの実ファイル同期・全文照合・安全条件再確認。

---

## Work復活時

1. `README.md`
2. `AGENTS.md`
3. `docs/CURRENT_STATE.md`
4. `docs/PROGRESS.md`
5. `docs/IMPLEMENTATION_READINESS.md`
6. `docs/ARTIFACT_SYNC_STATUS.md`
7. `docs/WORK_RESTART_PROMPT.md`
8. Master v2.2確認
9. 未公開作業版監査（まだコード変更しない）
10. M07同期状況を確認
11. 人間確認後にP0差分実装
12. M14同期済み判定に沿ってFAQ統合
13. M09/M09B記事と内部リンクを必要な分だけ実装
14. M08 QA
15. BLOCKER / CRITICAL = 0
16. 390px fresh render
17. 公開は別途人間承認

## 次

最優先は、回収済み6 Artifactの実ファイルをGitHubへ安全に同期すること。

同期手順：

`実ファイル受領 → 全文確認 → 既存Artifact照合 → Fintokei/HOLD安全条件確認 → 保存先確定 → GitHub同期 → 再Fetch/SHA確認 → Readiness再判定`

並行して安全に進められるもの：

- 14社ページの「次に読む」導線コピー最終調整
- SEO記事10本の掲載優先順位とSearch Console投入順の整理
- Metadata重複防止表

サイト・Master・SourceHealth・DiagnosisLogicV2・監視状態・本番公開は変更しない。
