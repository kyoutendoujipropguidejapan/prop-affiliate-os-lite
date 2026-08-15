# プロップファームの歩き方｜Manus進捗

更新日：2026-08-16

## 完了

- M01｜公開サイト・モバイルUX総監査 ✅
- M02｜診断7問UX監査 ✅
- M03｜SEO・検索流入設計 ✅
- M04｜14社ファーム詳細ページのSEO/UX設計 ✅
- M05｜公式ソース監視設計 ✅

M05では、14社について公式ソースの変更監視を「全ページ再調査」から「優先ソース監視＋差分確認＋人間確認」へ移行するための仕様を整理済み：

- 14社 Source Monitoring Master Table
- 日次 / 週次 / 月次監視一覧
- SourceHealth専用監視
- 変更分類ルール
- HTML差分と意味差分を分離する誤検知フィルター
- 人間確認必須項目
- 将来自動化できる範囲
- Work / Replit / GitHub / ChatGPTの役割分担
- 14社合計の最小監視セット
- 既存URLの維持 / 変更 / 追加 / 廃止候補の判定ルール

既存Master資産はGitHubに未同期のため、既存監視URLを削除せず、同期後に照合する前提。自動巡回、Cron、通知、コード変更、サイト変更、公開は未実施。

## 次

M06｜SourceHealth競合6件の再調査

担当：Manus 1.6推奨

対象：

1. Fintokei 速攻プロ
2. Funded7 1フェーズ
3. Funded7 Instant
4. Funded Trader Markets Instant Pro
5. Hantec Trader Instant Lite
6. FundedElite Flash Activation

目的：現在Block Top3となっている主要な公式情報競合について、一次情報を優先して再調査し、解消可能か判定する。

原則：

- 公式Terms / Rules / Help / FAQ / Product page等をSource Priority順に比較する
- 更新日・適用開始日・旧プラン/新プランの違いを分離する
- 1ページだけを根拠に既存競合を自動解消しない
- 解消できない場合は「解消不能 / 継続Block」を明示する
- Affiliate、SNS、第三者情報で公式ルール競合を上書きしない
- コード変更・サイト変更・公開は行わない

成果物：6件それぞれの証拠表、競合原因、採用可能な正本値、SourceHealth更新案、Top3 Block継続/解除の提案。
