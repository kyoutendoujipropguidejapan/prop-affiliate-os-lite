# COMPLIANCE_BASELINE_V1

更新日：2026-08-26 JST
用途：プロップファームの歩き方における公開コンテンツ・Firm詳細・Platform・Payout・Campaign・Coupon・Review・Case Studyの共通コンプライアンス基準。

Official source pack：
`docs/JAPAN_COMPLIANCE_OFFICIAL_SOURCE_PACK_2026-08-26.md`

Escalation matrix：
`docs/COMPLIANCE_ESCALATION_MATRIX_2026-08-26.md`

## 1. 基本原則

本基準は、免責文をフッターに置くだけの後付け対応ではなく、コンテンツ設計・データ境界・CTA・検証・公開Gateに組み込む。

必須5層：

1. Commercial Disclosure
2. Fact / Opinion Separation
3. Risk / Service Nature
4. Status / Freshness
5. Claim Control

## 2. Commercial Disclosure

Affiliate / Sponsor / Free Test Account / Giveaway提供等の商業関係は、読者が認識できる位置で明示する。

- Affiliate CTA付近に `PR / アフィリエイトリンクを含みます` 等を表示する。
- Official information link と Affiliate conversion CTA を分離する。
- 提供口座で検証した場合は、口座提供を明示する。
- スポンサー関係がある場合は、スポンサー関係を明示する。
- 商業関係を理由に事実確認・診断順位・検証結果を変更しない。
- Global disclosureを1回表示するだけで十分とは扱わず、表示全体と該当箇所で広告性が明瞭かを確認する。

標準表示例：

> 本ページにはアフィリエイトリンクを含む場合があり、リンク経由の申込み等により当サイトが報酬を受け取ることがあります。これによって診断順位、事実確認、検証結果を変更することはありません。

提供口座例：

> 本検証では事業者からテスト用口座の提供を受けています。口座提供は肯定的な評価や掲載を条件とするものではありません。

## 3. Fact / Opinion Separation

以下を明確に分離する。

- Official Fact
- Direct Contact Fact
- Verified User Experience
- Reviewer Opinion
- Editorial Interpretation
- Unknown / Unverified

推測を事実として表示しない。

Conflict は自動で Verified にしない。
Unknown は 0 / false / unsupported に変換しない。

## 4. Risk / Service Nature

各Firmのサービス性質は、当該Firmの公式Terms / FAQ / Service Descriptionに従う。

以下を根拠なしに使用しない。

- 実資金を提供される
- 投資会社から資金提供される
- 実口座を運用できる
- 利益が保証される
- 出金が保証される

Simulation / Demo / Evaluation / Reward Model等の表現はFirm固有の公式説明に合わせる。

Service natureが不明なまま公開上の断定が必要になった場合は`COMPLIANCE_HOLD`へ送る。

## 5. Japan Eligibility と Regulatory Status

日本から利用可能であることと、日本の金融商品取引業その他の登録・認可を受けていることを混同しない。

表示上は原則として以下を別項目にする。

- Japan eligibility
- Japanese-language availability
- KYC availability
- Regulatory / legal status（確認する場合のみ）

標準注意文：

> 日本からの利用可否に関する表示は、日本国内での登録・認可等を意味するものではありません。利用前に各事業者の最新条件をご確認ください。

金融庁の無登録業者警告リストに掲載がないことだけで、安全・合法・登録済みと表現しない。

法的評価が必要な場合は推測せずHOLDし、必要に応じて専門家確認へ送る。

## 6. Status / Freshness

公開情報は可能な限り以下を持つ。

- verified_at / last_checked_at
- lifecycle status
- caution / known unknowns

公開Status：

- verified → 公式根拠で確認済み
- conditional → 条件付き・追加確認が必要
- unverified → 未確認
- unsupported → 非対応
- unknown → 情報不足・不明

重要：

`unknown != unsupported`
`conditional != verified`
`unverified != false`
`conflict != verified`

## 7. Claim Control

原則禁止：

- 絶対に出金できる
- 必ず稼げる
- 確実に合格
- リスクなし
- 安全なFirm
- 誰でも勝てる
- 最強
- 絶対おすすめ
- 元本保証
- 利益保証

客観的根拠なしでは使用禁止：

- 業界No.1
- 日本一
- 最速
- 最安
- 最も人気
- 世界最大
- 信頼性No.1

