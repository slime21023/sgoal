---
name: sgoal-review
description: 審查輕量需求規格並建立 .sgoal/REVIEW.md 的實作就緒度技能。用於檢查需求品質、INVEST、MoSCoW 優先級、Volere fit criterion、追溯性、衝突、風險、變更影響、缺漏決策，以及實作前的 ready 或 not ready 狀態。
---

# SGoal Review

## 概覽

使用此技能審查 `.sgoal/SPEC.md` 並建立 `.sgoal/REVIEW.md`。把 Review 視為可控的就緒檢查：判斷需求是否清楚、可測試、可追溯，並且足以進入實作。

## 使用方式

使用者可用下列方式呼叫此技能：

```text
Use $sgoal-review to check .sgoal/SPEC.md and create .sgoal/REVIEW.md.
```

主要輸入是 `.sgoal/SPEC.md`，並可讀取 `.sgoal/INTAKE.md` 作為追溯來源。輸出固定為 `.sgoal/REVIEW.md`，除非使用者明確指定其他路徑。

若 spec 不完整，也要產出 review，並把狀態標為 `Conditionally ready` 或 `Not ready`。不要因為規格不完整而改寫 `.sgoal/SPEC.md`；只在 review 中指出缺口與建議決策。

## 操作指南

先確認每個 `REQ-*` 是否清楚、有價值、可測試且可追溯，再檢查 priority、NFR、衝突與變更影響。審查要以 requirement ID 為單位，避免只給整體評論。

將問題分成 blocking issues、non-blocking refinements 與 deferred items。`Must` 只用於版本不可行或不合規時真正必要的需求；低優先需求不等於不合格需求。

交接時，明確給出整體狀態：`Ready`、`Conditionally ready` 或 `Not ready`。若不是 ready，列出進入實作前最少需要解決的決策。

## 工作流程

1. 若 `.sgoal/SPEC.md` 存在，先讀取它；若 `.sgoal/INTAKE.md` 存在，作為輔助脈絡讀取。
2. 逐項檢查需求的清晰度、價值、大小、可測試性、追溯性與缺漏決策。
3. 使用精簡版審查方法：
   - INVEST：independent、negotiable、valuable、estimable、small、testable。
   - MoSCoW：Must、Should、Could、Won't for this version。
   - Volere fit criterion：確認需求被滿足時應出現的清楚證據。
   - Traceability：從 intake 來源到 requirement，再到 acceptance criteria。
   - Change impact：需求變更時可能影響的下游項目。
4. 找出衝突、歧義、重複需求、薄弱驗收條件、NFR 缺口與未解依賴。
5. 除非使用者指定其他路徑，否則建立或更新 `.sgoal/REVIEW.md`。

## 審查規則

- 先列出會阻塞實作就緒度的問題。
- 不要產出完整 roadmap 或 sprint plan。
- 區分「not ready」需求與「低優先但有效」需求。
- 只有版本不可行或不合規時才標記為 `Must`。
- 保留 `.sgoal/SPEC.md` 中的 requirement IDs。
- 對缺漏資訊提出具體 decision prompts。

## .sgoal/REVIEW.md 結構

除非專案已有更強的在地慣例，否則使用此結構：

```markdown
# Requirement Readiness Review

## Source Spec
- Spec artifact: .sgoal/SPEC.md
- Intake artifact: .sgoal/INTAKE.md
- Review date:

## Ready / Not Ready Summary
- Overall status: Ready / Conditionally ready / Not ready
- Reason:
- Minimum decisions needed before implementation:

## Quality Checklist
| ID | Clear | Valuable | Small | Testable | Traceable | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| REQ-001 | Yes/No | Yes/No | Yes/No | Yes/No | Yes/No |  |

## Priority Classification
| ID | Priority | Reason | Version Fit |
| --- | --- | --- | --- |
| REQ-001 | Must/Should/Could/Won't |  |  |

## Traceability Check
| ID | Source Goal / Job | Acceptance Criteria Present | Gap |
| --- | --- | --- | --- |
| REQ-001 |  | Yes/No |  |

## Risks and Conflicts
- Requirement ID:
  Risk or conflict:
  Impact:
  Suggested resolution:

## Missing Decisions
- Decision needed:
  Blocks:
  Recommended owner:

## Change Impact Notes
- Requirement ID:
  If changed:
  Likely impact:

## Next Review Actions
1. 
2. 
3. 
```

## 品質門檻

- 明確且可辯護地給出 readiness status。
- 每個阻塞問題都要連到 requirement ID 或缺漏來源決策。
- 讓 priority label 反映版本可行性，而不是泛泛的重要性。
- 除非清楚標記為 recommendation，否則不要創造新需求。
- 讓 `.sgoal/REVIEW.md` 聚焦於規格是否可以被實作與驗收。

## 交接

結尾要指出 `.sgoal/REVIEW.md` 的位置，並摘要實作可以開始、可有條件開始，或應等待哪些需求決策。
