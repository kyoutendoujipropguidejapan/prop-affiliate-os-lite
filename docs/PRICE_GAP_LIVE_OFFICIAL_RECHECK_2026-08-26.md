# PRICE GAP LIVE OFFICIAL RECHECK

確認日：2026-08-26 JST
Status：OFFICIAL WEB RECHECK / PRODUCTION PATCH NOT APPLIED
Production code changes：NONE

## 1. Purpose

Public surfaceで`価格確認中`として残っている2件について、2026-08-26時点の公式一次情報を再確認する。

対象：
- The5ers Futures | Day Trade 25K
- Blueberry Futures | Accelerated standard evaluation prices

この文書はProductionデータを自動更新しない。Work再入場後の最小patch候補のEvidenceとする。

## 2. The5ers Futures — Day Trade 25K

公式Futures pageで確認：

- Account Size：$25K
- Price：$59
- Activation fee upon passing：None
- one-time fee structure / no monthly fees と公式説明

Source：
- https://www.the5ers.com/futures/

Status：
`VERIFIED_OFFICIAL_CURRENT_WEB`

## 3. Blueberry Futures — Accelerated

Blueberry Futures公式Helpでstandard prices before discountsを確認：

- 25K：$129
- 50K：$184
- 100K：$276
- 150K：$454

同じ公式Helpで60% discount後の例も掲載されているが、Base PriceとCampaign / Discount表示を分離する。

Source：
- https://help.blueberryfutures.com/en/articles/11196037-what-are-your-prices-for-evaluations

Additional official confirmation：
- https://help.blueberryfutures.com/en/articles/12890893-detailed-parameters-of-our-challenges

Status：
`VERIFIED_OFFICIAL_CURRENT_HELP`

## 4. Current public discrepancy

2026-08-26 public crawlでは、両項目がまだ`現在、公式価格を確認中です。確認できるまで、価格や購入ボタンは表示していません。`として表示されている。

Therefore：

- Official source recheck = PASS
- Public surface update = NOT OBSERVED
- Production source/commit state = RECONCILIATION_REQUIRED

Public crawlだけを見てpatch済み／未patchを断定しない。

## 5. Compliance / price boundary

Blueberry Futuresは公式Siteで60% off campaign表示があるため：

- standard/base evaluation price
- current official campaign
- personal affiliate coupon

を別Layerで保持する。

Discounted priceをbase priceへ上書きしない。

The5ers Futuresの`$59`もcurrent official pageのDay Trade 25K priceとして扱い、他account size / Swing / future priceへ自動展開しない。

## 6. Work action after reconciliation

Current Production treeが未更新であることを確認できた場合のみ、最小patch候補：

- The5ers Futures Day Trade 25K：$59 / activation fee None
- Blueberry Futures Accelerated base prices：129 / 184 / 276 / 454 USD

Patch前に：
- exact data path
- price layer
- campaign separation
- protected hash scope
- regression
を確認する。

Final Status：
`PRICE_GAP_OFFICIAL_RECHECK_PASS_PRODUCTION_RECONCILIATION_PENDING`
