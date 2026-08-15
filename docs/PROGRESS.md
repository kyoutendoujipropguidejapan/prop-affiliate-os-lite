# プロップファームの歩き方｜Manus進捗

更新日：2026-08-16

## 完了

- M01｜公開サイト・モバイルUX総監査 ✅
- M02｜診断7問UX監査 ✅
- M03｜SEO・検索流入設計 ✅
- M04｜14社ファーム詳細ページのSEO/UX設計 ✅
- M05｜公式ソース監視設計 ✅
- M06｜SourceHealth競合6件の再調査 ✅

## M06結論

対象6件について、公式一次情報をSource Priority順に照合し、Evidence Table / Conflict Map / 原因仮説 / 判定 / SourceHealth更新案 / Diagnosis Top3 Block方針 / 次回監視URLを整理済み。

- Fintokei｜速攻プロ：2026-07-15以降の新規購入口座に限り Block解除候補
- Funded7｜1フェーズ：Block継続
- Funded7｜Instant：Block継続
- Funded Trader Markets｜Instant Pro：Block継続
- Hantec Trader｜Instant Lite：Block継続
- FundedElite｜Flash Activation：Block継続

Fintokei速攻プロは、旧口座と2026-07-15以降の新規購入口座を混同しないこと。Master / SourceHealth / DiagnosisPlanCurrentへ反映する場合は適用開始日または購入日条件を保持する。

SourceHealth・Master・DiagnosisLogicV2・コード・サイト・公開は未変更。

## 次

M07｜M01〜M06統合・Work実装仕様確定

目的：無料期間中に集めたUX、診断、SEO、14社ページ、監視、SourceHealth再調査を1つの実装仕様へ統合し、Work復活後を「差分実装＋fresh render＋回帰確認」に近づける。

M07では新しい大規模調査は行わず、既存成果の重複・矛盾を整理し、P0 / P1 / P2、変更禁止、実装順、受入条件、Fintokei速攻プロの条件付きBlock解除案を確定する。

コード変更・サイト変更・公開は行わない。
