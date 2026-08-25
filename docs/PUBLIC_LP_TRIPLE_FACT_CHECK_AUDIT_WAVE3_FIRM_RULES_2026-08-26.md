# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 3 / FIRM RULES

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / HANTEC HOLD APPROVED FOR VERIFIED_WITH_CAUTION / NO PRODUCTION CHANGE
Scope：公開中 `kyouten-prop-guide.utsr.chatgpt.site` の Blue Guardian / Blueberry Funded / Hantec Trader / SuperFunded
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Purpose

公開中LPの既存Firm/Plan Factへ最低3回のファクトチェックを遡及適用する。

原則：
- 同じページを3回読むことは3回チェックと数えない
- current official Help / current product page / current official article・rules等を可能な限り分ける
- cohort / purchase date差を保持する
- 検索非表示やクローラ不観測だけで不存在を断定しない
- Production sourceは内部Git認証HOLD中のため、本書では監査・修正候補の固定のみ行い、Production変更はしない

---

## 1. Blue Guardian — 1 Step Standard

### Public surface observed

Current public LP:
- Profit Target: 10%
- Daily DD: 4%
- Max DD: 6% trailing
- Minimum Trading Days: 3 profitable days
- Profit Split: 85% (add-on)
- Payout: 14 days

### Triple check

Check 1 — official Help Center / 1 Step Standard Rules
`https://help.blueguardian.com/en/articles/14062186-1-step-standard-rules`

Current rule for accounts purchased from 2026-08-20 onward:
- Profit Target 9%
- Daily DD 4%
- Max DD 6% trailing
- 3 profitable days
- standard split 85%, optional 90%
- 14-day payout, optional 7-day add-on

Accounts purchased before 2026-08-20 retain prior 10% target.

Check 2 — official Blue Guardian current comparison article, 2026-08-24
`https://origin.blueguardian.com/blogs/1-step-vs-1-step-nano-vs-2-step-standard-vs-2-step-nano-which-challenge-is-best-for-you`

Confirms current 1 Step Standard:
- 9% target
- 4% daily DD
- 6% trailing max DD
- 3 profitable days

Check 3 — current official Account Models collection + same current-model cohort context
`https://help.blueguardian.com/en/collections/18967956-account-models`

Current Account Models explicitly lists 1 Step Standard as current, not legacy, and separates legacy models. The current dedicated rule article is therefore the governing current-model source for new purchases.

### Result

Public `10%` is stale for new purchases from 2026-08-20 onward.

Status：`CORRECTION_REQUIRED / COHORT_AWARE`

Safe correction direction:
`新規購入（2026-08-20以降）9%／それ以前の対象口座10%`

Do not retroactively rewrite historical cohorts.

---

## 2. Blue Guardian — 2 Step Standard minimum trading days

### Public surface observed

Current public LP:
- Profit Target 8% / 4%
- Daily DD 4%
- Max DD 8% static
- Minimum Trading Days 5 profitable days
- standard split 85%
- payout 14 days

### Triple check

Check 1 — official Help Center / 2 Step Standard Rules
`https://help.blueguardian.com/en/articles/14062291-2-step-standard-rules`

For accounts purchased from 2026-08-20 onward:
- minimum 3 profitable trading days
- pre-2026-08-20 accounts retain 5 days

Check 2 — official article, 2026-08-20
`https://origin.blueguardian.com/blogs/blue-guardian-2-step-standard-vs-2-step-nano`

Confirms:
- 2 Step Standard = 8% / 4%
- 4% daily DD
- 8% static max DD
- 3 profitable days for accounts purchased from 2026-08-20

Check 3 — official four-model comparison, 2026-08-24
`https://origin.blueguardian.com/blogs/1-step-vs-1-step-nano-vs-2-step-standard-vs-2-step-nano-which-challenge-is-best-for-you`

Again confirms current 2 Step Standard = 3 profitable days for new cohort.

### Result

Public `5利益日` is stale as a current-new-purchase value.

Status：`CORRECTION_REQUIRED / COHORT_AWARE`

Safe correction direction:
`2026-08-20以降購入：3利益日／それ以前：5利益日`

---

## 3. Blue Guardian — Nano models missing from current public active set

### Public surface observed

