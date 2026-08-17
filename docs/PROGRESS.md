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

## M06結論

- Fintokei｜速攻プロ：2026-07-15以降の新規購入口座に限り Block解除候補
- Funded7｜1フェーズ：Block継続
- Funded7｜Instant：Block継続
- Funded Trader Markets｜Instant Pro：Block継続
- Hantec Trader｜Instant Lite：Block継続
- FundedElite｜Flash Activation：Block継続

Fintokei速攻プロは、旧口座と2026-07-15以降の新規購入口座を混同しないこと。Block解除は適用日・新規購入・旧口座分離・Evidence・人間承認をVariant単位で保持できる場合のみ候補とする。

## M08成果

`docs/M08_QA_REGRESSION_SPEC.md`

- Smoke / P0 Acceptance / Full Regression
- 390px Mobile
- Beginner Guide Regression
- Firm → Plan → Detail
- Diagnosis / SourceHealth / SEO / GA4 / Link / Error Matrix
- Fintokei 2026-07-15境界テスト
- Go / No-Go
- Work短縮QAプロンプト

M08はWorkに渡すQAの唯一の正本として使用する。BLOCKERまたはCRITICALが1件でも残る場合はNo-Go。

## M09成果

`docs/M09_SEO_CONTENT_PACK.md`

完成原稿5本：

1. 最大ドローダウンとは？
2. Static DDとは？
3. Trailing DDとは？
4. EOD DDとは？
5. プロップファームで失格しやすいルール

各記事にSEO Title / Meta / H1 / 本文 / FAQ / 内部リンク / CTA / fact-check gateを用意。

## M10成果

`docs/M10_SOURCE_MONITORING_AUTOMATION_DESIGN.md`

M05の監視仕様を技術設計へ変換。

- GitHub / Replit / ChatGPT / Workの役割分担
- monitor_sources / snapshot / change_eventデータ構造
- HTML正規化
- numeric / keyword差分検出
- change type分類
- Noise Filter
- Source Priority Gate
- SourceHealth cross-check
- Fintokei条件付き解除保護
- Failure handling
- low-cost Dry Run
- Phase A〜E段階導入
- MVP実装範囲

サイト自動更新、Master自動更新、Cron、通知、自動Issue作成は未実装。

## M11成果

`docs/M11_FIRM_FAQ_CONTENT_PACK.md`

14社すべてについて、ファーム詳細ページにそのまま使えるFAQ原稿を最大5問ずつ作成。

- 初心者が最初に確認するポイントを中心に構成
- 価格・割引をファーストビューの主役にしない
- SourceHealth競合は「確認中」を維持
- Fintokei速攻プロの適用日/旧口座分離を維持
- Funded7 1フェーズ/Instant、FTM Instant Pro、Hantec Instant Lite、FundedElite FlashはBlock継続前提
- FundingPips SH011を維持
- FAQ schema実装ルール
- 390pxではAccordion候補
- 公開前Fact-check Gate

`docs/WORK_RESTART_PROMPT.md` にM11参照も追加済み。

## M12成果

`docs/M12_DRY_RUN_SOURCE_SET.md`

M10の監視自動化を安全に試すための公式公開URLセットを確定。

### Primary Dry Run 5 URL

- Fintokei 速攻プロ公式Help
- Fintokei 参加条件/制限国公式Help
- FundingPips Get Started公式Help
- The5ers Promotions公式ページ
- Hantec Trader Instant Lite公式Help

### Shadow Cross-check 4 URL

- Hantec Instant Lite Product JP
- FTM Instant Pro Daily DD FAQ
- The5ers Futures EN
- The5ers Futures JP

14日Dry Run、category別抽出Field、country set diff、effective date / legacy-new split保護、domain別Noise Filter、Severity、GO / CONDITIONAL GO / NO-GO、Master / SourceHealth / siteへの自動書込禁止を定義済み。

## M13成果

GitHubへのMaster／成果物同期設計を完了。

- 推奨Repository Tree
- 二層Canonical Data：Excel Master + 承認済みGitHub Runtime Snapshot
- Excelに残すもの / JSON・CSV・Markdown化するもの
- M01〜M12保存先
- `verified_at` / `effective_from` / `supersedes` / `source_priority` / `human_approved` を使う版管理
- SourceHealth安全仕様
- AI Agent読み込み順
- Workとの片方向同期
- Backup / Archiveルール
- 将来の安全な同期手順
- 最大10件の最小同期ファイルセット

Fintokei速攻プロは `2026-07-15以降` / `新規購入` / `旧口座分離` / `Evidence` / `人間承認` をVariant単位で保持できない限りBlock継続。残る5件もBlock継続。

## M14成果

M11の全70 FAQをA1〜A4優先の公式一次情報で最終照合。

- PASS：32件
- PASS_WITH_CAUTION：23件
- UPDATE_REQUIRED：10件
- HOLD：5件

HOLD 5件：

- Funded7 1フェーズ
- Funded7 Instant
- Funded Trader Markets Instant Pro
- Hantec Trader Instant Lite
- FundedElite Flash Activation

これらはSourceHealth Blockを維持し、確定値・FAQ schema・診断Top3の根拠に使用しない。

Fintokei速攻プロは `2026-07-15以降` / `新規購入` / `旧口座分離` / `Evidence` / `人間承認` の限定Variant条件を維持する。

M14では14社総合表、70問全判定、UPDATE_REQUIRED 10件の差し替え文、SourceHealth対象、Eligibility / 無料トライアル確認、プラン変更候補、FAQ schema可否、公開前再確認項目、最終3分類を整理済み。

M14時点ではコード変更、Master変更、SourceHealth変更、サイト変更、公開は未実施。

## 次の優先順位

### Work復活時

1. `docs/WORK_RESTART_PROMPT.md` で未公開作業版を監査
2. M07 P0実装
3. M14判定を使い、M11 FAQのPASS / PASS_WITH_CAUTION / UPDATE_REQUIREDのみ必要な形で統合
4. HOLD 5件は確定FAQ schemaやTop3根拠に使用しない
5. `docs/M08_QA_REGRESSION_SPEC.md` でQA
6. BLOCKER/CRITICAL=0を確認
7. 390px fresh render
8. 公開は別途人間承認

### Manus利用可能時の次タスク

- M15｜M12 Dry Run用monitor_sources設定ファイル案

### ChatGPT側で並行可能

- M09追加SEO記事（無料トライアル、ニュース取引、週末持ち越し等）
- M13同期設計に沿った最小Runtime Snapshot仕様の準備

Manus/Workが停止しても、本体進行を止めない。
