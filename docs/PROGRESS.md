# プロップファームの歩き方｜進捗

更新日：2026-08-25 JST

## 完了

- M01〜M16：完了記録あり
- Work Day0監査：完了
- M07 P0-01〜P0-08：実装・検証完了
- M14 FAQ統合：完了
- 価格境界修正：完了
- GA4整理：完了 / 実送信のみCaution
- SEO必要分統合：完了
- ER-01 remediation：完了
- Firm → Plan Selector：完了
- Version 80：公開済み / rollback保持
- Graphic Style Refinement：COMPLETE
- SourceHealth recheck：COMPLETE
- Blue Guardian / Hantec Data Patch：PASS
- Release Candidate Final Verification：PASS_WITH_CAUTION
- **Version 81 Production Release：COMPLETE**
- Post-release price / SEO gap audit：COMPLETE

## Production V81

- HTTP 200
- Firm 14
- PlanCatalog 72
- Current 67
- Legacy / ended 4
- Listed-only 1
- Diagnosis 64
- Block 5
- SourceHealth 16
- Graphic 4点公開済み
- Blue Guardian / Hantec / Diagnosis / Graphic smoke PASS
- 新規BLOCKER / CRITICAL 0

390px実画面は既知NOT_EXECUTABLE。Production実iPhone確認待ち。

## Post-release gap audit

正本：`docs/POST_RELEASE_GAP_AUDIT_2026-08-25.md`

### 価格確認中2件

公式再確認済み：

- The5ers Futures Day Trade：25K $59
- Blueberry Futures Accelerated：25K $129 / 50K $184 / 100K $276 / 150K $454

未実装。次Workの最小patch候補。

### Remaining rule conflicts

KEEP_BLOCK：

1. Fintokei 速攻プロ
2. Funded7 1フェーズ
3. Funded7 Instant
4. FTM Instant Pro
5. FundedElite Flash Activation

その他：

- Blue Guardian 1 Step Crypto = listed-only / HOLD
- Blue Guardian BNPL = Active WITH_CAUTION / Diagnosis未接続

## SEO snapshot

broad queryでは競合comparison / ranking / beginner guideが強い。

long-tail `プロップファーム 1ステップ 2ステップ 違い` では当サイト `/one-step-two-step-instant` の検索露出を確認。

次のSEO方針：

1. rule-first long-tail clusterを強化
2. title / metaはGSC CTR確認後に調整
3. price intentをbase / campaign / coupon分離で強化
4.既存7記事の内部リンク / FAQ / freshnessを強化
5. main siteとManus firm専門サイトのcannibalizationを避ける

## Analytics Gate

GA4 / GSC実データ未取得。

実データ取得後に：

- high impressions / low CTR
- high views / low diagnosis completion
- organic landing pages
- query position
- beginner → diagnosis遷移

を使って改善順を決める。

## 次

P0：

- Price未確認2件の最小patch
- V81 public SourceHealth / 確認中一覧のfresh整合確認
- 390px実iPhone確認

P1：

- GSC / GA4接続後の実閲覧・検索分析
- SEO title / meta / internal links / content refresh
- high-opportunity page優先改善

新規機能追加を先にしない。
