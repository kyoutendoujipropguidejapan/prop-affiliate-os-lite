# M08｜実装前QA・回帰テスト仕様

更新日：2026-08-16
対象：プロップファームの歩き方
本番：Version 78
前提：M01〜M07完了、Master v2.2を正本、公開前の未公開作業版を検証する。

---

## 0. 目的

Work復活後、P0実装によって「見た目は改善したが、既存導線・診断・SourceHealth・GA4・リンク・SEOが壊れた」状態を防ぐ。

この仕様は以下を同時に確認する。

- P0 Acceptance
- Smoke Test
- Full Regression
- 390px Mobile
- Diagnosis
- SourceHealth
- SEO
- GA4
- Link separation
- Error / Empty state

コード上の成功だけでは合格にしない。fresh renderと実操作を必須とする。

---

## 1. 重要度

| Severity | 判定 | 意味 |
|---|---|---|
| BLOCKER | 公開不可 | 診断誤判定、Block対象露出、重大導線断、横スクロール等 |
| CRITICAL | 修正後再確認 | P0要件未達、主要CTA/リンク/SEO/GA4破損 |
| MAJOR | 次版までに修正 | 主要ではないUX/文章/表示不整合 |
| MINOR | 公開後改善可 | 軽微な余白・補助文・非主要表示 |

---

## 2. Go / No-Go基準

### GO

次をすべて満たすこと。

1. BLOCKER = 0
2. CRITICAL = 0
3. 390px主要画面で横スクロール = 0
4. 14社一覧 → ファーム → プラン → 詳細が正常
5. 診断7問を完走できる
6. Block継続5件がTop3へ出ない
7. Fintokei速攻プロの条件付き解除を誤適用しない
8. DiagnosisLogicV2が変更されていない
9. Affiliate / Coupon / Price / Commissionが診断採点へ入っていない
10. 既存GA4 ID・主要既存イベントが維持されている
11. 公式情報リンクとAffiliate CTAが分離されている
12. 基礎講座既存URLが維持されている
13. SEOのtitle/meta/canonical/sitemapに重大異常がない
14. Build / regression / lintが通る

### NO-GO

次のどれか1つでも発生したら公開しない。

- Block対象がTop3に出る
- Fintokei旧口座へ新条件が適用される
- DiagnosisLogicV2が無断変更される
- 公式確認リンクがAffiliate URLへ置換される
- 主要ページで横スクロール
- 基礎講座URL変更・404
- 診断完走不能
- GA4既存イベント破損
- canonical誤設定で別ページへ統合される
- 価格/クーポンがトップや基礎講座の主役へ戻る

---

# 3. Smoke Test

| ID | Pri | 対象 | 前提 | 操作 | 期待結果 | Fail | 種別 |
|---|---|---|---|---|---|---|---|
| SM-01 | P0 | Top | 未公開版起動 | Top表示 | 正常表示、主要崩れなし | BLOCKER | 手動 |
| SM-02 | P0 | 390px | 390px viewport | Top〜主要セクション確認 | 横スクロールなし | BLOCKER | 手動 |
| SM-03 | P0 | 基礎講座 | Top表示 | STEP01→基礎講座 | 正常遷移 | CRITICAL | 自動可 |
| SM-04 | P0 | 診断 | 診断開始 | 7問回答 | 結果まで完走 | BLOCKER | 手動+自動 |
| SM-05 | P0 | Firm | ファーム一覧 | 任意1社→プラン→詳細 | 階層が自然、詳細展開可 | BLOCKER | 手動 |
| SM-06 | P0 | SourceHealth | テスト条件 | Block対象をTop3候補に近づける | Top3へ出ない | BLOCKER | 自動推奨 |
| SM-07 | P0 | Coupon | 特典ページ | 3区分初期表示 | すべて折りたたみ | CRITICAL | 手動 |
| SM-08 | P0 | Link | 任意Firm詳細 | 公式情報→開始CTA | 公式とAffiliateの遷移先が分離 | BLOCKER | 自動可 |
| SM-09 | P0 | SEO | 主要URL | head確認 | title/meta/canonical存在 | CRITICAL | 自動可 |
| SM-10 | P0 | GA4 | DebugView等 | 主要導線操作 | 既存イベント維持、二重発火なし | CRITICAL | 手動 |

---

# 4. 390px Mobile Test

