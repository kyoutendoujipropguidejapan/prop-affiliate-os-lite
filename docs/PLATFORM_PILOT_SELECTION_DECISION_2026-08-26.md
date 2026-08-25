# PLATFORM PILOT SELECTION DECISION

更新日：2026-08-26 JST
Status：CONTENT PILOT DECISION / IMPLEMENTATION HOLD
Production code changes：NONE

## 1. Decision

Platform Pilotの事前候補を以下とする：

1. MT5
2. TradeLocker

MT4はCanonical Platformとして保持するが、初回Pilotの2ページには入れない。

## 2. Why MT5

MT5はProp Firm文脈で重要な比較基準として扱いやすく、Platform Hubの基準点になる。

ただし、Firm固有の以下はPlatform一般仕様から推測しない：
- EA利用可否
- copy trading
- symbols
- leverage
- execution
- server
- plugins
- account permissions

## 3. Why TradeLocker

TradeLockerはMT5と利用体験・配布形態・UIの性格が異なり、Pilotで共通Templateが異なるPlatformにも耐えられるか検証しやすい。

Vendor一般仕様とFirm固有実装は分離する。

## 4. Why not MT4 in Pilot

MT4はCanonicalとして残すが、初回PilotではMT5との重複が大きい。

初回2ページの目的は網羅ではなく、Template / relation / mobile / SEO / complianceの差分検証。

MT4はPilot PASS後のearly rollout候補。

## 5. Implementation gate

この決定はContent / Architecture上の優先候補であり、Production実装承認ではない。

実装前に必須：
- internal Git auth recovered
- accepted pending commits normalized
- Current Production reconciliation PASS
- Firm Detail Pilot PASS
- Firm × Platform mapping verified
- route collision check
- current Platform source freshness check

Firm mappingが確認できなければPlatform → Firm一覧を推測表示しない。

## 6. Expected Pilot

- `/platforms/`
- `/platforms/mt5/`
- `/platforms/tradelocker/`

初回公開ではランキングを作らない。

比較軸：
- access / device pattern
- chart / order workflow
- automation concept where officially verified
- beginner terminology
- Firmごとに変わる事項

## 7. Commercial boundary

Platformページ自体にAffiliate順位を持ち込まない。

Firm CTAへ接続する場合でも、verified Firm mapping + Firm page existing + disclosureが揃った時だけ有効化。

Final Status：
`PLATFORM_PILOT_MT5_TRADELOCKER_SELECTED_PENDING_GATES`