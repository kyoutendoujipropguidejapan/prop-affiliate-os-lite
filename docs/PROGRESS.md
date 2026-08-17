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

## 重要な安全条件

### Fintokei｜速攻プロ

Block解除候補は、次をVariant単位で保持できる場合のみ。

- effective_from: 2026-07-15
- new_purchase_only: true
- legacy account separation
- Evidence保持
- human approval

条件を保持できない場合はBlock継続。

### HOLD / Block継続 5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

確定値・FAQ schema・診断Top3根拠に使用しない。自動unblock禁止。

## M08

`docs/M08_QA_REGRESSION_SPEC.md` をWork向けQAの唯一の正本とする。

BLOCKERまたはCRITICALが1件でも残る場合はNo-Go。

## M09

`docs/M09_SEO_CONTENT_PACK.md`

完成原稿：最大DD / Static DD / Trailing DD / EOD DD / 失格しやすいルール。

## M10

`docs/M10_SOURCE_MONITORING_AUTOMATION_DESIGN.md`

監視は `公式URL → normalize → diff → noise filter → semantic candidate → SourceHealth cross-check → human review`。

Master / SourceHealth / Diagnosis / Work / siteへの自動反映は禁止。

## M11 / M14

M11で14社70 FAQを作成。M14でA1〜A4優先の公式一次情報により最終照合。

- PASS 32
- PASS_WITH_CAUTION 23
- UPDATE_REQUIRED 10
- HOLD 5

HOLD 5件はFAQ schema対象外。

## M12

`docs/M12_DRY_RUN_SOURCE_SET.md`

Primary 5 URL + Shadow 4 URLで14日Dry Runを設計。

## M13

GitHub同期設計：Excel Masterと承認済みGitHub Runtime Snapshotの二層Canonical Data。

`verified_at` / `effective_from` / `supersedes` / `source_priority` / `human_approved` を保持し、Workとは片方向同期。

## M15

M12 Dry Run用 `monitor_sources` 設定ファイル案を作成。

- Primary 5 / Shadow 4、合計9 URL
- JSON Draft / JSON Schema
- Field definitions
- Domain別Parser / Noise Profile
- SourceHealth連携
- HOLD 5件：`human_only` / `auto_unblock_allowed:false`
- Fintokei Variant保護
- Validation Rules
- Replit読み込み順
- Preflight Checklist
- 構文、9 URL、Primary 5 / Shadow 4、安全フラグ、Fintokei保護条件をローカル検証済み
- status: `DRAFT_NOT_ACTIVE`

監視、HTTP取得、Cron、通知、Issue作成、Master / SourceHealth / Diagnosis変更、Work反映、サイト変更、公開は未実施。

## M16

最小Runtime Snapshot仕様を確定。

- Excel Master = 編集・監査用の上位正本
- GitHub Runtime Snapshot = 人間承認済みの機械可読配布用正本
- Work / Replitへの片方向handoff
- manifest Draft
- Firm / Plan / Diagnosis Candidate / SourceHealth / Monitor Source Schema
- Fintokei速攻プロのVariant例と日付境界保護
- HOLD 5件：human_only / auto_unblock_allowed:false / top3_blocked:true
- Validation Rules
- Approval / Rollback Flow
- Work / Replit読み込み順
- Preflight Checklist
- Runtime Snapshot v0.1でExcel Masterから抽出する最小Field一覧

Runtime SnapshotはExcel Masterを置き換えない。APPROVED以外を本番データとして利用しない。Affiliate / commission / coupon / priceは診断採点データへ混ぜない。

M16時点ではJSON実ファイル生成、コード実装、Master / SourceHealth / DiagnosisLogicV2変更、Work反映、サイト変更、公開は未実施。

## 次

### 実装前Readiness Gate

M17のような新規設計を増やす前に、M01〜M16でWork復活時に必要なものが揃ったか総点検する。

確認項目：

- Work実装に必要なP0仕様が一意か
- QA正本が一意か
- FAQのPASS / UPDATE / HOLD扱いが明確か
- Runtime Snapshot / monitor_sourcesは仕様段階と実体段階を混同していないか
- GitHubに存在しないM13〜M16成果物を正本扱いしていないか
- Fintokei VariantとHOLD 5件の安全条件が全handoffで一致しているか
- Work復活時の最初の1プロンプトだけで監査開始できるか
- 実装前に不足する実ファイルがあるか

新規調査は原則行わず、欠落・重複・矛盾だけを洗い出す。

## Work復活時

1. `docs/WORK_RESTART_PROMPT.md` で未公開作業版を監査
2. M07 P0実装
3. M14判定に沿ってFAQ統合
4. M08 QA実行
5. BLOCKER / CRITICAL = 0
6. 390px fresh render
7. 公開は別途人間承認