| ID | Pri | 対象 | 操作 | 期待結果 | Fail | 種別 |
|---|---|---|---|---|---|---|
| MB-01 | P0 | Top | 390px表示 | document幅がviewport超過しない | BLOCKER | 自動+手動 |
| MB-02 | P0 | Top | Hero確認 | H1/Lead/CTAが欠けない | CRITICAL | 手動 |
| MB-03 | P0 | 全主要ページ | スクロール | 固定/sticky要素が本文を隠さない | CRITICAL | 手動 |
| MB-04 | P0 | CTA | 各主要セクション | Primaryが原則1つ、Secondary弱い | CRITICAL | 手動 |
| MB-05 | P0 | Firm list | 14社閲覧 | 巨大詳細カードが連続しない | CRITICAL | 手動 |
| MB-06 | P0 | Plan list | 5件以上のFirm | 一覧が縦に読め、表横スクロール不要 | BLOCKER | 手動 |
| MB-07 | P0 | Accordion | 複数開閉 | タップ正常、閉じてもレイアウト破損なし | CRITICAL | 手動 |
| MB-08 | P1 | Buttons | 全主要CTA | 指で押しやすいサイズ・余白 | MAJOR | 手動 |
| MB-09 | P0 | Diagnosis | Q1〜Q7 | 選択肢が画面外へ欠けない | BLOCKER | 手動 |
| MB-10 | P0 | Result | Top3 | 3候補が読みやすく広告一覧に見えない | CRITICAL | 手動 |
| MB-11 | P1 | Coupon | 展開 | code/effect/target/expiryが折返しで読める | MAJOR | 手動 |
| MB-12 | P0 | 404 | 直接アクセス | CTAが画面外へ飛び出さない | CRITICAL | 手動 |

---

# 5. 基礎講座 Regression

既存URLを変更しない。

- `/beginner-guide`
- `/beginner-guide/what-is-a-prop-firm`
- `/beginner-guide/no-need-to-buy-yet`
- `/beginner-guide/three-things-to-check`
- `/beginner-guide/rules-that-cause-disqualification`
- `/beginner-guide/find-your-fit`

| ID | Pri | 対象 | 操作 | 期待結果 | Fail | 種別 |
|---|---|---|---|---|---|---|
| BG-01 | P0 | Course Top | 直接アクセス | 200、内容正常 | BLOCKER | 自動可 |
| BG-02 | P0 | 01→02 | Next CTA | 02へ遷移 | CRITICAL | 自動可 |
| BG-03 | P0 | 02→03 | Next CTA | 03へ遷移 | CRITICAL | 自動可 |
| BG-04 | P0 | 03→04 | Next CTA | 04へ遷移 | CRITICAL | 自動可 |
| BG-05 | P0 | 04→05 | Primary CTA | 05へ遷移 | CRITICAL | 自動可 |
| BG-06 | P0 | 05→診断 | Primary CTA | 診断開始へ | CRITICAL | 自動可 |
| BG-07 | P0 | 全末尾 | Next Preview確認 | CTA前に次に分かることがある | CRITICAL | 手動 |
| BG-08 | P0 | 04 | Secondary | ルール比較がPrimaryより弱い | MAJOR | 手動 |
| BG-09 | P0 | 全講座 | 内容確認 | 価格/割引が主役化していない | CRITICAL | 手動 |

---

# 6. Firm → Plan → Detail Test

| ID | Pri | 対象 | 操作 | 期待結果 | Fail | 種別 |
|---|---|---|---|---|---|---|
| FP-01 | P0 | Firm list | 一覧表示 | 14社のみを主単位として表示 | BLOCKER | 自動+手動 |
| FP-02 | P0 | Firm list | スクロール | 65プラン詳細を一括展開しない | BLOCKER | 手動 |
| FP-03 | P0 | 任意Firm | 詳細を開く | 特徴→日本語→Trial→環境→注意→プラン順 | CRITICAL | 手動 |
| FP-04 | P0 | FundingPips | Firm表示 | 5プランがFirm内で確認可能 | CRITICAL | 自動+手動 |
| FP-05 | P0 | Plan list | 初期表示 | plan/type/target/max loss/特徴1行 | CRITICAL | 手動 |
| FP-06 | P0 | Plan detail | 展開 | Daily/DD/min days/news/weekend/payout等 | CRITICAL | 手動 |
| FP-07 | P0 | 確認中Plan | 展開 | 未確定値を断定せず「確認中」等 | BLOCKER | 自動推奨 |
| FP-08 | P1 | Firm末尾 | 次導線 | 診断/関連解説へ自然に進める | MAJOR | 手動 |

---

# 7. Diagnosis Test Matrix

DiagnosisLogicV2は変更禁止。

