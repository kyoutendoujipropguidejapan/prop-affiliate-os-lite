# PLATFORM × FIRM MAPPING VERIFICATION QUEUE

更新日：2026-08-26 JST
Status：PREIMPLEMENTATION VERIFICATION QUEUE
Production code changes：NONE

## 1. Purpose

Platform Detail / Firm Detail間の相互リンクを安全に作るため、Current Production reconciliation後にFirm × Platform mappingを確認する順序を定義する。

## 2. Mapping levels

### Level A — Firm-level verified
FirmがそのPlatformを利用していることを公式source / accepted Production dataで確認。

### Level B — Program / Plan-level verified
特定program / planがそのPlatformを利用していることを確認。

### Level C — Capability-level verified
特定Firm環境でEA、DOM、copy、market data、order type等が実際に有効かを確認。

Aが確認できてもB/Cを自動生成しない。

## 3. Verification order

Current Production reconciliation後：

1. 14 Firmのcurrent `planCatalog.platforms` displayをread-only inventory化
2. Official Firm page / purchase page / FAQでFirm-level mapping照合
3. Conflict / multiple-platform Firmを分離
4. Program / Plan mappingは必要なものだけ追加確認
5. Platform-specific capabilityはrelation notesとして別確認
6. accepted relationだけcross-link候補へ

## 4. Priority

Pilot selectionのために、まず利用Firm数が多い可能性のあるPlatformを優先するが、Display Stringから件数を推測して確定しない。

Priority inputs：
- verified Firm count
- beginner relevance
- current traffic opportunity
- Firm Detail cross-link value
- source clarity

## 5. Required fields

Conceptual mapping record：

- firmId
- platformId
- planId / programId nullable
- mappingLevel
- relationStatus
- officialSourceUrl / evidenceRef
- verifiedAt
- capabilityNotes
- caution

## 6. Conflict handling

例：Firm公式SiteではMT5、購入画面ではTradeLocker、FAQは旧情報など。

この場合：
- CONFLICT
- latest sourceだけを無条件採用しない
- purchase availability / account cohort / old-vs-new条件を確認
- cross-linkは解消までHOLD可能

## 7. Prohibited shortcuts

- Memoryからmapping作成
- 古いScreenshotだけで確定
- Platform一般仕様からFirm利用を推論
- Firm-level mappingを全Planへ展開
- Affiliate pageだけを唯一のofficial mapping根拠にする
- UnknownをUnsupportedへ変換

## 8. Output

Platform Pilot開始前に最低限：

- Pilot候補2 PlatformのFirm-level verified mapping
- relation conflict list
- unmapped / unknown list
- plan-level mapping必要性判断

Final Status：
`PLATFORM_FIRM_MAPPING_QUEUE_READY_AWAITING_CURRENT_PRODUCTION_RECONCILIATION`
