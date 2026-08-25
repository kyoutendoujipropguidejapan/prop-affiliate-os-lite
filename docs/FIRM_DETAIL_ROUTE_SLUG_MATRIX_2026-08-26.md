# FIRM DETAIL ROUTE / SLUG MATRIX

更新日：2026-08-26 JST
位置づけ：14社Firm Detailのroute候補。Production実装前に既存route collisionを確認し、衝突時は中央判断へ戻す。

| Firm ID | Firm | Proposed Route | Phase |
|---|---|---|---|
| PF001 | Fintokei | `/firms/fintokei/` | Pilot |
| PF002 | Funded7 | `/firms/funded7/` | Later / caution |
| PF003 | Fundora | `/firms/fundora/` | Pilot |
| PF004 | Funded Trader Markets | `/firms/funded-trader-markets/` | Wave 1 |
| PF005 | The5ers | `/firms/the5ers/` | Wave 2 |
| PF006 | Hantec Trader | `/firms/hantec-trader/` | Wave 2 / verify current truth |
| PF007 | SuperFunded | `/firms/superfunded/` | Wave 1 |
| PF008 | Blueberry Futures | `/firms/blueberry-futures/` | Wave 1 |
| PF009 | Trading Cult Pro | `/firms/trading-cult-pro/` | Wave 1 |
| PF010 | Blue Guardian | `/firms/blue-guardian/` | Wave 2 |
| PF011 | Blueberry Funded | `/firms/blueberry-funded/` | Wave 2 |
| PF012 | FundedElite | `/firms/fundedelite/` | Later / HOLD caution |
| PF013 | The5ers Futures | `/firms/the5ers-futures/` | Wave 2 |
| PF014 | FundingPips | `/firms/fundingpips/` | Wave 2 |

## Rules
- routeはlowercase kebab-case
- canonical routeは1 Firmにつき1つ
- existing article slug / legacy route collisionをWork開始時に検査
- redirectが必要な既存routeを発見した場合は勝手に変更しない
- Affiliate path / campaign pathをFirm canonicalにしない
- Firm名変更・ブランド統合時はhistorical aliasとcurrent canonicalを分離

## Pilot
最初に実装するのはPF003 Fundora / PF001 Fintokeiのみ。

## HOLD
routeが決まっていても、HOLD / unresolved sourceを理由に本文を推測して埋めない。
