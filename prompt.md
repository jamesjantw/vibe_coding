# BMad Method - Agent Prompts 集合

這份文件收集了各個 BMad Method Agent 常用的 prompt 模板和指令。這些 prompt 可以幫助你在不同場景下更有效地與 AI 代理互動。

## 📋 文件結構

- **通用 Prompt** - 適用於所有 Agent 的基礎指令
- **角色特定 Prompt** - 各個 Agent 的專用指令
- **任務特定 Prompt** - 針對特定任務的 prompt 模板
- **情境 Prompt** - 不同開發階段的 prompt 範例

## 🔧 通用 Prompt

### 基礎互動原則

```markdown
# 基本格式
@agent_name [任務描述]

# 範例
@pm 建立任務管理應用的 PRD
@architect 設計系統架構
@dev 實作使用者認證
```

### 品質要求提示

```markdown
# 要求高品質輸出
請提供詳細、結構化的回應，包含：
- 具體的實作步驟
- 相關的程式碼範例
- 潛在的風險考量
- 測試建議
```

### 格式化要求

```markdown
# 要求結構化輸出
請使用以下格式回應：
## 標題
- 要點 1
- 要點 2

## 程式碼範例
```language
// 程式碼內容
```
```

### 強制執行規則 (Mandatory Rules)

**所有 Agent 必須遵循：**

#### 1. 開發前準備
```markdown
# @dev 專用 - 開發前必須閱讀
@dev 開始任何開發任務前，請先閱讀 docs/architecture/coding-standards.md 並確認理解所有編碼標準。

確認已閱讀編碼標準 ✓
```

#### 2. 工作階段完成要求
```markdown
# 每個工作階段結束時必須執行
每個工作階段完成後，所有 Agent 必須：

1. **更新相關文件**
   - 記錄處理過程與完成事項
   - 更新任務狀態和進度
   - 記錄遇到的問題和解決方案

2. **更新 Change Log**
   - 在文件的 CHANGELOG 中記錄變更
   - 包含日期、作者、變更內容、影響範圍

3. **更新文件狀態**
   - 更新 docs/ 目錄下相關文件的狀態
   - 標記已完成、進行中、待處理的項目
   - 更新最後修改時間和負責人

# 範例更新格式
## [YYYY-MM-DD] - [Agent 名稱]
### 完成事項
- [具體完成內容]
- [影響的檔案/功能]

### 待處理事項
- [後續需要處理的項目]

### 問題與解決
- [遇到的問題]: [解決方案]
```

## 👥 角色特定 Prompt

### PM (Product Manager) Prompts

#### 建立 PRD
```markdown
@pm Create a comprehensive PRD for [產品名稱] with the following features:
- [功能 1]
- [功能 2]
- [功能 3]

包含：使用者故事、驗收標準、優先順序矩陣和成功指標。
```

#### 需求澄清
```markdown
@pm Help me clarify the requirements for [功能名稱].
Current understanding: [目前的理解]
Questions to resolve: [需要澄清的問題]
```

### Architect (架構師) Prompts

#### 系統設計
```markdown
@architect Design a scalable architecture for [系統名稱] using:
- Frontend: [技術棧]
- Backend: [技術棧]
- Database: [資料庫]
- Authentication: [認證方式]

考量：效能、安全性、可維護性和擴展性。
```

#### 技術選型建議
```markdown
@architect Recommend technology choices for [專案類型]:
- Current team skills: [團隊技能]
- Project constraints: [專案限制]
- Future scalability needs: [未來擴展需求]
```

### Dev (開發者) Prompts

#### 功能實作
```markdown
@dev Implement [功能名稱] with the following requirements:
- [需求 1]
- [需求 2]
- [需求 3]

Include: error handling, input validation, and unit tests.

⚠️  重要：開始前請先閱讀 docs/architecture/coding-standards.md
✅ 已閱讀編碼標準並遵循所有規範
```

#### 程式碼重構
```markdown
@dev Refactor [檔案/函式名稱] to improve:
- Readability
- Performance
- Maintainability

Current issues: [現有問題]

⚠️  重要：開始前請先閱讀 docs/architecture/coding-standards.md
✅ 已閱讀編碼標準並遵循所有規範
```

### QA (測試架構師) Prompts