| ID | Pri | 条件 | 操作 | 期待結果 | Fail | 種別 |
|---|---|---|---|---|---|---|
| DG-01 | P0 | 初期 | 診断開始 | 「65プランを7問で3候補まで」等の期待値 | CRITICAL | 手動 |
| DG-02 | P0 | Q1〜Q7 | 通常回答 | 7問完走 | BLOCKER | 自動+手動 |
| DG-03 | P0 | 任意Q | 戻る→再回答 | 回答保持/変更が正常 | CRITICAL | 手動 |
| DG-04 | P0 | optional系 | 「こだわらない」選択 | エラーなく次へ | CRITICAL | 自動可 |
| DG-05 | P0 | 途中 | 進捗確認 | 残り問数が正しい | MAJOR | 手動 |
| DG-06 | P0 | 完了 | 結果表示 | Top3 = firm + plan | BLOCKER | 自動可 |
| DG-07 | P0 | 結果 | 各カード確認 | 「あなたとの相性」表示 | CRITICAL | 手動 |
| DG-08 | P0 | 結果 | 各カード確認 | 理由2点＋注意1点 | CRITICAL | 手動 |
| DG-09 | P0 | 結果 | 見出し確認 | 「なぜ、この3つが候補になったのか」 | CRITICAL | 手動 |
| DG-10 | P0 | 結果 | 表現確認 | おすすめ順位/品質ランキング表現なし | BLOCKER | 手動 |
| DG-11 | P0 | scoring | データ/コード差分確認 | Affiliate/commission/coupon/price未使用 | BLOCKER | コードレビュー |
| DG-12 | P0 | logic | 差分確認 | DiagnosisLogicV2不変 | BLOCKER | コードレビュー |
| DG-13 | P1 | browser | reload/back | 状態が破損せず安全に再開/初期化 | MAJOR | 手動 |

---

# 8. SourceHealth Test Matrix

## Block継続5件

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

| ID | Pri | 対象 | 操作 | 期待結果 | Fail | 種別 |
|---|---|---|---|---|---|---|
| SH-01 | P0 | Funded7 1 Phase | 条件を近づける | Top3に出ない | BLOCKER | 自動推奨 |
| SH-02 | P0 | Funded7 Instant | 条件を近づける | Top3に出ない | BLOCKER | 自動推奨 |
| SH-03 | P0 | FTM Instant Pro | 条件を近づける | Top3に出ない | BLOCKER | 自動推奨 |
| SH-04 | P0 | Hantec Instant Lite | 条件を近づける | Top3に出ない | BLOCKER | 自動推奨 |
| SH-05 | P0 | FundedElite Flash | 条件を近づける | Top3に出ない | BLOCKER | 自動推奨 |
| SH-06 | P0 | Public UI | 上記詳細 | 確定値として誤表示しない | BLOCKER | 手動 |

## Fintokei 速攻プロ 条件付き解除

M06結論：2026-07-15以降の新規購入口座に限り解除候補。

解除条件：

1. effective_from = 2026-07-15 を保持
2. new_purchase_only = true を保持
3. legacy/old accountsと分離
4. human_approved = true
5. 実装環境で条件判定できない場合はBlock継続

| ID | Pri | 前提 | 操作 | 期待結果 | Fail | 種別 |
|---|---|---|---|---|---|---|
| FK-01 | P0 | purchase=2026-07-14 | 候補評価 | 新条件適用しない | BLOCKER | 自動必須 |
| FK-02 | P0 | purchase=2026-07-15,new | 候補評価 | 承認済なら解除対象になり得る | BLOCKER | 自動必須 |
| FK-03 | P0 | purchase=2026-07-16,new | 候補評価 | 承認済なら解除対象になり得る | BLOCKER | 自動必須 |
| FK-04 | P0 | date不明 | 候補評価 | 安全側でBlock | BLOCKER | 自動必須 |
| FK-05 | P0 | old account=true | 候補評価 | Block | BLOCKER | 自動必須 |
| FK-06 | P0 | human_approved=false | 候補評価 | Block | BLOCKER | 自動必須 |
| FK-07 | P0 | 条件保持不可 | 実装確認 | 単純Noへ変更せずBlock維持 | BLOCKER | コードレビュー |

---

# 9. Price / Coupon Test

| ID | Pri | 対象 | 操作 | 期待結果 | Fail | 種別 |
|---|---|---|---|---|---|---|
| PC-01 | P0 | 特典ページ | 初期表示 | 公式/個人/確認中の3区分折りたたみ | CRITICAL | 手動 |
| PC-02 | P0 | Coupon | 展開 | code/effect/target/expiry表示 | CRITICAL | 自動+手動 |
| PC-03 | P0 | Coupon | 表示確認 | 割引後最終価格を計算表示しない | BLOCKER | 自動可 |
| PC-04 | P0 | Coupon | footer/補足 | 購入前に公式で条件/価格確認案内 | CRITICAL | 手動 |
| PC-05 | P0 | FundingPips | coupon表示 | 公式詳細と概要の差異を断定解消しない | BLOCKER | 手動 |
| PC-06 | P1 | Hantec/Blue Guardian等 | 不明特典 | 「コード有効・内容確認中」等 | MAJOR | 手動 |

