# PUBLIC LP TRIPLE FACT-CHECK AUDIT — WAVE 10 / HANTEC CURRENT FAMILY

更新日：2026-08-26 JST
Status：AUDIT COMPLETE / NO PRODUCTION CHANGE
Scope：公開中HomeのHantec Trader 7プラン表示・現行モデル・Availability・高リスク条件
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Method

可能な限り以下を分離して照合した。

- current official EN Help Center account collection
- current official JP Help Center account collection
- current official JP main/product pages
- current official dedicated product pages / Help articles

同一翻訳記事だけを3回とは数えない。official同士のAvailability差は多数決で消さない。

Production sourceは内部Git認証HOLD中のため編集しない。

---

## 1. Hantec current program family = 7 program names

### Public surface observed

Current public LP says `Hantec Trader 7プラン` and manages:
- Instant24
- Instant Lite
- Instant Funding
- Express
- EnhancedX
- Enhanced
- Endurance

Instant Lite is currently separated as confirmation-in-progress in the public surface.

### Check 1 — current EN Help Center / Challenge Types
`https://help.htrader.hmarkets.com/en/support/solutions/folders/158001038630`

Lists exactly 7 current account/program articles:
- Express
- Enhanced
- EnhancedX
- Endurance
- Instant Funding
- Instant Lite
- Instant24

### Check 2 — current JP Help Center / 各チャレンジについて
`https://help.htrader.hmarkets.com/ja-JP/support/solutions/folders/158001038630`

Again lists the same 7 program families.

### Check 3 — current JP main site
`https://htrader.hmarkets.com/jp/`

Navigation/comparison exposes:
- Instant24
- Instant Lite
- Instant Funding
- Express
- EnhancedX
- Enhanced
- Endurance

### Result

The public company-level count `7プラン` is supported as a program-family count.

Status：`TRIPLE_VERIFIED_PROGRAM_FAMILY_COUNT / NO COUNT CORRECTION`

Caution: `7 program names exist` is not equivalent to `all 7 are unquestionably purchasable right now` because Endurance has a live Availability conflict described below.

---

## 2. Endurance — core numeric rules

### Public surface observed

- 3-step
- target 6% / 6% / 6%
- Daily Loss 4%
- Max Loss 8% Static
- min3 days each stage
- evaluation news allowed / Trader account ±3min restriction
- weekend hold allowed
- standard payout14d / 80%

### Check 1 — current EN dedicated product page
`https://htrader.hmarkets.com/programs/endurance/`

Confirms:
- 6/6/6
- Daily4
- Max8 Static
- min3 days each stage
- 1:50
- weekend holding allowed
- Challenge news allowed; Trader stage news restriction
- standard reward14d / 80%, add-ons may alter

### Check 2 — current JP dedicated product page
`https://htrader.hmarkets.com/jp/programs/endurance/`

Independently renders the same core 6/6/6, 4, 8 Static and 3-day structure.

### Check 3 — current EN Help article
`https://help.htrader.hmarkets.com/en/support/solutions/articles/158000445800-endurance-3-step-challenge-`

Again supports:
- target6/6/6
- Daily4
- Max8 Static
- standard payout14d
- standard split80%
- add-ons including95% / weekly / no-min-days where purchased

### Result

Status：`TRIPLE_VERIFIED_CORE_RULES`

No numeric correction required for the scoped public Endurance card.

---

## 3. Endurance — current purchase availability conflict

### Official source A — current JP main site

The Hantec JP navigation/comparison labels Endurance:
`近日公開 / Coming Soon`

### Official source B — current EN dedicated Endurance product page

The dedicated page exposes:
- multiple account sizes
- prices
- `GET STARTED`
- purchase-flow language

### Official source C — current JP dedicated Endurance product page

The JP dedicated page likewise exposes:
- account sizes
- prices
- `今すぐ始める`
- purchase-flow language

### Interpretation

The official ecosystem currently disagrees on Endurance availability state.

Possible explanations include rollout/cache/locale timing, but this audit does not infer one.

### Result

Status：`AVAILABILITY_CONFLICT / HOLD_ACTIVE_STATUS`

Safe public handling after Production reconciliation:
- keep the verified rule card if already present,
- do not state `販売中` or `購入可能` as a definitive current fact,
- add `販売状況は公式購入画面で確認` if needed,
- resolve against the live checkout/configurator immediately before publish.

Do not remove Endurance solely because the JP navigation says `近日公開`; the dedicated official purchase pages contradict that.

---

## 4. Instant24 — current core

### Public surface observed

- 24-hour window
- Daily2%
- Max3% trailing closed balance
- minimum reward profit3%
- one open position
- max open risk1%
- consistency15%
- news allowed
- EA not allowed
- payout after24h if conditions met
- standard split80%

### Triple check

Check 1 — current EN Help `Instant24`
`https://help.htrader.hmarkets.com/en/support/solutions/articles/158000445803-instant24`

Confirms all scoped values above.

Check 2 — current JP main comparison
`https://htrader.hmarkets.com/jp/`

Current model comparison identifies Instant24 as a live/new Instant program and independently exposes the 24-hour model in the current program family.

Check 3 — current EN/JP Help account collections
Instant24 remains a current account type in both current Help collections; current article is modified in the active rules set.

### Result

Status：`TRIPLE_CHECKED_WITH_MODEL-COLLECTION_DEPENDENCY / PUBLIC CORE MATERIALLY ALIGNED`

No correction required for the observed scoped fields.

---

## 5. Instant Funding — current core + legacy affiliate-page discrepancy

### Public surface observed

- no target
- Daily6%
- Max6% trailing closed balance -> lock at +6%
- no minimum trading days
- news ±3min
- weekend hold not allowed
- standard payout14d / 80%
- EA not allowed

