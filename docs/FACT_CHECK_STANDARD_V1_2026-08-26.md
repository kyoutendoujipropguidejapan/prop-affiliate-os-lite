# FACT CHECK STANDARD v1

更新日：2026-08-26 JST
Status：APPROVED OPERATING STANDARD
Scope：プロップファームの歩き方 全体

## 0. Purpose

公開・実装・Canonical昇格・HOLD解除に使う事実について、最低3回のファクトチェックを必須化する。

このルールは Firm / Plan / Platform / Payout / Coupon / Campaign / FAQ / Review / Case Study / B2B / Compliance / SEO fact / Evidence / Canonical Fact に適用する。

## 1. Minimum Three-Check Rule

重要Factは最低3回のチェックを完了するまで、最終確定値として公開・実装・Canonical昇格しない。

### Check 1 — Primary Source Verification

- 公式サイト
- 公式FAQ / Help Center
- 公式Terms / Rules
- 公式購入画面
- 公式PDF
- 直接担当者からの一次回答

のいずれかで対象Factを確認する。

記録：
- source URL / source type
- checked_at
- exact scope（Firm / Plan / Variant / cohort / locale）
- 対象値
- Evidence ID（存在時）

### Check 2 — Independent Reconciliation

Check 1と同じ結論を、可能な限り別の一次情報または別導線で再照合する。

優先：
1. 別の公式一次ページ
2. Terms / Rules / checkout / dashboard表示
3. 公式サポート回答
4. 同一公式ページの別locale / dedicated article

Check 1と同一ページを単に読み直すだけでは、原則として独立Checkと数えない。

別の一次情報が存在しない場合は、`SINGLE_SOURCE_LIMITATION`を付け、Check 2を「scope / date / cohort / wordingの独立再解析」として記録する。高リスクFactではこの状態のまま完全VERIFIEDへ上げない。

### Check 3 — Pre-Publication / Pre-Implementation Fresh Recheck

公開・実装・Canonical昇格・HOLD解除の直前に、対象Factが現在も有効かfresh recheckする。

必須確認：
- source still accessible
- value unchanged
- effective date / cohort unchanged
- locale差なし
- campaign expiry / coupon expiry
- legacy/current混同なし
- official conflictの新規発生なし

Check 1/2から時間が空いた場合でも、Check 3は省略しない。

## 2. Three Checks ≠ Three Random Websites

3回チェックは、検索結果を3サイト集めることではない。

優先順位：
`official primary > official secondary > direct contact > regulator / authoritative source > corroboration`

Affiliate blog / aggregator / social postだけを3件集めてもVERIFIEDにしない。

## 3. High-Risk Facts

以下は最低3回に加えて、可能な限り複数の独立一次根拠を要求する。

- Daily Loss / Max Loss / Trailing DD
- payout eligibility / refusal condition
- profit split
- account termination / breach condition
- Japan eligibility
- service nature / regulatory status
- KYC / payment / withdrawal
- security / data incident
- campaign discount / expiry
- coupon eligibility
- HOLD release
- regulatory warning

競合が1件でも残る場合：`CONFLICT` / `HOLD`を維持する。

## 4. HOLD Release Gate

HOLD解除には最低：

1. Check 1 PASS
2. Check 2 PASS
3. Check 3 PASS
4. 元Conflictの説明が完了
5. Variant / cohort / locale差が明示
6. Evidence / SourceHealth更新案
7. human approval

を要求する。

3回確認だけでHOLDを自動解除しない。

## 5. Canonical Fact Gate

Canonical Fact昇格に必要：

- `fact_check_count >= 3`
- `check_1_status = PASS`
- `check_2_status = PASS or PASS_WITH_SINGLE_SOURCE_LIMITATION`
- `check_3_status = PASS`
- `verified_at`
- `source_evidence_ids`
- `scope`
- `effective_from / effective_to` when relevant
- structured human approval

高リスクFactで`SINGLE_SOURCE_LIMITATION`が残る場合は、`VERIFIED_WITH_CAUTION`以下に留める。

## 6. Conflict Rule

3回のうち1回でも現行公式情報とのMaterial Conflictを発見した場合：

- 多数決しない
- newest-looking pageだけで決めない
- Marketing copyをRulesより自動優先しない
- locale差を誤差扱いしない
- Human reviewへ上げる

Status：`CONFLICT` / `HOLD`。

## 7. AI / Work Boundary

AIは3回のチェック実施・比較・Evidence整理を補助できる。

禁止：
- AI単独でHOLD解除
- AI単独でCanonical最終承認
- 3回未満でVerified化
- 3つの二次情報だけで一次Fact扱い
- source unavailableを推測補完

Workは実装前に、対象変更のCheck 3がfreshであることを確認する。

## 8. Publication Gate

公開前Acceptanceに以下を追加する。

- fact_check_count >= 3
- high-risk facts unresolved conflict = 0
- stale fact = 0 or clearly labeled
- HOLD auto release = 0
- source / scope / effective period preserved

未達なら：`FACT_CHECK_HOLD`。

## 9. Effective Decision

2026-08-26以降、新規Factおよび変更Factに本Standardを適用する。

既存公開Factを一括で即時再検証するのではなく、更新・再公開・Firm Detail展開時に最低3回ルールへ順次移行する。

Final Status：
`APPROVED_MINIMUM_THREE_FACT_CHECKS_REQUIRED`
