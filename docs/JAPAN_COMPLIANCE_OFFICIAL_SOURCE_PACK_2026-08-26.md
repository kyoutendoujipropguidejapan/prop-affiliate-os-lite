# JAPAN COMPLIANCE OFFICIAL SOURCE PACK

更新日：2026-08-26 JST
Status：OFFICIAL-SOURCE RESEARCH / EDITORIAL GOVERNANCE
Production code changes：NONE

この文書は編集・運用上のCompliance Source Packであり、個別案件への法的助言・法的適合性保証ではない。

## 1. PR / Affiliate disclosure — 消費者庁

公式Source：
- https://www.caa.go.jp/policies/policy/representation/fair_labeling/stealth_marketing
- https://www.caa.go.jp/policies/policy/representation/fair_labeling/faq/stealth_marketing/

確認事項：
- 2023-10-01から、広告であることが一般消費者に分からないステルスマーケティングは景品表示法上の規制対象となる。
- Internet表示、SNS、review等も対象例に含まれる。
- 消費者庁Q&Aでは「広告」「宣伝」「プロモーション」「PR」等の表示方法が明瞭性の例として示されている。
- Affiliate site冒頭に一度だけAffiliate利用表示があっても、表示全体から広告性が明瞭である必要がある。
- 一部だけを見ると非広告と誤認され得る表示では、その表示付近での説明が必要となる場合がある。

Site policy：
- Global disclosureだけに依存しない。
- Affiliate CTA / sponsor content / provided account review付近でもrelationを明示する。
- `PR`表示を小さすぎる文字・低contrast・折り畳み内部だけに置かない。
- Official information CTAとAffiliate CTAを視覚・意味上分離する。

## 2. Misleading claims — 景品表示法

Official sources：
- https://www.caa.go.jp/policies/policy/representation/fair_labeling/representation_regulation/
- https://www.caa.go.jp/policies/policy/representation/fair_labeling/faq/representation

確認事項：
- 商品・サービスの内容を実際より著しく優良に見せる表示は優良誤認の問題になり得る。
- 価格その他の取引条件を実際より著しく有利に見せる表示は有利誤認の問題になり得る。

Site policy：
Evidenceなしで以下を禁止／HOLD：
- 最強
- No.1
- 必ず稼げる
- 必ず合格
- 絶対出金
- 最速
- 最安
- 一番安全
- 一番信頼できる
- 実際より広いcoupon対象
- 終了campaignをcurrentとして表示

Price policy：
- base price / official campaign / personal couponを分離
- discount適用条件を省略して通常価格のように見せない
- 自動割引後価格を正本扱いしない

## 3. Overseas financial services — 金融庁

Official sources：
- https://www.fsa.go.jp/ordinary/kanyu/20090731.html
- https://www.fsa.go.jp/ordinary/iwagai/
- https://www.fsa.go.jp/ordinary/chuui/mutouroku.html

確認事項：
- 金融庁は、日本居住者向けのFX等の金融商品取引について海外所在業者・無登録業者に関する注意喚起を行っている。
- 無登録業者に関する警告一覧を公開している。
- 警告一覧に掲載されていないことだけで、登録や適法性を肯定できるわけではない旨の注意がある。

Prop Firm site policy：
- この金融庁説明を、サービス構造の異なる全Prop Firmへ一律に法的分類として適用しない。
- `日本から利用可能` と `日本の金融当局に登録・認可` を完全に分離する。
- Firmのservice natureをTerms / official sourceで確認する。
- Financial regulatory statusを確認していない場合は`UNKNOWN / NOT ASSESSED`。
- FSA warning list非掲載を`安全`や`合法`の証拠にしない。
- FSA warning掲載等の重大signalを発見した場合は通常content更新ではなくCompliance Escalationへ。

## 4. Site-wide wording rule

Safe concept：

`日本からの利用可否について確認しています。これは、日本の金融当局への登録・認可や、特定の法的評価を意味するものではありません。サービスの性質や利用条件は各事業者の最新の公式情報をご確認ください。`

この文言を全Firmへ機械的に長文表示するのではなく、Japan eligibility / regulationを扱うsectionの共通logicとして使用する。

## 5. Review / provided account / sponsor

Site policy：

Provided account：
`本検証では事業者からテスト用口座の提供を受けています。口座提供は肯定的な評価や掲載を条件とするものではありません。`

Sponsor：
`本コンテンツにはスポンサー関係があります。スポンサー関係と、確認した事実・注意点・検証結果は分けて扱います。`

Affiliate：
`PR / アフィリエイトリンクを含みます。リンク経由の申込み等により当サイトが報酬を受け取る場合があります。`

## 6. Required editorial separation

表示上、少なくとも次を区別可能にする：

- Official Fact
- Direct Contact Information
- Site Explanation / Editorial Interpretation
- Reviewer Experience
- Commercial Offer / Campaign / Coupon
- Affiliate CTA
- Unknown / Conflict / Hold

## 7. Release gate

公開前に：
- Commercial disclosure明瞭
- claim evidence確認
- outdated campaign除外
- Japan eligibility / regulation分離
- service nature確認
- unknown / conflict保持
- Affiliateによるranking影響0

重大な規制・法的分類の判断が必要になった場合はCentral Command / legal reviewへEscalateし、AI単独で結論を出さない。

Final Status：
`JAPAN_COMPLIANCE_OFFICIAL_SOURCE_PACK_READY`
