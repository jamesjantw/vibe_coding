# BMad Method V6 Alpha - 通用編碼標準 (Coding Standards)

**BMad Method 版本:** V6 Alpha (6.0.0-alpha.6)  
**文件版本:** 1.0  
**適用於:** 所有程式語言和框架  
**日期:** 2025-10-15

## 1. 介紹 (Introduction)

本文件定義了使用 BMad Method 進行軟體開發的通用編碼標準、風格指南與最佳實踐。這些標準適用於所有程式語言和框架，旨在確保程式碼的可讀性、一致性與可維護性。

---

## 2. 通用原則 (General Principles)

*   **清晰優於簡潔:** 程式碼首先是寫給人看的，其次才是給機器執行的。
*   **遵守 The Zen of Python:** 在終端機輸入 `import this`。
*   **DRY (Don't Repeat Yourself):** 避免重複的程式碼，盡可能地將其抽象化為可重用的函式或類別。
*   **KISS (Keep It Simple, Stupid):** 除非有充分的理由，否則應選擇最簡單直接的解決方案。
*   **請以正體中文回覆與文件撰寫** 
*   **內部工具** 請使用 read_file 取代 read_many_files, write_file 取代 replace
*   **修改前請請重新讀取檔案** 更新記憶 確保原有的功能不會被影響
*   **註解** 請加上 日期 agent人員 story task
*   **OS環境** Windows
*   **所有 Agent 角色** 請參考 docs/architecture/definition-of-done.md 理解 & align 相關定義
*   **處理方式與結果** 請詳實記錄 並更新文件狀態

---

### 2.1 開發者執行清單（Mandatory for Developers）

以下清單為開發者在進行任何變更時「必須」遵循的具體步驟，確保可追蹤、可回溯、不中斷既有功能：

1) 準備階段
   - 讀取將被修改的檔案與相關依賴檔案（避免猜測）。
   - 若需查找位置，先使用搜尋工具定位，再讀取檔案。
   - 記錄關鍵決策點和設計考量。

2) 依循規範
   - 遵循各程式語言的官方編碼標準。
   - 使用適當的格式化工具和 Linter。

3) 變更實施
   - 變更前加入註記（日期/作者/Story/Task）。
   - 使用最小化編輯；避免無關變更。
   - 追蹤待辦事項，完成時更新狀態。

4) 驗證與一致性
   - 執行 Lint 和格式檢查，修正發現的問題。

5) 文件同步
   - 更新相關文件和註解。

6) 提交說明
   - 使用清晰的提交訊息描述變更。

---

## 3. 通用程式語言標準

### 3.1. 風格與格式化

*   **語言特定標準:** 遵循各程式語言的官方編碼標準和慣例。
*   **自動格式化:** 使用適當的程式碼格式化工具（如 Prettier、Black、gofmt 等）。
*   **Linter:** 使用語言特定的靜態分析工具來捕捉潛在錯誤和不符合規範的寫法。

### 3.2. 通用命名慣例 (Naming Conventions)

不同程式語言有不同的命名慣例，但應保持一致性：

| 元素 | 常見慣例 | 範例 |
|------|----------|------|
| 變數 | camelCase 或 snake_case | `userName`, `user_name` |
| 函式/方法 | camelCase 或 snake_case | `calculateTotal()`, `calculate_total()` |
| 類別/型別 | PascalCase | `UserService`, `ProjectManager` |
| 常數 | UPPER_SNAKE_CASE | `MAX_RETRY_COUNT`, `DEFAULT_TIMEOUT` |
| 私有成員 | 前綴底線 | `_privateField`, `_internalMethod()` |

### 3.3. 文件與註解 (Documentation & Comments)

*   **公開 API:** 所有公開的函式、類別和模組都必須有完整文件。
*   **複雜邏輯:** 為複雜的業務邏輯和演算法加上註解。
*   **文件格式:** 使用各語言標準的文件格式（如 JSDoc、docstrings、XML comments）。

```javascript
/**
 * 驗證使用者認證資訊
 * @param {string} username - 使用者名稱
 * @param {string} password - 密碼
 * @returns {Promise<boolean>} 驗證結果
 */
async function validateCredentials(username, password) {
    // 實作驗證邏輯
}
```

---

## 4. 安全性 (Security)

*   **敏感資訊管理:** 所有敏感資訊（API 金鑰、資料庫密碼、憑證等）都必須儲存在環境變數或安全的配置管理系統中，絕不提交到版本控制。
*   **輸入驗證:** 始終驗證和清理使用者輸入，防止注入攻擊。
*   **認證與授權:** 實作適當的身份驗證和權限檢查機制。
*   **資料加密:** 敏感資料在儲存和傳輸時應進行加密。
*   **依賴更新:** 定期更新第三方依賴以修補已知的安全漏洞。

---

## 5. 測試 (Testing)

*   **測試框架:** 根據程式語言選擇適當的測試框架（如 JUnit、pytest、Jest、Vitest 等）。
*   **測試組織:** 將測試檔案與原始程式碼放在相應的目錄結構中。
*   **單元測試:** 測試個別函式、方法或類別的邏輯，使用模擬物件隔離外部依賴。
*   **整合測試:** 測試元件間的互動和資料流。
*   **測試覆蓋率:** 維持合理的程式碼覆蓋率，通常至少 70-80%。

---

## 6. 版本控制 (Version Control)

### 6.1. 分支策略

我們採用 `GitFlow` 的簡化版：
*   `main`: 代表穩定、可隨時發布的版本。只接受來自 `develop` 分支的合併。
*   `develop`: 開發分支，整合所有已完成的功能。
*   `feature/<feature-name>`: 開發新功能的分支，基於 `develop` 建立，完成後合併回 `develop`。

### 6.2. 版本控制實踐

*   **提交訊息:** 使用清晰、描述性的提交訊息，說明變更的內容和原因。
*   **分支策略:** 根據專案規模採用適當的分支策略（如 Git Flow、GitHub Flow）。
*   **程式碼審查:** 重要的變更應經過程式碼審查。
*   **變更追蹤:** 使用議題追蹤系統來追蹤功能請求和錯誤修復。
