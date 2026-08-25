# INTERNAL REPOSITORY AUTH BLOCKER RUNBOOK

更新日：2026-08-26 JST
Status：ACTIVE BLOCKER / NO PRODUCTION CHANGE

## 1. Blocker

対象：OpenAI Sites / ChatGPT Work internal repository

Remote：
`https://git.chatgpt-team.site/b8e60e22-a89f-4055-acd6-a90f434f0dd3/appgprj_6a538c9ce048819186407c56b6315d14.git`

再現済みエラー：
`fatal: could not read Username for 'https://git.chatgpt-team.site': terminal prompts disabled`

新規Work conversationでも同一エラーを再現済み。

## 2. Preserved local state

- branch：main
- local HEAD：`2191f06dc56006b4018f16ec8c2ac51161d2f70a`
- worktree：clean
- Evidence accepted commit：`3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f`
- Fundora accepted commit：`2191f06dc56006b4018f16ec8c2ac51161d2f70a`
- last known ahead / behind：2 / 0

この2 commitはSHAを変更せず保持する。

## 3. Prohibited recovery actions

禁止：
- origin URLの通常GitHubへの変更
- PAT / SSH keyの独自投入による回避
- rebase
- amend
- squash
- reset
- cherry-pickでcommit再作成
- force push
- unrelated repositoryへのcommit移植
- Production publish
- Version保存

## 4. User-side / support path

同一エラーを新規Workでも再現したため、単一Work session依存ではない。

推奨：OpenAI Supportへinternal repository authentication / credential injectionの再provisioningを依頼。

Supportへ伝える必須情報：
- internal remote URL
- exact error全文
- local HEAD
- preserved accepted commit SHAs
- worktree clean
- normal GitHub accessは正常
- new Work conversationでも再現
- repository historyをreset/rewriteしないでほしい旨

## 5. Retry policy

手動Work retryを連続実行しない。

既存のGit認証復旧監視でmaterial change / recoveryを待つ。

次のWork実行条件：
- authentication recovered signal
- またはOpenAI Supportから再試行指示

## 6. Recovery verification

復旧時は最初にread-onlyで以下を確認：
- origin URL
- authentication
- fetch/read
- current branch
- local HEAD
- remote HEAD
- ahead / behind
- worktree clean

認証復旧確認前にpushしない。

## 7. Recovery success path

認証PASS後：
1. fetch
2. remote history確認
3. accepted local commitsがfast-forwardで安全に反映可能か確認
4. Evidence → Fundoraの既存順序を維持してpush
5. local/remote SHA一致
6. ahead / behind = 0 / 0
7. worktree clean
8. Production再照合
9. そこで停止しCentral Commandへ報告

## 8. Current operational status

`HOLD_AUTH_BLOCKER`

Production / local accepted commitsに変更なし。