#### 風險評估
```markdown
@qa *risk [故事名稱]
評估實作風險並提供緩解策略。
```

#### 測試策略設計
```markdown
@qa *design [故事名稱]
建立完整的測試情境，包括：
- 單元測試
- 整合測試
- 端到端測試
- 邊界情況
```

#### 品質審核
```markdown
@qa *review [故事名稱]
執行全面的品質評估並提供：
- 測試覆蓋率分析
- 程式碼品質回饋
- 安全性考量
```

## 🎯 任務特定 Prompt

### 新功能開發

```markdown
@dev Implement a new feature for [功能描述]

Requirements:
- [具體需求]
- [技術限制]
- [品質標準]

請包含：
- 實作計劃
- 程式碼結構
- 錯誤處理
- 單元測試
```

### 錯誤修復

```markdown
@dev Fix the bug in [功能/檔案名稱]

問題描述：[問題描述]
預期行為：[預期行為]
目前行為：[目前行為]

重現步驟：
1. [步驟 1]
2. [步驟 2]
3. [步驟 3]
```

### 程式碼審查

```markdown
@qa Review the following code changes:

Files changed: [檔案列表]
Key changes: [主要變更]

重點關注：
- 程式碼品質
- 安全性漏洞
- 效能影響
- 測試覆蓋率
```

## 📝 情境 Prompt

### 專案啟動階段

```markdown
@pm We're starting a new project: [專案描述]

Initial requirements:
- [需求 1]
- [需求 2]

請建立：
- 高層次專案願景
- 初始史詩分解
- 技術建議
- 時間表估計
```

### 開發中期檢查

```markdown
@sm Review our current progress on [故事名稱]

Completed work: [已完成項目]
Remaining tasks: [待完成任務]
Blockers: [阻礙因素]

後續步驟建議：[建議下一步]
```

### 專案收尾階段

```markdown
@po Prepare for project closure: [專案名稱]

Deliverables checklist:
- [交付項目 1]
- [交付項目 2]

Documentation needed:
- [文件 1]
- [文件 2]

部署計劃：[部署計劃]
```

## 🔄 迭代優化 Prompt

### 回饋收集

```markdown
根據最近實作的 [功能名稱]，請分析：

運作良好的部分：[優點]
可以改進的地方：[改進點]
學到的經驗教訓：[經驗教訓]

針對未來類似任務的建議：[未來建議]
```

### 流程改進

```markdown
@sm Review our development process for [專案階段]

Current workflow: [現有流程]
Pain points identified: [痛點]
Proposed improvements: [改進建議]

請建議流程優化方案。
```

## 📚 使用提示

### 撰寫有效 Prompt 的原則

1. **具體明確** - 清楚描述期望的輸出
2. **提供上下文** - 包含相關背景資訊
3. **指定格式** - 說明期望的回應格式
4. **設定限制** - 明確範圍和限制條件

### 強制要求提醒

**⚠️ 所有 Agent 必須記住：**

每完成一個工作階段，必須立即執行以下三項：

1. **📝 更新相關文件**
   - 記錄處理過程與完成事項
   - 更新任務狀態和進度追蹤

2. **📋 更新 Change Log**
   - 在 CHANGELOG 中記錄所有變更
   - 包含日期、作者、變更內容和影響範圍

3. **🔄 更新文件狀態**
   - 更新 docs/ 目錄下所有相關文件的狀態
   - 標記完成項目、進行中項目、待處理項目
   - 更新最後修改時間和負責人資訊

### 最佳實踐

- **漸進式提問** - 從高層次開始，逐步細化
- **參考既有文件** - 利用專案中的既有文件
- **包含範例** - 提供期望輸出的範例
- **指定優先順序** - 明確哪些方面最重要
- **遵循編碼標準** - @dev 必須先閱讀 coding-standards.md
- **完整記錄** - 每個階段結束都要更新文件狀態

### 常見模式

- **任務分解**: 將大任務分解為小步驟
- **條件分支**: 根據不同情境提供不同處理方式
- **品質檢查**: 包含驗證和測試要求
- **文件生成**: 指定輸出文件的格式和內容
- **狀態追蹤**: 記錄每個步驟的進度和問題

---

*此文件將持續更新，歡迎貢獻新的 prompt 模板和最佳實踐。*