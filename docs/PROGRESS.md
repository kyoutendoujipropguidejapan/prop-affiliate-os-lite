# プロップファームの歩き方｜進捗

更新日：2026-08-16

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

## M06結論

- Fintokei｜速攻プロ：2026-07-15以降の新規購入口座に限り Block解除候補
- Funded7｜1フェーズ：Block継続
- Funded7｜Instant：Block継続
- Funded Trader Markets｜Instant Pro：Block継続
- Hantec Trader｜Instant Lite：Block継続
- FundedElite｜Flash Activation：Block継続

Fintokei速攻プロは、旧口座と2026-07-15以降の新規購入口座を混同しないこと。Block解除は適用日・新規購入・旧口座分離・人間承認を保持できる場合のみ候補とする。

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

- 14日Dry Run設計
- category別抽出Field
- country set diff
- effective date / legacy-new split保護
- domain別Noise Filter
- Severity
- GO / CONDITIONAL GO / NO-GO
- Master / SourceHealth / siteへの自動書込禁止

URLは2026-08-16時点で公式公開情報として再確認済み。

コード変更・Master変更・サイト変更・公開・自動監視設定は未実施。

## 次の優先順位

### Work復活時

1. `docs/WORK_RESTART_PROMPT.md` で未公開作業版を監査
2. M07 P0実装
3. M11 FAQを14社ページへ必要な分だけ統合
4. `docs/M08_QA_REGRESSION_SPEC.md` でQA
5. BLOCKER/CRITICAL=0を確認
6. 390px fresh render
7. 公開は別途人間承認

### Work復活前に追加できるもの

- M13｜GitHubへのMaster/成果物同期設計
- M14｜M09追加SEO記事（無料トライアル、ニュース取引、週末持ち越し等）
- 14社FAQの公式一次情報最終チェック
- M12 Dry Run用monitor_sources設定ファイル案

Manus/Workが停止していても、本体進行を止めない。
