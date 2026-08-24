# プロップファームの歩き方｜進捗

更新日：2026-08-24 JST

## 完了

- M01〜M16：完了記録あり
- Work Day0監査：完了
- M07 P0-01〜P0-08：実装・検証完了
- M14 FAQ統合：完了
- 価格境界修正：完了
- GA4整理：完了 / 実送信のみCaution
- SEO必要分統合：完了
- ER-01 remediation：完了
- M08 Full Regression：PASS_WITH_CAUTION
- Firm → Plan Selector：実装・検証完了
- Version 80：本番公開済み
- Graphic Style Refinement：implementation COMPLETE / PASS_WITH_CAUTION
- SourceHealth recheck 2026-08-24：REVIEWED / PATCH_SPEC_READY

---

## 本番

- Production = **Version 80**
- Firm 14社
- PlanCatalog 69
- Firm → Plan → Detail 3段階Selector公開済み
- Firm紹介 14/14
- プラン一言紹介 69/69
- Diagnosis 7問 / DiagnosisLogicV2変更なし
- Price / Couponは後段のまま

※ 未公開Workのグラフィック4点はまだ本番へ反映していない。

---

## 未公開Graphic Work

4点を都会・日常・プロップファーム / トレード文脈へ差し替え済み：

- learning-path.webp
- diagnosis-flow.webp
- firm-compare.webp
- selector-flow.webp

検証：

- 1363px fresh PASS
- regression 46/46 PASS
- build PASS
- lint error 0 / existing warning 1
- git diff --check PASS
- console error 0
- BLOCKER 0 / CRITICAL 0
- DiagnosisLogicV2 / Master / GA4 / Sitemap hash不変
- 390px fresh実画面：NOT_EXECUTABLE

判定：**Graphic Style Refinement = PASS_WITH_CAUTION**

Cautionは390px実画面未確認のみ。

---

## SourceHealth再評価

判断記録：`docs/SOURCEHEALTH_RECHECK_2026-08-24.md`

### Block継続

- Fintokei｜速攻プロ
- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- FundedElite｜Flash Activation

### Block解除候補

- Hantec Trader｜Instant Lite
  - 標準 Max Loss 5%
  - Add-on +1%
  - Master整理 + 回帰後にunblock候補

### Blue Guardian

- 1 Step Crypto：listed-only / HOLD維持
- 1 Step Pro：Legacy維持
- 3 Step：Legacy変更候補 / Diagnosis除外候補
- 1 Step Nano：Active catalog追加候補 / 初回Diagnosis未接続
- 2 Step Nano：Active catalog追加候補 / 初回Diagnosis未接続
- BNPL：Active catalog追加候補 / 初回Diagnosis未接続

Blue Guardian 3 Stepは、現行Masterのcurrent扱いと現行公式専用ページのLegacy表記が一致しないため、次回データパッチ最優先。

---

## 次回データパッチ見込み

Blue Guardian 3 StepをLegacy化し、Nano 2件 + BNPLをcatalogへ追加する場合：

- PlanCatalog 69 → 72
- current plan families 65 → 67
- legacy / ended 3 → 4
- listed-only 1維持

新規3モデルを初回Diagnosisへ接続しない場合：

- Diagnosis rows 65 → 64

Hantec Instant Liteを回帰後にunblockした場合：

- Block 6 → 5

3 StepのLegacy不整合をSourceHealth履歴へ追加する場合：

- SourceHealth 14 → 15

件数維持のためだけに新規PlanをDiagnosisへ接続しない。

---

## 現在のGate

### Graphic

- implementation = COMPLETE
- Final Verification = PASS_WITH_CAUTION
- 390px = NOT_EXECUTABLE
- Version保存 / publish = 未実施

### SourceHealth / Master

- Recheck = REVIEWED / PATCH_SPEC_READY
- Master update = NOT_STARTED
- Diagnosis data update = NOT_STARTED
- DiagnosisLogicV2 update = NOT_REQUIRED / PROHIBITED
- Work implementation = NOT_STARTED

### Monitoring / Runtime

- Monitoring Dry Run = NO-GO
- Runtime Snapshot = NO-GO

---

## 次

Workへ調査をさせず、Chat / GitHubで以下を先に確定する。

1. Blue Guardian 1 Step Nano / 2 Step Nano / BNPLのMaster必須フィールド
2. 日本居住者Eligibility
3. platform
4. news trading
5. weekend holding
6. payout timing / first payout
7. consistency
8. drawdown type / calculation timing
9. source URLs / checked_at
10. Hantec Instant Lite Add-onの最終表現

確定後、Workへ渡すのは**最小データ差分仕様のみ**。

Graphic本番反映とSourceHealth / Master更新は別Gateで扱う。
