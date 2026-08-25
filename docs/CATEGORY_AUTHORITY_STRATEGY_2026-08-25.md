# Category Authority Strategy 2026-08-25

確認日：2026-08-25 JST
対象：プロップファームの歩き方
目的：日本語圏におけるプロップファーム情報の第一想起・第一参照サイトを目指すための運用戦略。

## 0. 現状

Production：Version 81

- Firm 14
- PlanCatalog 72
- Diagnosis 64
- Block 5
- SourceHealth 16
- Graphic 4点公開済み

Google Search Console直近28日：

- Clicks 0
- Impressions 8
- Homeのみ8 impressions
- Home average position 3.625
- Sitemap 22 URLs
- HomeはSubmitted and indexed
- 主要7記事はURL Inspectionで `URL is unknown to Google`

Bing Webmaster Tools：GSC Wizard側でAPI key未設定のため実データ未取得。
GA4：GSC Wizard側でAnalytics scope未接続。

## 1. 勝ち方

単純な「おすすめランキング」競争へ寄せない。

競合の主戦場：

- 総合ランキング
- 最安価格
- 編集部スコア
- 日本語対応一覧
- 一般比較

当サイトの差別化軸：

1. rule-first：失格しやすいルールから理解する
2. plan-level：会社単位ではなくプラン単位で管理
3. conflict transparency：公式情報の競合や未確定を隠さない
4. diagnosis：条件から3候補へ絞る
5. beginner path：基礎→診断→会社→プラン→詳細
6. payout / real-use evidence：実際の出金・利用事実を分離して扱う
7. X distribution：最新情報と市場反応を記事・診断・比較へ戻す

目標は「検索1位」単体ではなく、日本語圏でプロップファームを調べるときの情報インフラになること。

## 2. P0：Indexing

最優先はSEOコピー変更ではなく、Googleに主要記事を認識させること。

優先URL：

1. /one-step-two-step-instant
2. /daily-loss-vs-max-loss
3. /fixed-vs-trailing-drawdown
4. /articles/news-trading-rules
5. /articles/weekend-holding-rules
6. /articles/minimum-trading-days
7. /first-payout-checklist

対応：

- sitemap 200 / canonical self / indexable維持
- Home・Beginner・関連記事から文脈内部リンクを増やす
- 孤立ページを作らない
- 更新日・検証日をvisible contentとschemaで一致
- GoogleのURL Inspectionを定期確認
- Bing接続後はIndexNowを活用

## 3. P1：Content depth

薄い記事を単なる文字増量ではなく、検索者の判断に必要な分岐で拡張する。

### News Trading

追加：

- 評価中とFundedの違い
- high-impact / FOMC
- 前後何分制限の代表パターン
- open/close禁止と保有許可の違い
- 公式ルール確認手順
- 実際に失格につながる例

### Weekend Holding

追加：

- 金曜close必須 / allowed / add-on型
- weekend gap risk
- CFD / Futures差
- 長期保有戦略との相性
- 購入前チェックリスト

### Minimum Trading Days

追加：

- evaluation min days
- profitable days
- payout cycle min days
- minimum trading days 0でも即出金とは限らない
- 最短合格との違い

### Daily / Max Loss

- Balance / Equity
- daily reset
- initial balance固定 / reset時基準
- static / trailingとの組合せ
- 数値例

### Drawdown

- Static / EOD / Intraday / Closed Balance Trailing
- lock point
- withdrawal後の影響
- 同じ「Max 6%」でも難易度が違う理由

### First Payout

- KYC
- profitable days
- consistency
- buffer
- min withdrawal
- payout cap
- payment rail

## 4. P2：Search CTR

GSCデータが少ない現段階ではHome titleを大幅に変えない。

表示回数が増えた後、以下を優先：

- high impressions + low CTR
- position 3-10 + low CTR
- query intentとtitle不一致
- 検索結果で競合との差別化が弱いページ

Home title候補：

`プロップファーム比較【2026年】14社72プラン｜ルール・出金・30秒診断`

ただし実装は十分なGSCデータ取得後。

## 5. P3：Authority / Brand Demand

検索SEOだけでなく、指名検索を増やす。

- Xの反応が強いテーマを24-72時間以内に記事化
- 記事からXへ戻す
- 週刊プロップファーム通信を継続
- 出金報告 / rule change / security incident / CEO来日などニュースを一次情報付きで整理
- 「驚天童子」「プロップファームの歩き方」の指名検索を増やす
- 競合が扱いにくいConflict / HOLD / Legacyを透明に公開

## 6. P4：Firm Authority Pages

14社すべてを同じ深さにせず、需要と関係性で重点化。

重点候補：

- Fintokei
- Funded7
- FTM
- Blue Guardian
- Hantec Trader
- SuperFunded
- Blueberry Funded / Futures
- FundingPips

各Firmで目指す構造：

- 何の会社か
- 日本人利用可否
- 現行プラン
- 失格ルール
- 出金条件
- ニュース / weekend
- platform
- 日本語
- 価格
- 現在のConflict / caution
- 実利用 / 出金Evidence
- FAQ
- 公式source

## 7. P5：Measurement

Google Search Console：接続済み。

毎週見る：

- indexed URLs
- clicks / impressions
- queries
- pages
- CTR
- average position
- position 4-20 opportunity
- cannibalization
- device

GA4接続後：

- pageviews / users
- X / Direct / Organic
- landing pages
- mobile / Safari
- beginner_course_start / next / complete
- diagnosis_start / complete
- Firm selector engagement
- price / coupon reach

Bing接続後：

- Bing / Yahoo / DuckDuckGo organic
- IndexNow
- crawl issues
- query / page stats

## 8. North Star

短期：主要22URLを検索エンジンに認識させる。
中期：ルール系long-tailで上位面を増やす。
長期：「プロップファームのことを日本語で確認するなら、まずプロップファームの歩き方」という第一想起を取る。

ランキングサイトではなく、**日本語プロップファーム情報の基準点**を目指す。
