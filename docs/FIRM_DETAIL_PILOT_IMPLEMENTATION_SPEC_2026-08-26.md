# FIRM_DETAIL_PILOT_IMPLEMENTATION_SPEC

更新日：2026-08-26 JST
対象：Fundora / Fintokei Firm Detail Pilot
位置づけ：Work向けImplementation Spec。Productionコード実装はこの文書作成時点では未実施。

## 0. Start Gate

Workは以下が満たされるまで実装開始しない。

- git.chatgpt-team.site authentication recovered
- Evidence local commit `3e72c0b1e46fa83e9ee2abcda03fcfc583670f2f` がremoteへ確定
- Fundora local commit `2191f06dc56006b4018f16ec8c2ac51161d2f70a` がremoteへ確定
- Fundora campaign Production handling 完了
- Current Production再確認完了
- Worktree clean
- Production baselineに未知差分なし

GitHub handoff repositoryはProduction Application Sourceではない。Production実体を優先する。

## 1. Objective

既存ProductionのMaster / Diagnosis / Affiliate / Coupon / Priceを壊さず、Firm個別ページの共通Templateが実用に耐えるかを2社で検証する。

Pilot：

1. Fundora：比較的シンプルなFirm
2. Fintokei：複数Plan / Academy / Variant注意を持つ複雑なFirm

2社PASS後に残り12社へ横展開判断を行う。

## 2. In Scope

- Firm Detail共通Page Template
- `/firms/fundora/`
- `/firms/fintokei/`
- Firm Snapshot
- まず確認する3点
- Current Plan表示
- Rule summary
- existing platform display
- Japan section
- verified payout summary where existing source permits
- M11 + M14 FAQ
- related internal links
- Base Price / Campaign / Coupon section separation
- Official / Affiliate CTA separation
- last checked / status
- disclosure / disclaimer
- SEO title/meta/canonical
- tests
- regression
- 390px QA

## 3. Out of Scope

- remaining 12 Firm pages
- `/firms/` full directory redesign beyond minimum Pilot access
- Platform Registry
- Platform individual pages
- Payout Registry / Route DB
- Payout Source reconstruction
- Review score / stars
- user-generated reviews
- AI rating
- new ranking
- Diagnosis changes
- Master schema redesign
- Affiliate calculation changes
- automatic campaign price calculation
- new GA4 initialization

## 4. Frozen Assets

Do not change unless separately approved:

- `app/master-data.json` schema/meaning
- DiagnosisLogicV2
- 7 questions / order
- score
- eligibility
- ranking
- Affiliate logic
- Commission logic
- Coupon logic
- Base Price logic
- existing GA4 initialization
- Evidence Phase1 schema

Plan data may only be consumed from accepted Production sources; do not rewrite Master merely to support the page.

## 5. Shared Page Order

1. Breadcrumb / H1
2. Firm Snapshot
3. まず確認する3点
4. このFirmの特徴
5. 現行プラン
6. 主要ルール
7. 取引Platform
8. 日本から利用する際の確認事項
9. Payout
10. FAQ
11. 関連ガイド
12. Price / Campaign / Coupon
13. Official / Affiliate CTA
14. 情報確認状況
15. Disclosure / Disclaimer

`docs/FIRM_DETAIL_CONTENT_CONTRACT_2026-08-26.md` を共通Contractとして使用する。

## 6. Fundora Pilot

### Route

`/firms/fundora/`

### SEO Title

`Fundoraとは？プラン・ルール・日本語対応を初心者向けに整理`

### H1

`Fundoraを使う前に確認したいプラン・ルール・取引環境`

### Intro

Fundoraを検討するときは、価格だけでなく、利益目標、日次損失、最大損失、取引環境、出金条件を順番に確認することが重要です。このページでは、現在確認できている情報を初心者向けに整理します。

### Characteristic wording

M11 Q1はM14でPASS_WITH_CAUTION。断定を強めず、次の程度に留める。

`プランを比較するときは、まず利益目標、日次損失、最大損失など主要条件から確認すると整理しやすい構成です。`

### FAQ

M14判定：

- Q1 PASS_WITH_CAUTION
- Q2 PASS
- Q3 PASS
- Q4 PASS
- Q5 PASS

M11本文をBaseとして不要なrewriteをしない。

### Campaign Boundary

Fundora `初挑戦応援キャンペーン` は通常Firm情報と分離する。

- Base Priceへ混ぜない
- Official Campaign Layerとして表示する場合はcurrent status / start / end / conditionsを維持
- Campaign終了後は通常Firm情報から自動的に恒久価格扱いしない
- Affiliate CTAとOfficial information CTAを分離

## 7. Fintokei Pilot

### Route

`/firms/fintokei/`

### SEO Title

`Fintokeiとは？プラン・ルール・日本語対応を初心者向けに整理`

### H1

`Fintokeiを使う前に確認したいプラン・ルール・取引環境`

### Intro

Fintokeiには複数のプランがあり、評価の進み方や損失ルールなどが異なります。このページでは、最初からすべての条件を比較するのではなく、まず見るべきポイントから順番に整理します。

### Beginner Entry

Fintokei Academyは初心者向け入口として関連導線を置いてよい。

注意：

- Academy XP と Fintokei本体の制度を混同しない
- Academyの特典・条件は既存accepted contentを再利用
- Academyを利用しないとFirmを利用できないような誤認を作らない

### Plan wording / M14 U01

Fintokei Q2はM14 UPDATE_REQUIRED。次を使用：

`現行の公式サイトでは、チャレンジプラン、チャレンジプラン・スイング、チャレンジプラン・スリム、速攻プロプランが案内されています。最初から全ルールを比べるより、まず「評価の進み方」「損失ルール」「最低取引日数」の3点で候補を絞り、該当プランだけ詳細を確認すると分かりやすいです。`

