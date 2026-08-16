# M12｜監視Dry Run用URLセット確定

更新日：2026-08-16 JST
対象：プロップファームの歩き方
前提：M05 Source Monitoring Spec / M06 SourceHealth / M10 Source Monitoring Automation Design

## 0. 目的

M10の監視自動化を、いきなり14社全URLへ広げず、**少数の公式公開URLで誤検知・取得失敗・意味差分分類の精度を確認する**。

初期Dry Runは14日間を目安とし、サイト・Master・SourceHealthへ自動反映しない。

フロー：

`公式URL取得 → 正規化 → hash比較 → 差分 → noise filter → change type候補 → 人間確認`

---

# 1. 結論

## Primary Dry Run：5 URL

最初にFetcherへ入れる本命セット。

| ID | Firm | Source | URL | Priority | Watch | Frequency | SourceHealth | 人間確認 |
|---|---|---|---|---|---|---|---|---|
| DR01 | Fintokei | 速攻プロ 公式Help | https://support.fintokei.com/ja/articles/12040973-速攻プロプランの各ステップにはどのようなルールがありますか | A2 | Profit Target / Daily Loss / Max Loss / Min Days / Effective Date / legacy-new split | 週次 | Swift競合 | 必須 |
| DR02 | Fintokei | 参加条件・制限国 公式Help | https://support.fintokei.com/ja/articles/6538820-fintokeiに参加できる条件はありますか | A2 | Restricted countries / temporary restrictions / new-purchase restrictions / Japan / age | 週次 | eligibility全般 | 必須 |
| DR03 | FundingPips | Get Started 公式Help | https://help.fundingpips.com/hc/en-us/articles/44390730743825-Get-Started | A2 | Model list / account sizes / eligibility / restricted countries / first-purchase coupon wording | 日次 | SH011周辺・eligibility | 重要変更は必須 |
| DR04 | The5ers | Promotions公式ページ | https://the5ers.com/promotions/ | A4 | promotion / coupon / discount / valid until / program availability | 日次 | campaign | Campaignのみ確認 |
| DR05 | Hantec Trader | Instant Lite 公式Help | https://help.htrader.hmarkets.com/en/support/solutions/articles/158000445802-instant-lite | A2 | Daily Loss / Max Loss / trailing / add-on / payout / weekend / EA | 週次 | Instant Lite競合 | 必須 |

### Primary 5の狙い

- DR01：**effective date + grandfathering** を正しく保持できるか
- DR02：**国リスト追加削除**を高精度に検出できるか
- DR03：1ページ内に複数カテゴリがある場合の**意味差分分類**を試す
- DR04：期限・割引率などの**高頻度commercial change**を試す
- DR05：既存Conflictを持つ**rule page**を安全に監視できるか

---

# 2. Shadow Cross-check：4 URL

Primaryで変更候補が出た場合のクロスチェック、またはDry Run後半で追加する。

| ID | Firm | Source | URL | Priority | Watch | Frequency | SourceHealth | 用途 |
|---|---|---|---|---|---|---|---|---|
| DR06 | Hantec Trader | Instant Lite Product JP | https://htrader.hmarkets.com/jp/programs/instant-lite/ | A4 | Max Loss / add-on / price / jurisdiction / payout | 週次 | Instant Lite競合 | DR05との公式内cross-check |
| DR07 | Funded Trader Markets | Instant Pro Daily DD FAQ | https://fundedtradermarkets.com/faq/how-does-the-maximum-daily-drawdown-limit-for-the-instant-pro-account-work | A3 | Daily Drawdown / calculation basis / breach | 週次 | FTM Instant Pro競合 | 3%記載側の継続監視 |
| DR08 | The5ers Futures | Futures EN | https://www.the5ers.com/futures/ | A4 | price / activation / Max Loss EOD / program availability | 週次 | locale price conflict | EN基準観測 |
| DR09 | The5ers Futures | Futures JP | https://the5ers.com/jp/futures/ | A4 | price / activation / Max Loss EOD / program availability | 週次 | locale price conflict | DR08とのlocale cross-check |

Shadow URLは最初から全件毎日回さない。Primaryで取得・正規化・分類が安定した後に順次有効化する。

---

# 3. 2026-08-16時点の初期Baselineで保持する重要Token

## DR01 Fintokei Swift

新規口座側の境界：

- `2026年7月15日以降に購入`
- Max Loss 3%
- Daily Loss 2%
- Profit Target 6%
- Minimum Trading Days 3
- Maximum Trading Days 60

旧口座側：

- `2026年7月15日より前に購入`
- Max Loss 6%
- Daily Loss 3%
- Profit Target 10%
- Minimum Trading Days 5
- time limitなし

**重要：旧側ブロックがページから消えた場合も、自動的にlegacy不要と判断しない。CRITICAL + human review。**

## DR02 Fintokei Eligibility

構造を3群に分けて保存：

1. service unavailable countries
2. temporary restriction countries
3. new-purchase restricted countries

さらに：

- age 18+
- Japanの存在/非存在
- payout method jurisdiction information

を別Fieldで持つ。

国リストは文字列全体ではなくset差分：

`added_countries[] / removed_countries[]`

で保存する。

## DR03 FundingPips Get Started

別Fieldへ抽出：

- trading_models[]
- account_sizes[]
- restricted_countries[]
- minimum_age
- first_purchase_coupon_code
- first_purchase_coupon_effect
- first_purchase_coupon_exclusions

1ページ内でcouponが変わってもRULE_CHANGEにしない。

## DR04 The5ers Promotions

抽出：

