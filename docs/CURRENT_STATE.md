# CURRENT_STATE

確認基準日：2026-08-25 JST

## Production

- 公開サイト：`https://kyouten-prop-guide.utsr.chatgpt.site`
- Production：**Version 81**
- V80：rollback用として保持
- V81はGraphic + Data Patch統合Release Candidateをfingerprint一致確認後に公開
- 公開直前fingerprint：`83a32d0118ced8415e323e5fb3580ebb39d6b066c6242f68a6bbd6eb7deac910`
- Production起動：HTTP 200
- 公開後追加変更：0件
- 新規BLOCKER / CRITICAL：0 / 0

## V81 actual data

- Firm = 14
- PlanCatalog = 72
- Current = 67
- Legacy / ended = 4
- Listed-only = 1
- Diagnosis rows = 64
- Block = 5
- SourceHealth = 16

### Blue Guardian

- P042 3 Step：Legacy / Diagnosis除外
- P070 1 Step Nano：Active / Diagnosis未接続
- P071 2 Step Nano：Active / Diagnosis未接続
- P072 BNPL：Active WITH_CAUTION / Diagnosis未接続
- P045 1 Step Crypto：listed-only / HOLD
- P046 1 Step Pro：Legacy

Public grouping：Active 8 / 確認中1 / Legacy 2。

### Hantec Trader

- P028 Instant Lite：Daily 3% / Standard Max 5% / Add-on 6%
- SH003：RESOLVED
- blockTop3 = false

### Remaining Block 5

1. Fintokei｜速攻プロ
2. Funded7｜1フェーズ
3. Funded7｜Instant
4. Funded Trader Markets｜Instant Pro
5. FundedElite｜Flash Activation

## Graphic

4点を都会・日常・プロップファーム / トレード文脈の線画へ更新済み・V81で公開。

- learning-path.webp
- diagnosis-flow.webp
- firm-compare.webp
- selector-flow.webp

4/4 HTTP 200 / RC hash一致。

## Verification

Release Candidate Final：PASS_WITH_CAUTION。

- Regression 48/48 PASS
- Build PASS
- lint error 0 / existing no-img-element warning 1
- git diff --check PASS
- protected hash一致
- Blue Guardian / Hantec / Diagnosis / Graphic smoke PASS
- 390px実画面 = NOT_EXECUTABLE（既知Caution。Production実iPhone確認待ち）

## Price / Content Gap Audit

最新判断：`docs/POST_RELEASE_GAP_AUDIT_2026-08-25.md`

価格確認中2件をChat側で公式再確認：

### The5ers Futures｜Day Trade

- 25K = $59
- Activation fee = None
- 公式Futuresページ確認
- Price表示更新候補 = CONFIRMED

### Blueberry Futures｜Accelerated

standard evaluation price：

- 25K $129
- 50K $184
- 100K $276
- 150K $454

60% discount後表示はcampaignとして別レイヤー。base priceへ混ぜない。

## SEO snapshot

Public検索確認では、broad query（プロップファーム / 比較 / クーポン / 出金 / 失格）は競合のranking / comparison / beginner guideが強い。

一方 `プロップファーム 1ステップ 2ステップ 違い` では当サイト `/one-step-two-step-instant` の露出を確認。

方針：ranking模倣ではなく、既存のrule-first long-tail clusterを強化する。

優先：

- 1 Step / 2 Step / Instant
- Daily vs Max Loss
- Static / EOD / Trailing DD
- News trading
- Weekend holding
- Minimum trading days
- First payout
- Price comparison（base / campaign / coupon分離）

## Analytics Gate

実閲覧数・CTR・検索queryベースの最適化はGA4 / Google Search Console実データ待ち。

取得したい指標：

- pageviews / users / engaged sessions
- landing page
- organic clicks / impressions / CTR / avg position
- beginner → diagnosis transition
- diagnosis_start / diagnosis_complete
- Firm selector engagement
- price / coupon reach

public検索snapshotは仮シグナルであり、実閲覧数とは扱わない。

## 絶対保護

- DiagnosisLogicV2を変更しない
- 7問 / 質問順を変更しない
- Affiliate / commission / coupon / priceを採点へ入れない
- Unknownを0 / falseで代用しない
- Conflictを自動Verified化しない
- 新規Planを件数合わせでDiagnosisへ接続しない
- Price base / campaign / personal couponを混同しない

## GitHub canonical

重要：

- `docs/RELEASE_CANDIDATE_FINAL_2026-08-25.md`
- `docs/WORK_DATA_PATCH_RESULT_2026-08-24.md`
- `docs/POST_RELEASE_GAP_AUDIT_2026-08-25.md`
- `docs/SOURCEHEALTH_RECHECK_2026-08-24.md`
- `docs/BLUE_GUARDIAN_MASTER_PATCH_SPEC_2026-08-24.md`
- `docs/HANTEC_INSTANT_LITE_PATCH_SPEC_2026-08-24.md`
- `docs/BLOCK_REVIEW_FINAL_2026-08-24.md`

Excel Masterは別正本。GitHub要約だけでExcelを上書きしない。

## 次

1. 価格確認中2件をWorkへ最小patch
2. V81 public SourceHealth / 確認中一覧のfresh整合確認
3. 実iPhoneで390px確認
4. GSC / GA4実データ取得後にSEO / UXの優先順位を決定
5. high-impression low-CTR / high-view low-conversionページを優先改善
