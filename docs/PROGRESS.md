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

コード変更・Master変更・サイト変更・公開・自動監視設定は未実施。

## 次の優先順位

### Work復活時

1. `docs/WORK_RESTART_PROMPT.md` で未公開作業版を監査
2. M07 P0実装
3. `docs/M08_QA_REGRESSION_SPEC.md` でQA
4. BLOCKER/CRITICAL=0を確認
5. 390px fresh render
6. 公開は別途人間承認

### Work復活前に追加できるもの

- M09記事の追加テーマ原稿
- 14社FAQ完成原稿
- 監視Dry Run用URLセットの確定
- GitHubへのMaster/成果物同期設計

Manus/Workが停止していても、本体進行を止めない。
