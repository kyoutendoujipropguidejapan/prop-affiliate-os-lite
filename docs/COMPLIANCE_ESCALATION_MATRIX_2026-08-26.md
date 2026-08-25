# COMPLIANCE ESCALATION MATRIX

更新日：2026-08-26 JST
Status：MANDATORY GOVERNANCE
Production code changes：NONE

## 1. Purpose

通常の編集判断で処理してよいものと、Central Command / specialist reviewへEscalateすべきものを分離する。

## 2. Levels

### C0 — Routine editorial
通常のSource確認で処理可能。

例：
- typo
- outdated checked date
- neutral wording
- known campaign end
- FAQ PASS text sync

### C1 — Compliance caution
公開可能だが注意表示とEvidenceが必要。

例：
- provided review account
- sponsor relation
- affiliate CTA
- Japan availability with limited evidence
- vendor marketing claim requiring neutralization

### C2 — Central Command required
AI / Workが単独判断しない。

例：
- Firm service natureが不明
- Japanese regulatory statusに関する主張
- FSA warning / regulator warning signal
- payout refusal / fraud allegation
- security incident / personal-data incident
- direct-contact claim that conflicts with Terms
- legal threat / cease-and-desist
- claim using No.1 / safest / guaranteed等をどうしても使う必要

### C3 — Specialist review recommended before publication
高リスクで、必要に応じ日本法その他の専門家確認を検討。

例：
- 当サイト自身がfinancial product勧誘主体と評価され得る新Business Model
- revenue-share / performance-based structureが商品提供への関与を大きく変える
- user fundsを当サイトが受け取る／仲介する仕組み
- KYC / bank / wallet等のsensitive dataを当サイトが収集する仕組み
- regulated financial adviceに近い個別推奨機能

## 3. Stop rule

C2 / C3 signalを検知したら：

- publish停止
- status `COMPLIANCE_HOLD`
- evidence preserve
- claimを削除して無かったことにしない
- Central Commandへ報告

## 4. Review-account rule

Firmからfree / discounted / sponsored account提供がある場合：
- relation disclosure必須
- positive review保証禁止
- payout / result保証禁止
- reviewer自身のexperienceとOfficial Factを分離

## 5. Allegation rule

Fraud / scam / payout denial / data breach等：
- social postだけで事実化しない
- Firm statement / official notice / affected-user evidence等を分離
- unresolvedならCONFLICT / UNVERIFIED
- sensational headline優先禁止

## 6. Commercial pressure rule

Firmから文言修正依頼が来ても：
- factual error correctionは受理可能
- negative fact削除を対価条件にしない
- affiliate commission上昇でverification statusを変更しない
- sponsorshipでrankingを変更しない

Final Status：
`COMPLIANCE_ESCALATION_MATRIX_CONFIRMED`
