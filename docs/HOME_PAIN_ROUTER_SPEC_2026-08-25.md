# Home Pain Router Spec 2026-08-25

確認日：2026-08-25 JST
対象：プロップファームの歩き方 Home
目的：Firm / 商品起点ではなく、利用者の現在地・悩みから最適な教育導線へ送る。

重要：本仕様は情報設計。Version 81へまだ実装しない。
最新Evidence coding：`docs/HISTORICAL_VOC_EVIDENCE_CODING_2026-08-25.md`

## 0. 基本方針

Homeの新しい最初の役割は `Decision Router`。

現行の Beginner / Diagnosis / Firm Selector / Price は削除せず、入口の順序と意味を整理する。

Pain Routerでは商品名・価格・割引コードを出さない。

X事前検証は必須条件ではない。過去のVoice / 運用履歴 / Master / DiagnosisのEvidenceを先に使い、実装後にGA4 / GSC / actual usageで改善する。

---

# 1. 推奨Hero

### H1候補

`どのプロップファームを選ぶかの前に、失格・出金・信頼性を確認しよう。`

### Sub

`今の悩みから必要な情報だけ確認して、自分に合う候補まで順番に進めます。`

### Primary CTA

`今の悩みから見る`

### Secondary CTA

`30秒診断へ`

HeroでFirm名・価格・Campaignを主役にしない。

---

# 2. Home「あなたは今どこ？」6入口

6入口はHistorical VOC Evidence CodingでSTRONG判定された論点を中心にする。

## R01 はじめて

表示：
`初めてで、何から見ればいいか分からない`

補足：
`仕組み・失格ルール・出金・選び方を順番に確認します。`

Route：
Beginner Guide → 最初に見る3つ → Diagnosis

Evidence：STRONG

---

## R02 失格ルールが不安

表示：
`失格ルールが複雑で、どこで失格するのか不安`

補足：
`Daily Loss・Max Loss・DD・禁止事項を先に整理します。`

Route：
Daily vs Max → Static / EOD / Trailing → 禁止事項 → Diagnosis

Evidence：STRONG

---

## R03 出金・KYCが不安

表示：
`利益はあるけど、出金条件やKYCが不安`

補足：
`出金日・Consistency・Profitable Days・KYCを確認します。`

Route：
First Payout Checklist → Payout conditions → Evidence → Firm Detail

Evidence：STRONG

注意：日本人Payout Evidenceは補助判断材料として扱い、将来の出金保証とは表現しない。

---

## R04 どの形式が合うか分からない

表示：
`1-Step・2-Step・Instantのどれが自分向きか分からない`

補足：
`早さだけでなく、利益目標とDDの余裕から違いを確認します。`

Route：
1-Step / 2-Step / Instant Guide → DD / target比較 → Diagnosis

Evidence：STRONG

---

## R05 日本から使えるか確認したい

表示：
`日本から本当に使えるか、日本語で困らないか確認したい`

補足：
`日本居住者利用可否・日本語UI・サポート・KYCを分けて確認します。`

Route：
Japan Eligibility / Japanese Support → KYC → Firm Detail

Evidence：STRONG

注意：日本語サイトがあることと、日本語サポート・日本人利用可否を同一扱いしない。

---

## R06 情報が古くないか確認したい

表示：
`前に見た情報が古くないか、今のルールを確認したい`

補足：
`現在ルール・旧モデル・公式情報差・変更履歴を分けて確認します。`

Route：
Latest Changes / Change Log → Current Rule → Firm Detail

Evidence：STRONG

---

# 3. 初期表示順

1. R01 はじめて
2. R02 失格ルールが不安
3. R03 出金・KYCが不安
4. R05 日本から使えるか確認したい
5. R04 どの形式が合うか分からない
6. R06 情報が古くないか確認したい

理由：初心者 → Survival → Payout → Japan eligibility → Program fit → Freshnessの順で、購入前に必要な判断を優先する。

これは人気順位ではない。GA4 / actual usageで後から並べ替え可能。

---

# 4. Secondary routes

以下は重要だがHome primary cardには置かず、Guide / Advanced areaで扱う。

- Funded後のRisk / 心理
- 高額口座 / 小口分散 / Scale
- 複数Firm管理
- News Trading
- Weekend Holding
- Copy Trading / EA
- Minimum Trading Days / Profitable Days

News / Weekend / Copy / EAはR02またはR04の下位導線として露出する。

---

# 5. Card UI原則

- 6枚を一度に重く見せない
- Mobileでは1列
- 1 Card = 1悩み
- Heading 1行〜2行
- 補足2行以内
- CTAは `確認する` 程度
- Firm logo / price / coupon禁止
- 赤い警告UIを乱用しない
- 恐怖を煽らず「整理できる」方向へ

---

# 6. Home全体の推奨順

1. Hero
2. あなたは今どこ？ Pain Router
3. まず見る3本柱：失格 / 出金 / 信頼性
4. Beginner 5 Steps
5. Evidenceの見方
6. 30秒Diagnosis
7. Firm → Plan Selector
8. 最新の変更 / Rule Change
9. 学ぶ / Guides
10. Price / Campaign / Coupon

既存Priceを削除せず、最下段近くに維持。

---

# 7. Evidence section候補

見出し：
`「確認済み」の意味も、分けて表示します。`

Badge候補：

- `公式確認済み`
- `公式情報を確認中`
- `公式内で情報差あり`
- `旧モデル`
- `日本人利用報告あり`
- `出金Evidenceあり`

注意：

- 日本人利用報告 = 人気や安全保証ではない
- Payout Evidence = 将来Payout保証ではない
- Affiliate関係 = Evidence評価に影響させない
- Internal Confidence / SourceHealth / Block Top3をそのままpublic labelにしない

---

# 8. Measurement

Home RouterはX反応待ちではなく、公開後のactual behaviorで改善する。

優先計測：

- route card click
- Beginner遷移
- Diagnosis start
- Diagnosis complete
- Firm detail到達
- Payout guide到達
- Rule guide到達

GA4 event追加が必要な場合は既存GA4 architecture内に限定し、Diagnosis event仕様を壊さない。

Xは補助検証：

- Evidenceが弱いsecondary Pain
- wordingの改善
- 新しい市場変化
- 利用者の生の表現収集

---

# 9. 実装Gate

現時点：`EVIDENCE_BACKED_DESIGN_READY / NOT_IMPLEMENTED`

実装前条件：

1. V81後Price P0 patch完了
2. Pain Router CTAの既存URL mapping確定
3. 未実装Routeのfallbackを決定
4. GA4 event追加有無を確定
5. 390px CSS/DOM設計を先に保証
6. DiagnosisLogicV2変更なし
7. Firm / Plan / Price / Couponの現行順序・データを破壊しない

X事前検証はGateから削除。

Workへは条件確定後に最小patchだけ渡す。
