# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 4 / HOME + PAYG

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / NO PRODUCTION CHANGE
Scope：公開中 Home / `/pay-after-pass-payg` / related commercial surfaces
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Rules

- 同じURLを3回読むことは3回チェックと数えない
- current product / FAQ / comparison / localized surfaceを可能な限り分離
- official同士が競合した場合は多数決せず `CONFLICT / HOLD`
- 検索非表示を不存在証明に使わない
- public crawler/index cacheの差はProduction sourceと同一視しない
- Production sourceは内部Git認証HOLD中のため編集しない

---

## 1. FTM — 日本語対応

### Public surface observed

Home currently contains:

`日本語対応予定`

and describes Japanese support as future-facing.

### Triple check

Check 1 — current official Japanese FAQ category
`https://fundedtradermarkets.com/ja/faq/category/trading-platforms`

Japanese UI and Japanese FAQ content are live.

Check 2 — current official Japanese Payments & Withdrawals FAQ
`https://fundedtradermarkets.com/ja/faq/category/payments-and-withdrawals`

Japanese payout/support content is live.

Check 3 — current official Japanese Terms
`https://fundedtradermarkets.com/ja/terms-conditions`

Japanese legal/terms surface is live.

Additional corroboration:
`https://fundedtradermarkets.com/ja/variations`

Japanese purchase/configuration surface is live.

### Result

Public `日本語対応予定` is stale.

Status：`CORRECTION_REQUIRED`

Safe correction direction:

`日本語サイト・FAQあり`

Do not overstate support quality or complete localization coverage. Prefer:

`日本語サイト・FAQを確認済み。プラン固有条件は購入前に公式画面で確認。`

---

## 2. FTM — current platforms

Current official Japanese FAQ states the firm currently offers:

- cTrader
- TradeLocker
- Match-Trader
- MetaTrader 5

Current Japanese variations page also exposes platform selection and US-specific restrictions.

Status：`CURRENT_OFFICIAL_SUPPORTED`

No immediate Home correction is required because current Home only says `複数形式FX・CFD`; exact platform expansion belongs in Firm Detail / Platform mapping after Production reconciliation.

---

## 3. Funded7 PAYG — public article risk values

### Public surface observed

`/pay-after-pass-payg` currently describes PAYG as:

- Phase 1 / Phase 2 = 8% / 6%
- Daily Loss = 4%
- Max Loss = 8%
- Static
- MT5
- 80/20
- outside standard allocation cap
- monthly payout cap $20,000

### Official checks

Check 1 — current official challenge comparison EN
`https://funded7.com/challenge-comparison/`

Current PAYG row shows:
- 8% / 6%
- 3 minimum trading days
- 10 trades
- Daily Loss 5%
- Max Loss 10%
- Static
- 80/20
- MT5
- 7-day payout
- $100 minimum

Check 2 — current official challenge comparison JP
`https://funded7.com/ja/challenge-comparison/`

Current Japanese PAYG row again shows:
- 8% / 6%
- Daily 5%
- Max 10%
- static / absolute drawdown
- 80/20
- MT5

Check 3 — current official Funded7 blog dated 2026-06-15/23
`https://funded7.com/blog/how-to-pass-the-funded7-challenge-a-step-by-step-guide/`

This official article says PAYG:
- 8% / 6%
- Daily 4%
- Max 8%
- Static
- MT5
- 80/20

### Additional official support

Allocation / payout cap FAQ:
`https://funded7.com/ja/faq/evaluation-maximum-allocation-limits-per-client/`

confirms:
- PAYG does not count toward standard allocation cap
- PAYG monthly payout cap = $20,000

### Result

Official current sources conflict on PAYG drawdown values:

`5% / 10%` vs `4% / 8%`

The public LP currently uses one side of an unresolved official conflict.

Status：`CONFLICT / HOLD / HIGH_PRIORITY`

Do not silently change to 5/10 and do not retain 4/8 as definitively current without another authoritative source.

Required resolution:
1. current purchase/configuration screen for PAYG,
2. dedicated current PAYG rules/FAQ if available,
3. direct Funded7 confirmation if official surfaces remain inconsistent,
4. fresh Check 3 immediately before Production patch.

Until resolved, safe public wording should avoid the disputed figures or explicitly say `公式情報を確認中`.

---

## 4. Funded7 PAYG — payment structure / allocation / payout cap

The following scoped claims are materially supported across current official sources:

- payment is staged: next stage fee only after passing current stage
- PAYG can sit outside standard maximum allocation cap
- PAYG monthly payout cap = $20,000

Status：`TRIPLE_VERIFIED_SCOPED`

Do not infer the disputed drawdown numbers from this verification.

---

## 5. FundedElite Flash Activation — Japan vs Global product layer

### Public surface observed

`/pay-after-pass-payg` says:
- starts from $5
- pay Activation after pass
- Japanese purchase route
- account size-dependent remaining/activation cost

### Check 1 — current global official FAQ
`https://faq.fundedelite.com/en/articles/12683940-flash-activation-challenge`

Base/default structure:
- entry from $5 depending on account/add-ons
- 1 phase
- default target 6%
- Daily DD 3%
- Max DD 6% static during evaluation
- no minimum evaluation days
- after pass: KYC + agreement + activation fee
- activation fee due within 29 days
- Live: 3 profitable days each >=0.5%, 30% consistency
- base split 80%
- base payout cycle 14 days

