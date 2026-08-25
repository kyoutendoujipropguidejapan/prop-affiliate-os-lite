# FIRM_DETAIL_DATA_CONTRACT_V1

更新日：2026-08-26 JST
目的：Firm個別ページが既存Production資産を壊さず再利用するための表示用Data Contract。

## 0. 原則

- `app/master-data.json` のschemaをFirm Detailのために変更しない。
- Firm Detailは既存Accepted dataを読むPresentation Layer。
- 不足値を補うための新Master record生成は禁止。
- Platform / Payout / EvidenceをMasterへflattenしない。
- Commercial dataはFact / Rankingへ影響させない。

## 1. FirmDetailViewModel（概念）

```ts
interface FirmDetailViewModel {
  firmId: string;
  name: string;
  slug: string;
  summary: string;
  japan: JapanDisplay;
  serviceNature: StatusText;
  plans: PlanDisplayGroup[];
  rules: RuleSummary[];
  platforms: StatusText[];
  payout: PayoutSummaryDisplay;
  faq: FaqDisplay[];
  relatedLinks: RelatedLink[];
  commercial: CommercialDisplay;
  verification: VerificationDisplay;
  disclosures: DisclosureDisplay[];
}
```

これは実装指示上の概念interfaceであり、既存Production architectureに同等表現がある場合は新しい型を乱立させない。

## 2. StatusText

```ts
interface StatusText {
  value?: string;
  status: 'verified' | 'conditional' | 'unverified' | 'unsupported' | 'unknown';
  verifiedAt?: string;
  sourceLabel?: string;
}
```

表示ルール：

- verified → 公式根拠で確認済み
- conditional → 条件付き・追加確認が必要
- unverified → 未確認
- unsupported → 非対応
- unknown → 情報不足・不明

`unknown`を`unsupported`へ落とさない。

## 3. JapanDisplay

```ts
interface JapanDisplay {
  eligibility: StatusText;
  japaneseSite: StatusText;
  japaneseSupport: StatusText;
  kycNotes?: StatusText;
  regulatoryNoteRequired: boolean;
}
```

`eligibility` は日本居住者が利用できるかの事実。

`regulatoryNoteRequired` は「日本から利用可能」と「日本の金融規制上の登録・認可」を混同させないための表示制御。

Firm Detailで規制登録を推測しない。

## 4. PlanDisplayGroup

```ts
interface PlanDisplayGroup {
  group: 'current' | 'conditional' | 'listed_only' | 'legacy' | 'ended';
  plans: ExistingPlanReference[];
}
```

Planの実値は既存Production PlanCatalogを参照。

禁止：

- Firm Detail専用にPlanを複製
- HOLD PlanをCurrentへ昇格
- Diagnosis未接続を非対応扱い
- Legacyを現行料金として表示

## 5. RuleSummary

Firm Detailで最初に見せるRuleは絞る。

候補：

- evaluation steps
- profit target
- daily loss
- max loss
- drawdown type
- minimum trading days
- news trading
- weekend holding

Plan間で違う場合はFirm単一値に潰さず、`プランにより異なる` またはPlan単位表示へ送る。

## 6. Platform

Phase 1：既存 `planCatalog.platforms` のDisplay Stringを利用。

- 新Platform Registryはまだ作らない
- 一般Platform仕様とFirm実装仕様を混同しない
- 将来Platform Registry接続時にAdapterで置換可能な境界を維持

## 7. PayoutSummaryDisplay

```ts
interface PayoutSummaryDisplay {
  status: 'verified' | 'conditional' | 'unverified' | 'unknown';
  summary?: string;
  sourceRequired?: boolean;
}
```

P00R/P01/P10 Source不足中：

- Route生成禁止
- Provider推測禁止
- Wallet/Bank route推測禁止
- verified firm-specific summaryがない場合は最小表示またはunknown

## 8. FAQ

M11をBase、M14を判定Layerとして使用。

```ts
interface FaqDisplay {
  question: string;
  answer: string;
  status: 'pass' | 'caution' | 'hold';
  schemaEligible: boolean;
}
```

- UPDATE_REQUIREDはM14 replacement textを使用
- HOLDは確定回答へ変えない
- schemaEligible=falseのFAQをFAQ schemaへ入れない
- screen textとstructured dataを一致させる

## 9. CommercialDisplay

```ts
interface CommercialDisplay {
  basePrice?: ExistingPriceReference;
  officialCampaigns?: ExistingCampaignReference[];
  coupons?: ExistingCouponReference[];
  affiliateCta?: LinkDisplay;
  officialCta?: LinkDisplay;
}
```

境界：

- base price != campaign price
- campaign != coupon
- official CTA != affiliate CTA
- commissionを公開順位へ利用しない
- discount後価格の自動計算は別承認なしで行わない

## 10. VerificationDisplay

```ts
interface VerificationDisplay {
  lastChecked?: string;
  overallStatus: 'verified' | 'conditional' | 'unverified' | 'unknown';
  cautions: string[];
}
```

`overallStatus` はFirmの安全性・信頼性評価ではない。

意味は「このページに掲載する情報の確認状態」。

ラベルでFirm自体が公的認証済みであるような誤認を作らない。

## 11. DisclosureDisplay

必要条件に応じて表示：

- affiliate
- sponsored
- provided_account
- editorial_independence
- general_information
- risk_and_change

Disclosure文言は `COMPLIANCE_COPY_LIBRARY_V1_2026-08-26.md` を優先再利用する。

## 12. Missing Data Behavior

不足情報がある場合の優先順位：

1. Section内で`情報不足・不明`
2. `追加確認が必要`
3. Sectionを最小化
4. Claim単位HOLD

禁止：

- 推測値
- 0
- false
- `なし`
- 他Firmの値を流用

## 13. Staleness

Firm Detailは`lastChecked`を表示する。

変動性の高い情報：

- price
- campaign
- coupon
- plan availability
- eligibility
- support scope
- payout conditions

は公開直前再確認対象。

## 14. Analytics Boundary

Firm Detail ViewModelにPIIを持たせない。

GA4へ送れるのは公開Entity IDやUI action程度。

禁止：

- email
- name
- KYC status tied to user
- bank details
- wallet address
- trading account ID

## 15. Acceptance

Firm Detail Pilotで次を確認：

- Master schema 0 change
- Diagnosis result 0 change
- Commercial influence on ranking 0
- unknown preservation PASS
- Plan status grouping PASS
- FAQ M14 application PASS
- Disclosure PASS
- current / campaign / legacy separation PASS

このContractはPilot後に必要な最小修正だけ行い、14社横展開前にVersion固定する。
