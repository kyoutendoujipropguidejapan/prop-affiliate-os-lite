# Voice of Customer Baseline Method 2026-08-25

確認日：2026-08-25 JST
対象：プロップファームの歩き方 / Pain Database / Home Pain Router
目的：Xで新規調査を必須条件にせず、これまで蓄積した日本人トレーダーの声・質問・行動・レビュー・問い合わせを優先してサイト設計へ反映する。

## 0. 結論

X検証は実装前の必須Gateにしない。

優先順：

1. 既存の一次Voice / 実利用記録
2. 既存の行動データ
3. 既存の公式問い合わせ / Reviewer観察
4. GA4 / GSC / site behavior
5. Xは不足部分の追加検証・反証に使用

目的はXで反応を取ることではなく、既存Evidenceを最大限利用してPain設計を行い、データ不足の箇所だけXで補うこと。

## 1. 統計化の単位

市場統計と呼ぶためには、元の個票が必要。

Voice record最低fields：

- record_id
- date
- source_type
- anonymous_person_id（個人特定情報は保持しない）
- segment
- stage
- exact_or_paraphrased_voice
- pain_tag
- action_tag
- firm / plan（必要な場合）
- evidence_level
- duplicate_group

同一人物が同じ悩みを繰り返した場合は、原則1 unique voiceとして集計し、mentionsは別集計する。

## 2. Source type

A：本人から直接受けた質問 / DM / コメント / Review team feedback
B：実際の利用・出金・失格・KYC等の行動記録
C：日本人利用者報告をユーザーが確認した記録
D：Firm担当者への公式問い合わせ
E：公式FAQ / Terms / Product data
F：Chat / AI仮説

Pain prevalenceの統計ではA〜Cを中心にし、D/Eは市場の声の件数へ混ぜない。
Fは件数0として扱い、仮説タグのみ。

## 3. 既存資料から確認できる反復論点

現時点のProject記録では、以下が繰り返し重要項目として管理されている。

- 出金条件 / KYC
- Daily Loss / Max Loss / DD
- Minimum Trading Days / Profitable Days
- News Trading
- Weekend Holding
- 1 Step / 2 Step / Instantの選択
- 日本居住者可否 / 日本語Support
- Copy Trading / EA
- 価格 / 割引 / Purchase timing
- Rule change / Source conflict
- Security / Incident

ただし、これは現状では『資料内での論点出現頻度』であり、『日本人利用者の何%が悩んでいる』という人口統計ではない。

## 4. 初期反映ルール

個票の完全集計前でも、以下はHome / Guide設計のEvidenceとして利用できる。

### Strong

- 複数の独立した一次Voiceがある
- 実際の行動記録がある
- 過去の問い合わせで繰り返し出ている

→ Home Router /主要Guide候補

### Medium

- Project内で反復するが個票不足
- Reviewer観察とRule dataが一致

→ Guide / FAQ /内部リンク候補

### Hypothesis

- Chat推論のみ
- 市場感のみ

→ Home primary入口には使わず、追加検証候補

## 5. Xの役割

X = 必須調査装置ではなく補助検証装置。

使用する場合：

- 既存Voiceでサンプルが薄いPain
- 2つの導線候補の優先順位が拮抗
- 新しい市場変化の確認
- 言葉遣い / inner monologueの精度向上

既存一次Evidenceが十分なら、X投稿を待たずサイトへ反映してよい。

## 6. 今後の統計

集計は二種類に分ける。

### Unique Voice Count

何人の独立した利用者が同じPainを持っていたか。

### Mention Count

同じPainが何回出たか。

Publicに出す場合はN数と期間を明示する。
例：`2026年8月までに確認した匿名化された相談42件中...`

元個票が揃っていない期間について、後から推測で人数を作らない。

## 7. Design Gate変更

Home Pain RouterはX検証待ちにしない。

新Gate：

1. 既存Voice / Project recordをEvidence coding
2. Strong / Medium / Hypothesis分類
3. Strong中心にHome Router initial版を設計
4. GA4 / Search / actual usageで改善
5. Xは必要なPainだけ追加検証

## Status

- VOC methodology = READY
- Historical evidence coding = NEXT
- X pre-validation requirement = REMOVED
- Home Router = can proceed after evidence coding
