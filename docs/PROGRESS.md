# プロップファームの歩き方｜Manus進捗

更新日：2026-08-16

## 完了

- M01｜公開サイト・モバイルUX総監査 ✅
- M02｜診断7問UX監査 ✅
- M03｜SEO・検索流入設計 ✅
- M04｜14社ファーム詳細ページのSEO/UX設計 ✅

M04では、M03の検索意図・内部リンク方針とMaster v2.2の `FirmUXCopy` / `FirmPlanFlow` / `UXCopyFinal` / `PlanCatalogV2` / `SourceHealth` を統合し、以下を整理済み：

- 14社比較表
- 各社のSEO Title / Meta description / H1
- 冒頭1〜2行の特徴
- 最初に確認するポイント
- 日本語対応 / 無料トライアル / 取引環境 / 注意したいルール
- プランのグループ分け
- 初期表示項目 / 詳細展開項目
- FAQ候補
- 関連基礎講座 / 関連ルール解説
- 診断 / 公式情報への自然な導線
- ページ末尾の次が気になるコピー
- 14社共通テンプレート
- 各社固有差分
- Workでコンポーネント化できる部分
- ファーム詳細ページのP0 / P1 / P2優先順位
- 実装前のファクトチェックゲート

数値・現行条件はSourceHealthと公式一次情報の照合前に断定しない。コード変更・サイト変更・公開は未実施。

## 次

M05｜公式ソース監視設計

担当：Manus 1.6 Lite推奨

目的：今後のファクトチェックを「毎回全ページを再調査」から「優先ソースの変更監視＋人間確認」へ近づける。

各14社について、最低限以下を設計する：

- 最優先監視URL
- Rules / FAQ / Pricing / Restricted countries / Platform / Payout / Campaign の監視URL
- 更新検知したいキーワード
- 推奨監視頻度（日次 / 週次 / 月次）
- 変更時に人間確認が必要な項目
- SourceHealthとの接続
- Campaign / Coupon / Price / Plan / Eligibility / Platform / Rule の変更分類
- 誤検知しやすいページや注意点

成果物：Source Monitoring Spec。

実装・自動巡回・通知設定はまだ行わず、まず監視仕様だけ作る。
