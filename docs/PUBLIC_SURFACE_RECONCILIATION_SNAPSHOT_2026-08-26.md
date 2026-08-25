# PUBLIC SURFACE RECONCILIATION SNAPSHOT

確認日：2026-08-26 JST
対象：`https://kyouten-prop-guide.utsr.chatgpt.site`
Status：PUBLIC SIGNAL ONLY / MULTIPLE CRAWL VARIANTS OBSERVED / NOT PRODUCTION CANONICAL
Production code changes：NONE

## 1. Purpose

公開サイトを外部crawlでread-only確認し、GitHub Handoff・既知のProduction記録・pending local commitsとの差分確認に使う。

重要：このSnapshotはPublic Surfaceの観測結果であり、OpenAI Sites Production Repository / Version / commitの正本ではない。

## 2. Observed public surface — crawl variants

2026-08-26の複数crawlで、同一Homeについて異なる表示snapshotが返った。

### Observation A

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

### Observation B — later public crawl/index snapshot

別のcurrent crawlでは：

- `14社 · 69プラン`
- Home-level `更新 2026.08.14`
- Fintokei速攻プロは依然として旧/new Conflict-style表示
- FTMは依然として `日本語対応予定`
- footer/page-level表示も `2026-08-14` または古いsection dateを含む

さらに別の検索index snapshotではHomeの旧構成：
- `情報確認 2026.08.02`
- Current Pick `VERIFIED 2026.08.01`
- footer `掲載内容は2026年8月2日時点の確認情報を含みます`

が返っている。

### Interpretation

これらの差は、少なくとも以下のどれかを含み得る：

- search index/cache差
- dynamic rendering差
- crawl取得時点差
- current Productionの複数surface/cache propagation

したがって：

- `72 -> 69` をProduction上の実削除と断定しない
- footer date差をVersion確定根拠にしない
- public crawler/countをProduction source truthにしない

Status：`PUBLIC_CACHE_OR_RENDER_DIVERGENCE`

Authoritative reconciliationでは actual Production source + current browser rendering を優先する。

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

2026-08-26の遡及3重公式確認では、これは現行公式間の未解決競合ではなく purchase-date cohort difference として整理できた：

- 2026-07-15以降購入：6% / Daily2% Equity / Max3% Static / min3 evaluation days
- 2026-07-15より前の対象口座：旧10% / 3% / 6% / 5日

従ってpublic sourceが実際にこのConflict表示を保持しているなら、Production reconciliation後の修正候補。

ただしPublic crawlだけを根拠に source code変更は行わない。

### D. FTM Japanese support

Later public crawl still renders `日本語対応予定`。

Current official FTM Japanese FAQ / Payments / Terms / variations surfaces are live, so actual Production sourceに同文言が存在する場合は `CORRECTION_REQUIRED`。

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
3. actual current rendered Home in browser
4. actual Firm count / Plan count from source, not crawler snippet
5. Evidence commit presence
6. Fundora commit presence
7. Academy-related files / routes
8. Fintokei Sokkou Pro current source values/status
9. FTM Japan-support source wording
10. current protected hashes
11. branch ahead / behind
12. worktree clean

差分が説明できるまで新規Firm Detail implementationを開始しない。

## 7. Stop rule

Public crawl / GitHub Handoff / local accepted commits / Production repoのいずれかが矛盾した場合：

`RECONCILIATION_REQUIRED`

として、推測でCurrent Truthを選ばない。

Final Status：
`MULTIPLE_PUBLIC_SURFACE_VARIANTS_CAPTURED_RECONCILIATION_REQUIRED_BEFORE_NEW_IMPLEMENTATION`
