

# 🧠 System Requirement SSOT

**系統需求單一真實來源（Single Source of Truth）母板**
用途：業主訪談 / 架構設計 / 工程開發 
核心原則：

> **系統可理解性 > 系統可驗證性 > 系統可演化性**

---

## 0. Meta Layer（文件定位層）

| 欄位              | 說明                      |
| --------------- | ----------------------- |
| System Codename | 系統代號，避免專案在文件中出現模糊稱呼     |
| Stakeholders    | 所有利害關係人                 |
| Version         | 控制需求版本，避免「口頭改規格」        |

📌 作用：

> 此區讓整個團隊對「現在討論的是哪一個系統、哪一版規格」沒有認知分歧。

---

## 1. Problem Definition Layer（存在理由層）

```
目前我們在 [流程] 發生 [問題]，導致 [損失]。
```

📌 作用：

> 強制所有系統存在都必須有「成本損失依據」。

---

## 2. System Goal & KPI（成果驗證層）

| KPI | 現況 | 目標 | 驗證方式 |
| --- | -- | -- | ---- |

📌 作用：

> 把「我們希望好一點」轉成「什麼叫成功」。

---

## 3. Stakeholder / Role Model（權限與責任模型）

| Role | Can | Cannot |

📌 作用：

> 明確誰能做什麼，避免權限邊界模糊導致資安與責任事故。

---

## 4. System Boundary（系統邊界）

| In Scope | Out of Scope |

📌 作用：

> 控制開發膨脹（Scope Creep），避免無止境需求擴張。

---

## 5. High-Level Architecture Skeleton（系統骨架）

```
Input → Core Logic → Output
```

📌 作用：

> 定義資料如何流動，是所有 Flowchart / API / 資料管線的母骨架。

---

## 6. Functional Requirements（功能契約層）

| FR-ID | 行為 | Input | Output | Priority |

📌 作用：

> 每一個功能必須有「輸入與輸出」，確保功能可實作、可驗證、可測試。

---

## 7. Logical Data Model（資料定義）

| Entity | PK | Fields | Data Source |

📌 作用：

> 這裡一旦填好，ERD、Schema、Migration 全部可以自動生成。

---

## 8. API Contract（機器對話契約）

```
POST /api/xxx
Input: {}
Output: {}
```

📌 作用：

> API 是服務間「法律契約」，LLM 可依此直接生程式碼。

---

## 9. State Machine / Flow Control（狀態與流程）

| State | Next State | Trigger |

📌 作用：

> 定義系統會經歷哪些生命狀態，是流程錯誤率最低的設計方式。

---

## 10. NFR / SLA（非功能性承諾）

| Item | Target |
| ---- | ------ |

📌 作用：

> 明確效能、穩定性、維運責任，避免事後無法驗收。

---

## 11. Failure & Recovery Strategy（災害復原）

| Scenario | System Behavior |

📌 作用：

> 預先定義災害處理策略，是系統穩定度的根基。

---

## 12. Deployment Model（部署與維運）

| Environment | Stack |

📌 作用：

> 控制系統交付品質與環境一致性。

---

## 13. Open Issues / Decision Log（決策稽核）

| Topic | Decision | Owner | Date |

📌 作用：

> 留下「為何這樣設計」的決策軌跡。

---

