# Historical VOC Evidence Coding 2026-08-25

確認日：2026-08-25 JST
対象：プロップファームの歩き方 / Home Pain Router / Pain Database
目的：Xの新規反応調査を前提にせず、これまでの会話・運用台帳・診断設計・利用者関連記録から確認できる論点をEvidence強度で整理し、Home初版へ反映する。

## 0. 重要な前提

本書は『日本人トレーダーの何%がこの悩みを持つ』という人口統計ではない。

現在確認できるのは主に：

- 過去の質問・相談・運用上の反復論点
- Master / Diagnosisで最優先管理されてきた項目
- 日本向け利用可否・KYC・出金・ルール差の確認履歴
- Reviewer / 利用者観察

同一人物の重複除外を含む完全な個票集計が未整備のため、割合は出さない。

Evidence band：

- STRONG：複数の独立した記録・運用・実際の問い合わせ/行動で反復
- MEDIUM：運用上重要かつ反復するが、一次Voice個票が不足
- HYPOTHESIS：市場感・戦略仮説としては有力だが、一次Voiceの裏付けがまだ薄い

---

# 1. STRONG｜Home primary入口に使える

## S1 出金 / KYC / 出金条件

確認根拠：

- これまでの初心者教育で出金関係を早期に扱う方針が反復
- Masterでは payout_frequency / consistency_rule / KYC が最優先または高重要度
- SuperFunded等でKYCを出金条件として明示管理
- 初回/以降のPayout cycleを分離して管理

利用者の悩みとしての解釈：

`利益が出ても、いつ・どうすれば本当に出金できるのか分からない。`

Home：PRIMARY

Route：First Payout Checklist → KYC / Consistency / Profitable Days → Evidence → Firm Detail

---

## S2 失格ルール / Daily Loss / Max Loss / DD

確認根拠：

- 過去の初心者不安整理で「ルール」が主要項目
- Master / RulesSchemaで daily_loss / max_loss / dd_type は最優先
- Diagnosisでも失格しにくさ・DD余裕が主要判断軸
- Source conflict監視でもDD方式・損失率の差が繰り返し問題化

利用者の悩み：

`利益より先に、どこで失格するのかを理解できていない。`

Home：PRIMARY

Route：Daily vs Max → Static/EOD/Trailing → 禁止事項 → Diagnosis

---

## S3 日本居住者利用可否 / 日本語対応

確認根拠：

- 過去に「以前は日本人が使えなかったと思う」「日本制限解除？」という確認が発生
- Masterで japan_eligibility は最優先、japanese_supportは診断/LP用途
- 日本語サイト / 管理画面 / FAQ / Supportを分離して確認する運用が必要になった
- FTM等で「日本語対応あり」でも全面日本語ではない差を管理

利用者の悩み：

`日本から登録できても、KYC・Support・出金まで本当に使えるのか分からない。`

Home：PRIMARY

Route：Japan eligibility → 日本語Support → KYC → Firm Detail

---

## S4 自分に合う1-Step / 2-Step / Instantが分からない

確認根拠：

- Diagnosis設計でProgram typeを主要条件として採用
- 過去の比較・初心者記事でPhase形式の違いを継続して扱う
- Plan-level Masterでも1-Step / 2-Step / Instantを別Entityとして管理

利用者の悩み：

`早そうな1-Stepと、余裕がありそうな2-Step。自分にはどちらが楽なのか分からない。`

Home：PRIMARY

Route：Phase comparison → DD / targetとの関係 → Diagnosis

---

## S5 古い情報 / Rule Change / Source Conflict

確認根拠：

- SuperFundedのKYC表現、最低取引日など公式表記差の訂正履歴
- Blueberry等で購入日や言語版によるRule差を履歴管理
- SourceHealth / ChangeLogを継続運用
- Terms version / update dateを最優先監視項目として保持

利用者の悩み：

`前に見たレビューが、今のルールにも当てはまるのか分からない。`

Home：PRIMARYまたはEvidence section上位

Route：Latest Changes → Change Log → Current Rule → Firm Detail

---

## S6 初心者が何から見ればよいか分からない

確認根拠：

- 過去の初心者不安整理：怪しい / ルール / 出金 / 時間 / 参加費
- Beginner Guideを5ステップで構築済み
- 現行サイトの最重要導線が初心者教育

