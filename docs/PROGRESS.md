# プロップファームの歩き方｜進捗

更新日：2026-08-20

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
- 実装前Readiness Gate ✅
- M01〜M16 Artifact回収・照合 ✅
- M13↔M16 cross-check ✅
- Work Day0監査 ✅
- M07 P0-01〜P0-03 実装・検証 ✅（Work報告ベース）
- M07 P0-05 Firm-first段階表示 ✅（Work報告ベース）
- 追加SEO完成原稿5本 ✅
- SEO内部リンク／Metadata Guardrail設計 ✅

Readiness Gate正本：`docs/IMPLEMENTATION_READINESS.md`
Artifact台帳：`docs/ARTIFACT_SYNC_STATUS.md`

---

## Work最新状態

### P0-01〜03

Work報告ベースでPASS。

- Firm = 14
- PlanCatalog = 69
- Diagnosis data rows = 65
- SourceHealth = 14
- FundingPips = 5 plans
- SH011〜SH014 synced
- Block 6件維持
- SuperFunded 1-Step = Trailing / min 3 days
- SuperFunded 2-Step = min 4 days each phase
- DiagnosisLogicV2差分なし
- commercial dataの診断採点混入なし
- total 29/29 PASS
- build PASS
- lint error 0 / existing img warning 1
- Production publish / Version save = not done

### P0-05 Firm-first

PASS。

- 14社を会社単位で初期表示
- 全69プランを初期閉鎖
- 会社 → プラン一覧 → 詳細の3段階
- FundingPips検索 = 1社 / 5プラン
- Block 6件を「公式情報を確認中」として公開UIで区別
- 内部用語は公開UIに出さない
- DiagnosisLogicV2 / 質問 / 採点 / GA4 / price / couponは変更なし
- 29/29 tests PASS
- build PASS
- lint error 0
- git diff --check PASS

### P0-04 390px Mobile UX

**PASS_WITH_CAUTION**。

390px fresh renderを再試行したが環境制約で取得できなかった。

- Playwright package：利用可能
- Chromium / Firefox / WebKit binary：未配置
- OS browser：なし
- CDP接続先：未稼働
- Cloud Browser：1363x936固定、390px変更不可
- 390px向けCSS / 構造テスト：PASS
- 29/29 tests：PASS
- build：PASS
- lint：0 errors / existing warning 1
- 修正ファイル：なし

P0-04は完全PASSへ上げない。ただし、同じ環境で再試行しても390px evidence取得不能であることが確認できたため、**P0-06〜08の実装は止めず、公開GateへCautionとして持ち越す**。

---

## 重要な安全条件

### Fintokei｜速攻プロ

- `effective_from = 2026-07-15`
- new purchase only
- 旧口座分離
- Evidence
- human approval

現行Workでは条件付き解除を実装せず、Top3 Block継続。

### HOLD / Block継続 5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

共通：human-only / auto-unblock禁止 / Top3 Block継続 / FAQ schemaへ使わない / 診断Top3根拠へ使わない。

### Diagnosis

- DiagnosisLogicV2不変
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0/falseで代用しない
- Conflictを自動Verified化しない

---

## M08

`docs/M08_QA_REGRESSION_SPEC.md` をWork向けQAの唯一の正本とする。

BLOCKERまたはCRITICALが1件でも残る場合はNo-Go。

---

## M09 / M09B

完成原稿10本：

- 最大DD
- Static DD
- Trailing DD
- EOD DD
- 失格しやすいルール
- 無料トライアル
- ニュース取引
- 週末持ち越し
- 最低取引日数
- 出金条件

内部リンク・Metadata Guardrail：`docs/SEO_INTERNAL_LINK_MAP.md`

---

## M10 / M12 / M15

監視はまだ `DRAFT_NOT_ACTIVE`。

M15 JSON / SchemaはGitHub同期・構造検証済みだが、SourceHealth ID mapping / Preflight / 人間承認未完了のためDry RunはNO-GO。

Master / SourceHealth / Diagnosis / Work / siteへの自動反映は禁止。

---

## M11 / M14

M14最終判定：

- PASS 32
- PASS_WITH_CAUTION 23
- UPDATE_REQUIRED 10
- HOLD 5

P0-06〜08後にM11 Q IDとWorkを照合し、M14の10件差し替えを統合する。

---

## M13 / M16

大原則は一致するが、Runtime contractは未確定。

Runtime Snapshot実装はNO-GO。Work P0では `data/canonical/*` / `runtime/*` を作らない。

---

## 現在のGate

- Day0監査：完了
- P0-01〜03：PASS
- P0-04：PASS_WITH_CAUTION
- P0-05：PASS
- P0-06〜08：GO
- FAQ統合：CONDITIONAL GO
- 監視Dry Run：NO-GO
- Runtime Snapshot：NO-GO
- 本番公開：NO-GO

## 次

最優先：WorkでP0-06〜P0-08のみ実装・検証。

390px fresh evidenceは取得可能な環境が得られた時点で再確認し、公開Gateで必ず再評価する。

公開はまだ行わない。
