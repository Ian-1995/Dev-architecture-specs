

### 1. 📝 Product Charter 通用模板

> **💡 Google PM Tip:** 好的 Charter 要能回答「如果不做這個專案，公司會損失什麼？」

**專案名稱：** [Project Name]
**文件擁有者 (Owner)：** [Name]
**最後更新日期：** [YYYY/MM/DD]
**專案狀態：** [Drafting / Reviewing / Approved]

#### 1. Problem Statement (痛點陳述)

* **用戶是誰？** [Target Audience]
* **他們遇到什麼問題？** [描述現狀的痛苦、效率低落或金錢損失]
* **數據佐證：** [例如：目前有 40% 的用戶在結帳流程流失...]

#### 2. Why Now? (急迫性與時機)

* **為什麼是現在做？** [是市場趨勢、競爭對手壓力、還是技術成熟了？]
* **延後一季做的代價？** [如果這季不做，我們會失去市佔率/客戶/營收？]

#### 3. Solution & Value Proposition (解決方案與價值)

* **我們要做什麼？(High-level)：** [一句話描述產品核心功能]
* **商業價值 (Business Impact)：** [預計帶來多少營收、節省多少成本、或提升多少效率]

#### 4. Scope (產品邊界) - 最重要的一欄！

| ✅ In Scope (本期要做) | ❌ Out of Scope (本期不做) |
| --- | --- |
| [核心功能 A] | [未來功能 X] |
| [核心功能 B] | [非關鍵的優化 Y] |
| [必要的整合 C] | [複雜的後台報表 Z] |

#### 5. Success Metrics (成功定義)

* **北極星指標 (North Star Metric)：** [唯一最重要的指標，如：每週活躍用戶數、訂單完成率]
* **護欄指標 (Counter Metrics)：** [確保不發生負面影響，如：系統延遲不可增加、客訴率不可上升]

#### 6. Key Stakeholders (關鍵利害關係人)

* **Sponsor (出錢/決策者)：**
* **Core Team (PM/Eng/Design)：**
* **Dependent Team (被依賴的團隊)：** [例如：需要 Platform Team 開 API]

#### 7. Risks & Assumptions (風險與假設)

* **風險：** [例如：第三方 API 漲價、技術實作難度高]
* **假設：** [例如：假設用戶願意授權 Line 登入]

---

### 2. 🌟 實戰範例：美業管理系統 (Beauty SaaS) - MVP

這是一個以你之前的「美業系統」構想為背景的 Charter 範例。

**專案名稱：** BeautyConnect SaaS (MVP 版本)
**Owner：** Gemini (Your Name)
**日期：** 2025/12/29

#### 1. Problem Statement (痛點)

目前台灣 80% 的中小型個人美容工作室（美甲、美睫）仍使用**紙本**或 **Line 文字訊息**管理預約。

* **痛點：** 美容師在服務中無法回訊息，導致**預約流失 (約 20%)**；且缺乏客戶資料庫（CRM），難以進行二次行銷，熟客回流率低。

#### 2. Why Now? (急迫性)

* **市場缺口：** 現有競品（如 SimplyBook）對長輩不友善且費用高，市場缺乏「Line 原生」的輕量級解決方案。
* **時機：** 疫後數位轉型需求大增，若現在不切入，將被大型平台（如 FunNow）壟斷市場。

#### 3. Solution (解決方案)

開發一套 **基於 Line OA (官方帳號) 的輕量級預約管理系統**。

* 美容師端：透過手機網頁管理行事曆。
* 消費者端：在 Line 內直接點選時段預約，無須下載 App。

#### 4. Scope (產品邊界)

| ✅ In Scope (MVP 範圍) | ❌ Out of Scope (二期再做) |
| --- | --- |
| **Line 預約模組** (選時段/確認) | **金流支付** (先做現場付款) |
| **美容師行事曆** (查看/手動新增) | **庫存進銷存管理** |
| **基礎 CRM** (客戶名單/歷史紀錄) | **薪資抽成計算** |
| **自動提醒** (前一天 Line 推播) | **多店點/連鎖店管理** |

#### 5. Success Metrics (成功定義)

* **⭐ 北極星指標：** **每週成功預約單數 (Weekly Completed Bookings)** > 1,000 單 (上線 3 個月內)。
* **商業指標：** 付費訂閱轉換率 > 5%。
* **技術指標：** Line Webhook 回應速度 < 1秒 (P95)。

#### 6. Stakeholders (利害關係人)

* **Sponsor：** CEO / 投資人
* **Tech Lead：** 後端架構師 (需評估 Line API 限制)
* **Sales：** 業務團隊 (需確認定價策略)

#### 7. Risks (風險)

* **平台風險：** Line API 政策改變導致推播成本暴增（Mitigation: 設計時預留切換 Email/SMS 通知的彈性）。
* **採用風險：** 年長美容師覺得設定太複雜（Mitigation: 需設計「一鍵設定」的 Onboarding 流程）。

---
