# プロップファームの歩き方｜再設計 2026-08-25

確認日：2026-08-25 JST
対象：Production Version 81以降の中期設計
目的：単なる比較・アフィリエイトサイトではなく、日本語圏のプロップファーム意思決定・検証インフラへ発展させる。

## 0. 結論

現行の `基礎 → 診断 → Firm → Plan → Detail → 価格/特典` は残す。

ただしサイト全体の中心を「会社・商品」から「利用者の悩み・判断・証拠」へ移す。

新しい中核：

`悩み → 教育 → ルール理解 → Evidence確認 → 診断/比較 → Firm/Plan詳細 → 必要な人だけ価格・Affiliate`

目標はランキングサイトではなく、**日本語でプロップファームを調べる時の意思決定基盤**。

---

# 1. Fact Check Round 1｜一次情報確認

## 日本FX市場

金融先物取引業協会の2026年7月速報：

- 店頭FX取扱会員 46社
- 出来高 8,820,768億円（約882.1兆円）
- 月末建玉 119,642億円（約12.0兆円）

重要：出来高は市場活動量であり、利用者数ではない。FX人口やProp利用人口へ換算しない。

## 日本でのProp普及シグナル

Fintokei公式では2026年上半期の日本人新規参加について、個別CEO記事に「約9,000人」、ブログ一覧等に「約10,000人」という表記差がある。

したがって公開上は：

- `2026年上半期に約9,000〜10,000人規模の新しい日本人トレーダー参加をFintokei自身が公表`

までとし、単一の10,000人を確定値扱いしない。

この数値から日本Prop市場全体の利用者数を外挿しない。

## 法規制

金融庁は、日本居住者へFX取引を業として提供する場合は日本で金融商品取引業登録が必要と明示している。

一方、2026-08-25時点で、Modern Prop Firmの純粋なsimulation challenge / performance rewardモデル全般を一括して法的に分類する金融庁の専用公表資料は本調査で確認できていない。

そのため公開上は：

- `FXを実取引として提供する場合の登録ルール`
- `各Prop Firm自身がsimulated environmentと説明している事実`
- `Modern Prop Firm自体の日本法上の個別評価は実態依存であり断定しない`

を分ける。

Eightcap Challengesの2026 TermsはサービスをSimulated Trading Experienceとし、ライブ市場ではないことを明示。Blue Guardianもfundedを含む全口座をdemo / simulated environmentと説明。

## PR / Affiliate

消費者庁のステマ告示では、直接の規制対象は原則として広告主である事業者。インフルエンサー/アフィリエイターは通常、告示の直接対象ではないとQ&Aに明記される。

ただし広告表示は一般消費者に明瞭である必要があるため、当サイトのPR明示・Affiliate方針は維持する。

「アフィリエイター自身が常に景表法の直接規制対象」と単純化して記載しない。

---

# 2. Fact Check Round 2｜反証・過大主張チェック

以下を修正・禁止する。

## A. 日本Prop市場の人数推定

以前の事業仮説として使った `2026年2〜4万人 / 2031年7〜15万人` のような推定は、現時点で公的/業界統計の裏付けが十分でない。

→ 公開事実として使わない。内部シナリオでも前提・誤差を明示する。

## B. 「日本人は他の日本人を確認してから参加する」

市場感として有力な仮説だが、Prop業界の日本人を対象にした統計的確認は未取得。

→ **User Behavior Hypothesis**として扱い、X反応、アンケート、GA4、レビュー行動で検証する。

## C. 「日本No.1」「情報インフラ」

現時点では目標であり事実ではない。

→ No.1表現を自称しない。
→ `第一参照点を目指す` / `判断材料を集約する` と表現。

## D. Search / SEO

GSCでは直近28日でHomeのみ8 impressions、優先7記事のURL Inspectionは `URL is unknown to Google`。

On-page live auditではcritical/high/medium issueは0だが、News / Weekend / Minimum Trading Days等にthin-content指摘あり。

→ 現時点ではCTR最適化より `indexing + content depth + internal links` を優先する。

## E. Safari/Bing

Safariは検索エンジンではない。Google以外のSearch流入を確認するにはBing等のデータが必要。

Bing Webmaster Toolsは現時点で未接続。

→ 「Safariで検索されていない」とは言わない。

---

# 3. 再設計の思想

## Before

`Firmを比較するサイト`

## After

`トレーダーが、自分の悩みを言語化し、失格・出金・信頼性を確認し、最後に自分で選べるサイト`

差別化軸：

1. Pain-first
2. Rule-first
3. Plan-level
4. Evidence-first
5. Conflict transparency
6. Change history
7. Diagnosis
8. Primary information
9. Affiliate separation
10. X → Data → Article → Diagnosis循環

---

# 4. Homeの役割変更

Homeは巨大な商品一覧ではなく **Decision Router** にする。

## 推奨順

### HERO

主語をFirmではなく利用者にする。

候補：

