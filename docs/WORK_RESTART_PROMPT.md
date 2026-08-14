# WORK_RESTART_PROMPT

Work復活時に最初に使用するプロンプト。

---

「プロップファームの歩き方」の続きです。

**既存成果を作り直さず、現在の未公開作業版の続きから進めてください。まだ公開しないでください。**

本番はVersion 78です。

最初にGitHub：

`kyoutendoujipropguidejapan/prop-affiliate-os-lite`

を確認し、README.md → AGENTS.md → docs/CURRENT_STATE.md の順に読んでください。

また、最新Master v2.2の以下を正本として扱います。

- PlanCatalogV2
- PlanCoverage
- DiagnosisPlanCurrent
- DiagnosisLogicV2
- SourceHealth
- Coupons
- PriceOffers
- UXJourney
- PageUXSpec
- CuriosityCopy
- UXCopyFinal
- FirmUXCopy
- FirmPlanFlow
- MicrocopyRules
- UXMeasurement
- UXBacklog

## 最初はコードを書かない

まず：

1. 現在の未公開作業版の状態
2. v2.2との差分
3. 使用技術/依存
4. GitHub OSSを部分流用すべき箇所
5. 既存実装を維持すべき箇所
6. 最小実装プラン

を報告してください。

既知OSS候補：shadcn/ui、Formity、TanStack Table、openstatusHQ/data-table-filters、Payload。

OSS導入自体を目的にしません。既存実装の方が軽く安全なら導入しないでください。

## 公開UI

基本構造：

ファーム一覧 → そのファームのプラン一覧 → 必要なプランだけ詳細

全プラン詳細カードを一度に並べない。

ファーム詳細冒頭は：

- 特徴
- 日本語対応
- 無料トライアル
- 取引環境
- 注意点
- プラン一覧

その後必要なプランのみ展開。

## UX

`見やすい → 少し分かる → 次が気になる → 自分で進みたくなる`

- 1画面1テーマ
- Primary CTAは原則1つ
- Secondaryを弱く
- CTA前に次に何が分かるか予告
- ページを行き止まりにしない
- 価格/特典を途中の主役にしない

## 基礎講座

既存URLを維持：

01 プロップファームって何？
→ 02 いきなり購入しなくていい
→ 03 まず確認する3つ
→ 04 失格しやすいルールを知る
→ 05 自分に合う候補を探す
→ 30秒診断

## 診断

DiagnosisPlanCurrentを候補母集団として使用。
DiagnosisLogicV2は変更禁止。

Affiliate/コミッション/クーポン/価格を採点に使用禁止。

Block Top3=YesはTop3から除外。

結果は「なぜこの3つ？」から始め、各候補は：

- あなたとの相性
- 理由2点
- 注意1点
- 詳しいルールを見る

を中心にする。

## 価格・クーポン

割引適用後金額を公開しない。

クーポンは：

コード｜効果｜対象｜期限

を中心に表示。

「購入前に公式サイトで適用条件と最終価格を確認してください」と案内。

価格3区分は初期折りたたみ。

## SourceHealth

公式情報競合を勝手に解消しない。

確認中のものを確定表示しない。

## モバイル

390px fresh render必須。

- 横スクロールなし
- 1画面1テーマ
- CTA競合なし
- 大型カード連続なし
- ファーム→プラン→詳細が分かる
- ページ末尾に次の予告
- 価格/特典が途中の主役にならない

コード上の成功だけで完了扱いにしない。

## 最初の返答

まだ実装せず、以下だけ報告：

1. 現在の未公開版
2. v2.2との差分
3. 採用/不採用するOSS
4. 最小実装プラン
5. 固定する部分

私が確認してから実装を開始してください。

---