### Check 1 — current EN product page
`https://htrader.hmarkets.com/programs/instant-funding/`

Confirms all scoped fields, standard split80% -> up to95% with add-on.

### Check 2 — current JP product page
`https://htrader.hmarkets.com/jp/programs/instant-funding/`

Again confirms 6/6, no minimum days, 80->95, ±3min, weekend no.

### Check 3 — current Help article/current account collection
Current Help identifies Instant Funding as an active Instant model and the current rule article supports the same 6/6 structure.

### Legacy/stale official surface

Current-accessible affiliate programme pages still render an older split structure:
- standard75%
- +15% add-on -> 90%

while current main product pages say:
- standard80%
- up to95%

### Result

Core risk/trading rules：`TRIPLE_VERIFIED_SCOPED`

Current reward split primary handling：`80% standard / up to95% add-on`, supported by the current main product family.

Legacy affiliate page discrepancy：`STALE_OR_LEGACY_OFFICIAL_SURFACE_CAUTION`

Do not resurrect 75/90 in current public cards unless live purchase flow specifically uses it.

---

## 6. Express — current core

Current public card:
- target10
- Daily5
- Max6 trailing -> lock
- no evaluation minimum trading days
- challenge news allowed / Trader account ±3min
- weekend allowed
- payout14d / standard80%

Current official checks:
1. EN Help Express
2. current program family/product routing
3. current main-site/Help current-account collections

Materially align on the scoped fields.

Important add-ons:
- target10 -> 8 option
- Max6 -> 8 option
- split80 ->95
- standard14 -> weekly7
- first payout on demand

Status：`CURRENT_OFFICIAL_SUPPORTED / NO CORRECTION REQUIRED`

Do not flatten add-on values into defaults.

---

## 7. Enhanced — current core

### Triple check

Check 1 — EN Help Enhanced
`https://help.htrader.hmarkets.com/en/support/solutions/articles/158000445798-enhanced`

Check 2 — JP dedicated product
`https://htrader.hmarkets.com/jp/programs/enhanced-challenge/`

Check 3 — current EN/JP account collections

Current core:
- target10/5
- Daily5
- Max10 Static
- 3 profitable days each stage; current rule describes >=0.5% qualifying day in product context
- challenge news allowed / Trader ±3min
- weekend allowed
- standard14d /80
- Funded max open risk3%

### Result

Status：`TRIPLE_VERIFIED_SCOPED / NO CORRECTION REQUIRED`

---

## 8. EnhancedX — public minimum-days field can be improved

### Public surface observed

Current public card says:
`最低取引日数：要確認`

and separately notes consistency35%.

### Check 1 — current EN EnhancedX product page
`https://htrader.hmarkets.com/programs/enhancedx/`

Explicitly:
- Minimum Trading Days = 0 / 0
- no minimum trading days, but must meet consistency score
- target8/4
- Daily4
- Max8 Static
- consistency35% per evaluation stage unless removed with add-on

### Check 2 — current locale product mirror
Current Korean/other locale product page exposes the same 0-day +35% consistency model.

### Check 3 — current EN/JP Help account collection
EnhancedX remains a current dedicated 2-Step Consistency account type, separate from Enhanced.

### Result

Public `要確認` is conservative, but a clearer current statement is supported:

`最低取引日数：なし（ただしChallengeはConsistency 35%以下が必要。対象Add-onで評価側Consistency解除可）`

Status：`UPDATE_CANDIDATE`

Fresh dedicated Help/product recheck required immediately before edit.

---

## 9. Instant Lite — already centrally approved

Do not reopen the resolved base-vs-add-on issue without new contradictory evidence.

Approved:
`HOLD -> VERIFIED_WITH_CAUTION`

- standard Daily3
- standard Max5 trailing -> lock at +5
- optional +1% max-loss add-on -> 6
- no general minimum trading days
- payout cycle requires5 profitable days, each>=0.5%
- standard14d /80
- EA no / weekend no

Public current wording still reflects the old unresolved-HOLD text; Production correction remains queued after auth/reconciliation.

---

## 10. Service-nature / compliance

Current official Help describes Hantec Trader as:
- simulated trading environment
- demo accounts / virtual funds
- performance-based rewards from virtual profits

Public copy must retain this distinction and must not convert marketing `funded` wording into customer-deposit or guaranteed-real-capital claims.

---

## 11. Wave 10 queue

### P0/P1 after auth + Production reconciliation

1. Instant Lite old HOLD wording -> approved `VERIFIED_WITH_CAUTION` wording.

2. EnhancedX minimum-days field:
   - `要確認` -> current `なし`, with35% consistency condition preserved.

### HOLD / do not force a binary availability status

3. Endurance purchase availability:
   - JP main says Coming Soon
   - EN/JP dedicated pages expose purchase/GET STARTED
   - keep `AVAILABILITY_CONFLICT`

### No correction

4. company-level 7-program family count
5. Endurance core numeric values
6. Instant24 scoped core
7. Instant Funding scoped risk/trading values
8. Express scoped core
9. Enhanced scoped core

### Caution only

10. Instant Funding old affiliate programme page still shows75/90 split; current main product says80/95. Use current main product as primary but retain stale-surface evidence.

---

## 12. Production boundary

No Production modification performed.

Internal Sites Git remains auth-blocked / Support-escalated.

Final Status：
`WAVE10_HANTEC_AUDIT_COMPLETE_7_PROGRAM_FAMILY_VERIFIED_ENDURANCE_AVAILABILITY_CONFLICT_ENHANCEDX_UPDATE_CANDIDATE_NO_PRODUCTION_CHANGE`