---

# 10. Official / Affiliate Link Separation

| ID | Pri | リンク種別 | 期待遷移 | Fail | 種別 |
|---|---|---|---|---|---|
| LK-01 | P0 | 詳しいルール | 通常公式URL | BLOCKER | 自動可 |
| LK-02 | P0 | 情報源 | 通常公式URL | BLOCKER | 自動可 |
| LK-03 | P0 | 公式情報を確認 | 通常公式URL | BLOCKER | 自動可 |
| LK-04 | P0 | 始める/購入/申し込む | 設定済みAffiliate CTA | CRITICAL | 自動可 |
| LK-05 | P0 | FundingPips情報 | Help/official | BLOCKER | 自動可 |
| LK-06 | P0 | FundingPips開始 | referral URL | CRITICAL | 自動可 |
| LK-07 | P0 | diagnosis result primary | プラン詳細 | CRITICAL | 手動 |
| LK-08 | P0 | diagnosis result official secondary | 公式情報 | CRITICAL | 手動 |

---

# 11. SEO Test Matrix

| ID | Pri | 対象 | 確認 | 期待結果 | Fail |
|---|---|---|---|---|---|
| SEO-01 | P0 | Top | title | 固有・適切 | CRITICAL |
| SEO-02 | P0 | Beginner 01〜05 | title | 各ページ固有 | CRITICAL |
| SEO-03 | P0 | Firm14社 | title | 各社固有 | CRITICAL |
| SEO-04 | P0 | 主要ページ | meta description | 空/重複過多なし | MAJOR |
| SEO-05 | P0 | 全index対象 | canonical | 自己canonicalまたは意図した正規URL | BLOCKER |
| SEO-06 | P0 | 全主要 | H1 | 原則1つ、検索意図と整合 | CRITICAL |
| SEO-07 | P0 | sitemap | URL一覧 | Top/講座/14社/主要比較等を含む | CRITICAL |
| SEO-08 | P0 | robots | index対象 | 誤noindexなし | BLOCKER |
| SEO-09 | P1 | 内部リンク | 関連導線 | 検索→理解→比較→診断の流れ | MAJOR |
| SEO-10 | P1 | カニバリ | Top vs 講座01等 | 同一意図を過剰競合させない | MAJOR |

可能なら自動化：head要素/canonical/sitemap/robots/status code/重複title。

---

# 12. GA4 Test Matrix

既存GA4 IDは変更禁止。

既存主要イベント：

- beginner_course_start
- beginner_course_next
- beginner_course_complete
- 既存診断/比較/外部CTA系

追加候補：

- home_to_beginner
- firm_open
- firm_plan_list_view
- plan_detail_open
- plan_to_diagnosis
- diagnosis_start
- diagnosis_complete
- result_plan_open
- external_cta

| ID | Pri | 操作 | 期待結果 | Fail |
|---|---|---|---|---|
| GA-01 | P0 | Course開始 | beginner_course_start 1回 | CRITICAL |
| GA-02 | P0 | Course次へ | beginner_course_next 1回/遷移 | CRITICAL |
| GA-03 | P0 | 05完了 | beginner_course_complete 1回 | CRITICAL |
| GA-04 | P0 | 診断開始/完了 | 各イベント1回 | CRITICAL |
| GA-05 | P0 | Firm開く | firm_open 0または1回（仕様通り） | MAJOR |
| GA-06 | P0 | Plan詳細 | plan_detail_open二重発火なし | CRITICAL |
| GA-07 | P0 | Result→Plan | result_plan_open二重発火なし | CRITICAL |
| GA-08 | P0 | External CTA | 1クリック1発火 | CRITICAL |
| GA-09 | P0 | Back/Reload | 不要な再発火なし | CRITICAL |

---

# 13. Error / Empty State