- promotion_name
- discount_percent
- program
- valid_until
- redeem target

`Valid Until`が過去日付のまま残るケースを想定し、ページ掲載＝現在有効と自動判定しない。

## DR05 Hantec Instant Lite

抽出：

- profit_target
- daily_loss
- max_total_loss
- dd_type
- minimum_profitable_days
- consistency
- payout_cycle
- reward_split
- weekend
- news
- EA
- add_on_max_loss_text

本文値とAdd-On説明が矛盾した場合、**同一ページ内Conflict**として保存する。

---

# 4. Noise Filter個別設定

## Fintokei Help / FundingPips Help

ignore候補：

- `こちらの回答で解決しましたか`
- support widget
- breadcrumb順序
- footer disclaimerのレイアウト変更
- related articles順序
- 検索UI

ただし `○週間前に更新` はhash対象からは外してよいが、ページ更新の補助metadataとして別保存する。

## The5ers

ignore候補：

- testimonial
- subscriber form
- social blocks
- footer navigation
- copyright year
- generic marketing hero copy

promotionsでは `% / Valid Until / Program name` は絶対に除去しない。

## Hantec

HelpとProductで同じ説明が重複しても重複自体をChangeにしない。

Product pageの価格カード順序変更はPRICE_CHANGE候補にはするがRULE_CHANGEへ昇格しない。

---

# 5. Severity

## CRITICAL

- Daily Loss
- Max Loss
- DD方式
- Profit Target
- Minimum Days
- Effective Date
- legacy/new purchase condition
- Restricted Countries
- Japan eligibility
- payout eligibility rule
- prohibited ↔ allowed

## HIGH

- plan追加/終了
- platform追加/終了
- payout cadence
- Profit Split
- account size availability

## MEDIUM

- price
- promotion
- coupon
- activation fee

## LOW / CONTENT_ONLY

- marketing copy
- section reorder
- styling
- footer
- testimonial

---

# 6. Dry Run実行順

## Day 0

全Primary URLを取得しBaseline Snapshot作成。

保存：

- final_url
- http_status
- etag / last-modified（存在時）
- normalized_hash
- structured fields
- important excerpt

## Day 1〜7

Primary 5のみ。

- Daily対象：DR03 / DR04
- Weekly対象もDry Run検証のためDay 1とDay 7で取得：DR01 / DR02 / DR05

## Day 8

誤検知レビュー。

- NOISE率
- Parser failure
- structured extraction failure
- duplicate events
- semantic classification mismatch

を確認。

## Day 8〜14

Shadowを追加。

- DR06
- DR07
- DR08
- DR09

SourceHealth cross-checkとlocale差分を試す。

---

# 7. Dry Run合格条件

本番監視へ拡張する前に最低限：

1. 同一内容の再取得で重複Change Eventを作らない
2. footer / cookie / section reorderだけでCRITICALを出さない
3. 数値変更をold → newで抽出できる
4. 国リスト追加削除をset diffで出せる
5. Fintokei Swiftの日付境界を保持できる
6. SourceHealth URLの変更を自動解消しない
7. A2 vs A4不一致をCONFLICT / NEEDS_CROSSCHECKへ送れる
8. 404 / 403 / 429 / parser failureで前回正本を上書きしない
9. 変更イベントにSource URL / Priority / excerpt / checked_atが残る
10. Master / SourceHealth / siteへの自動書込が0件

## 精度評価

14日間の人間レビューで、

- CRITICAL候補の誤検知が継続的に出る場合 → 拡張しない
- 同一イベントの重複が多い場合 → hash/normalizationを修正
- parser failureが特定ドメインで続く場合 → そのURLをbrowser-requiredへ
- 商用変更をRULE_CHANGEへ誤分類する場合 → category extractionを修正

数値目標を先に固定するより、Dry Runでは**誤ったCRITICALを安全に止められること**を優先する。

---

# 8. 実装MVPで必要な設定例

```text
source_id
url
firm
source_priority
watch_category
frequency
critical_keywords
ignore_patterns
sourcehealth_ids
extract_fields
browser_required=false
active=true
```

初期はCSS selectorを過度に固定せず、本文抽出 + heading/key-value認識を優先する。サイト改修でDOM classが変わっただけで監視不能になる構成を避ける。

---

# 9. 禁止事項

Dry Run中は以下をしない。

- Master自動更新
- SourceHealth自動解除
- DiagnosisPlanCurrent自動更新
- Work自動反映
- サイト自動公開
- Affiliate CTA自動変更
- couponの割引後価格計算
- login/private portal scraping
- 1時間未満の高頻度巡回

---

# 10. Dry Run後の判断

## GO

Primary 5で安定 → 14社最小監視セットへ拡張。

## CONDITIONAL GO

特定ドメインだけ不安定 → 安定URLのみ拡張し、不安定URLはmanual/browser-required。

## NO-GO

- CRITICAL誤検知が多い
- effective dateを失う
- country set diffが壊れる
- SourceHealthを自動解消しうる
- snapshot failureで正本を上書きする

場合はMVPを拡張しない。

---

# 11. 次工程

Work / Manusが止まっていても、このM12は実装前の正本として利用できる。

Replit等が利用可能になったら最初に実装するのはPrimary 5のみ。

実装順：

1. DR01〜DR05設定
2. fetch + normalize
3. baseline snapshot
4. same-content test
5. numeric / country / coupon extraction test
6. event JSON出力
7. manual review
8. DR06〜DR09追加
9. 14日Dry Run
10. GO判定後に14社へ拡張

公開処理は別工程とする。
