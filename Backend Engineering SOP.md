# 後端開發標準規範 (Backend Engineering SOP)

> **版本：** v1.0
> **適用對象：** 後端開發人員、架構師、新進員工
> **核心原則：** **可讀性 (Readability)** > **可維護性 (Maintainability)** > **擴充性 (Scalability)**

---

## 1. 專案結構規範 (Project Structure Standards)

### 規則 1.1：拒絕扁平化，強制分層 (No Flat Structure)

* ❌ **禁止：** 將所有 `.py` 檔案全部堆在專案根目錄。
* ✅ **強制：** 必須採用 **「src 隔離模式」** 或 **「模組化結構」**。

**標準結構範例：**

```text
project_root/
├── docker-compose.yml       # 基礎設施編排
├── README.md                # 專案說明書
├── .gitignore               # 守門員 (必備)
└── src/ (或 backend/)       # 原始碼根目錄
    ├── main.py              # 唯一入口點
    ├── api/                 # 介面層 (Routes/Controllers)
    ├── core/                # 核心層 (Config, Security, Utils)
    ├── services/            # 業務邏輯層 (Business Logic)
    ├── models/              # 資料層 (DB Schemas)
    └── tests/               # 測試代碼 (與源碼平行)

```

### 規則 1.2：生產環境與實驗環境分離

* ❌ **禁止：** 在 `src/` 或 `backend/` 內放入 `.ipynb` (Jupyter Notebooks) 或臨時測試腳本 (`temp.py`, `test_old.py`)。
* ✅ **強制：** 所有的實驗、數據分析、一次性腳本，必須移至專案根目錄下的 `notebooks/` 或 `scripts/` 資料夾。

---

## 2. 職責分離原則 (Separation of Concerns)

### 規則 2.1：嚴格的分層依賴 (Layered Dependency)

代碼只能由上往下呼叫，**禁止反向或跳躍**。

1. **API 層 (`api/`)**：
* 只負責接收 Request、驗證參數、呼叫 Service、回傳 Response。
* **禁止**寫業務邏輯。


2. **Service 層 (`services/`)**：
* 核心業務邏輯所在（計算、流程控制）。
* 只呼叫 Models 或其他 Services。
* **禁止**直接操作 HTTP Request 物件。


3. **Model 層 (`models/`)**：
* 只負責定義資料庫結構與基礎 CRUD。
* **禁止**包含複雜業務邏輯。



### 規則 2.2：單一職責 (SRP)

一個檔案應該只做一種類型的事。

* ❌ **錯誤示範：** `app.py` 裡面同時有 `Connect DB`, `Define Route`, `Process Data`。
* ✅ **正確做法：** `db.py` 連線 DB，`routes.py` 定義路徑，`service.py` 處理資料。

---

## 3. 命名與代碼衛生 (Naming & Hygiene)

### 規則 3.1：拒絕模糊命名 (No Vague Naming)

* ❌ **禁止使用：** `processor.py`, `manager.py`, `handler.py`, `data.py`, `common.py`, `util.py` (除非是非常通用的工具)。這些名字是大雜燴的溫床。
* ✅ **強制使用：** 「領域名詞」+「功能」。
* **Bad:** `processor.py`
* **Good:** `order_processor.py`, `image_resizer.py`, `whitelist_service.py`


* **變數命名：** `ssot` 這種縮寫是禁忌。請使用 `global_constants.py` 或 `app_config.py`。

### 規則 3.2：設定檔與憑證管理 (Configuration & Secrets)

* 🛑 **絕對禁止 (P0 級錯誤)：** 將 `credentials.json`, `password`, `API Key` 硬寫在程式碼裡或 commit 到 Git。
* ✅ **強制：**
1. 使用 `.env` 檔案管理環境變數。
2. 程式碼透過 `os.getenv` 或 Config Object 讀取。
3. `.gitignore` 必須包含 `*.env`, `*.json` (憑證類), `__pycache__/`, `.DS_Store`。



---

## 4. 基礎設施與依賴 (Infrastructure & Dependencies)

### 規則 4.1：明確的依賴管理

* ❌ **禁止：** 依賴全域 Python 環境。
* ✅ **強制：** 專案必須包含 `requirements.txt` (或 `Pipfile`/`pyproject.toml`)。
* **Docker 化：** `Dockerfile` 應放在應用程式目錄 (`backend/`)，而 `docker-compose.yml` 放在專案根目錄 (`root/`) 以便同時管理 DB 和 App。

---

## 5. 開發前的自我審查清單 (Self-Checklist)

在開始寫任何一行新的 Code 之前，或是在準備 Commit 之前，請問自己以下三個問題：

1. [ ] **如果這個專案擴大 10 倍，我現在新增的這個檔案位置還合理嗎？** (如果是 `processor.py`，答案通常是不合理)。
2. [ ] **新來的同事如果不問我，光看檔名和資料夾結構，能知道這段 Code 在做什麼嗎？**
3. [ ] **如果我把這段 Code 開源，我的密碼會外洩嗎？**

---
