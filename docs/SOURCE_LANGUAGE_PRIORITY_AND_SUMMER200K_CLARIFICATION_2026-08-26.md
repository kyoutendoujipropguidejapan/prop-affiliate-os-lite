# SOURCE LANGUAGE PRIORITY & THE5ERS SUMMER 200K CLARIFICATION

更新日：2026-08-26 JST
Status：APPROVED OPERATING CLARIFICATION

## 1. The5ers Summer 200K — correction of project record

ユーザーはThe5ers Summer 200Kの削除を指示していない。

正しい経緯：

1. 遡及監査の初回で、static/crawlableな公式Summerページに100K中心の表示しか見えなかった。
2. そこから監査側が独自に「200Kが終了・supersededの可能性」を高く見積もり、correction candidateへ入れた。
3. ユーザーから「Summer 200Kは現在も存在する」と訂正が入った。
4. そのため削除・100K-only化候補は撤回した。

したがって、今後以下のように記録する。

`NO USER DELETION INSTRUCTION / CURRENT AVAILABILITY ASSERTED BY OPERATOR / OFFICIAL DYNAMIC PURCHASE RECHECK PENDING`

禁止：
- 「ユーザーの指示で削除しなかった」と記録すること
- static landing page非表示だけで終了判定すること
- 100K中心の英語landing pageを根拠に200Kを自動削除すること

現行英語公式Summer landing pageは100K中心の静的表示を返す一方、公式Hub purchase flowはdynamicで、crawlerから完全なprogram selectorが取得できない。したがってstatic pageだけでは200Kの不存在を証明しない。

## 2. English-first freshness rule

ユーザー運用知見として、日本語ページは英語公式ページより更新が遅れるケースが多い。

そのためRules / Product Specs / Platform / Payout / PriceのCurrent Truth調査は原則：

1. English official current product / Help / FAQ / Rules
2. English official checkout / configurator / Terms
3. Japanese official page
4. other locale / direct official support

の順で開始する。

ただしEnglishを機械的に優先して結論にしない。

## 3. Japan-specific exception

以下は日本語・Japan-specific sourceを必須候補とする。

- Japan eligibility / restricted-country applicability
- JPY pricing
- Japan-only coupon / campaign
- Japanese support availability
- Japan-specific KYC/payment
- Japan-specific legal/service wording

Global ENで一般条件が確認できても、日本適用範囲は別Gate。

## 4. Locale conflict handling

JPとENが違う場合：
- ENをfreshness anchorにする
- page modified/effective dateを確認
- dedicated Rules / Helpを優先
- checkout/configuratorを確認
- cohort / purchase date / locale scopeを分離
- unresolvedなら HOLD / CONFLICT

翻訳ページが古い可能性は考慮するが、単に「日本語だから古い」と決めつけて無視しない。

## 5. Immediate re-audit impact

このルールにより、既存監査のうちlocale差が主要因だった項目を再確認する。

優先：
- The5ers Futures locale discrepancy
- Hantec Endurance availability wording
- Fintokei NEW20 Japan scope
- その他JP pageのみで作ったstaleness/conflict判定

Funded7のように英語公式同士でも値が競合する案件は、このルールでは解消しないためHOLD継続。

Final Status：
`ENGLISH_FIRST_FRESHNESS_APPROVED / JAPAN_SCOPE_SEPARATE_GATE / SUMMER200K_NO_DELETION_INSTRUCTION`
