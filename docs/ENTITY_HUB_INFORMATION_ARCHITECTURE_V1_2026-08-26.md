# ENTITY HUB INFORMATION ARCHITECTURE V1

更新日：2026-08-26 JST
Status：IA CONFIRMED / IMPLEMENTATION NOT AUTHORIZED
Production code changes：NONE

Purpose：将来のFirm / Platform / Payout個別ページを、既存初心者導線・Diagnosis・Comparisonを壊さず接続するためのInformation Architectureを固定する。

## 1. Top-level concept

Existing user journey：
初心者理解 → Diagnosis → Comparison → Firm selection

Future entity layer：
Firm ↔ Platform ↔ Payout

両者を置換せず接続する。

## 2. Future route families

### Firm
- `/firms/`
- `/firms/{firm-slug}/`

### Platform
- `/platforms/`
- `/platforms/{platform-slug}/`
- `/platforms/compare/`（将来）

### Payout
- `/payout/`
- `/payout/methods/`
- `/payout/providers/{provider-slug}/`
- `/payout/routes/`

PayoutはSource Arrival GateまでProduction route実装HOLD。

## 3. Relationship model

Firm Registry
↓
Firm Detail
↔ Firm × Platform Relation ↔ Platform Registry / Detail
↔ Firm × Payout Method Relation ↔ Payout Method
↔ Firm × Provider Relation ↔ Provider Detail
↔ Verified Route Relation ↔ Payout Route

Relationsは別Layer。Masterへflattenしない。

## 4. Navigation principle

Top navigationをすぐ肥大化させない。

初期：
- existing beginner / diagnosis / comparison中心を維持
- Firm Detailはcontextual internal linksから開始

Firm Detailが十分揃った後：
- `ファーム` HubをNavigation候補

Platform Pilot安定後：
- `取引プラットフォーム` HubをNavigation候補

Payout Data acceptance後：
- `出金` HubをNavigation候補

Feature未完成のHubをNavigationへ先に出さない。

## 5. Internal linking rules

### Diagnosis → Firm
Diagnosis resultから該当Firm Detailへ。
Diagnosis score自体は変更しない。

### Comparison → Firm
Firm名 / 詳細CTAからFirm Detailへ。

### Firm → Platform
verified mappingがある場合のみ。

### Platform → Firm
verified Firm × Platform relationのみ。

### Firm → Payout
Source accepted後のみ。

### Provider → Firm
accepted relationのみ。Affiliate有無で並べ替えない。

## 6. SEO ownership

Entity pageは自分自身のentity topicを所有する。

Firm Detail：Firm-specific intent
Platform Detail：platform-general intent + Firm variance
Payout Provider：provider/service-general intent + Prop Firm context
Article：concept / education intent

同じ本文を複数Entityへ複製しない。

## 7. Commercial boundary

Entity relation / search order / canonical / sitemap / statusはAffiliate・Coupon・Commissionに依存させない。

Commercial CTAはEntity contentの後段Layer。

## 8. Compliance boundary

各Entityで最低限：
- information status
- checked date
- disclaimer
- PR disclosure where applicable
- official vs affiliate link separation
- fact vs editorial separation

Platform：Firm-specific configurationとの差を明示。
Payout：送金・手数料・network等の変更可能性を明示。
Firm：Japan eligibilityとregulatory statusを分離。

## 9. Mobile principle

390px first。
Entity relationship UIで横長matrixを強制しない。
Mobileではcards / accordion / progressive disclosureを優先。

## 10. Build order

1. Firm Detail Pilot
2. Firm Detail rollout
3. Firm Directory Hub
4. Platform Pilot
5. Platform rollout
6. Payout Source arrival / Data acceptance
7. Payout Hub / Provider Detail
8. Cross-entity relation expansion

## 11. Non-goals

- 全Entityを同時実装
- graph database導入
- master-data.json巨大化
- public user reviews
- ranking marketplace
- AI auto-canonical

Final Status：
`ENTITY_HUB_IA_V1_CONFIRMED`