比較表現は、比較条件・対象・時点・根拠が明確な場合のみ使用する。

Vendor marketing wordingやFirm promotional copyを、本サイトの独立評価としてそのまま再掲しない。

## 8. Firm Detail Disclaimer

標準文：

> 本サイトは、プロップファームや関連サービスについて一般的な情報を整理・比較することを目的としています。掲載内容は個別の投資判断、利益、合格、出金等を保証するものではありません。ルール・価格・利用可能地域・キャンペーン・サービス内容は変更される場合があります。購入・登録前に必ず各事業者の最新の公式情報をご確認ください。

ページ本文と別に、商業関係Disclosureを表示する。

## 9. Platform固有注意

標準文：

> 同じ取引プラットフォームでも、Firmごとに利用可能な機能、銘柄、データ、約定環境、口座仕様等が異なる場合があります。最終仕様は利用するFirmの公式情報をご確認ください。

Platform一般仕様と Firm × Platform 仕様を混同しない。

EA / algorithmic / copy / DOM等のVendor-level機能をFirm permissionとして扱わない。

## 10. Payout固有注意

標準文：

> 掲載している出金方法・受取サービス・出金経路は、利用可否、手数料、対応地域、ネットワーク、本人確認条件等が変更される場合があります。送金前にFirmおよび各サービスの最新条件をご確認ください。

Crypto / Wallet / Bridge等はNetworkや送付先を推測しない。
税務・法務・個別金融判断として断定しない。

## 11. Campaign / Coupon

Base Price / Official Campaign / Personal Couponを分離する。

- 終了Campaignを通常価格へ残さない。
- 有効期限・対象・併用条件を表示する。
- 割引後価格を根拠なしに自動計算しない。
- Campaign名だけを見て対象ユーザーを推測しない。
- 有利誤認を避けるため、条件付き割引を通常価格のように見せない。

## 12. Review / Case Study

Reviewer口座提供・スポンサー・Affiliate関係をDisclosureする。

Case Studyは観測可能な数字を優先する。

例：

- Reviewer 5名
- 問題8件発見
- 4件修正確認
- X impressions 25,000
- Affiliate clicks XX

因果関係が確認できない場合、`当方施策により売上が増加した` のような表現を使用しない。

Scam / payout denial / security incident等の重大claimはsocial情報だけで確定せず、`COMPLIANCE_ESCALATION_MATRIX`に従う。

## 13. Analytics / Privacy

Analyticsへ送信禁止：

- 氏名
- email
- 電話番号
- KYCデータ
- 銀行口座
- カード情報
- wallet address
- 個人のpayout受取情報

GA4は既存初期化を維持し、新規 `gtag("config")` を追加しない。

## 14. FAQ / Structured Data

- 画面に実際に表示するQ&Aのみschema化する。
- HOLD / Conflict / Coupon / Eligibility等、変動・注意性が高い項目は原則schema対象外。
- schema本文と画面本文を一致させる。
- Review / AggregateRating schemaを実在する公開review datasetなしに生成しない。

## 15. Production COMPLIANCE_GATE

以下を全公開Releaseで確認する。

- PR disclosure visible
- Official URL / Affiliate URL separation PASS
- Free test account disclosure PASS（該当時）
- Sponsor disclosure PASS（該当時）
- Guaranteed-return wording = 0
- Unsupported superiority claims = 0
- Service nature misrepresentation = 0
- Japan eligibility / regulatory status confusion = 0
- Unknown → verified conversion = 0
- Current / Campaign / Legacy confusion = 0
- last checked / status表示 PASS
- Disclaimer表示 PASS
- PII analytics = 0
- KYC analytics = 0

1件でもFAILならProduction publish不可。

## 16. Escalation

次はAI / Work単独で確定せず`COMPLIANCE_HOLD`：

- Firm service nature不明
- regulatory / legal statusの断定
- regulator warning signal
- fraud / scam / payout refusal allegation
- security / personal-data incident
- Direct ContactとTermsの重大Conflict
- legal threat
- user funds / KYC / bank / wallet dataを当サイトが扱う新機能

詳細：
`docs/COMPLIANCE_ESCALATION_MATRIX_2026-08-26.md`

## 17. 運用上の位置づけ

本基準は公開安全性を高めるための運用基準であり、法的適合性を保証するものではない。高リスクな法的評価や日本向け商業展開を大きく拡大する場合は、必要に応じて専門家確認をRelease Gateへ追加する。
