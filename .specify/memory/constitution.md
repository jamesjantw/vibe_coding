# Speckit Constitution

## 核心原則 (Core Principles)

### I. 高品質與乾淨程式碼 (High Quality & Clean Code)
程式碼首先是寫給人看的，其次才是給機器執行的。遵循 DRY (Don't Repeat Yourself) 原則，避免重複程式碼。採用 KISS (Keep It Simple, Stupid) 原則，除非有充分理由，否則選擇最簡單直接的解決方案。

### II. 可測試性 (Testability)
所有程式碼必須是可測試的。採用測試驅動開發 (TDD) 方法：先寫測試 → 測試失敗 → 實作功能 → 測試通過 → 重構。維持合理的程式碼覆蓋率，通常至少 70-80%。

### III. 最小可行產品 (Minimum Viable Product)
避免過度設計。從最簡單的解決方案開始，根據實際需求逐步迭代。遵循 YAGNI (You Aren't Gonna Need It) 原則。

### IV. 正體中文優先 (Traditional Chinese First)
所有文件、註解和回覆均使用正體中文。確保團隊溝通一致性。

### V. 開發者執行清單 (Developer Execution Checklist)
開發者在進行任何變更時必須遵循以下步驟：
1. 準備階段：讀取將被修改的檔案與相關依賴檔案，避免猜測。若需查找位置，先使用搜尋工具定位，再讀取檔案。記錄關鍵決策點和設計考量。
2. 依循規範：遵循各程式語言的官方編碼標準。使用適當的格式化工具和 Linter。
3. 變更實施：變更前加入註記（日期/作者/Story/Task）。使用最小化編輯；避免無關變更。追蹤待辦事項，完成時更新狀態。
4. 驗證與一致性：執行 Lint 和格式檢查，修正發現的問題。
5. 文件同步：更新相關文件和註解。
6. 提交說明：使用清晰的提交訊息描述變更。

## 編碼標準 (Coding Standards)

### 風格與格式化
- 遵循各程式語言的官方編碼標準和慣例。
- 使用自動格式化工具（如 Prettier、Black、gofmt 等）。
- 使用語言特定的靜態分析工具 (Linter) 來捕捉潛在錯誤。

### 命名慣例
保持一致的命名慣例：

| 元素 | 常見慣例 | 範例 |
|------|----------|------|
| 變數 | camelCase 或 snake_case | `userName`, `user_name` |
| 函式/方法 | camelCase 或 snake_case | `calculateTotal()`, `calculate_total()` |
| 類別/型別 | PascalCase | `UserService`, `ProjectManager` |
| 常數 | UPPER_SNAKE_CASE | `MAX_RETRY_COUNT`, `DEFAULT_TIMEOUT` |
| 私有成員 | 前綴底線 | `_privateField`, `_internalMethod()` |

### 文件與註解
- 所有公開 API 必須有完整文件。
- 複雜邏輯需加上註解。
- 使用標準文件格式（如 JSDoc、docstrings、XML comments）。

## 安全性 (Security)
- 敏感資訊管理：所有敏感資訊儲存在環境變數或安全配置系統中，絕不提交到版本控制。
- 輸入驗證：始終驗證和清理使用者輸入，防止注入攻擊。
- 認證與授權：實作適當的身份驗證和權限檢查機制。
- 資料加密：敏感資料在儲存和傳輸時進行加密。
- 依賴更新：定期更新第三方依賴以修補安全漏洞。

## 測試策略 (Testing Strategy)
- 根據程式語言選擇適當測試框架（如 JUnit、pytest、Jest、Vitest 等）。
- 測試檔案與原始程式碼放在相應目錄結構中。
- 單元測試：測試個別函式、方法或類別邏輯，使用模擬物件隔離外部依賴。
- 整合測試：測試元件間互動和資料流。
- 測試覆蓋率：維持 70-80% 以上。

## 版本控制 (Version Control)
採用 GitFlow 簡化版：
- `main`: 穩定可發布版本，只接受來自 `develop` 的合併。
- `develop`: 開發分支，整合所有完成功能。
- `feature/<feature-name>`: 新功能分支，基於 `develop` 建立，完成後合併回 `develop`。

實踐：
- 清晰描述性提交訊息。
- 重要變更經過程式碼審查。
- 使用議題追蹤系統追蹤功能請求和錯誤修復。

## 開發工作流程 (Development Workflow)

### 程式碼審查
所有變更必須經過程式碼審查。審查重點包括：
- 符合編碼標準
- 測試覆蓋率
- 安全性考量
- 效能影響

### 品質門檻
- 所有測試必須通過
- Lint 檢查無錯誤
- 程式碼覆蓋率達標
- 安全掃描通過

## 治理 (Governance)
憲法優於所有其他實踐。所有 PR/審查必須驗證合規性。複雜性必須有正當理由。使用相關指導文件進行開發指導。

**版本**: 1.0 | **通過日期**: 2025-10-28 | **最後修訂**: 2025-10-28