| ID | Pri | 条件 | 期待結果 | Fail |
|---|---|---|---|---|
| ER-01 | P0 | 存在しないURL | 404、基礎講座/診断への導線 | CRITICAL |
| ER-02 | P0 | 存在しないFirm | 安全な404/empty、壊れない | CRITICAL |
| ER-03 | P0 | 存在しないPlan | 安全な404/empty | CRITICAL |
| ER-04 | P0 | rule value欠損 | `確認中`等、0/falseへ誤変換しない | BLOCKER |
| ER-05 | P0 | Source conflict | `確認中`表示、確定値にしない | BLOCKER |
| ER-06 | P1 | browser back | 状態が破損しない | MAJOR |
| ER-07 | P1 | reload | 主要ページ正常復帰 | MAJOR |
| ER-08 | P1 | direct deep link | Firm/Plan詳細へ直接入り正常表示 | MAJOR |

---

# 14. P0 Acceptance Test

M07 P0実装後、最低限以下を全件PASSする。

1. 390px横スクロールなし
2. Primary CTA競合なし
3. ページ末尾Next Previewあり
4. ファーム→プラン→詳細のprogressive disclosure
5. 14社共通Firm template正常
6. 診断7問コピー/進捗正常
7. Result「なぜこの3つ？」＋理由2＋注意1
8. SEO title/meta/canonical正常
9. 内部リンク正常
10. sitemap正常
11. SourceHealth競合安全表示
12. 価格/クーポン補助位置維持
13. GA4既存イベント維持
14. Block継続5件がTop3に出ない
15. Fintokei速攻プロを条件判定不能ならBlock維持
16. 公式/Affiliate link separation維持
17. Build/Regression/Lint PASS

---

# 15. Full Regression実行順

1. Build / lint / existing automated tests
2. Smoke Test
3. 390px Top
4. Beginner 01〜05
5. Firm list 14社
6. 各Firm plan grouping
7. Plan details
8. Diagnosis Q1〜Q7
9. SourceHealth Block matrix
10. Fintokei date/purchase matrix
11. Coupon/Price
12. Official/Affiliate links
13. SEO head/sitemap/robots
14. GA4 DebugView
15. 404/empty/direct URL
16. 390px fresh render再確認
17. 最終Go/No-Go

---

# 16. 自動化推奨

Work/コード側で可能なら次は自動テスト化を優先する。

- 主要URL HTTP status
- 既存beginner URLs
- Firm count = 14
- Block継続5件 Top3 exclusion
- Fintokei date boundary test
- DiagnosisLogicV2 snapshot/hash
- Discounted final price文字列の禁止検知
- Official/Affiliate URL分類
- title重複
- canonical
- sitemap entries
- horizontal overflowの簡易DOM check
- GA4 event handler重複の静的確認

fresh render・視認性・CTA強弱は手動必須。

---

# 17. Work向け短縮QAプロンプト

以下をそのままWorkへ渡せる。

---

P0実装後、まだ公開しないでください。

GitHub `kyoutendoujipropguidejapan/prop-affiliate-os-lite` の `docs/M08_QA_REGRESSION_SPEC.md` を正本としてQAを実施してください。

順番：

1. Build / lint /既存回帰テスト
2. Smoke Test
3. 390px fresh render
4. 基礎講座01〜05
5. 14社 Firm → Plan → Detail
6. 診断7問とResult Top3
7. SourceHealth Block5件
8. Fintokei速攻プロの2026-07-15境界・新規購入・旧口座分離・human approval条件
9. Price/Coupon
10. Official/Affiliate link separation
11. SEO title/meta/canonical/sitemap/robots
12. GA4既存イベント＋追加イベントの二重発火
13. 404/empty/direct URL
14. 390px最終fresh render
15. Go/No-Go判定

BLOCKERまたはCRITICALが1件でもあれば公開可能と判定しないでください。

特に次を絶対条件とします。

- DiagnosisLogicV2変更なし
- Affiliate/commission/coupon/priceを診断採点に使用しない
- Funded7 1フェーズ / Funded7 Instant / FTM Instant Pro / Hantec Instant Lite / FundedElite Flash ActivationはTop3 Block継続
- Fintokei速攻プロは条件判定できない場合Block継続
- 旧口座へ2026-07-15以降の新規購入条件を誤適用しない
- 公式情報リンクとAffiliate CTAを分離
- 基礎講座既存URL維持
- 390px横スクロールなし
- 本番Version 78をまだ変更しない

終了時に、

- PASS件数
- FAIL件数
- BLOCKER / CRITICAL / MAJOR / MINOR内訳
- FAIL Test ID
- 390px確認結果
- SourceHealth確認結果
- GA4確認結果
- Go / No-Go

を報告してください。

---

# 18. 完了定義

M08自体の完了は「テスト仕様作成」であり、実テストのPASSを意味しない。

実装後のリリース候補は、上記Go条件をすべて満たし、fresh renderと実操作QAを通過した場合のみ公開候補とする。
