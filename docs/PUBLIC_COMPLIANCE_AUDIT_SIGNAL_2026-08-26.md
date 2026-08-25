# PUBLIC COMPLIANCE AUDIT SIGNAL

確認日：2026-08-26 JST
対象：公開ホーム `https://kyouten-prop-guide.utsr.chatgpt.site`
Status：PUBLIC-SURFACE SIGNAL / NOT LEGAL OPINION / NOT PRODUCTION CANONICAL
Production code changes：NONE

## 1. Confirmed in public crawl

Footerに次の趣旨を確認：

- Affiliate linkを含む場合がある
- 診断順に紹介有無 / 報酬率を使用しない
- 情報提供目的
- 投資助言ではない
- 最新条件は公式page / purchase pageで確認

またDiagnosis近くに、診断結果は利用者条件との相性であり、Firmの優良性や収益性のrankingではない旨がある。

価格確認中項目について、確認できるまで価格・購入Buttonを表示しない安全設計もPublic crawlで確認。

## 2. Caution

Global footer disclosureの存在だけでは、今後の`COMPLIANCE_BASELINE_V1`を満たしたとは判定しない。

消費者庁のステルスマーケティングQ&Aを踏まえ、Affiliate / Sponsored / provided-account relationは表示全体と該当箇所付近で明瞭かを確認する。

Text crawlだけでは、以下を十分に視覚判定できない：

- Affiliate CTA直近のPR表示
- font size / contrast
- mobile first-viewでのvisibility
- disclosureがaccordion等に隠れていないか
- Official CTAとAffiliate CTAの視覚分離

したがってこれらはactual rendered page / 390px / iPhone QA項目とする。

## 3. Current public compliance strengths

Signalとして確認：

- diagnosis ranking neutrality disclosure
- confirmation-pending price suppression
- campaign / personal coupon conceptual separation wording
- last checked / information update date
- footer affiliate / informational disclaimer

## 4. Required improvement checks before next public release

- CTA-level `PR / アフィリエイトリンクを含みます` visibility
- Official vs Affiliate link separation
- sponsored / provided account disclosure when applicable
- Firm Japan eligibility vs regulatory status separation
- service-nature wording per Firm
- no guarantee / superiority claim
- no outdated current campaign
- no PII / KYC in analytics

## 5. Release status

現状を`COMPLIANCE_FAIL`とは断定しない。

Current label：
`PUBLIC_COMPLIANCE_BASE_PRESENT_LOCAL_DISCLOSURE_RENDER_QA_REQUIRED`

次のProduction releaseで`COMPLIANCE_BASELINE_V1`をmandatory Gateとして適用する。
