# SITE-WIDE DISCLOSURE / INFORMATION ARCHITECTURE

更新日：2026-08-26 JST
位置づけ：サイト全体のDisclosure / Disclaimer配置設計。法的適合性を保証する文書ではなく、誤認防止・透明性・運用一貫性のための設計基準。

## 1. Three-Level Disclosure
### Level A｜Global
サイト全体で確認できる場所に、以下の存在を確認・必要に応じて整備する。
- 運営者情報
- 広告 / Affiliate方針
- 一般免責
- Privacy / Analytics説明

### Level B｜Page Type
ページ種別に応じた追加注意：
- Firm：利用条件・ルール変更・Affiliate
- Platform：Firmごとの差
- Payout：送金条件・ネットワーク・手数料・本人確認
- Campaign：期限・対象・通常条件との分離
- Review：提供口座・スポンサー・個人差
- Case Study：観測値と因果推論の分離

### Level C｜Point of Action
CTA、Coupon、Sponsor content、Affiliate link、提供口座Review等の近くに必要Disclosureを表示。
Global footerだけで代替しない。

## 2. Minimum Page Footer Block
Firm / Platform / Payout detailの末尾に最低限：
- information disclaimer
- last checked / freshness
- affiliate disclosure when applicable
- latest official source confirmation guidance

## 3. Official vs Commercial Link
Official evidence/info linkとAffiliate conversion linkをUI上も役割分離。

例：
- `公式情報を確認する`
- `PR｜公式サイトを見る`

同一URL・同一ラベルに統合しない。

## 4. Advertising Relationship Types
区別して開示：
- affiliate relationship
- sponsored content
- provided test account
- giveaway account provision
- direct commercial support

複数該当時は必要なDisclosureを併記。

## 5. Review Independence
Commercial relationshipがある場合でも：
- positive review guarantee禁止
- issue suppression禁止
- ranking purchase禁止
- paymentとfact verificationを分離

## 6. Privacy / Analytics
Public pageに個人のKYC、口座番号、銀行情報、wallet address等を出さない。
Analyticsへも送らない。

必要なScreenshot掲載時は個人情報・識別子をredactする。

## 7. Service Nature
各FirmのTermsに沿ってsimulation / demo / evaluation / reward等の性質を記述する。
実資金提供、投資運用、利益保証等を推測しない。

## 8. Regulatory Wording
`日本から利用可能` と `日本で登録・認可されている` を分離する。
規制状況を扱う場合はcurrent official authority / legal sourceを別途確認する。

## 9. Publication Gate
新しいPage Type公開前に：
- disclosure placement review
- misleading claim review
- source freshness review
- PII review
- commercial relationship review

を必須化する。

## 10. Future Legal Review
サイトの商業規模・スポンサー案件・B2B支援が拡大した段階では、日本法の専門家による広告表示、金融関連表現、Privacy等のレビューをProduction Gateへ追加することを推奨する。
