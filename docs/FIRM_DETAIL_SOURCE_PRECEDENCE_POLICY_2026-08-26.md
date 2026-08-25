# FIRM DETAIL SOURCE PRECEDENCE / FRESHNESS POLICY

更新日：2026-08-26 JST
対象：全Firm個別ページ

## 1. Purpose
Firm Detailで古いFAQ、旧Campaign、過去Plan、Direct message、公式Terms等が競合した時の判断順を固定する。

## 2. Source Precedence
原則優先：
1. Current official Terms / Rules / FAQ / purchase page
2. Current official product / help page
3. Current direct written confirmation from Firm（ただしTermsを自動上書きしない）
4. Accepted verified extraction / Evidence with current validity
5. Historical official source
6. Social post
7. Third-party source

## 3. Direct Contact Rule
Direct contactは重要Evidenceだが、公式Termsと矛盾する場合は自動的に勝たせない。

矛盾は `CONFLICT` / `確認中` とし、人間確認まで確定値にしない。

## 4. Freshness
変動性が高い項目：
- price
- campaign
- coupon
- Japan eligibility
- KYC
- payout
- supported platform
- news/weekend rules
- minimum trading days
- profit target / drawdown rules

公開前にcurrent sourceと照合する。

## 5. M11 / M14 Use
M11は本文Baseとして再利用可能。
M14は検証判定・UPDATE_REQUIRED・HOLDを上から適用する。

ただしM14以降にCurrent Productionで正式に解決・更新された項目は、accepted newer truthを優先する。

古いHOLDを機械的に永久固定しない一方、解決Evidenceなしで解除しない。

## 6. Status Conversion
verified → 公式根拠で確認済み
conditional → 条件付き・追加確認が必要
unverified → 未確認
unsupported → 非対応
unknown → 情報不足・不明

禁止：
- unknown → unsupported
- conditional → verified
- conflict → verified
- diagnosis未接続 → 利用不可

## 7. Historical / Current Separation
旧Plan、旧口座条件、終了CampaignをCurrentへ混ぜない。

特に購入時期で条件が異なるVariantはvalidity boundaryを明示する。

## 8. Campaign / Coupon
Base priceとは別Layer。
終了後はENDEDとして履歴化可能だが、通常価格へ残さない。

## 9. Evidence Requirements
公開上重要な変更には可能な限り以下を残す：
- source URL / document
- checked_at
- effective date
- status
- conflict note

## 10. Stop Condition
必要な値を公開するために推測、Web代替、類似Firmから補完、要約から再構築が必要になった場合は `HOLD_FOR_SOURCE`。
