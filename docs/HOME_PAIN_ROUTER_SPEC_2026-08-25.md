# Home Pain Router Spec 2026-08-25

確認日：2026-08-25 JST
対象：プロップファームの歩き方 Home
目的：Firm / 商品起点ではなく、利用者の現在地・悩みから最適な教育導線へ送る。

重要：本仕様は情報設計。Version 81へまだ実装しない。X検証前の初期仮説を含む。

## 0. 基本方針

Homeの新しい最初の役割は `Decision Router`。

現行の Beginner / Diagnosis / Firm Selector / Price は削除せず、入口の順序と意味を整理する。

Pain Routerでは商品名・価格・割引コードを出さない。

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

# 2. Home「あなたは今どこ？」8入口

## R01 はじめて

表示：
`初めてで、何から見ればいいか分からない`

補足：
`詐欺・失格ルール・選び方を順番に確認します。`

Route：
Beginner Guide → 最初に見る3つ → Diagnosis

Pain：P001 / P002 / P003

---

## R02 購入前

表示：
`買おうと思っているけど、ルールを読み切れていない`

補足：
`割引より先に、失格条件と出金条件を確認します。`

Route：
購入前Checklist → 1Step/2Step/Instant → Firm/Plan

Pain：P004 / P005 / P006

---

## R03 失格した

表示：
`チャレンジで失格して、次を買う前に原因を知りたい`

補足：
`Daily Loss・Max Loss・DD・禁止事項から原因を整理します。`

Route：
失格原因 → Daily/Max → DD → Diagnosis

Pain：P007 / P008 / P009

---

## R04 合格できない

表示：
`利益は出せるのに、評価をなかなか通過できない`

補足：
`Profit Targetだけでなく、手法とDDの相性を確認します。`

Route：
Evaluation Risk → Phase比較 → Diagnosis

Pain：P010 / P011 / P012

---

## R05 Funded後が怖い

表示：
`Fundedには到達したけど、失格したくなくて普段通りできない`

補足：
`評価中とFunded後で変えるべきリスクとルールを確認します。`

Route：
Funded Risk → Rule Delta → Payout Checklist

Pain：P013 / P014 / P015

---

## R06 出金が不安

表示：
`利益はあるけど、本当に出金できるのか不安`

補足：
`KYC・Consistency・Profitable Days・日本人利用Evidenceを確認します。`

Route：
First Payout Checklist → Payout Evidence → Firm Detail

Pain：P016 / P017 / P018 / P019

---

## R07 乗り換えたい

表示：
`今のFirmが自分の手法に合わず、別の選択肢を探したい`

補足：
`ニュース・週末・DD・日本語対応などの違いから比較します。`

Route：
Rule Difference → Diagnosis → Firm/Plan Compare

Pain：P023 / P024 / P025

---

## R08 大きな口座・複数Firm

表示：
`口座サイズを上げるか、複数Firmへ分散するか迷っている`

補足：
`価格ではなく、失格時の余力・心理負荷・ルール管理から考えます。`

Route：
Scale / Small-account Strategy → Multi-Firm Rules → Plan

Pain：P020 / P021 / P022 / P026-P031

---

# 3. 8入口の優先表示順

初期順：

1. R01 はじめて
2. R03 失格した
3. R06 出金が不安
4. R02 購入前
5. R04 合格できない
6. R05 Funded後が怖い
7. R07 乗り換えたい
8. R08 大きな口座・複数Firm

理由：初心者・失格・Payoutの3大不安を上段に置く。価格・購入は4番目以降。

ただし順序はX / GA4の実反応で変更する。

---

# 4. Card UI原則

- 8枚を一度に重く見せない
- Mobileでは1列
- 1 Card = 1悩み
- Heading 1行〜2行
- 補足2行以内
- CTAは `確認する` 程度
- Firm logo / price / coupon禁止
- 赤い警告UIを乱用しない
- 恐怖を煽らず「整理できる」方向へ

---

# 5. Home全体の推奨順

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

# 6. Evidence section候補

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

---

# 7. 最初のX検証とHome Routerの関係

Homeへ実装する前に、以下5Painを優先してXで検証：

1. P001 海外Firmを信用してよいか
2. P007 再失格が怖い
3. P016 出金申請が怖い
4. P019 日本人のPayout実績を複数確認したい
5. P025 古いレビューを信じてよいか

反応指標：Replies / Bookmarks / Profile Click / Site Click。

Like数だけで判断しない。

---

# 8. 実装Gate

現時点：`DESIGN_READY / NOT_IMPLEMENTED`

実装前条件：

1. V81後Price P0 patch完了
2. 主要SEO記事indexing改善と競合しないこと
3. Pain Router CTAの既存URL mapping確定
4. GA4 eventを新設する場合は既存GA4 architecture内で仕様確定
5. 390px設計をCSS/DOMで先に保証
6. DiagnosisLogicV2変更なし

Workへは条件確定後に最小patchだけ渡す。