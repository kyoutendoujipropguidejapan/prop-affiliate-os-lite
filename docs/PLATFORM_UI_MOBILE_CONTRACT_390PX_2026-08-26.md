# PLATFORM UI / MOBILE CONTRACT — 390PX

更新日：2026-08-26 JST
Status：UI PREIMPLEMENTATION CONTRACT
Production code changes：NONE

## 1. Principle

Platform Hub / Detail / Compareは390px firstで設計し、Desktop向け横長比較表をMobileへそのまま縮小しない。

## 2. Hub

390px：
- 1 column platform cards
- card title wrap
- concise 2–4 key facts
- no horizontal scroll
- status / checked date readable
- detail CTA only if route public

## 3. Detail

390px section order：
1. H1 / intro
2. beginner summary
3. access surfaces
4. general features
5. Firm-specific variance caution
6. verified Firm links when accepted
7. glossary / FAQ
8. status / disclaimer

## 4. Comparison UI

Future `/platforms/compare/`：

Default mobile strategy：
- filter / choose 2–3 platforms
- attribute cards or stacked rows
- status labels next to values
- progressive disclosure

横幅の広い9-column tableをMobile defaultにしない。

Desktop tableを使う場合もMobileでは別presentationを許可。

## 5. Long labels

以下は折返しを許容：
- Match-Trader
- Data Entitlement
- Firm × Platform
- Algorithmic Trading
- Platform固有日本語label

text-overflowで重要Statusを隠さない。

## 6. Status display

Icon / colorだけでStatusを表さずtext labelも表示。

- 公式根拠で確認済み
- 条件付き・追加確認が必要
- 未確認
- 非対応
- 情報不足・不明

## 7. Disclaimer

- font sizeを読めないほど小さくしない
- accordionに完全に隠して必須Disclosureを見えなくしない
- PR表示はAffiliate CTA付近でもvisible

## 8. CTA

- Official info CTAとAffiliate CTAを区別
- tap target follows existing site standard
- adjacent CTAsが誤tapしやすい配置を避ける

## 9. QA

- horizontal overflow = 0
- clipped text = 0
- status hidden = 0
- dead CTA = 0
- disclaimer readable
- orientation / 390px fresh render
- actual iPhone Safari before public enable

Final Status：
`PLATFORM_390PX_UI_CONTRACT_CONFIRMED`
