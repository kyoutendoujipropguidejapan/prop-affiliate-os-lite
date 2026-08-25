# FIRM DETAIL ANALYTICS CONTRACT

更新日：2026-08-26 JST
対象：Firm個別ページの計測設計
位置づけ：GA4既存初期化を保護したまま、後続Measurement Releaseで使うContract。Firm Detail Pilot実装の必須条件ではない。

## 1. Principle
Firm Detailの公開を新規Analytics実装でブロックしない。

既存GA4初期化 `public/site-events.js` を使用し、新しい `gtag("config")` は追加しない。

## 2. Event候補
最小セット：
- `firm_view`
- `affiliate_click`
- `campaign_click`
- `coupon_copy`

既存Measurement v0.1と衝突しないことを優先する。

## 3. Common Parameters
許可候補：
- `firm_id`
- `program_id`（確認済みの場合のみ）
- `campaign_id`
- `coupon_id`
- `content_id`
- `asset_id`
- `cta_position`
- `page_path`
- `source_channel`

Unknown programを推測して送らない。

## 4. Event Rules
### firm_view
Firm Detail pageが実際に表示された時のみ。

### affiliate_click
Affiliate CTAの明示的クリックのみ。
Official information clickと混同しない。

### campaign_click
Official Campaign Layer内のCTAのみ。
通常Firm CTAと分離。

### coupon_copy
コードが実際にコピー操作された時のみ。
表示だけで発火しない。

## 5. PII / Sensitive Data Prohibition
送信禁止：
- name
- email
- phone
- KYC information
- date of birth
- address
- bank account
- card information
- wallet address
- payout recipient data
- personal trading history
- exact account identifier

## 6. Affiliate Independence
Affiliate commission / conversion valueをFirm ranking、Diagnosis、search order、verification statusへフィードバックしない。

計測は観測LayerでありFact Layerを変更しない。

## 7. Attribution Limitation
`affiliate_click` はsaleではない。
Sale / affiliate revenueはaffiliate portal等の別Revenue Ledgerで確認する。

因果関係を証明できない場合、Firm Detail閲覧をsale原因として断定しない。

## 8. Release Gate
Analytics追加を行う場合：
- existing GA4 init hash確認
- duplicate config 0
- event duplicate firing 0
- PII 0
- Official clickとAffiliate click分離
- campaign/base separation
- regression PASS

## 9. Firm Detail Pilot
Pilot初回ReleaseはAnalytics追加なしでもACCEPT可能。
後続Measurement Releaseで追加してよい。
