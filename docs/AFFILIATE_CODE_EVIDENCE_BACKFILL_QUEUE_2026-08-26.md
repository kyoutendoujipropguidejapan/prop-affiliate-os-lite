# AFFILIATE CODE EVIDENCE BACKFILL QUEUE

更新日：2026-08-26 JST
Status：BACKFILL REQUIRED / DO NOT INVALIDATE PUBLIC CODES
Scope：公開Home `使える専用クーポン` + commercial routes
Standard：`FACT_CHECK_STANDARD_V1_2026-08-26.md`

## 0. Purpose

公開中の専用/パートナーコードについて、2026-08-26から導入した「最低3回ファクトチェック」を遡及適用する。

重要：
- 公開Web検索にコードが出ないことは無効の証明ではない。
- partner-only / affiliate-only codeはcheckout、partner portal、担当者回答にのみ存在し得る。
- 過去に運営者確認済みでも、Evidence Packetが未整備なら遡及監査上はbackfill対象。
- 3回揃うまで削除・無効扱いしない。

## 1. Public claims captured from Home crawl

| Firm | Code | Public claimed benefit | Public claimed scope | Current retrospective status |
|---|---|---:|---|---|
| Trading Cult Pro | `AFFCB0D9` | 10% OFF | 期限なし / 対象は購入画面 | `EVIDENCE_BACKFILL_REQUIRED` |
| Funded7 | `KYOUTEN50` | 50% OFF | 期限なし / 新規2フェーズ | `EVIDENCE_BACKFILL_REQUIRED` |
| Funded7 | `KYOUTEN25` | 25% OFF | 期限なし / NEO以外の再購入・買い増し | `EVIDENCE_BACKFILL_REQUIRED` |
| Funded7 | `KYOUTENP` | 利益配分 +10% | PAYG / 期限は購入画面 | `EVIDENCE_BACKFILL_REQUIRED_HIGH_PRIORITY` |
| Funded Trader Markets | `KYOUTEN` | 10% OFF | 対象・期限は購入画面 | `EVIDENCE_BACKFILL_REQUIRED` |
| SuperFunded | `KYOUTEN` | 30% OFF | 期限なし / 対象は購入画面 | `EVIDENCE_BACKFILL_REQUIRED` |
| Blueberry Funded | `kyouten30` | 30% OFF | 期限なし / 対象は購入画面 | `EVIDENCE_BACKFILL_REQUIRED` |
| Blueberry Futures | `KYOUTEN60` | 60% OFF | 期限なし / 対象は購入画面 | `EVIDENCE_BACKFILL_REQUIRED` |
| Hantec Trader | `A76tgek48` | 5% OFF | 期限なし / 適用可否は購入画面 | `EVIDENCE_BACKFILL_REQUIRED` |
| The5ers | `736DR0F6PX` | 初回5% OFF | 期限なし / 対象は購入画面 | `EVIDENCE_BACKFILL_REQUIRED` |

## 2. Public-search check

2026-08-26に各コードを該当Firm公式domainへ限定して検索したが、上記partner/exclusive codeの直接公開ページは検索結果から確認できなかった。

Result：
`PUBLIC_SEARCH_NOT_OBSERVED`

これは `INVALID` / `ENDED` を意味しない。

## 3. Minimum evidence set per code

各コードを `TRIPLE_VERIFIED` へ上げるには原則：

### Check 1 — Operational official/partner source
いずれか：
- current live checkoutでcode acceptance
- partner portal current campaign/coupon record
- current affiliate dashboard

### Check 2 — Independent official confirmation
いずれか：
- current direct partner/affiliate-manager confirmation
- separate current checkout/account flow
- Firm-issued campaign/partner document

### Check 3 — Fresh pre-publication check
- publish/patch直前のcheckout acceptance
- effect / scope / expiry / combinability再確認

Evidence Packetには少なくとも：
- firm
- code
- effect
- scope
- new/existing user condition
- eligible plans
- expiry or `not stated`
- combinability
- checked_at
- source type
- screenshot/export/message reference where permitted
を保持する。

## 4. Priority order

### P0 — payout/reward economics changes
1. Funded7 `KYOUTENP` — profit split +10%

Reason：discountではなくreward economicsを変更する主張で、誤りの影響が大きい。

### P1 — large discounts
2. Funded7 `KYOUTEN50`
3. Blueberry Futures `KYOUTEN60`
4. SuperFunded `KYOUTEN`
5. Blueberry Funded `kyouten30`

### P2 — remaining commercial codes
6. Funded7 `KYOUTEN25`
7. Trading Cult Pro `AFFCB0D9`
8. FTM `KYOUTEN`
9. Hantec `A76tgek48`
10. The5ers `736DR0F6PX`

Priority is verification workload/risk only; it does not imply which code is more valuable or valid.

## 5. Public wording until backfill completes

Avoid blanket:
`掲載コードは有効です`

Preferred:
`掲載コードは運営者が有効性を確認したものです。割引率・対象・併用可否・最終適用は購入画面で再確認してください。`

For codes with existing immutable direct-confirmation evidence, that evidence may count toward the three checks after it is formally ingested into Evidence Registry.

## 6. Relationship to official public codes

Firm-public codes such as a code displayed directly on the Firm's current English official product page are audited separately from partner-exclusive codes.

Do not mix:
- Official Public Campaign
- Operator Exclusive Code
- Affiliate Referral Tracking
- Base Price

## 7. Production boundary

No code is removed, disabled or changed by this document.
No Production change performed.

When internal Git auth recovers:
1. inspect actual current Home code block
2. ingest available retained partner evidence
3. fill missing operational checks
4. patch only claims that fail/currently changed
5. keep CTA-level PR disclosure

Final Status：
`EXCLUSIVE_CODE_BACKFILL_QUEUE_DEFINED_NO_CODE_INVALIDATED`
