---
name: sgoal-discover
description: 建立 .sgoal/INTAKE.md 的早期需求探索技能。用於釐清模糊專案意圖、散落筆記、利害關係人需求、使用者工作、期望結果、範圍、限制、假設、非目標、風險與待決問題，並在撰寫輕量規格前完成需求收斂。
---

# SGoal Discover

## 概覽

使用此技能將尚未清楚的專案意圖收斂成 `.sgoal/INTAKE.md`。把 Discover 視為輕量需求擷取階段：先檢查既有資料，只詢問阻塞性問題，並清楚區分事實與假設。

## 使用方式

使用者可用下列方式呼叫此技能：

```text
Use $sgoal-discover to clarify this project and create .sgoal/INTAKE.md.
```

輸入通常來自專案 README、issue、ticket、會議筆記、既有規格、原始想法或使用者口頭描述。輸出固定為 `.sgoal/INTAKE.md`，除非使用者明確指定其他路徑。

若使用者只提供模糊想法，也要先嘗試整理可得資訊，再用少量問題補齊阻塞缺口。不要等待完整需求才開始建立 intake。

## 操作指南

先讀取可用脈絡，並用「事實、假設、問題」三類整理資訊。若現有資料足以產生有用的 intake，就直接建立文件；若不足，僅詢問會改變目標、範圍、主要使用者或成功判準的問題。

撰寫 `.sgoal/INTAKE.md` 時，優先收斂需求背後的工作與結果，而不是擴寫功能清單。對每個重要解法要求，至少追問或推論其背後的 user/job、pain、outcome，並把未確認內容標為 assumption。

交接時，說明 intake 是否足以進入 `$sgoal-specify`。若仍有阻塞問題，列出最少必要決策，而不是產生完整訪談清單。

## 工作流程

1. 先檢查既有專案檔案、筆記、ticket、README、既有規格與對話脈絡，再決定是否提問。
2. 萃取已知的目標、使用者、利害關係人、工作情境、痛點、期望結果、限制、假設、風險與非目標。
3. 只有在缺少資訊會阻塞可用的 intake 文件時才提問。優先提出一到三個高影響問題。
4. 使用精簡版探索方法：
   - 訪談：詢問目標、使用者、工作流程與決策限制。
   - 5 Whys：把功能請求追問回真正需求。
   - JTBD：記錄「When ..., I want to ..., so I can ...」情境。
   - Impact Mapping：連結目標、行為者、行為改變與可能交付物。
5. 除非使用者指定其他路徑，否則建立或更新 `.sgoal/INTAKE.md`。

## Intake 規則

- 只有來源資料或使用者確認支持時，才把內容記為事實。
- 將推論標記為假設。
- 保留解法想法，但不要讓解法取代背後需求。
- 優先使用可觀察或可衡量的結果。
- 明確記錄非目標，避免範圍失控。
- 讓文件保持精簡，使 `$sgoal-specify` 能直接使用。

## .sgoal/INTAKE.md 結構

除非專案已有更強的在地慣例，否則使用此結構：

```markdown
# Requirement Intake

## Objective
用一段話說明專案要達成什麼，以及為什麼要做。

## Stakeholders and Users
| Group | Need | Current Pain | Decision Role |
| --- | --- | --- | --- |
|  |  |  |  |

## Jobs / Situations
- When:
  I want to:
  So I can:

## Desired Outcomes
| Outcome | Why It Matters | How To Observe Success |
| --- | --- | --- |
|  |  |  |

## Scope
### In Scope
- 

### Out of Scope
- 

## Constraints
- Technical:
- Product:
- Time or delivery:
- Operational:
- Compliance or policy:

## Assumptions
- Assumption:
  Confidence:
  Validation needed:

## Risks and Unknowns
- Risk or unknown:
  Impact:
  Next validation step:

## Decision Log
- YYYY-MM-DD: Decision and reason.
```

## 品質門檻

- 讓 objective 具體到足以支援後續需求撰寫。
- 保留未解問題，不要編造硬性需求。
- 確保重要使用者群體至少有一個 need 或 job。
- 明確記錄 scope 與 out of scope。
- 不要產生 feature-level acceptance criteria；那是 `$sgoal-specify` 的責任。

## 交接

結尾要指出 `.sgoal/INTAKE.md` 的位置，並建議下一步：當 intake 已穩定到足以描述具體行為與驗收條件時，使用 `$sgoal-specify`。
