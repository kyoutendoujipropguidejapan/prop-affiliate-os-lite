# FIRM DIRECTORY HUB CONTENT SPEC

更新日：2026-08-26 JST
Status：CONTENT / IA CONFIRMED
Production code changes：NONE

Purpose：将来の `/firms/` を、14社個別ページへの入口として設計する。ランキングLPではなく、初心者が条件を確認して各Firm詳細へ進むDirectory Hubとする。

## 1. Route

`/firms/`

個別Routeは `FIRM_DETAIL_ROUTE_SLUG_MATRIX_2026-08-26.md` を参照し、Production実装時にroute collisionを再確認する。

## 2. Hub purpose

このページの目的：
- サイト内のFirm Entityを一覧できる
- 何から見ればよいか分からない初心者を詳細ページへ案内する
- Diagnosis / Comparisonの結果からFirm Detailへ自然に遷移する
- Campaign / Couponを一覧の順位要因にしない

## 3. Page order

1. Breadcrumb / H1
2. 初心者向け説明：Firm一覧の見方
3. まず確認する3点（ルール / 入口 / 取引環境）
4. Firm directory cards
5. Status explanation
6. Diagnosisへの導線
7. Platform / Payout将来導線（公開済みのみ）
8. Disclosure / Disclaimer

## 4. Firm card minimum fields

- Firm name
- Firm ID（内部。公開表示は任意）
- high-level program type
- Japan status（確認済み範囲）
- Japanese support/UI status（事実がある場合）
- platform display string（既存Layer）
- verification / last checked
- `詳しく見る` internal CTA

価格・Coupon・CommissionはCard主役にしない。

## 5. Ordering

Default orderはCommercial relationship / commission / couponで決めない。

許容候補：
- existing Production order
- alphabetical / canonical order
- manually fixed neutral order

Diagnosis rankingをDirectoryの恒久順位へ流用しない。

将来sort/filterを追加する場合も、Affiliate revenueを入力にしない。

## 6. Status handling

- verified → 公式根拠で確認済み
- conditional → 条件付き・追加確認が必要
- unverified → 未確認
- unsupported → 非対応
- unknown → 情報不足・不明

HOLD planがあるFirmでもFirm全体を自動的に非対応扱いしない。

## 7. SEO

Title候補：
`プロップファーム一覧｜各社のプラン・ルール・取引環境を確認`

H1候補：
`プロップファーム一覧｜まずルール・入口・取引環境から確認`

Meta候補：
`プロップファーム各社のプラン、主要ルール、日本語対応、取引環境などを確認し、詳しい個別ページへ進める一覧です。価格や割引だけでなく利用条件から比較できます。`

## 8. Compliance

- `おすすめ順` と誤認するUI禁止 unless明示根拠あり
- sponsored Firmを上位固定する場合はCommercial placementとして別表示が必要。初期版では採用しない
- affiliate relationshipはDirectory orderへ影響させない
- Japan eligibilityとregulatory statusを混同しない
- verified dateを維持
- Official / Affiliate CTAをDirectory cardで混ぜない。初期版はinternal detail CTA中心

## 9. Future expansion

Platform Hub公開後：Firm card/detailからPlatform Entityへ接続。
Payout公開後：Firm DetailからPayout Relationへ接続。

Directory Hub自体へPayout Route DBをflattenしない。

## 10. Release strategy

Pilot 2 Firmだけでも `/firms/` を公開するか、一定数揃ってから公開するかはProduction implementation時に判断可能。ただし未作成Firmの空Routeは生成しない。

推奨：Pilot時は既存比較/selectorから2 Firm detailへのdirect linkで検証し、Directory Hubは4〜6 Firm以上のdetail pageが揃った時点で公開判断。

Final Status：
`FIRM_DIRECTORY_HUB_SPEC_CONFIRMED`