利用者の悩み：

`会社もプランも多すぎて、何から確認すればいいのか分からない。`

Home：PRIMARY

Route：Beginner → 最初に見る3つ → Diagnosis

---

# 2. MEDIUM｜Guide / secondary入口に使う

## M1 News Trading

Master上は最優先級の比較・速報項目。Challenge / Fundedで差があるFirmも複数。

ただし一次Voiceの独立件数は未集計。

→ Homeの3本柱「失格」に内包。専用Guideを強化。

## M2 Weekend Holding

Plan比較で繰り返し管理。手法適合には重要。

→ Home primary cardにはせず、Rule compare / 乗り換え導線で出す。

## M3 Copy Trading / EA

Firmごとの差が大きく、自己口座間 / 第三者 / EAを分離管理している。

→ 複数Firm利用者・Algo利用者向けGuide。

## M4 Minimum Trading Days / Profitable Days

出金と評価で意味が違い、実運用上混同が起きやすい。

→ Payout / Phase Guideで上位化。

## M5 価格 / 割引

問い合わせ・投稿では関心があるが、サイト設計上はRisk / Payout / Eligibilityの後段。

→ Home最下部。Pain Routerには置かない。

---

# 3. HYPOTHESIS｜今はHome primaryにしない

## H1 Funded後の心理崩れ

`合格した途端、失格したくなくて普段通りできない。`

戦略上は重要だが、今回確認できた過去一次Voice個票は不足。

→ Advanced Guide候補。GA4 /相談記録で実需確認。

## H2 高額口座で心理負荷が増える

小口分散戦略と整合するが、現在はユーザーの運用思想・市場仮説が中心。

→ Homeではsecondary。独自記事・Risk educationで扱う。

## H3 日本人の複数Payout実績が最重要の社会的証明

日本市場戦略として有力で、提携交渉でも重要視しているが、現時点で統計的なVOC N数はない。

→ Evidence sectionでは『日本人利用/出金Evidence』を用意する。ただし『日本人の大多数が最重要視』とは書かない。

## H4 複数Firm利用時のRule混同

実務上合理的な痛点だが独立Voice件数は不足。

→ 将来Watchlist / Rule Matrix候補。

---

# 4. EvidenceベースのHome初版｜6 primary routes

X事前検証なしで実装候補にできるのは以下6つ。

1. `初めてで、何から見ればいいか分からない`
2. `失格ルールが複雑で、どこで失格するのか不安`
3. `利益はあるけど、出金条件やKYCが不安`
4. `1-Step・2-Step・Instantのどれが自分向きか分からない`
5. `日本から本当に使えるか、日本語で困らないか確認したい`
6. `前に見た情報が古くないか、今のルールを確認したい`

この6つは既存記録・Master設計・運用履歴との整合が高い。

---

# 5. Homeから外す / secondaryにするもの

初版Homeのprimary cardからは以下を外す。

- Funded後の心理
- 高額口座の心理負荷
- 複数Firm分散
- 日本人Payout複数例そのもの
- News / Weekend / Copy / EA個別

理由：重要ではあるが、6 primaryよりEvidenceが弱い、または上位Painの下位テーマとして扱える。

---

# 6. 初期優先順位

Evidence + Journey impactで暫定順：

1. 初心者の確認順
2. 失格ルール / DD
3. 出金 / KYC
4. 日本利用可否 / 日本語
5. 1-Step / 2-Step / Instant
6. Rule Change / 古い情報

これは『人気ランキング』ではなく、Home情報設計の優先順位。

---

# 7. 次の実装判断

Home Pain Routerは、Xの反応待ちを解除。

実装前に必要なのは：

1. 各routeの既存URL mapping
2. まだ存在しないGuideのfallback route
3. GA4 eventを増やすか既存eventで計測するか決定
4. V81後P0 price patchと競合しない差分設計
5. 390px DOM/CSS設計

DiagnosisLogicV2 / scoring / Price layerは変更しない。

## Status

Historical VOC Evidence Coding = COMPLETE
Home Primary Pain Set = 6 STRONG routes
X pre-validation = NOT REQUIRED
Percent/statistical prevalence claims = NOT ALLOWED until unique voice records are built
