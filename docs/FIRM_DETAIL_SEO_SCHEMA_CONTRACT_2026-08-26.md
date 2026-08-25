# FIRM DETAIL SEO / SCHEMA CONTRACT

更新日：2026-08-26 JST
対象：全Firm個別ページ

## 1. SEO Role
Firm個別ページはランキングLPではなく、各Firmの確認・比較・理解のためのEntity Detail Pageとする。

## 2. URL
基本形：`/firms/{firm-slug}/`

slugは既存Namingと衝突しないcanonical slugを1つだけ持つ。

## 3. Title
基本形：
`{Firm}とは？プラン・ルール・日本語対応を初心者向けに整理`

Firm特性により一部語句変更可。ただし以下禁止：
- 最強
- 絶対おすすめ
- No.1
- 必ず出金
- 安全保証
- 根拠のない最安 / 最速 / 最大

## 4. H1
1ページ1 H1。

基本形：
`{Firm}を使う前に確認したいプラン・ルール・取引環境`

Titleと完全一致必須ではないが、検索意図をずらさない。

## 5. Meta Description
- Firm名
- プラン
- 主要ルール
- 日本語 / 日本利用確認
- 初心者向け整理

を中心とし、割引を主役にしない。

変動Campaignを恒久metaへ埋め込まない。

## 6. Canonical
各公開Firm routeはself canonical。

Affiliate URL、campaign URL、tracking URLをcanonicalにしない。

## 7. Sitemap
公開QA PASS後のみ掲載。

Draft / HOLD / direct-access-disabled routeは掲載しない。

## 8. Structured Data
使用候補：
- BreadcrumbList
- FAQPage（M14安全ルール適用時のみ）

禁止：
- Review / AggregateRatingの捏造
- 星評価の構造化
- 画面に存在しないFAQのschema化
- HOLD FAQのschema化
- Coupon / Affiliate / Eligibility等の変動・注意項目を無理にFAQ schemaへ入れる

## 9. FAQ Schema Gate
FAQ schema化には以下すべて必要：
- 画面本文と完全一致
- M14でHOLDではない
- source conflictなし
-公開直前再確認済み

## 10. Internal Linking
Firm Detailから許可：
- beginner guide
- diagnosis
- comparison
- relevant rule guides
- Academy等accepted related page
- current campaign/coupon section

将来：
- Platform detail
- Payout detail

未公開routeへのリンクは禁止。

## 11. Duplicate / Cannibalization
Firm DetailはFirm全体のEntityページ。
Articleは特定テーマ。
Campaignは時限情報。
Couponは価格補助。

同一検索意図を複数canonical pageで競合させない。

## 12. Compliance SEO Gate
Title / meta / H1 / schemaにもCOMPLIANCE_BASELINE_V1を適用。

SEO目的でも事実を強めない。
Unknown / conditional / unverifiedを確定表現へ変換しない。
