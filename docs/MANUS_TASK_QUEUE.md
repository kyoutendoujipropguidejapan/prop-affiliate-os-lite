# MANUS_TASK_QUEUE

期間：Manus 1.6 / 1.6 Lite 無料期間中（ユーザー画面では2026-08-25 SGTまで）

目的：Workが使えない期間に、**実装以外をできるだけ前倒し**して、Work復活後を「差分実装＋QA」だけにする。

## 運用ルール

- Manus 1.6：深い調査・比較・設計・判断
- Manus 1.6 Lite：反復確認・一覧化・リンクチェック・QAチェック
- いきなりサイトを書き直さない
- まずGitHub `kyoutendoujipropguidejapan/prop-affiliate-os-lite` を読む
- 公開サイトは監査対象であり、直接変更しない
- 調査結果は「事実 / 推測 / 提案」を分離する
- 変更され得るプロップファーム情報は一次情報を優先する

---

# P0：無料期間中に必ず終わらせる

## M01｜公開サイト・モバイルUX総監査

**担当：Manus 1.6**

対象：`https://kyouten-prop-guide.utsr.chatgpt.site`

確認：

- 初見3秒で何のサイトか分かるか
- STEP01基礎講座が主役になっているか
- 次に何を押せばよいか迷わないか
- 390px前後で文章が長すぎないか
- 同じ見た目のカードが続きすぎないか
- ページ末尾に自然な次の導線があるか
- 価格・クーポンが途中で主役になっていないか
- 14社→プラン→詳細の階層が分かりやすいか
- 診断が広告ランキングに見えないか

成果物：

- ページ別問題一覧
- 離脱リスク High / Medium / Low
- 修正案
- Workで直すべきP0だけ最大10件
- 現在の良い部分（変更禁止候補）

## M02｜診断7問UX監査

**担当：Manus 1.6**

目的：65候補を裏で扱っても、ユーザーが7問を苦痛なく完走できるか評価。

確認：

- 質問順序
- 専門用語の難しさ
- 「こだわらない」が必要な設問
- 1問あたりの選択肢数
- 進捗表示
- 戻る操作
- 結果への期待感
- 7問より減らせるか（ただしDiagnosisLogicV2は変更せず提案のみ）

成果物：

- 現行7問の改善コピー
- 選択肢ラベル改善
- 説明文1行版
- 離脱しやすい質問ランキング
- Logicを変えない最小UX改善案

## M03｜SEO・検索流入設計

**担当：Manus 1.6**

目的：広告ではなく検索から初心者を基礎講座・ファーム詳細へ入れる。

対象：

- プロップファームとは
- プロップファーム 比較
- プロップファーム おすすめ（順位断定ではなく意図分析）
- プロップファーム 失格
- 最大ドローダウン
- Static / Trailing / EOD
- 無料トライアル
- 各14社のブランド名＋プラン名＋ルール
- 各社＋日本
- 各社＋出金
- 各社＋クーポン

成果物：

- Keyword cluster
- Search intent
- 既存ページで取るキーワード
- 新規ページが必要なキーワード
- Title案
- Meta description案
- FAQ案
- 内部リンク案
- Sitemap優先順位

## M04｜14社ファーム詳細ページのSEO/UX設計

**担当：Manus 1.6 Lite**

14社それぞれについて：

- 1〜2行の特徴
- 最初に見るべき違い
- プランのグループ分け
- FAQ候補5件以内
- 関連基礎講座
- 診断への自然な導線
- 公式情報への導線

価格・割引を主役にしない。

## M05｜公式ソース監視設計

**担当：Manus 1.6 Lite**

目的：今後のファクトチェックを「全ページ再調査」から「変更監視」へ近づける。

各社について：

- 最優先監視URL
- Rules / FAQ / Pricing / Restricted countries / Platform / Payout / Campaign
- 更新検知したいキーワード
- 日次 / 週次 / 月次の適切な頻度
- 変更時に人間確認が必要な項目

成果物：Source monitoring spec。

## M06｜SourceHealth競合6件の再調査

**担当：Manus 1.6**

優先：

- Fintokei 速攻プロ
- Funded7 1フェーズ
- Funded7 Instant
- FTM Instant Pro
- Hantec Instant Lite
- FundedElite Flash Activation

一次情報を再確認し、解消できない場合は「解消不能」と明示する。

勝手に確定値を作らない。

---

# P1：P0後に進める

## M07｜競合サイト/参考UX調査

**担当：Manus 1.6**

対象はプロップサイトだけに限定しない。

参考にする業界：

- 保険比較
- クレジットカード比較
- SaaS比較
- 転職診断
- スマホ料金比較
- 金融教育

見るもの：

- 初心者を迷わせない入口
- 段階開示
- 診断への誘導
- 比較しすぎ防止
- CTAの強弱
- 「次が気になる」構成

成果物：そのままコピーせず、プロップファームの歩き方へ転用できるパターン最大10件。

## M08｜GitHub OSS二次調査

**担当：Manus 1.6**

既知候補：

- shadcn/ui
- Formity
- TanStack Table
- openstatusHQ/data-table-filters
- Payload

新候補は最大3件追加まで。

各機能について：

- 既存実装維持
- 部分流用
- 新規導入

のどれかを判断。

コードはまだ書かない。

## M09｜管理画面MVP設計

**担当：Manus 1.6**

将来的にスマホ中心で更新できることを前提に、以下を管理できる最小UIを設計：

- Firms
- Plans
- Rules
- Coupons
- Campaigns
- SourceHealth
- Verification date
- Public ready

Payload等の導入は結論を急がず、Google Sheets的UI / 軽量DB / GitHub JSON等も比較。

## M10｜GA4ファネル・イベント仕様

**担当：Manus 1.6 Lite**

既存イベントを壊さず、以下を計測する仕様書を作る：

- home → beginner
- beginner start → complete
- beginner complete → diagnosis start
- diagnosis start → complete
- firm list → firm detail
- firm plan list → plan detail
- result → plan detail
- plan detail → official CTA

イベント名、parameters、発火条件、二重発火防止、見るレポートを定義。

## M11｜QA回帰テスト増強

**担当：Manus 1.6 Lite**

現行24テストに加えて必要なテストケースを設計。

重点：

- Block Top3
- Affiliate非採点
- 価格非表示
- Coupon対象/期限
- Firm grouping
- Accordion初期状態
- 390px overflow
- SourceHealth競合
- Legacy非表示
- Free Trial表示
- The5ers Summer維持
- FundingPips 5プラン

---

# P2：余力があれば

## M12｜記事ロードマップ

基礎講座とファーム詳細から自然に派生するSEO記事を優先順位付け。

## M13｜FAQ Schema/Structured Data仕様

実装はせず、WebSite / Breadcrumb / FAQの適用候補と重複リスクを整理。

## M14｜アフィリエイト導線監査

「売り込みを強くする」ではなく、必要な人だけ自然に公式購入画面まで進める構造を監査。

## M15｜公開前チェックリスト

Version 79以降を公開する前に、人間が5〜10分で確認できるチェックリストを作る。

---

# Manus作業の終了条件

無料期間終了時に、最低でも次が揃っている状態を目標にする。

1. Work P0修正リスト
2. 診断UX完成コピー
3. 14社SEO/UXページ仕様
4. SEO keyword map
5. Source monitoring spec
6. SourceHealth再調査結果
7. GA4仕様
8. QA追加テスト仕様
9. GitHub OSS採否表
10. Work復活後の差分実装指示

この10点があれば、Work復活後に長い調査をやり直さず実装へ進める。