### Sokkou Pro Boundary

速攻プロは2026-07-15以降の新規購入口座を対象とする限定Variantとして扱う。

- current new-purchase variant と historical account conditionsを混同しない
- 旧口座へ新条件を適用しない
- FAQ schema対象はM14安全ルールに従う

### FAQ

M14判定：

- Q1 PASS
- Q2 UPDATE_REQUIRED → U01
- Q3 PASS_WITH_CAUTION
- Q4 PASS_WITH_CAUTION
- Q5 PASS

不要なrewrite禁止。

## 8. Plan / Status Presentation

表示Group：

- Current
- 条件付き / 確認中
- Legacy / Ended
- Listed-only / HOLD（存在時）

HOLDをCurrentとして強調しない。
Diagnosis未接続を`利用不可`に変換しない。
Unknownを`非対応`に変換しない。

## 9. Platform Boundary

Phase 1は既存 `planCatalog.platforms` Display Stringを使用。

- Platform Registryを新設しない
- Firm Detail内で独自mapping DBを作らない
- 未公開 `/platforms/...` へのリンクを作らない

## 10. Payout Boundary

P00R / P01 / P10不足中。

- 確認済みのFirm固有情報のみ
- Payout Route生成禁止
- Provider推測禁止
- P10 load禁止
- Source不足をページ完成のために補完しない

不足時は `詳細確認中` 等のStatusで安全に表示するか、Sectionを最小化する。

## 11. CTA Boundary

Official：

`公式情報を確認する` → normal official URL

Affiliate：

`PR｜公式サイトを見る` → accepted affiliate URL

同一リンクとして扱わない。
Affiliate CTA付近にCommercial Disclosureを表示する。

## 12. Compliance

必須参照：

`docs/COMPLIANCE_BASELINE_V1_2026-08-26.md`

Pilotで必須：

- PR disclosure visible
- official / affiliate URL separation
- provided account disclosure（該当時）
- sponsor disclosure（該当時）
- guaranteed claim 0
- unsupported superiority claim 0
- service nature misrepresentation 0
- Japan eligibility / regulatory status confusion 0
- status / last checked visible
- disclaimer visible
- PII analytics 0

## 13. Analytics

Firm Detail Pilotのために新しいGA4 initializationを追加しない。

既存event systemに安全に追加できることが明確な場合のみ、別承認でFirm page view / CTA click eventを追加する。

Firm Detail Pilotの公開をAnalytics新設でブロックしない。

## 14. SEO

各Route：

- unique title
- unique meta
- self canonical
- one H1
- duplicate canonical 0

Sitemap追加はPilot QA PASSと公開承認後。

FAQ schemaはM14安全ルールを適用し、画面表示本文と一致させる。

## 15. Test / Regression

最低限：

- existing V82-series regression >= 53/53 PASS
- Build PASS
- lint errors 0
- git diff --check PASS
- Master protected hash unchanged
- Diagnosis protected hash unchanged
- GA4 initialization protected hash unchanged（Analytics非変更時）

Pilot tests：

- Fundora route render
- Fintokei route render
- unique title/meta/canonical
- official / affiliate CTA separation
- disclosure present
- disclaimer present
- last checked/status present
- Fundora Campaign/base separation
- Fintokei U01 text applied
- Sokkou Pro historical/current separation
- M14 HOLD rules not promoted
- no payout fabricated data
- no platform registry creation
- Diagnosis result unchanged

## 16. 390px QA

両Routeについて：

- horizontal overflow = 0
- snapshot/status cards fit
- long Japanese labels wrap
- plan cards 1-column where required
- CTA tap height >= existing site standard
- accordion / FAQ clipping 0
- campaign section overflow 0
- disclaimer readable

Production Feature ON / publish前にactual iPhone Safari checkを行う。

## 17. Commit Strategy

Pilotは既存Evidence/Fundora commitsを変更しない。

推奨：

1. Firm Detail shared template + tests
2. Fundora + Fintokei content wiring

ただし既存Production architecture上、1 commitの方がrollback安全性が高い場合は、Pilot全体1 commitまで許容。Workが勝手に大規模refactorを分離・追加しない。

rebase / amend / squashで既存accepted commitsを変更しない。

## 18. Publish Gate

コード実装完了だけではpublishしない。

必要：

- baseline reconciliation PASS
- all tests PASS
- Compliance Gate PASS
- SEO PASS
- 390px PASS
- actual iPhone PASS
- no protected asset drift
- no unknown production diff
- human / central command approval

## 19. Stop Conditions

以下で即HOLD：

- current Production baseline不一致
- Git auth failure
- pending local commits未整理
- Master schema変更が必要
- Diagnosis変更が必要
- M14 HOLDを解除する必要
- Payout Source推測が必要
- Platform mapping再構築が必要
- Official/Affiliate URLを分離できない
- service natureが確認できないのに断定が必要
- unknownをfalse/unsupported化する必要
- regression failure
- protected hash unexpected change

最終Statusは `HOLD_FOR_CENTRAL_COMMAND` として返す。

## 20. Acceptance Result Format

Workは最低限次を報告する。

- baseline / commit
- changed files
- new files
- route status
- Fundora content status
- Fintokei content status
- M11/M14 application status
- Compliance Gate
- tests / regression
- build / lint / diff-check
- protected hashes
- 390px result
- actual iPhone result
- sitemap/canonical result
- worktree status
- commit SHA（作成時）
- publish status
- blockers / cautions

Expected final pre-publish status：

`FIRM_DETAIL_PILOT_RC_READY`

Publishは中央承認後のみ。