Current public Firm section does not present 1 Step Nano / 2 Step Nano as normal current active plans.

### Triple check

Check 1 — official Account Models collection
`https://help.blueguardian.com/en/collections/18967956-account-models`

Lists both current:
- 1 Step Nano Rules
- 2 Step Nano Rules

Check 2 — official 1 Step Nano Rules
`https://help.blueguardian.com/en/articles/16444654-1-step-nano-rules`

Current model exists.

Check 3 — official 2 Step Nano Rules
`https://help.blueguardian.com/en/articles/16445450-2-step-nano-rules`

Current model exists.

Additional corroboration: official 2026-08-24 four-model comparison treats both Nano models as current.

### Result

Not a false existing value, but a current-product coverage gap.

Status：`CONTENT_GAP / ADD_CURRENT_MODELS_AFTER_PRODUCTION_RECONCILIATION`

Do not infer pricing or checkout availability from Help alone; add only after current purchase surface is reconciled.

---

## 4. Blueberry Funded — Instant Lite post-2026-08-17

### Public surface observed

Current public LP presents Instant Lite generally as:
- Daily DD 2%
- Max DD 4% trailing -> lock
- Minimum Trading Days 5
- payout 14 days / 80%
- purchase-date differences noted, but no current-new-cohort values shown

### Triple check

Check 1 — current official Help / New Instant Lite Rules
`https://help.blueberryfunded.com/en/articles/16385107-new-what-are-the-rules-on-an-instant-lite-account`

Applies to accounts purchased on/after 2026-08-17:
- 4% maximum loss = static
- 2% daily loss
- no minimum trading days
- 80% split, scaling to 90%
- 14-day payout cycle
- 15% consistency check at payout

Check 2 — current official Help / active trading days
`https://help.blueberryfunded.com/en/articles/12136639-how-many-active-trading-days-do-i-need`

Confirms:
- Instant Lite from 2026-08-17: no minimum trading days
- 2026-02-17 to 2026-08-16: 5 days / reward cycle
- before 2026-02-17: 3 days / reward cycle

Check 3 — current official Help / payout timing
`https://help.blueberryfunded.com/en/articles/13756854-how-fast-can-i-withdraw-profits-from-instant-accounts`

Again confirms post-2026-08-17:
- no minimum trading days
- 14-day standard cycle
- 15% consistency check

Additional corroboration:
`https://help.blueberryfunded.com/en/articles/9812246-does-blueberry-funded-enforce-a-consistency-rule-in-trading`

### Result

Current public generic Instant Lite card is stale for new purchases in two important fields:
- `5日` -> post-2026-08-17 is `なし`
- `4% Trailing→Lock` -> post-2026-08-17 dedicated current rule says `4% static`

It also omits the current 15% payout consistency rule.

Status：`CORRECTION_REQUIRED / HIGH_PRIORITY / COHORT_AWARE`

Safe correction direction:
- current-new cohort first
- legacy cohort clearly separated
- do not overwrite historical accounts

---

## 5. Blueberry Funded — Prime minimum trading days

### Public surface observed

Current public Prime card shows `Minimum Trading Days: 要確認`.

### Triple check

Check 1 — current Blueberry Funded homepage
`https://blueberryfunded.com/`

Current Prime 2-Step shows 3 Days / Phase.

Check 2 — affiliate/ref current homepage rendering
`https://blueberryfunded.com/ref/349/`

Again shows Prime = 3 Days / Phase.

Check 3 — current Prime product page
`https://blueberryfunded.com/prime/`

Shows `3 or 5 Days / Phase`, with current 3-day path and legacy/add-on context.

### Result

Public `要確認` is conservative, not false, but can now be improved with cohort wording.

Status：`UPDATE_CANDIDATE`

Safe wording:
`現行新規購入は3日/Phase。旧購入条件・一部表示では5日を保持するため購入日を確認。`

Fresh implementation-time recheck required.

---

## 6. Hantec Trader — Instant Lite max loss HOLD

### Public surface observed

Current public LP marks Instant Lite as confirmation-in-progress because it interpreted official sources as:
- body = 5% max loss
- add-on wording = standard 6% implication

### Triple check

Check 1 — current official Help / Instant Lite
`https://help.htrader.hmarkets.com/en/support/solutions/articles/158000445802-instant-lite`

