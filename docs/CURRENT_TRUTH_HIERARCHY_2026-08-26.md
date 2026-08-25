# CURRENT TRUTH HIERARCHY

更新日：2026-08-26 JST
位置づけ：Production統合前のTruth優先順位。GitHub Handoffと実Productionを混同しないための運用正本。

## 1. 優先順位

### T1｜Current Production Truth
OpenAI Sites managed repository上で実際に公開されているProduction実体を最優先とする。

中央管理上の最新確認はProduction Version 82。GitHub HandoffのVersion表記だけでProductionを巻き戻さない。

### T2｜Accepted Pending Local State
Work/Sites側で実装・検証済みだがremote未反映のaccepted commit。

既知pending：
- Evidence MVP `3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f`
- Fundora campaign `2191f06dc56006b4018f16ec8c2ac51161d2f70a`

これらはrebase / amend / squash / recreateしない。

### T3｜GitHub Handoff / Canonical補助
`kyoutendoujipropguidejapan/prop-affiliate-os-lite`

役割：
- Current State documentation
- Evidence / Schema
- Monitoring
- Work Spec
- Handoff
- Canonical補助

GitHubはProduction Application Sourceではない。

### T4｜Historical Baseline / Archived Artifacts
過去Version、旧資料、旧PDF、旧Zip等。
Current Truthへ自動昇格させない。

## 2. Conflict Rule

Production実体とGitHub要約が不一致の場合：
1. Production実体を確認
2. pending accepted stateを確認
3. GitHub Handoffを更新候補とする
4. GitHub要約だけを根拠にProduction Masterを変更しない

不一致が解消できない場合は `HOLD_FOR_RECONCILIATION`。

## 3. Work Start Gate

新規Production実装前に必ず確認：
- current Production version / commit
- pending local commits
- worktree clean
- origin authentication / read status
- protected hashes
- unknown production diff = 0

## 4. 禁止

- GitHub READMEのVersion表記だけでProductionを判断
- Historical artifactからCurrent dataを推測
- accepted pending commitの作り直し
- ProductionとHandoffを同一repositoryと仮定
- stale GitHub summaryでMasterを上書き

## 5. 現行統合順

Current Production正常化
→ Evidence / Fundora pending処理
→ Fundora release handling
→ Firm Detail Pilot
→ Firm Detail rollout
→ Platform
→ Payout Source到着後にPayout

この順番は中央承認なく前後させない。
