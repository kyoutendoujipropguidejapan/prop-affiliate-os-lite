# M14_VERIFIED_EXTRACTION_FROM_PDF

更新日：2026-08-19 JST
対象：`M14｜14社FAQの公式一次情報最終チェック.pdf`
Source SHA-256：`f2c05035952f8ec38033ff31eecf89b324000462c2e9a85e99d00b8b437e648d`
原文確認日：2026-08-17 JST
位置づけ：**元M14成果物そのものではなく、回収PDFをChatGPTが全文確認して作成した実装用の検証済み抽出。** 元Artifactと同一扱いしない。

## 結論

14社・70 FAQの判定は以下。

- PASS：32
- PASS_WITH_CAUTION：23
- UPDATE_REQUIRED：10
- HOLD：5

HOLD 5件は確定値へ変更せず、FAQ schema対象外、診断Top3根拠に使わない。

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

Fintokei速攻プロは2026-07-15以降の新規購入口座だけを扱う限定Variant。旧口座へ新条件を誤適用しない。

## 14社 FAQ判定マトリクス

| Firm | Q1 | Q2 | Q3 | Q4 | Q5 |
|---|---|---|---|---|---|
| Fintokei | PASS | UPDATE_REQUIRED | PASS_WITH_CAUTION | PASS_WITH_CAUTION | PASS |
| Funded7 | PASS_WITH_CAUTION | HOLD | HOLD | PASS | UPDATE_REQUIRED |
| Fundora | PASS_WITH_CAUTION | PASS | PASS | PASS | PASS |
| Funded Trader Markets | PASS | HOLD | PASS_WITH_CAUTION | PASS | PASS |
| The5ers | UPDATE_REQUIRED | UPDATE_REQUIRED | PASS_WITH_CAUTION | PASS_WITH_CAUTION | PASS |
| Hantec Trader | PASS | HOLD | PASS_WITH_CAUTION | PASS | PASS_WITH_CAUTION |
| SuperFunded | PASS | PASS | UPDATE_REQUIRED | PASS | PASS |
| Blueberry Futures | PASS | UPDATE_REQUIRED | PASS | UPDATE_REQUIRED | PASS |
| Trading Cult Pro | PASS | PASS_WITH_CAUTION | PASS | PASS | UPDATE_REQUIRED |
| Blue Guardian | PASS_WITH_CAUTION | PASS | PASS_WITH_CAUTION | PASS_WITH_CAUTION | PASS_WITH_CAUTION |
| Blueberry Funded | PASS_WITH_CAUTION | UPDATE_REQUIRED | PASS_WITH_CAUTION | PASS_WITH_CAUTION | PASS |
| FundedElite | PASS_WITH_CAUTION | PASS_WITH_CAUTION | HOLD | PASS | PASS |
| The5ers Futures | PASS | PASS_WITH_CAUTION | UPDATE_REQUIRED | PASS_WITH_CAUTION | PASS |
| FundingPips | PASS | PASS | PASS_WITH_CAUTION | PASS | PASS_WITH_CAUTION |

## UPDATE_REQUIRED 10件の差し替え本文

すべて `verified_at = 2026-08-17 JST`。

### U01｜PF001 Fintokei Q2

> 現行の公式サイトでは、チャレンジプラン、チャレンジプラン・スイング、チャレンジプラン・スリム、速攻プロプランが案内されています。最初から全ルールを比べるより、まず「評価の進み方」「損失ルール」「最低取引日数」の3点で候補を絞り、該当プランだけ詳細を確認すると分かりやすいです。

### U02｜PF002 Funded7 Q5

> クーポンやキャンペーンは、対象プラン・新規／既存の区分・期限が変わることがあります。本サイトではコード、効果、対象、期限を分けて案内し、適用可否と最終価格は購入前に公式購入画面で確認する流れにします。

### U03｜PF005 The5ers Q1

