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

`docs/M08_QA_REGRESSION_SPEC.md` を追加。

含むもの：

- Smoke Test
- P0 Acceptance Test
- Full Regression Test
- 390px Mobile Test
- Beginner Guide Regression
- Firm → Plan → Detail Test
- Diagnosis Test Matrix
- SourceHealth Test Matrix
- Fintokei速攻プロの日付境界/新規購入/旧口座/人間承認テスト
- Price / Coupon Test
- Official / Affiliate Link Separation
- SEO Test Matrix
- GA4 Test Matrix
- Error / Empty State
- 公開前Go / No-Go基準
- Work向け短縮QAプロンプト

M08は仕様作成のみ。実テストはWorkでP0実装後に実行する。

コード変更・Master変更・サイト変更・公開・自動監視設定は未実施。

## 次

M09｜SEO記事・ルール解説の完成原稿

Work/Manusを待たず通常チャット側で前倒しする。

優先テーマ候補：

1. 最大ドローダウンとは
2. Static DDとは
3. Trailing DDとは
4. EOD DDとは
5. プロップファームで失格しやすいルール

目的：M03の検索流入設計と基礎講座を接続し、Work復活時にそのまま掲載できる原稿まで用意する。
