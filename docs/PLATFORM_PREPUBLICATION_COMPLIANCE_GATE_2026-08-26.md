# PLATFORM PREPUBLICATION COMPLIANCE GATE

更新日：2026-08-26 JST
Status：MANDATORY RELEASE GATE
Production code changes：NONE

## 1. Applies to

- `/platforms/`
- all Platform Detail routes
- future `/platforms/compare/`
- Firm ↔ Platform cross-links

## 2. Mandatory PASS items

### Role clarity
- Platform vendor / Broker / Prop Firm / Exchange / Liquidity Providerの役割混同 0
- Platform availabilityをJapan eligibilityと表現 0

### Claim safety
- guaranteed profit / pass / payout claims 0
- unsupported fastest / safest / best / lowest-latency claims 0
- vendor marketing wordingを独立検証値として使用 0

### Firm-specific separation
- Vendor capabilityをFirm-enabled capabilityとして断定 0
- EA / algo / copy permissionの無根拠断定 0
- symbol / market-data / DOM / order-typeのFirm-level推測 0

### Status / freshness
- checked date visible
- UNKNOWN preserved
- CONDITIONAL visible
- conflict hidden 0

### Commercial
- Affiliate / sponsor relationがあるCTAはPR開示
- commercial relationがPlatform評価 / ranking / verificationへ影響 0

### Privacy / analytics
- account ID / login / server login / email / phone / KYC dataをGA4へ送信 0
- existing GA4 initializationのみ

### SEO
- unique title/meta/H1
- correct self canonical
- no index before release approval
- sitemap only after approval
- fake Review/AggregateRating schema 0

### Mobile
- 390px horizontal overflow 0
- compare table clipping 0
- long Platform / Firm names wrap
- disclaimer readable
- CTA tap target follows existing site standard

## 3. Platform-specific checks

- MT5 / MT4：EA / copy permissionはFirm別
- Match-Trader：Japanese vendor capabilityとFirm actual displayを分離
- DXtrade：white-label configuration差を表示
- BlackArrow：technology platformでありbroker等ではない役割表示
- Quantower：license / connection差
- Volumetrica：server-side rollout差
- TradeLocker / cTrader：general capabilityとFirm-specific settings分離

## 4. Fail behavior

1つでもmandatory itemがFAILの場合：

`PLATFORM_RELEASE_HOLD_COMPLIANCE`

としてpublishしない。

## 5. Legal scope

このGateは編集・運用上の安全基準であり、法的適合性の保証ではない。新たな金融商品性・勧誘性・スポンサー構造・規制論点が生じた場合は必要に応じて専門家確認を追加する。

Final Status：
`PLATFORM_COMPLIANCE_GATE_CONFIRMED`