> プラン名を横並びで見るより、まず公式のProgram selectorで対象市場と評価方式を分けて見ると整理しやすくなります。その後、利益目標、損失ルール、出金条件、最低日数を必要なプランだけ確認してください。

### U04｜PF005 The5ers Q2

> The5ersのプログラムは何から見分ければよいですか？ まず公式のProgram selectorで対象市場と評価方式を選び、その後に利益目標、最大損失、出金条件を確認してください。すべてのプログラム詳細を最初から読む必要はなく、自分の取引対象と方式に合う候補だけを開けば十分です。

### U05｜PF007 SuperFunded Q3

> 合格までの期間を重視する場合は、公式FAQで時間制限と不活動条件を確認してください。現行FAQではassessmentとfunded stageに時間制限はない一方、不活動30日で口座が自動終了すると案内されています。プラン固有の条件は購入前に該当ルールで確認してください。

### U06｜PF008 Blueberry Futures Q2

> まずDD方式です。現行の公式Productでは、AscentはEOD、AcceleratedはTrailingとして案内されています。その後、利益目標、最低日数、出金条件などを確認してください。DDの計算時点は購入前に該当ルールで確認するのが安全です。

### U07｜PF008 Blueberry Futures Q4

> 公式Help Centerには日本語の言語選択肢があります。ただし、プラン固有のルールがすべて同じ範囲で日本語化されているとは限りません。本サイトでは重要項目を日本語で整理しつつ、購入前は選んだプランの公式RulesとHelpを確認してください。

### U08｜PF009 Trading Cult Pro Q5

> クーポンや紹介コードは、対象モデルや期限が変わることがあります。本サイトでは、運営者確認済みのコードだけをコード・効果・対象・期限に分けて表示し、購入前に公式購入画面で適用可否を確認するよう案内します。

### U09｜PF011 Blueberry Funded Q2

> Instant Access系のルールは同じですか？ Instantという名前だけで一括りにせず、選ぶ口座のRules、損失条件、出金条件をプラン別に確認してください。旧プランや購入時期の異なる口座は、現行条件と混ぜないことが重要です。

### U10｜PF013 The5ers Futures Q3

> Day TradeとSwingの最大損失は、現行の公式FAQでは最高のmidnight balanceまたはequityを基準に4%で計算されます。日中の値動きだけでなく、日次の確定値が基準更新にどう影響するかを理解しておくことが重要です。

## FAQ schemaの安全ルール

HOLD 5件はschemaへ入れない。

また、次は原則schemaへ入れない／入れない方がよい。

- Fintokei速攻プロの限定Variant FAQ
- SourceHealth競合・Eligibility・SH011に触れるFAQ
- Coupon / Referral FAQ
- Legacy / Campaign / Cryptoなど変動しやすいFAQ
- ロケール価格差や購入時期・言語差を含むFAQ

画面に実際に表示するQ&Aのみschema化し、公開直前に本文と完全一致を再確認する。

## 公開前P0再確認

- HOLD 5件がFAQ・診断ともBlock継続
- Fintokei速攻プロ：新規購入 / 2026-07-15 / 旧口座分離 / Evidence / 人間承認
- U01〜U10が他ページ文言と矛盾しない
- FundingPips SH011のAffiliate Help概要と詳細tier / Coupon購入画面の差を再確認

## 公開前P1再確認

- 日本居住者Eligibilityと日本語表示範囲
- Trialが通常プラン・診断候補へ混入していない
- 公式情報リンクがAffiliate CTAへ置換されていない
- FAQ schemaが本文Q&Aと一致し、HOLD / Coupon / Eligibilityを構造化していない

## 禁止

- 本抽出を元M14 Artifactそのものと称さない
- HOLDを自動解除しない
- SourceHealthを自動更新しない
- Diagnosis Top3根拠へHOLDを使わない
- CouponやAffiliate情報を診断採点へ使わない
