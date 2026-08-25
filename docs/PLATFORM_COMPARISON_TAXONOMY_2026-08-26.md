# PLATFORM COMPARISON TAXONOMY

更新日：2026-08-26 JST
Status：COMPARISON CONTRACT CONFIRMED
Production code changes：NONE

## 1. Principle

Platform比較はランキングではなく、初心者が「自分が確認すべき差」を理解するための教育機能とする。

## 2. Allowed comparison dimensions

Evidenceがある場合に比較可能：

- access_surface：desktop / web / mobile
- chart_workflow
- order_entry_model
- supported_order_concepts
- DOM / market-depth capability
- volume / order-flow analysis capability
- algorithmic / EA environment at vendor level
- copy capability at vendor level
- connection model
- market-data / entitlement model
- customization / workspace model
- vendor-level Japanese UI/documentation

## 3. Two-level rule

比較値は必ず2層に分ける。

### Vendor-level
Platform一般仕様として公式sourceで確認した内容。

### Firm-level
特定Firmで実際に有効な機能・permission・data・connection。

`Vendor capability != Firm enabled capability`

## 4. Status values

- VERIFIED
- CONDITIONAL
- UNVERIFIED
- UNSUPPORTED
- UNKNOWN

UnknownをUnsupportedへ変換しない。

## 5. Prohibited comparison labels

Evidenceなしで禁止：

- 最強
- 一番使いやすい
- 一番速い
- 約定最速
- 最も安全
- 最も信頼できる
- 初心者No.1
- プロ向けNo.1
- 失格しにくい
- 勝ちやすい

## 6. Vendor marketing claim handling

Vendorがfast / low latency / professional / secure / best等と表現していても、比較表では独立検証済み性能値として扱わない。

必要なら：
`Vendor states ...`相当のattribute付き内部Evidenceとして保持し、公開比較値には原則使用しない。

## 7. Platform-specific cautions

- MT4 / MT5：EA / copy機能がPlatformに存在してもFirm ruleで許可されるとは限らない
- Match-Trader：vendor Japanese language supportとFirm表示範囲を分離
- DXtrade：white-label configuration差が大きい
- BlackArrow：Platform / Broker / Prop Firmの役割を分離
- Quantower：license / connectionで機能差
- Volumetrica：server-side rollout差
- TradeLocker / cTrader：Firm-specific symbols / permissions / executionを一般化しない

## 8. Future compare page

Future route：`/platforms/compare/`

最初のPilotでは必須ではない。

比較ページを公開する場合：
- mobile table strategy
- horizontal overflow control
- status legend
- checked date
- source/evidence note
- no affiliate ranking influence

が必須。

Final Status：
`PLATFORM_COMPARISON_TAXONOMY_CONFIRMED`