`どのプロップファームを選ぶかの前に、失格・出金・信頼性を確認しよう。`

補足：

`ルール、実績、変更履歴を整理して、自分に合う候補まで順番に確認できます。`

Primary CTA：`今の悩みから見る`
Secondary：`30秒診断`

価格・割引はHeroに置かない。

### SECTION 1｜あなたは今どこ？

悩み/ステージ入口：

1. 初めてで何から見ればいいかわからない
2. チャレンジで何度も失格している
3. 合格できるがFunded後に崩れる
4. 出金できるか不安
5. 他社へ乗り換えたい
6. Firm名から調べたい

### SECTION 2｜まず確認する3本柱

- 失格：Daily / Max / DD / 禁止事項
- 出金：日数 / consistency / KYC / cap
- 信頼性：運営履歴 / 日本人利用 / incident / Source

### SECTION 3｜初心者5ステップ

既存Beginner Guideを維持。

### SECTION 4｜Evidenceの見方

Public badge候補：

- 公式確認済み
- 公式情報を確認中
- 公式内で情報差あり
- 旧モデル
- 日本人利用報告あり
- 出金Evidenceあり

内部Confidence %やBlock Top3等はpublicに出さない。

### SECTION 5｜30秒診断

現行7問・Logicを変更しない。

### SECTION 6｜Firm → Plan Selector

現行14社/72Plan設計を維持。

Homeでは概要のみ。将来的にはFull Database Hubへ分離可能。

### SECTION 7｜最新の変更

新しい価値：

- Rule Change
- Payout変更
- Legacy化
- Security Incident
- 日本向け対応

Campaignだけのfeedにしない。

### SECTION 8｜学ぶ / SEO Guides

悩み起点cluster：

- 日次損失で失格した
- Trailing DDがわからない
- ニュース前後何分？
- 週末保有していい？
- 最低取引日数0なのに出金できない？
- 1Step / 2Step / Instantどれ？
- KYCが不安
- 出金できるか確認したい

### SECTION 9｜価格・クーポン

最後に置く。base price / campaign / personal code分離を維持。

---

# 5. Navigation再設計候補

Top Navは商品分類ではなく利用目的で整理。

1. `はじめて`
2. `失格ルール`
3. `出金・実績`
4. `ファームを調べる`
5. `30秒診断`
6. `最新情報`

価格/クーポンはMoreまたはFirm detailの後段。

既存URLのcanonical / redirectを変更しない。Hubはadditiveに作る。

---

# 6. Segment別Journey

## 完全初心者

悩み：詐欺？何を買う？用語が難しい

Journey：
`悩み → Beginner → 失格3本柱 → Diagnosis → Firm`

## 購入検討中

悩み：安いけど失格しないか

`Rule checklist → Plan compare → Evidence → Price`

## 失格経験者

悩み：また同じことを繰り返す

`失格原因 → Daily/Max/DD Guide → 自分の手法条件 → Diagnosis`

将来Tool：`失格原因チェック`

## 合格未経験

悩み：Profit Targetだけ追って崩れる

`Phase形式 → DD余裕 → Risk/Target → 1/2Step比較`

## Funded / 出金未経験

悩み：利益はあるが申請が怖い

`Payout checklist → KYC/Consistency → Evidence → Firm detail`

## 出金経験者

`Payout benchmark → Scale / multi-firm → Change Feed`

## 乗り換え層

`現在の不満 → Rule difference → Firm/Plan compare → Evidence`

## 高額口座検討者

`心理負荷 / risk → 小口分散教育 → Scale strategy → Plan`

## 複数Firm利用者

`Watchlist → Rule Change / Incident → Payout history`

---

# 7. 情報インフラとして追加すべきData Layer

## A. Rule Registry

既存Master / SourceHealthを発展。

- current rule
- effective date
- generation
- source
- conflict
- legacy

## B. Change Log

Firm / Plan単位：

- before
- after
- effective date
- source
- impact

## C. Payout Evidence Registry

個人情報を持たない形で：

- Firm / Plan
- request date
- received date
- amount range
- payment rail
- source type
- evidence type
- Japan user yes/no
- verified date

`公式testimonial` と `独自確認` と `利用者報告` を混ぜない。

## D. Incident Registry

- Security breach
- payout delay
- platform outage
- rule dispute
- closure / acquisition
- Japan restriction

事実 / allegation / resolvedを分離。

## E. Japan Experience Layer

- 日本語UI
- 日本語support
- 日本人利用Evidence
- KYC experience
- payment methods
- Japan-specific issue

「日本人利用あり」を人気ランキングへ直結させない。

## F. Commercial Layer

- Base Price
- Official Campaign
- Personal Coupon
- Affiliate URL

Decision / Diagnosis scoringから完全分離。

---

# 8. Pain Database

Chat側で持つ市場理解の中心。

推奨fields：

