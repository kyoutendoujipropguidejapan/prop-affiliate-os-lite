# Release Candidate Final Verification 2026-08-25

確認日：2026-08-25 JST
対象：未公開Work / Graphic + Data Patch 統合状態
判定：**PASS_WITH_CAUTION**

## Release Candidate

現在の未公開WorkをRelease Candidateとして固定。

統合差分：

- Graphic：4画像、配置、関連CSS
- Data Patch：Blue Guardian / Hantec / SourceHealth
- 対応回帰テスト
- 変更ファイル9件 + 画像4件

差分fingerprint：

`83a32d0118ced8415e323e5fb3580ebb39d6b066c6242f68a6bbd6eb7deac910`

検証前後で完全一致。QAによるソース変更0、想定外差分0。

## Verification

- Regression：48/48 PASS
- Build：PASS
- Lint：error 0 / existing no-img-element warning 1
- git diff --check：PASS
- 新規BLOCKER：0
- 新規CRITICAL：0

## Fresh確認

### Blue Guardian

PASS。

- 11プラン
- Active 8 / 確認中1 / Legacy 2
- 1 Step Nano詳細開閉・全ルール表示正常

### Hantec Trader

PASS。

- Instant Lite詳細開閉正常
- Daily 3% / Max 5% / Add-on 6%
- 最低取引日数とPayout cycle条件を分離表示

### Diagnosis

PASS。

- Q1〜Q7完走
- Top3表示
- 理由2点 + 注意1点
- Block 5 / P042 / P070〜P072のTop3混入0

### Graphic

PASS。

- 4/4画像読込成功
- 960×640 / ratio正常
- Top / Diagnosis / Firm比較 / Selector / Beginner top表示正常
- CTA表示正常
- 画像欠損0
- 通常幅horizontal overflow 0
- site console error 0
- extension由来ログは分離

## Protected hashes

検証前後一致：

- Master：`c7a8410696594592065caea226efce2a6e21af3a52fd35b2749e3b09965d6f8d`
- DiagnosisLogicV2：`c0b52a8153c0be5c6e8e18f66ccc3b2348fa431dcb505a729767e19baed56f21`
- GA4：`9b878d2243e35fa7b87653ea5319184f9f745b56abf27a254f2314660e593c34`
- Sitemap：`f692026d220b5915beca858112823d718921c78456f4eeee1533705a646af971`
- Graphic 4点：検証前後一致

## Caution

390px実画面：**NOT_EXECUTABLE**。

既知の環境制約。再試行していない。本RCにおける唯一のCaution。

## Release status

- Release Candidate Final Verification：**PASS_WITH_CAUTION**
- Version保存：未実施
- commit / push：未実施
- publish：未実施
- Production：Version 80のまま

## Release判断

新規BLOCKER / CRITICAL = 0、統合回帰・fresh確認・protected hash・差分fingerprintはPASS。

次工程は新規実装ではなく、Release承認後の **Version保存 → Production publish**。

公開後、Production URLを実iPhoneで確認できるため、390px確認はpost-release限定確認として実行可能。重大なモバイル崩れが見つかった場合はVersion 80をrollback候補とする。
