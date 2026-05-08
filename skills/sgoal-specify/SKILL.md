---
name: sgoal-specify
description: 從 .sgoal/INTAKE.md 或等價探索脈絡建立 .sgoal/SPEC.md 的輕量需求規格技能。用於定義穩定需求 ID、User Story、Job Story、功能行為、驗收條件、非功能需求、資料與介面需求、邊界情境、排除項與待決問題。
---

# SGoal Specify

## 概覽

使用此技能將探索脈絡轉成 `.sgoal/SPEC.md`。把 Specify 視為輕量需求規格階段：把行為寫到足以實作與測試，但不產生過重的企業級 SRS。

## 使用方式

使用者可用下列方式呼叫此技能：

```text
Use $sgoal-specify to turn .sgoal/INTAKE.md into a lightweight .sgoal/SPEC.md.
```

主要輸入是 `.sgoal/INTAKE.md`。若該檔不存在，改從 README、issue、ticket、既有規格或對話脈絡取得來源，並在 `.sgoal/SPEC.md` 中標記 assumptions。輸出固定為 `.sgoal/SPEC.md`，除非使用者明確指定其他路徑。

若 intake 仍有疑問但不阻塞需求草案，先用 assumption 或 open question 記錄，不要停止產出規格。只有當缺口會導致 requirement ID、主要行為或驗收條件無法成立時才提問。

## 操作指南

先建立 requirement index，再撰寫每個 `REQ-*` 的行為與 acceptance criteria。每個需求都應對應一個可觀察行為、使用者工作或可驗證限制，並保持 ID 穩定。

將需求切到足以獨立審查的大小。若一個需求同時包含多個 actor、互不相關的流程或多組驗收條件，拆成多個 `REQ-*`。NFR 使用 `NFR-*`，並以 fit criterion 表示如何判斷滿足。

交接時，說明 `.sgoal/SPEC.md` 是否足以進入 `$sgoal-review`。若有 open questions，指出哪些會阻塞實作、哪些只是後續精化。

## 工作流程

1. 若 `.sgoal/INTAKE.md` 存在，先讀取它；若不存在，檢查可用專案脈絡並標記假設。
2. 從目標、jobs、限制、範圍、風險與決策推導需求。
3. 指派穩定需求 ID，例如 `REQ-001`。更新既有規格時保持既有 ID 穩定。
4. 使用最精簡且有用的形式描述行為：
   - User Story：「As a ..., I want ..., so that ...」
   - Job Story：「When ..., I want to ..., so I can ...」
   - Use Case Slice：actor、trigger、main flow、alternate flow、outcome。
   - BDD/ATDD：精簡 Given/When/Then 驗收條件。
5. 捕捉非功能需求、資料需求、介面需求、邊界情境、排除項與待決問題。
6. 除非使用者指定其他路徑，否則建立或更新 `.sgoal/SPEC.md`。

## 規格規則

- 將需求寫成外部可觀察行為或可驗證限制。
- 避免把實作任務寫成需求，除非它是表達真實需求的必要資訊。
- 每個功能需求都必須有 acceptance criteria。
- 每個非功能需求都必須有可衡量或可審查的 fit criterion。
- 讓每個需求小到可以獨立評估。
- 不要排序實作；就緒審查屬於 `$sgoal-review`。

## .sgoal/SPEC.md 結構

除非專案已有更強的在地慣例，否則使用此結構：

```markdown
# Lightweight Requirement Specification

## Source Intake
- Intake artifact: .sgoal/INTAKE.md
- Specification date:
- Key assumptions:

## Requirement Index
| ID | Title | Type | Source / Goal | Status |
| --- | --- | --- | --- | --- |
| REQ-001 |  | Functional |  | Proposed |

## Functional Requirements

### REQ-001: <title>
Summary:

User / Job Story:
- As a:
  I want:
  So that:
- When:
  I want to:
  So I can:

Behavior:
- Actor:
- Trigger:
- Main flow:
- Alternate or failure flow:
- Expected outcome:

Acceptance Criteria:
- Given:
  When:
  Then:

Edge Cases:
- 

Dependencies:
- 

## Non-Functional Requirements
| ID | Quality Attribute | Requirement | Fit Criterion |
| --- | --- | --- | --- |
| NFR-001 |  |  |  |

## Data and Interfaces
- Inputs:
- Outputs:
- External systems:
- Data ownership:
- Error handling expectations:

## Out of Scope
- 

## Open Questions
- Question:
  Impact:
  Needed decision:
```

## 品質門檻

- 確保每個 `REQ-*` 都能追溯到來源目標、job、scope item 或明確假設。
- 使用具體 acceptance criteria，不使用「正常運作」這類模糊語句。
- 將功能需求、NFR 與限制分開記錄。
- 把未解決決策列為 open questions，不要藏在需求文字中。
- 讓 `.sgoal/SPEC.md` 精簡到 `$sgoal-review` 能一次完成審查。

## 交接

結尾要指出 `.sgoal/SPEC.md` 的位置，並建議下一步：當需要檢查規格就緒度、優先級、追溯性與缺漏決策時，使用 `$sgoal-review`。
