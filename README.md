# プロップファームの歩き方｜開発ハンドオフ

このリポジトリは「プロップファームの歩き方」のAI/Codex/Manus向けハンドオフ基盤です。

## 現在地

- 本番：Version 78
- Work：利用上限のため一時停止中
- 最新データ正本：Master v2.2（2026-08-14）
- 対象：14社
- 内部管理：プラン単位
- 公開表示：ファーム → そのファームのプラン一覧 → 必要な詳細だけ展開

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

## GitHub/OSS方針

新規実装前に、まず既存資産とGitHubの成熟したOSSを確認します。ただしOSS導入自体を目的にしません。

現時点の候補：

- shadcn/ui：Accordion / Collapsible等のUI部品のみ部分流用候補
- Formity：30秒診断のマルチステップUXの参考候補
- TanStack Table：将来の絞り込み/faceting候補
- openstatusHQ/data-table-filters：高度な検索が必要になった場合のみ検討
- Payload：将来の管理画面候補

既存実装の方が軽く安全なら、新しい依存は追加しません。

## AIエージェント向け

最初に `AGENTS.md` と `docs/CURRENT_STATE.md` を読んでください。Work復活前の調査は `docs/MANUS_MASTER_PROMPT.md`、Work復活後は `docs/WORK_RESTART_PROMPT.md` を基準にします。
