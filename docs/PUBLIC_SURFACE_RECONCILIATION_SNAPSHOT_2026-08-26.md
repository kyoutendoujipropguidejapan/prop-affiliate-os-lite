# PUBLIC SURFACE RECONCILIATION SNAPSHOT

確認日：2026-08-26 JST
対象：`https://kyouten-prop-guide.utsr.chatgpt.site`
Status：PUBLIC SIGNAL ONLY / NOT PRODUCTION CANONICAL
Production code changes：NONE

## 1. Purpose

公開サイトを外部crawlでread-only確認し、GitHub Handoff・既知のProduction記録・pending local commitsとの差分確認に使う。

重要：このSnapshotはPublic Surfaceの観測結果であり、OpenAI Sites Production Repository / Version / commitの正本ではない。

## 2. Observed public surface

外部crawlで確認できた表示：

- `14社 · 72プラン`
- Firm selector / Diagnosis導線あり
- Fintokeiの取引環境表示に `MT4 / MT5 / cTrader / TradingView`
- Fintokei速攻プロは公開画面上で `公式情報を確認中` として表示
- 速攻プロは診断Top3から除外する旨の注意表示あり
- Fintokei FAQにはM14 U01系の現行プラン説明が表示されている
- coupon / campaign update historyへの導線あり
- Affiliate disclosure footerあり
- footer `情報更新日 2026-08-24`

## 3. Important signals requiring authoritative reconciliation

### A. Fundora time-limited campaign

Public crawlでは文字列 `初挑戦応援キャンペーン` を確認できなかった。

これは次のどれかを意味し得るが、このSnapshotでは決定しない：

- Fundora local commitがまだProduction未反映
- crawl surfaceがdynamic contentを取りこぼしている
- route / section位置がcrawl対象外
- Production baselineが想定と異なる

Authoritative Production repo確認まで `PUBLIC_NOT_OBSERVED` とする。`NOT_DEPLOYED` と断定しない。

### B. Fintokei Academy

Public crawlでは文字列 `Fintokei Academy` を確認できなかった。

同様に `PUBLIC_NOT_OBSERVED` とし、Production repo / actual iPhone browser確認前に削除・未実装と断定しない。

### C. Fintokei Sokkou Pro

Public crawlでは速攻プロに旧Conflict-style表示が残っている：

- Profit Target：公開FAQ 10% / 8月案内 6%
- Daily Loss：公開FAQ 3% / 8月案内 2%
- Max Loss：公開FAQ 6% / 8月案内 3%固定
- Minimum Trading Days：公開FAQ 5日 / 8月案内 最短3日

一方、GitHub HandoffにはM14で2026-07-15以降新規購入口座の限定Variant再確認記録がある。

この差はCurrent Truth reconciliation対象。Public crawlだけでどちらをcanonicalにしない。

## 4. Compliance observation

Public footerにはAffiliate relationと診断順位非影響のDisclosureが確認できた。

ただし今後のCompliance BaselineではGlobal footerだけではなく、Affiliate CTA / Sponsor / provided accountの該当箇所近くでも明瞭なDisclosureを要求する。

したがって現行footerの存在だけでSite-wide Compliance PASSとはしない。

## 5. Platform signal

Public surfaceで少なくともFintokeiに `MT4 / MT5 / cTrader / TradingView` displayがあることを確認。

これはMT4 / MT5をCanonical Platform scopeへ追加したArchitecture Decisionの妥当性を補強するSignalだが、Firm × Platform canonical relationを自動生成する根拠にはしない。

## 6. Required Work reconciliation when auth recovers

Read-only first：

1. actual current Production Version / SHA
2. latest Production source tree
3. public route source
4. Evidence commit presence
5. Fundora commit presence
6. Academy-related files / routes
7. Fintokei Sokkou Pro current source values/status
8. current protected hashes
9. branch ahead / behind
10. worktree clean

差分が説明できるまで新規Firm Detail implementationを開始しない。

## 7. Stop rule

Public crawl / GitHub Handoff / local accepted commits / Production repoのいずれかが矛盾した場合：

`RECONCILIATION_REQUIRED`

として、推測でCurrent Truthを選ばない。

Final Status：
`PUBLIC_SURFACE_SIGNAL_CAPTURED_RECONCILIATION_REQUIRED_BEFORE_NEW_IMPLEMENTATION`
