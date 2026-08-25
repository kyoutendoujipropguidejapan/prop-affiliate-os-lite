# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 14 / FINTOKEI PROTRADER SLIM CURRENT STATUS

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / CORRECTION REQUIRED / NO PRODUCTION CHANGE
Scope：Home Fintokei plan card + Fintokei FAQ/current-plan wording
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Trigger

Current public Home contains an internal status inconsistency:

- `チャレンジ・スリム` card is marked `現在は新規販売対象外` / `2026年3月31日で新規販売終了`
- the public Fintokei FAQ/current-plan wording still includes `チャレンジプラン・スリム` among current official plans

This required a fresh English-first recheck.

---

## 1. Check 1 — current English dedicated Fintokei FAQ

Official:
`https://support.fintokei.com/en/articles/13913487-what-is-protrader-slim`

Current article is shown as updated recently and describes ProTrader Slim in the present tense as a current ProTrader-family offer.

It states:
- ProTrader Slim is a current member of the ProTrader family
- exclusive to JPY accounts / Japan or Japanese-primary-language users
- available challenge sizes: Quartz, Crystal, Pearl, Ruby, Sapphire, Topaz
- Emerald not available
- platform: MT5 exclusive
- optimized simulation environment with lower-spread/JPY-commission specifications

There is no current `discontinued` or `legacy only` language in this dedicated English source.

Check 1：PASS for current existence.

---

## 2. Check 2 — current English Fintokei Products / ProTrader collections

Official:
`https://support.fintokei.com/en/collections/12355578-fintokei-products`
`https://support.fintokei.com/en/collections/6763127-protrader`

Current English product/help collections include `What is ProTrader Slim?` under ProTrader.

This supports treating Slim as a current ProTrader variant rather than a removed historical-only product.

Check 2：PASS.

---

## 3. Check 3 — current Japan-specific official product surface

Official:
`https://www.fintokei.com/jp/protrader-slim/`

Because ProTrader Slim itself is a Japan/Japanese-targeted offer, the Japanese product page is a relevant primary availability surface even under the English-first policy.

Current page renders:
- `今すぐ始める`
- active account-size cards and plan prices
- free-trial links
- current plan detail links
- current rules / simulation disclosures

Current examples include Quartz/Crystal/Pearl/Ruby/Sapphire/Topaz Slim.

No historical-only disclaimer is shown on the current product page.

Check 3：PASS for current public offer status.

---

## 4. Core-rule cross-check

Current English standard ProTrader rule FAQ:
`https://support.fintokei.com/en/articles/6538822-how-does-the-protrader-challenge-work-what-are-the-rules`

States current ProTrader baseline:
- Phase 1 target 8%
- Phase 2 target 6%
- Daily Loss 5%
- Maximum Loss 10%
- minimum 3 trading days per phase

The dedicated Slim FAQ says Slim follows standard ProTrader rules while changing trading-cost/environment specifications.

The current Japan Slim product page materially corroborates 8% / 6%, Daily5%, Max10%, min3 days.

Status for these scoped baseline fields：`TRIPLE_VERIFIED_WITH_VARIANT_SCOPE`

---

## 5. Result

The current public Home legacy status for `チャレンジ・スリム` is stale.

Status：
`CORRECTION_REQUIRED / CURRENT_JAPAN_VARIANT`

The old project statement `new sales ended 2026-03-31` may describe an earlier limited-release phase, but it is not current truth after the relaunched/powered-up Slim offer.

Do not erase historical chronology; separate:
- earlier limited release / former sale status
- current relaunched ProTrader Slim offer

---

## 6. Safe Production direction after auth recovery

After actual Production-source reconciliation + fresh Check3:

1. remove current `新規販売対象外` / legacy-only status from ProTrader Slim
2. classify it as a current Fintokei ProTrader variant for Japan/JPY scope
3. current headline baseline may use:
   - 2-Step
   - target 8% / 6%
   - Daily5%
   - Max10%
   - min3 days each phase
   - MT5 exclusive
4. preserve Japan/Japanese-user scope
5. do not auto-add or reweight Slim in Diagnosis scoring in the same patch
6. preserve historical sale/relaunch notes only in history context

---

## 7. Important count semantics

Fintokei's current English onboarding article says it offers four **programs**:
- StartTrader
- SwiftTrader
- ProTrader
- ProTrader Swing

Slim is a **ProTrader variant**, not necessarily a fifth top-level program in Fintokei's own English taxonomy.

Therefore public site may display five user-facing plan families/cards if useful, but should not claim that Fintokei itself defines five top-level programs solely because Slim has its own card.

Final Status：
`WAVE14_COMPLETE_FINTOKEI_SLIM_LEGACY_STATUS_STALE_CURRENT_VARIANT_RESTORATION_QUEUED`
