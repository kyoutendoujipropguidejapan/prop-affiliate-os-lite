# WORK RE-ENTRY RECONCILIATION PROMPT

更新日：2026-08-26 JST
Status：READY TO USE AFTER INTERNAL GIT AUTH RECOVERY
Production code changes：NONE

以下をWork/Codexへ最初に渡す。新規実装タスクではない。

---

Repository認証復旧後の再入場確認だけを行ってください。

## Objective

Current Production / internal remote / accepted local commits / public surfaceのCurrent Truthを確定する。

このタスクでは新機能実装、refactor、Version保存、Production publishを行わないでください。

## Preserve exactly

既存accepted local commitsを変更しない：

- Evidence: `3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f`
- Fundora: `2191f06dc56006b4018f16ec8c2ac51161d2f70a`

禁止：
- amend
- rebase
- squash
- cherry-pick into unrelated history
- recreate
- force push

## Read-only first

最初に報告：

1. origin URL
2. authentication status
3. fetch/read status
4. current branch
5. local HEAD SHA
6. remote HEAD SHA
7. ahead / behind
8. Worktree clean / dirty
9. current Production Version if repository metadata exposes it
10. protected-file hashes

## Reconciliation targets

確認する：

- Evidence commitがremoteに存在するか
- Fundora commitがremoteに存在するか
- Fundora `初挑戦応援キャンペーン` sourceがcurrent treeに存在するか
- Fintokei Academy関連source / routeがcurrent treeに存在するか
- Fintokei速攻プロのcurrent source values / status
- 14 Firm / 72 Plan data baseline
- current sitemap/routes
- current regression baseline

参考Signal：
`docs/PUBLIC_SURFACE_RECONCILIATION_SNAPSHOT_2026-08-26.md`

ただしPublic crawlはcanonicalではない。

## Current Truth rule

Priority：

1. actual OpenAI Sites Production / managed repository state
2. accepted local pending commits
3. ordinary GitHub Handoff documents
4. historical artifacts

GitHub HandoffのV81/V78表記でProductionを巻き戻さない。

## Do not implement yet

このreconciliation taskでは以下を開始しない：

- Firm Detail Pilot
- Platform Registry
- Platform routes
- Payout
- Analytics changes
- SEO rollout

## Stop conditions

以下ならその場で停止：

- auth failure
- fetch failure
- current Production baseline不明
- unknown remote history divergence
- accepted commit historyが想定外
- protected hash unexpected change
- worktree dirty with unknown files

## Final status

問題なくCurrent Truthを確定できた場合：
`PRODUCTION_RECONCILIATION_READY`

問題がある場合：
`HOLD_RECONCILIATION_BLOCKER`

報告だけして終了。push / publishはCentral Commandの次指示まで行わない。
