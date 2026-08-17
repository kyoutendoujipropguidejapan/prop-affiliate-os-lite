# プロップファームの歩き方｜開発ハンドオフ

このリポジトリは「プロップファームの歩き方」のAI/Codex/Manus/Work向けハンドオフ基盤です。

## 現在地

- 本番：Version 78
- Work：最新把握では利用上限のため一時停止中
- 最新データ正本：Master v2.2（2026-08-14）
- 対象：14社
- 内部管理：プラン単位
- 公開表示：ファーム → そのファームのプラン一覧 → 必要な詳細だけ展開
- M01〜M16：完了記録あり

## 最初に読む

1. `AGENTS.md`
2. `docs/CURRENT_STATE.md`
3. `docs/PROGRESS.md`
4. `docs/IMPLEMENTATION_READINESS.md`
5. 必要なタスク別実体ファイル

Work復活後は `docs/WORK_RESTART_PROMPT.md` を使用します。

## 重要：完了記録と実体ファイルを分ける

`docs/PROGRESS.md` に完了と記録されていても、GitHubに成果物全文が保存されているとは限りません。

実体確認済みの主要成果物：

- M08：`docs/M08_QA_REGRESSION_SPEC.md`
- M09：`docs/M09_SEO_CONTENT_PACK.md`
- M10：`docs/M10_SOURCE_MONITORING_AUTOMATION_DESIGN.md`
- M11：`docs/M11_FIRM_FAQ_CONTENT_PACK.md`
- M12：`docs/M12_DRY_RUN_SOURCE_SET.md`

M07 / M13 / M14 / M15 / M16等は、詳細成果物がGitHub未同期の部分があります。存在しない内容を推測して正本扱いしないでください。詳細は `docs/IMPLEMENTATION_READINESS.md` を確認します。

## 最重要方針

サイト体験は次の順番を守ります。

**見やすい → 少し分かる → 次が気になる → 自分で進みたくなる**

価格や割引を主役にせず、初心者がルール・無料トライアル・取引環境を理解してから候補を絞れる構成にします。

## 変更してはいけない原則

- DiagnosisLogicV2を不用意に変更しない
- Affiliate、コミッション、クーポン、価格を診断スコアに使わない
- SourceHealthで競合中の値を勝手に確定しない
- 割引適用後の金額を公開画面で自動計算しない
- 公式情報リンクとAffiliate CTAの役割を分離する
- 全プランの詳細カードを一度に並べない
- 本番へ自動公開しない
- Fintokei速攻プロの新規購入Variantと旧口座を混同しない
- HOLD 5件を自動unblockしない

## 公開前Gate

`docs/M08_QA_REGRESSION_SPEC.md` がQAの唯一の正本です。

- BLOCKER = 0
- CRITICAL = 0
- 390px fresh render PASS
- 人間承認

を満たすまで公開しません。

## GitHub/OSS方針

新規実装前に、まず既存資産とGitHubの成熟したOSSを確認します。ただしOSS導入自体を目的にしません。

現時点の候補：

- shadcn/ui：Accordion / Collapsible等のUI部品のみ部分流用候補
- Formity：30秒診断のマルチステップUXの参考候補
- TanStack Table：将来の絞り込み/faceting候補
- openstatusHQ/data-table-filters：高度な検索が必要になった場合のみ検討
- Payload：将来の管理画面候補

既存実装の方が軽く安全なら、新しい依存は追加しません。
