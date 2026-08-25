# PLATFORM BEGINNER GLOSSARY CONTENT PACK

更新日：2026-08-26 JST
Status：CONTENT READY / NOT IMPLEMENTED

Platform Hub / Detailで共通利用できる初心者向け用語集。Firm固有値を入れない。

## 取引プラットフォーム

チャートを見たり、注文を出したり、保有ポジションを管理したりするための取引画面・ソフトウェアです。プロップファームそのものとは別の役割です。

## Connection / 接続先

取引プラットフォームが、口座・Broker・Firm・市場データ等とどのようにつながるかを示す概念です。同じPlatformでも接続先によって利用条件が異なる場合があります。

## Server / サーバー

口座への接続先として表示されることがある環境です。Platform名が同じでも、Firmや口座によって接続先が異なる場合があります。

## Execution / 約定・注文処理

出した注文がどのように処理されるかに関する概念です。Platform一般仕様だけで、特定Firmの約定速度や品質を判断することはできません。

## Market Data / 市場データ

価格、Bid/Ask、出来高、板情報など、取引画面へ表示される市場情報です。提供内容は市場・Data Provider・Firm・契約条件等で異なる場合があります。

## Data Entitlement / データ利用権限

どの市場データをどの深さ・リアルタイム性で利用できるかに関する権限です。PlatformにDOM機能があっても、必要なDataが提供されていなければ同じ表示になるとは限りません。

## DOM / Depth of Market / 板情報

価格帯ごとの注文数量など、市場の深さを見るための画面・機能です。Platformによって表示方式が異なり、利用できるDataも接続先によって変わります。

## Market Order / 成行注文

現在の市場価格付近で約定を目指す注文方式です。実際の約定価格は市場状況・取引条件等により変わる場合があります。

## Limit Order / 指値注文

指定した価格またはそれより有利な価格での約定を目指す注文方式です。

## Stop Order / 逆指値系注文

指定した条件に価格が到達した際に注文を有効化するために使われる注文方式です。Platformによって名称や動作が異なる場合があります。

## Stop Loss / SL

損失を一定範囲で止めるための決済条件です。SLを設定しても、相場状況等により指定価格と完全に同じ価格で約定することを保証するものではありません。

## Take Profit / TP

利益確定のために設定する決済条件です。

## OCO

一方の注文が成立した場合に、もう一方をキャンセルするよう設計された注文関係です。Platformや接続先によって仕様が異なります。

## EA / Expert Advisor

MetaTrader系で使われる自動売買プログラムの呼称です。PlatformがEAに対応していても、プロップファーム側がEA利用を許可しているとは限りません。

## Algorithmic Trading / 自動売買

ルールをプログラム化し、注文や判断を自動化する仕組みです。利用可否はPlatformとFirm ruleの両方を確認します。

## Copy Trading

別口座やstrategyの取引を複製・追随する機能や仕組みです。Platformに機能が存在しても、Firm ruleで禁止・制限される場合があります。

## Web / Desktop / Mobile

同じPlatformでも利用端末に応じた版が存在する場合があります。全Versionで同じ機能が使えるとは限りません。

## Slippage / スリッページ

注文時に想定した価格と実際の約定価格に差が出ることです。Platform名だけでスリッページの大小を断定しません。

## Latency / 遅延

情報伝達や注文処理にかかる時間を表す概念です。Vendor marketingの速度表現を、独立検証なしに比較ランキングへ使いません。

Final Status：
`PLATFORM_BEGINNER_GLOSSARY_READY`
