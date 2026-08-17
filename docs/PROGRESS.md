# プロップファームの歩き方｜進捗

更新日：2026-08-17

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

Readiness Gate正本：`docs/IMPLEMENTATION_READINESS.md`

---

## GitHub上のArtifact状態

### 実体確認済み

- `docs/M08_QA_REGRESSION_SPEC.md`
- `docs/M09_SEO_CONTENT_PACK.md`
- `docs/M10_SOURCE_MONITORING_AUTOMATION_DESIGN.md`
- `docs/M11_FIRM_FAQ_CONTENT_PACK.md`
- `docs/M12_DRY_RUN_SOURCE_SET.md`
- `docs/WORK_RESTART_PROMPT.md`
- `docs/IMPLEMENTATION_READINESS.md`

### 完了記録はあるが詳細実体をGitHubで確認できないもの

- M01〜M07の詳細報告／M07最終統合仕様
- M13 GitHub同期設計全文
- M14 全70FAQ判定・UPDATE_REQUIRED 10件の差し替え全文
- M15 `monitor_sources` JSON Draft / JSON Schema
- M16 Runtime Snapshot仕様書 / 各Schema

PROGRESSの要約から未保存成果物の詳細を推測・復元して「元成果物」と扱わない。

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

---

## M08

`docs/M08_QA_REGRESSION_SPEC.md` をWork向けQAの唯一の正本とする。

BLOCKERまたはCRITICALが1件でも残る場合はNo-Go。

## M09

`docs/M09_SEO_CONTENT_PACK.md`

完成原稿：最大DD / Static DD / Trailing DD / EOD DD / 失格しやすいルール。

## M10 / M12 / M15

監視設計：

`公式URL → normalize → diff → noise filter → semantic candidate → SourceHealth cross-check → human review`

- M12：Primary 5 + Shadow 4 URL実体あり
- M15：9 URL設定案・Schema・Preflight完了記録あり、status `DRAFT_NOT_ACTIVE`
- ただしM15実JSON/SchemaはGitHub未同期

**M15実体同期＋Preflight＋人間承認までDry Runは開始しない。**

Master / SourceHealth / Diagnosis / Work / siteへの自動反映は禁止。

## M11 / M14

M11で14社70 FAQを作成。M14で公式一次情報により最終照合。

- PASS 32
- PASS_WITH_CAUTION 23
- UPDATE_REQUIRED 10
- HOLD 5

M14の差し替え全文がGitHub未同期のため、UPDATE_REQUIRED 10件はM11のまま公開しない。差し替え実体を回収するか、公開前に再照合する。

## M13 / M16

二層Canonical設計：

- Excel Master = 編集・監査用上位正本
- GitHub Runtime Snapshot = 人間承認済み機械可読配布層
- Work / Replitへ片方向handoff

M16ではmanifest / Firm / Plan / Diagnosis Candidate / SourceHealth / Monitor Source Schema、Approval / Rollback / Preflightまで仕様確定記録あり。

ただしM16実Schema/仕様書はGitHub未同期。

**Runtime実装はM16実体同期まで開始しない。APPROVED以外を本番データとして使わない。**

Affiliate / commission / coupon / priceは診断採点データへ混ぜない。

---

## Readiness Gate v1 結論

- Work監査開始：GO
- P0実装：CONDITIONAL GO
- FAQ統合：CONDITIONAL GO
- 監視Dry Run：NO-GO
- Runtime Snapshot実装：NO-GO
- 本番公開：M08 PASS + 人間承認までNO-GO

### 実装前に回収すると価値が高い成果物

P0：

1. M07最終統合仕様書
2. M14全判定 + UPDATE_REQUIRED 10件の差し替え全文

P1：

3. M15 `monitor_sources.json` Draft
4. M15 JSON Schema
5. M16 Runtime Snapshot仕様書 / Schema
6. M13同期設計全文

詳細：`docs/IMPLEMENTATION_READINESS.md`

---

## Work復活時

1. `README.md`
2. `AGENTS.md`
3. `docs/CURRENT_STATE.md`
4. `docs/PROGRESS.md`
5. `docs/IMPLEMENTATION_READINESS.md`
6. `docs/WORK_RESTART_PROMPT.md`
7. Master v2.2確認
8. 未公開作業版監査（まだコード変更しない）
9. M07実体の有無を確認
10. 人間確認後にP0差分実装
11. M14条件に沿ってFAQ統合
12. M08 QA
13. BLOCKER / CRITICAL = 0
14. 390px fresh render
15. 公開は別途人間承認

## 次

新規のM17/M18設計を増やすより、まず不足成果物の回収・同期を優先する。

並行して安全に進められるもの：

- M09追加SEO記事の完成原稿
- 既存SEO原稿の内部リンク設計
- 公開前のタイトル/description重複防止表
- 14社ページの「次に読む」導線コピー最終調整

サイト・Master・SourceHealth・DiagnosisLogicV2・監視状態・本番公開は変更しない。