Current standard:
- Daily Loss 3%
- Max Total Loss 5% trailing closed balance -> locks at starting balance after 5% profit
- Max Loss +1% add-on increases standard 5% to 6%

Check 2 — current official EN product page
`https://htrader.hmarkets.com/programs/instant-lite/`

Confirms standard 5% trailing max loss.

Check 3 — current official JP product page
`https://htrader.hmarkets.com/jp/programs/instant-lite/`

Again confirms standard 5% trailing max loss.

### Result

The previous apparent `5% vs 6%` conflict is explainable as base rule vs optional +1% add-on.

User/central command approved resolution on 2026-08-26.

Status transition:
`HOLD -> VERIFIED_WITH_CAUTION`

Approved canonical display:
`標準5% Trailing（決済後残高追随→5%利益到達後に開始残高でLock）／+1% Max Loss Add-onで6%`

Production edit remains blocked until internal Git auth recovery + source reconciliation + fresh recheck.

---

## 7. Hantec Trader — Instant Lite trading-day wording

### Official distinction

Current product pages say `No minimum trading days` for entering/operating the Instant Lite program.

Current Help article says payout eligibility requires `5 profitable days` per payout cycle, each >=0.5% profit.

These are not contradictory; they describe different scopes.

### Result

Public card field `最低取引日数 5利益日` can be misread as a general program minimum.

Status：`WORDING_CORRECTION_REQUIRED`

Safe wording:
`評価・開始の最低取引日数：なし／出金周期の条件：5利益日（各0.5%以上）`

---

## 8. SuperFunded — current scoped recheck

### Public surface observed

1 Step:
- target 8%
- daily 3%
- max 5% trailing
- min 3 days
- standard split 80%, optional 90%

Payout article:
- first 3 successful payouts cap 5%
- distribution 40% / 30% for >=50K
- standard 14-day cycle

### Triple check

Check 1 — current official FAQ
`https://superfunded.com/faqs/`

Confirms 1 Step 8/3/5, 2 Step 10+5/5/10, Profit Distribution 40% / 30%, first-three payout cap rules.

Check 2 — Rules and Conditions V2.0
`https://superfunded.com/wp-content/uploads/2026/01/SuperFunded-Rules-and-Conditions.pdf`

Confirms 1 Step 8% target, 5% max DD, 3 min days; 2 Step 10%+5%, 10% max DD, 4 evaluation days / 5 funded days.

Check 3 — current product/challenge page
`https://superfunded.com/challenges/`

Confirms current 1 Step headline values and 2 Step headline values.

### Result

Scoped headline values remain supported.

Status：`TRIPLE_VERIFIED / NO CORRECTION REQUIRED` for the audited fields.

Do not generalize to every add-on or historical cohort without a fresh check.

---

## 9. Wave 3 correction queue

### P0 after internal Git recovery + Production reconciliation

1. Blueberry Funded Instant Lite current-new cohort
   - min trading days
   - max DD type
   - 15% consistency
   - preserve legacy cohorts

2. Blue Guardian 1 Step Standard
   - 10% -> current new cohort 9%

3. Blue Guardian 2 Step Standard
   - 5 profitable days -> current new cohort 3

### P1

4. Hantec Instant Lite wording
   - no general minimum days vs 5 profitable payout days

5. Blue Guardian current Nano plan coverage

6. Blueberry Prime minimum-day wording improvement

### Approved status change, awaiting Production implementation gate

7. Hantec Instant Lite
   - `HOLD -> VERIFIED_WITH_CAUTION`
   - standard max loss 5% trailing
   - optional +1% add-on = 6%

### No correction from this Wave

8. SuperFunded scoped core values

---

## 10. Production boundary

No Production modification performed.

Internal Sites Git remains auth-blocked and Support-escalated.

When auth recovers:
1. reconcile actual Production source
2. fresh third check immediately before edit
3. confirm cohort fields exist in source architecture
4. minimal patch only
5. regression + protected hashes + 390px + compliance
6. human approval for publish

Final Status：
`WAVE3_AUDIT_COMPLETE_HANTEC_VERIFIED_WITH_CAUTION_APPROVED_CORRECTIONS_QUEUED_NO_PRODUCTION_CHANGE`
