# プロップファームの歩き方｜Manus進捗

更新日：2026-08-16

## 完了

- M01｜公開サイト・モバイルUX総監査 ✅
- M02｜診断7問UX監査 ✅
- M03｜SEO・検索流入設計 ✅
- M04｜14社ファーム詳細ページのSEO/UX設計 ✅
- M05｜公式ソース監視設計 ✅
- M06｜SourceHealth競合6件の再調査 ✅
- M07｜M01〜M06統合・Work実装仕様確定 ✅

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

コード変更・Master変更・サイト変更・公開・自動監視設定は未実施。

## 次

M08｜実装前QA・回帰テスト仕様

担当：Manus 1.6 Lite推奨

目的：Work復活後、P0実装直後に『見た目は良いが既存機能が壊れた』状態を防ぐため、M07の13項目を中心に実行可能なQA/回帰テスト仕様を先に完成させる。

必須範囲：

- 390pxモバイル
- ファーム→プラン→詳細の階層
- 診断7問と結果Top3
- SourceHealth Block
- Fintokei速攻プロ条件付き解除
- 価格 / クーポン表示
- 公式リンク / Affiliate CTA分離
- 基礎講座01〜05
- SEO title / meta / canonical / sitemap
- GA4既存イベントと追加候補
- 404 / 空状態 / 未確認表示
- 回帰テスト
- 公開前Go / No-Go基準

M08もコード変更・サイト変更・公開は行わない。
