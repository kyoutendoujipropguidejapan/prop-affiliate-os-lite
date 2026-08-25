# PLATFORM DETAIL SEO MATRIX

更新日：2026-08-26 JST
Status：SEO PLANNING CONFIRMED
Production code changes：NONE

Public route実装はFirm Detail foundation後までHOLD。

| Platform | Route | Suggested SEO Title | Suggested H1 |
|---|---|---|---|
| MetaTrader 5 | `/platforms/mt5/` | `MetaTrader 5（MT5）とは？プロップファームで使う前に確認したい特徴` | `MetaTrader 5（MT5）をプロップファームで使う前に確認したいこと` |
| MetaTrader 4 | `/platforms/mt4/` | `MetaTrader 4（MT4）とは？プロップファームで使う前に確認したい特徴` | `MetaTrader 4（MT4）をプロップファームで使う前に確認したいこと` |
| TradeLocker | `/platforms/tradelocker/` | `TradeLockerとは？プロップファームで使う前に知りたい特徴と注意点` | `TradeLockerをプロップファームで使う前に確認したいこと` |
| cTrader | `/platforms/ctrader/` | `cTraderとは？プロップファームで使う前に知りたい特徴と注意点` | `cTraderをプロップファームで使う前に確認したいこと` |
| Match-Trader | `/platforms/match-trader/` | `Match-Traderとは？プロップファームで使う前に確認したい特徴` | `Match-Traderをプロップファームで使う前に確認したいこと` |
| DXtrade | `/platforms/dxtrade/` | `DXtradeとは？プロップファームで使う前に確認したい特徴` | `DXtradeをプロップファームで使う前に確認したいこと` |
| BlackArrow | `/platforms/blackarrow/` | `BlackArrowとは？プロップファームで使う前に確認したい特徴` | `BlackArrowをプロップファームで使う前に確認したいこと` |
| Quantower | `/platforms/quantower/` | `Quantowerとは？プロップファームで使う前に確認したい特徴` | `Quantowerをプロップファームで使う前に確認したいこと` |
| Volumetrica | `/platforms/volumetrica/` | `Volumetricaとは？プロップファームで使う前に確認したい特徴` | `Volumetricaをプロップファームで使う前に確認したいこと` |

## Meta description contract

各ページで重複生成せず、次の要素をPlatform固有情報に合わせて作る：

- Platformの利用形態
- 注文 / chart / analysisの特徴
- Firmによって仕様が異なる注意
- 初心者向け整理であること

「おすすめ」「最強」「勝ちやすい」等のranking / performance claimをmetaへ入れない。

## Canonical / Sitemap

- self canonical
- one H1
- no index until QA acceptance
- sitemap inclusion only after public release approval
- future compare pageとのcanonical衝突禁止

## Duplicate-content control

9 pagesで共通Disclaimerやstatus legendは許容するが、本文はPlatform固有Research Packから構成し、template文の大量複製を避ける。

Final Status：
`PLATFORM_DETAIL_SEO_MATRIX_CONFIRMED`
