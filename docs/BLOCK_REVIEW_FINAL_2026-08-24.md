# Block Review Final 2026-08-24

確認日：2026-08-24 JST
目的：Hantec Instant Lite以外の現行Block候補を、次回Workパッチ前に最終固定する。

この文書だけでMaster / Diagnosisを自動更新しない。DiagnosisLogicV2は変更禁止。

## 0. 最終結論

次回パッチ後のBlock候補は5件。

1. Fintokei｜速攻プロ — KEEP_BLOCK
2. Funded7｜1フェーズ — KEEP_BLOCK
3. Funded7｜Instant — KEEP_BLOCK
4. Funded Trader Markets｜Instant Pro — KEEP_BLOCK
5. FundedElite｜Flash Activation — KEEP_BLOCK

Hantec Trader｜Instant Liteは別仕様書によりSH003 RESOLVED_FOR_PATCH / unblock候補。

## 1. Fintokei 速攻プロ

### 現行公式

2026-07-15以降購入：

- Profit Target 6%
- Daily Loss 2%
- Overall Loss 3%
- Minimum Trading Days 3
- Evaluation maximum period 60 days
- new profit-day restrictionあり

2026-07-15より前購入：

- Profit Target / rule setが別世代
- Daily Loss 3%
- Overall Loss 6%
- Minimum Trading Days 5
- maximum periodなし

### 判定

公式競合ではなく、購入日で明示的に分かれた世代Variant。

しかし現在のDiagnosis runtimeはユーザーの口座購入日 / rule generationを安全に判定しない。

**KEEP_BLOCK**。

将来、`effective_from + purchase_date + legacy/new variant`をruntimeで保持できる場合のみconditional unblockを再検討する。

## 2. Funded7 1フェーズ

### 公式内の現在値

FAQ：

- Profit Target 10%
- Daily Loss 4%
- Max Total Loss 8%
- Min 3 days + 10 trades

Challenges comparisonも4% / 8% / Profit Split 80%を示す。

一方、現行商品ページ：

- Profit Target 10%
- Daily Loss 5%
- Max Total Loss 10%
- Profit Split 50%
- Trailing

### 判定

同一現行プランについてscoring-criticalなDaily / Max LossとProfit Splitが公式内で不一致。

**KEEP_BLOCK**。

商品ページとFAQが収束するか、公式回答で適用世代 / checkout条件が特定できるまで一本化しない。

## 3. Funded7 Instant

### 公式内の現在値

英語FAQ：

- Daily Loss 5%
- Max Total Loss 6%
- Profit Split 50%

日本語FAQ：

- Daily / TotalはOREFの口座tierに従う

Challenges comparison：

- Max Total Loss 6%（またはtier依存）
- Daily 5%（またはtier依存）

商品ページ：

- Daily Loss 5%
- Max Total Loss 10%
- Profit Split 50/50
- Trailing

### 判定

Max Lossが6% / tier依存 / 10%で公式内不一致。OREF適用範囲の正確な世代・tier mappingが必要。

**KEEP_BLOCK**。

6% / 8% / 10%等の歴史値を削除して1つに寄せない。

## 4. Funded Trader Markets Instant Pro

### 公式内の現在値

専用FAQ：

- Maximum Daily Drawdown 3% of initial balance

現行variation / comparison matrix：

- Daily Drawdown 3%
- Overall Drawdown 3%

一方、Instant Funding紹介コピー：

- Instant Proを「no Daily Drawdown Limit」と説明する箇所が残る

### 判定

詳細FAQ / matrixは3%へ強く収束しているが、同じ公式導線上に「no Daily DD」が残っている。

Daily DDは失格に直結するため、安全側で**KEEP_BLOCK**。

紹介コピーが修正されるか、公式から優先ルール回答が得られるまで解除しない。

## 5. FundedElite Flash Activation

### 公式内のBase FAQ

商品ページ内FAQ / 専用FAQ：

- Base Profit Target 6%
- Daily DD 3%
- Total DD 6%
- Evaluation DD static
- Evaluation minimum daysなし
- Live: DD trailing
- Live minimum 3 profitable days（各0.5%以上）
- Live consistency 30%
- Profit Split 80%
- Payout 14 days

### Marketing / customization

同じ商品ページ上部では：

- target as low as 2%
- up to 95% profit split
- instant payouts
- customizable rules

と訴求される。

これ自体はBaseとAdd-on / customizationの違いで説明できる可能性が高いが、現在のMasterにはvariant/add-on mappingが不足している。

### 判定

Baseルールはかなり明確になったが、診断へ単一行として接続するとcustomized variantへ誤適用する可能性がある。

**KEEP_BLOCK**。

解除条件：

- base variantを明示的に独立
- target / split / payout等のcustom option mappingを別フィールド化
- checkoutまたは公式FAQで各optionの適用条件を確認

## 6. 次回Workパッチ後の見込み

Blue Guardian patch + Hantec patchを適用した場合：

- PlanCatalog：69 → 72
- Blue Guardian 3 Step：Legacy化
- Blue Guardian Nano x2 + BNPL：Active catalog追加、Diagnosis未接続
- Diagnosis rows：65 → 64
- Hantec Instant Lite：既存Diagnosis rowをVerified化 / unblock候補
- Block：6 → 5

残るBlock 5は本書の5件。

件数維持を目的に未確認プランをDiagnosisへ接続しない。

## 7. Status

- Remaining Block review: COMPLETE
- Keep Block: 5
- Hantec SH003: RESOLVED_FOR_PATCH
- Blue Guardian patch: READY_FOR_REVIEW
- Work data patch: READY_TO_SPEC
- Master write: NOT_STARTED
- Diagnosis write: NOT_STARTED
