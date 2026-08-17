# WORK_RESTART_PROMPT

Work復活時に最初に使用するプロンプト。

---

「プロップファームの歩き方」の続きです。

**既存成果を作り直さず、現在の未公開作業版の続きから進めてください。まだ公開しないでください。**

本番はVersion 78です。

最初にGitHub：

`kyoutendoujipropguidejapan/prop-affiliate-os-lite`

を確認し、次の順に読んでください。

1. `README.md`
2. `AGENTS.md`
3. `docs/CURRENT_STATE.md`
4. `docs/PROGRESS.md`
5. `docs/IMPLEMENTATION_READINESS.md`
6. この `docs/WORK_RESTART_PROMPT.md`

## Artifact Existence Gate

PROGRESSで「完了」とされていても、GitHubに成果物実体がない場合があります。

GitHubで実体確認済みの主要成果物：

- `docs/M08_QA_REGRESSION_SPEC.md`
- `docs/M09_SEO_CONTENT_PACK.md`
- `docs/M10_SOURCE_MONITORING_AUTOMATION_DESIGN.md`
- `docs/M11_FIRM_FAQ_CONTENT_PACK.md`
- `docs/M12_DRY_RUN_SOURCE_SET.md`

M07 / M13 / M14 / M15 / M16等の詳細成果物が見つからない場合、PROGRESS要約から詳細を推測・復元して「元仕様」と扱わないでください。

特に：

- M07最終仕様書が見つからない場合、このプロンプト + PROGRESS + Master v2.2をfallback contractとして扱い、実装範囲を報告して人間確認後に実装する
- M14のUPDATE_REQUIRED 10件の差し替え本文がない場合、M11原稿を勝手に最新化せず、該当FAQは保留または公式一次情報で再照合する
- M15実JSONがない状態で監視を開始しない
- M16実Schemaがない状態でRuntime Snapshotを実装しない

また、最新Master v2.2の以下をデータ・診断・SourceHealthの上位正本として扱います。

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

GitHub上の完成原稿・QAも使用してください。

- `docs/M08_QA_REGRESSION_SPEC.md`：実装後QA正本
- `docs/M09_SEO_CONTENT_PACK.md`：ルール解説SEO完成原稿
- `docs/M11_FIRM_FAQ_CONTENT_PACK.md`：14社FAQ原稿。M14後続判定を必ず考慮

## 最初はコードを書かない

まず：

1. 現在の未公開作業版の状態
2. v2.2との差分
3. 使用技術/依存
4. GitHub OSSを部分流用すべき箇所
5. 既存実装を維持すべき箇所
6. GitHub上で不足している成果物実体
7. 最小実装プラン

を報告してください。

**ここで実装を開始しないでください。**

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

ファーム詳細FAQは `docs/M11_FIRM_FAQ_CONTENT_PACK.md` を基礎原稿として使います。

M14では70FAQを：

- PASS 32
- PASS_WITH_CAUTION 23
- UPDATE_REQUIRED 10
- HOLD 5

に再分類済みです。

M14差し替え本文が手元にないUPDATE_REQUIREDは、そのままM11を公開しないでください。公式一次情報で再照合するか、差し替え実体を回収するまで保留します。

FAQは各社3〜5問程度、ファーム概要・プラン詳細の後段へ。ファーストビューの主役にしないでください。

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

## SourceHealth追加前提

M06で以下を再調査済み。

### Fintokei 速攻プロ

2026-07-15以降の新規購入口座のみBlock解除候補。

必須保護：

- effective_from = 2026-07-15
- new_purchase_only = true
- 旧口座分離
- Evidence保持
- 人間承認

これらをVariant単位で保持できない場合はBlock継続。

単純に `Block Top3 = No` へ変更しないでください。

### Block継続5件

- Funded7 1フェーズ
- Funded7 Instant
- FTM Instant Pro
- Hantec Instant Lite
- FundedElite Flash Activation

自動unblock禁止。確定値・FAQ schema・診断Top3根拠に使用しない。

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

## Monitoring / Runtime

M10 / M12はGitHub上に実体があります。

M15 `monitor_sources` 実JSON / Schemaが確認できない状態では監視Dry Runを開始しないでください。

M16 Runtime Snapshot実Schemaが確認できない状態ではRuntime実装を開始しないでください。

Master / SourceHealth / Diagnosis / Work / siteへの自動反映は禁止です。

## モバイル

390px fresh render必須。

- 横スクロールなし
- 1画面1テーマ
- CTA競合なし
- 大型カード連続なし
- ファーム→プラン→詳細が分かる
- FAQはAccordion等で情報密度を抑える
- ページ末尾に次の予告
- 価格/特典が途中の主役にならない

コード上の成功だけで完了扱いにしない。

## 実装後QA

P0実装後、公開前に必ず：

`docs/M08_QA_REGRESSION_SPEC.md`

を唯一のQA正本として実行してください。

BLOCKERまたはCRITICALが1件でも残っている場合はGo判定にしないでください。

特に：

- 390px横スクロール
- 基礎講座既存URL
- 診断7問完走
- Block継続5件のTop3除外
- Fintokei速攻プロの日付境界/旧口座誤適用防止
- DiagnosisLogicV2不変
- Official/Affiliate link separation
- SEO title/meta/canonical/sitemap
- GA4既存イベントと二重発火
- FAQのSourceHealth表現とFAQ schema整合

を必須確認してください。

## 最初の返答

まだ実装せず、以下だけ報告してください。

1. 現在の未公開版
2. v2.2との差分
3. GitHub上で実体確認できた成果物
4. 欠落している成果物と、その実装への影響
5. 採用/不採用するOSS
6. 最小実装プラン
7. 固定する部分

私が確認してから実装を開始してください。

---
