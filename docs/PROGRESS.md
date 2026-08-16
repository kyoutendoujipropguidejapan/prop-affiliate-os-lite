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

## M06結論

- Fintokei｜速攻プロ：2026-07-15以降の新規購入口座に限り Block解除候補
- Funded7｜1フェーズ：Block継続
- Funded7｜Instant：Block継続
- Funded Trader Markets｜Instant Pro：Block継続
- Hantec Trader｜Instant Lite：Block継続
- FundedElite｜Flash Activation：Block継続

Fintokei速攻プロは、旧口座と2026-07-15以降の新規購入口座を混同しないこと。Block解除は適用日・新規購入・旧口座分離・人間承認を保持できる場合のみ候補とする。

## M07統合結果

M01〜M06の成果とMaster v2.2方針を統合し、Work復活後の実装仕様を確定済み。

- 採用 / 修正採用 / 保留 / 却下
- P0 / P1 / P2（P0は13項目）
- 安全なWork実装順
- ページ別変更一覧
- データ別変更一覧
- SourceHealth変更案
- Fintokei速攻プロの条件付きBlock解除仕様
- 残り5件のBlock継続仕様
- OSS最終採否
- 変更禁止リスト
- P0受入条件
- 公開指示を含まない完全版Work実装プロンプト

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

Work復活後に記事化できる完成原稿5本：

1. 最大ドローダウンとは？
2. Static DDとは？
3. Trailing DDとは？
4. EOD DDとは？
5. プロップファームで失格しやすいルール

各記事にSEO Title / Meta description / H1 / 本文 / FAQ / 内部リンク / CTA / fact-check gateを用意。

コード変更・Master変更・サイト変更・公開・自動監視設定は未実施。

## 次

M10｜公式ソース監視の自動化技術設計

Work/Manusを待たず通常チャット側で設計する。

目的：M05のSource Monitoring Specを、Replit / GitHub / ChatGPTを中心に低コストで実装できる具体的な技術仕様へ変換する。

M10ではまだCron・通知・サイト自動更新は実行しない。安全な差分取得、意味差分分類、人間承認、SourceHealth接続、履歴保存、失敗時フォールバックまで設計する。
