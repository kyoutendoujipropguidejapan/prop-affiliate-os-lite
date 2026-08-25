# WORK RESUME AFTER AUTH RECOVERY

更新日：2026-08-26 JST
Status：PREPARED / DO NOT EXECUTE UNTIL AUTH RECOVERS

Purpose：内部Repository認証復旧後に、Workが余計な実装へ進まず安全にCurrent Truthを一本化するための再開手順。

## 1. Entry condition

以下のどちらかのみ：
- Git認証復旧監視がrecoveryを検知
- OpenAI Supportから再試行可能と案内

それ以前はWorkを消費しない。

## 2. Phase A — Read-only verification

確認のみ：
- origin URL
- authentication status
- fetch/read status
- current branch
- local HEAD
- remote HEAD
- ahead / behind
- worktree clean

失敗時は即停止：`HOLD_AUTH_BLOCKER`

## 3. Phase B — Preserve accepted local history

必須commit：
- Evidence：`3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f`
- Fundora：`2191f06dc56006b4018f16ec8c2ac51161d2f70a`

禁止：
- amend
- rebase
- squash
- reset
- cherry-pickによるSHA変更
- force push

remoteがfast-forward可能な場合だけ既存historyのままpush。

## 4. Phase C — Post-push integrity

必須：
- local HEAD / remote HEAD整合
- accepted commitsがremoteに存在
- ahead / behind = 0 / 0
- worktree clean
- unknown diff = 0

## 5. Phase D — Production reconciliation

Central Command latest accepted reference：
- Production Version：82
- Production commit：`ee6a5d518d8d586f728466443e068c40105e4bee`
- RC fingerprint：`cb96556cd1be7bfd7902779f42dc45f641308cd028518acf3c1e894dc00177df`

Protected hashes：
- Master：`c7a8410696594592065caea226efce2a6e21af3a52fd35b2749e3b09965d6f8d`
- Diagnosis：`39b152e17889cbb7634062e369e3814300407de167ecfca70379910b76073169`
- GA4：`9b878d2243e35fa7b87653ea5319184f9f745b56abf27a254f2314660e593c34`

GitHub Handoffの旧Current StateをProduction Truthとして採用しない。

実ProductionがV82以降であることを確認し、曖昧なら：
`HOLD_BASELINE_AMBIGUOUS`

## 6. Stop point

この再開Workでは新規実装しない。

以下を行わない：
- Firm Detail
- Platform
- MT4 / MT5
- Payout
- sitemap
- GA4
- Master / Diagnosis
- Version保存
- Production publish

成功Status：
`REPOSITORY_RECOVERED_AND_RECONCILED`

成功してもここで停止しCentral Commandへ返す。