- Pain ID
- Segment
- Situation
- Inner monologue
- Fear
- Desired outcome
- Severity
- Urgency
- Commercial intent
- Primary evidence
- X test angle
- Impressions
- Replies
- Saves / Bookmarks
- Profile clicks
- Site clicks
- Winning / Hold
- Next content

例：

`またチャレンジを買って失格したら、今月だけで3万円以上無駄になる。`

このPainから：

X → thread → graphic → Shorts → Article → DD guide → Diagnosis

へ展開する。

---

# 9. X / YouTube / SEO統合

X = Market Research。

1テーマを：

- Fear
- Failure
- Number
- Contrarian
- Experience
- Comparison
- Unexpected

でテスト。

勝ちテーマだけSiteへ昇格。

YouTubeは検索需要と一次情報が両方あるテーマを優先。

SEOは`キーワード`ではなく`悩み + 判断`を狙う。

例：

- プロップファーム 日次損失 含み損
- プロップファーム ニュース取引 前後5分
- プロップファーム 出金 条件
- プロップファーム KYC 日本
- 1ステップ 2ステップ 違い
- Instant Funding 向いている人

---

# 10. SEO再設計

## P0 Indexing

まず優先7記事をGoogleに認識させる。

- Home / Beginner / rule articlesからcontextual internal links
- Sitemap / canonical維持
- orphan 0

## P1 Content depth

最優先：

1. News Trading
2. Weekend Holding
3. Minimum Trading Days
4. Daily vs Max Loss
5. DD types
6. First Payout

文字数目的でなく、検索者の判断分岐を追加。

## P2 Authority Pages

Firm pageを「紹介文」で終わらせない。

- current plans
- change history
- rules
- payout
- Japanese evidence
- incidents
- current cautions
- source

## P3 CTR

Impressionが十分に溜まってからTitle / Meta ABを行う。

現時点でHome titleの大幅変更を急がない。

---

# 11. Trust / Editorial Design

サイト上で分離表示する。

### Facts

`公式確認済み`

### First-party evidence

`運営者確認 / 独自検証`

### Community evidence

`日本人利用者からの報告`

### Uncertainty

`公式情報を確認中 / 公式内で情報差あり`

### Commercial

`PR / Affiliate`

同じカード内に混在させても、見た目で区別できるようにする。

---

# 12. 2026-2031 Roadmap

## 2026-2027｜Foundation

- Indexing
- Pain DB
- Rule DB
- SourceHealth
- Change Log
- Payout evidence
- Incident history
- Beginner
- Diagnosis
- X tests
- Weekly news

目的：**履歴を貯める。**

## 2028-2029｜Authority

- Firm Authority Pages
- Payout benchmarks
- Rule change alerts
- monthly market report
- YouTube long-form
- reviewer network
- Japan market report

目的：利用者だけでなくFirm側も参照する媒体へ。

## 2030-2031｜Infrastructure

- historical datasets
- API / feeds
- change monitoring
- Japan market intelligence
- public methodology
- industry report

目的：記事数ではなく履歴・Evidence・方法論を競争優位にする。

---

# 13. 実装順｜V81以降

巨大リニューアルを一度に行わない。

## Wave A｜P0

- 確認中Priceの解消
- priority article indexing
- thin articlesブラッシュアップ
- contextual internal links
- public SourceHealth整合

## Wave B｜Home Pain-first

- `あなたは今どこ？` module追加
- Heroを悩み/判断中心へ
- Evidenceの見方追加
- Price / Couponは後段維持
- Selector / Diagnosis logic不変

## Wave C｜Evidence Infrastructure

- Change Log
- Payout Evidence
- Incident Registry
- Japan Experience

## Wave D｜Authority hubs

- Rules hub
- Payout hub
- Firm DB hub
- Latest Changes

既存slugは維持し、additive architectureで構築。

---

# 14. Protected Boundaries

- DiagnosisLogicV2不変
- Affiliate / commission / couponをscoreへ接続しない
- Unknownをfalse/0にしない
- Conflictを自動Verifiedにしない
- PR明示
- Base / campaign / personal coupon分離
- Evidence source type分離
- 未確認の日本市場規模を事実扱いしない
- 法的評価を断定しない
- No.1自称禁止（外部根拠ができるまで）

---

# 15. Double Fact Check後の最終結論

**「プロップファームの歩き方」は、比較サイトから情報インフラへ進化させる。ただし、先に売るサイトにはしない。**

ユーザーが最初に見るのは会社名ではなく、自分の悩み。

次にルール、出金、Evidenceを理解し、その後でDiagnosis / Firm / Planへ進む。

長期的な競争優位はAffiliate条件ではなく、2026年から蓄積する：

- rule history
- source conflicts
- payout evidence
- Japan user evidence
- incidents
- pain response data
- search / behavior data

に置く。

2026年時点では市場規模や法的位置づけに未確定部分があるため、成長予測をサイトの権威づけに使わない。

**Fact / Evidence / Hypothesis / Commercialを分けて表示できること自体をブランド価値にする。**
