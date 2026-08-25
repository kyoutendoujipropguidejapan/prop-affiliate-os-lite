# FIRM_DETAIL_ROLLOUT_MATRIX

更新日：2026-08-26 JST
用途：Firm Detail Pilot成功後の14社横展開順とM14注意点の管理。

## 1. Rollout Principle

いきなり14社同時実装しない。

- Wave 0：Pilot 2社
- Wave 1：高優先4社
- Wave 2：中優先4社
- Wave 3：残り4社

各WaveごとにQA / Compliance / 390px / SEOを完了してから次へ進む。

M11本文をBaseとし、M14判定を必ず適用する。

## 2. Wave 0 — Pilot

| Firm | ID | 目的 | M14主要注意 |
|---|---|---|---|
| Fundora | PF003 | Simple template validation | Q1 PASS_WITH_CAUTION |
| Fintokei | PF001 | Complex template validation | Q2 UPDATE_REQUIRED / Q3-Q4 CAUTION / 速攻プロ限定Variant |

Pilot PASS条件：TemplateがSimple / Complex双方で破綻しないこと。

## 3. Wave 1 — Priority Expansion

| Firm | ID | 主な理由 | M14主要注意 |
|---|---|---|---|
| Funded Trader Markets | PF004 | 評価系/Instantを持つ複雑ケース | Q2 HOLD / Q3 CAUTION |
| Blueberry Futures | PF008 | Futures + DD方式差を扱う | Q2/Q4 UPDATE_REQUIRED |
| Trading Cult Pro | PF009 | Platform/モデル差・Campaign導線の検証に適する | Q2 CAUTION / Q5 UPDATE_REQUIRED |
| SuperFunded | PF007 | 比較的公開しやすい構成 | Q3 UPDATE_REQUIRED |

Wave 1ではHOLD FAQをCurrent factとして表示しない。

## 4. Wave 2 — Standard Expansion

| Firm | ID | M14主要注意 |
|---|---|---|
| The5ers | PF005 | Q1/Q2 UPDATE_REQUIRED / Q3/Q4 CAUTION |
| Hantec Trader | PF006 | Q2 HOLD / Q3/Q5 CAUTION |
| Blue Guardian | PF010 | Q1/Q3/Q4/Q5 CAUTION |
| Blueberry Funded | PF011 | Q2 UPDATE_REQUIRED / Q1/Q3/Q4 CAUTION |

## 5. Wave 3 — Controlled Expansion

| Firm | ID | M14主要注意 |
|---|---|---|
| Funded7 | PF002 | Q2/Q3 HOLD / Q5 UPDATE_REQUIRED / Q1 CAUTION |
| FundedElite | PF012 | Q3 HOLD / Q1/Q2 CAUTION |
| The5ers Futures | PF013 | Q3 UPDATE_REQUIRED / Q2/Q4 CAUTION |
| FundingPips | PF014 | Q3/Q5 CAUTION |

Wave 3はHOLD / SourceHealth / Eligibility等の注意が強いFirmを含むため、公開前再確認を厚くする。

## 6. Per-Firm Release Gate

各Firmで最低限：

- Firm ID一致
- M11 Base適用
- M14判定適用
- UPDATE_REQUIRED差替え確認
- HOLD非断定
- Current / Legacy / Campaign分離
- Official / Affiliate CTA分離
- PR disclosure
- Disclaimer
- last checked
- unique title/meta/H1
- canonical
- 390px PASS
- regression PASS

## 7. HOLD FAQ

M14 HOLD 5件：

- Funded7｜1フェーズ
- Funded7｜Instant
- Funded Trader Markets｜Instant Pro
- Hantec Trader｜Instant Lite
- FundedElite｜Flash Activation

HOLDは：

- FAQ schemaへ入れない
- Diagnosis Top3根拠へ使わない
- Firm Detailで確定値として断定しない
- 自動解除しない

## 8. Future Entity Connection

Firm Detail横展開完了後、別Release Trainで以下へ接続する。

1. Platform Hub / individual pages
2. Firm × Platform
3. Payout Source arrival
4. Payout Method / Provider / Route pages
5. Firm × Payout

Firm rollout中に未完成Platform/Payout Registryを再構築しない。

## 9. Stop Rule

1 Firmで重大なTemplate defectが見つかった場合、残りFirmへ機械的に横展開しない。

Waveを停止し、TemplateをPilotへ戻して修正・再QAする。