### Check 2 — current global official product page
`https://fundedelite.com/challenges/flash-activation`

Confirms:
- $5 start
- customizable rules
- target can be reduced from 6% to as low as 2%
- up to 95% split
- payout pace customizable
- FAQ section still presents base 6/3/6 structure and activation fees

### Check 3 — current Japanese official dedicated page
`https://fundedelite.jp/challenges/flash-activation`

Current JP localized layer shows:
- start 700円
- 500万円〜3,500万円 accounts
- base FAQ: target 6%, Daily 3%, Total 6% static, no minimum eval days
- activation fees in JPY
- customizable target down to 2%
- up to 95% split
- payout as fast as 3 days
- 3 profitable days >=0.5% and 30% consistency in live phase

### Result

Core Pay-After-Pass structure is confirmed.

However, current global base FAQ and Japanese customized/localized page differ materially on payout/split defaults:

- global base: 80% / 14 days
- JP current page: up to 95% / 3-day pace with customization

This can plausibly be base-vs-option / locale configuration, but the exact option matrix is still not fully exposed.

Status：
- Pay-after-pass structure: `TRIPLE_VERIFIED`
- exact Flash reward split / payout pace default: `CONFLICT_OR_VARIANT / HOLD`
- entry price for Japan: `LOCALIZED_UPDATE_CANDIDATE` (`700円` current JP page vs `$5` global)

Do not release the old Flash HOLD as a single universal rule set yet.

---

## 6. The5ers Summer Plan — Home 100K card

### Public surface observed

Home current pick shows:
- 2-Step 10/5 = $149
- 2-Step 8/5 = $179
- 1-Step = $249
- Daily loss 3% for all
- 2-Step Max loss 10%
- 1-Step Max loss 6%

### Triple check

Check 1 — current Summer product page
`https://the5ers.com/summer-plan/`

Check 2 — current Summer 2026 official article
`https://the5ers.com/prop-firm-summer-plan-2026/`

Check 3 — current Japanese Summer product page
`https://the5ers.com/jp/summer-plan/`

Check 4 — current Summer FAQ / 2-Step rules
`https://the5ers.com/faqs/2-step-plan-rules-specifications/`

All scoped Home values above align.

Status：`TRIPLE_VERIFIED / NO CORRECTION REQUIRED`

Important: this audit does not negate the separately user-confirmed current Summer 200K variant. Public static 100K Summer pages are not proof that the 200K route is absent.

---

## 7. Trading Cult Pro — Home platform/model wording

### Public surface observed

Home says:
- evaluation + Instant
- MT5
- multiple models
- FX/CFD

Current official homepage supports:
- TC 1 STEP
- TC 2 STEP
- TC INSTANT
- MetaTrader 5
- Forex / Indices / Commodities / Crypto

Current no-evaluation conditions page also states MetaTrader 5 and the same major market set.

Status：`SUPPORTED / THIRD-INDEPENDENT-CHECK_PENDING`

No correction required now. Do not promote this scoped item to `TRIPLE_VERIFIED` until a third independent current official route is captured.

---

## 8. Home freshness metadata

Current publicly crawled Home still contains:
- header information date `2026.08.02`
- footer text that listed information includes `2026年8月2日時点`

Yet the site now contains later-dated public pages (e.g. payout comparison updated 2026-08-13) and the production program has accepted later changes.

This is an internal freshness-label problem rather than an external Firm-rule fact.

Status：`FRESHNESS_METADATA_STALE / CORRECTION_REQUIRED`

Safe direction after Production reconciliation:
- replace one global ambiguous date with `ページごとの最終確認日` where possible,
- Home should display its own fresh verification date,
- do not imply every linked page was verified on the same date.

---

## 9. Public crawler cache caution

Search-index snippets for the same Home currently expose content variants that do not perfectly match a direct crawl. Therefore:

- crawler/index absence is not deployment proof,
- search snippet text is not canonical Production truth,
- actual source reconciliation is mandatory before edit.

Status：`PUBLIC_CACHE_DIVERGENCE_NOTED`

---

## 10. Wave 4 correction / hold queue

### P0 after internal Git recovery + Production reconciliation

1. FTM Home Japanese support
   - `日本語対応予定` -> current Japanese site/FAQ available

2. Funded7 PAYG disputed risk values
   - current public article uses 4/8
   - current official comparison uses 5/10
   - official blog uses 4/8
   - keep `CONFLICT/HOLD` until authoritative resolution

3. Home freshness metadata
   - current date label is stale

### P1

4. FundedElite Japan localized Flash entry price
   - `$5` global vs `700円` current JP route
   - localize carefully rather than calling either universally wrong

### Remain HOLD

5. FundedElite Flash exact reward split / payout pace default-vs-custom matrix

### No correction

6. The5ers Home Summer 100K scoped card

7. Trading Cult Home model/platform wording — supported, third check pending

---

## 11. Production boundary

No Production modification performed.

Internal Sites Git remains auth-blocked / Support-escalated.

When auth recovers:
1. reconcile actual Production source
2. fresh source check
3. resolve Funded7 PAYG before publishing numeric correction
4. minimal patch only
5. regression + protected hashes + 390px + compliance
6. human publish approval

Final Status：
`WAVE4_AUDIT_COMPLETE_FTM_CORRECTION_FUNDED7_PAYG_CONFLICT_HOME_FRESHNESS_STALE_NO_PRODUCTION_CHANGE`
