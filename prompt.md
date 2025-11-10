# BMad Method V6 Alpha - Agent Prompts 集合

這份文件收集了各個 BMad Method V6 Alpha Agent 常用的 prompt 模板和工作流程指令。這些 prompt 可以幫助你在不同場景下更有效地與 AI 代理互動。

**版本**: V6 Alpha (6.0.0-alpha.6)  
**重要變更**: V6 使用工作流程系統（Workflow）取代舊版任務（Tasks），指令格式為 `*workflow-name`

## 📋 文件結構

- **通用 Prompt** - 適用於所有 Agent 的基礎指令
- **角色特定 Prompt** - 各個 Agent 的專用指令
- **任務特定 Prompt** - 針對特定任務的 prompt 模板
- **情境 Prompt** - 不同開發階段的 prompt 範例

## 🔧 通用 Prompt

### V6 Alpha 工作流程指令格式

V6 使用新的工作流程系統，支援多種指令格式：

```markdown
# 方式 1: 使用 * 前綴（推薦）
*workflow-init          # 初始化工作流程
*prd                    # 建立 PRD
*create-architecture    # 建立架構
*sprint-planning       # 衝刺規劃
*create-story          # 建立故事
*dev-story             # 實作故事
*code-review           # 程式碼審查

# 方式 2: 使用自然語言
"執行工作流程初始化"
"建立 PRD"
"建立架構文件"

# 方式 3: 使用菜單選項
# 代理會顯示可用工作流程選單，選擇編號即可
```

### 基礎互動原則

```markdown
# V6 Alpha 基本格式
*workflow-name          # 執行工作流程（推薦）
或
"自然語言描述"          # 使用自然語言啟動工作流程

# 範例
*prd                    # 建立產品需求文件
*create-architecture    # 建立架構文件
*dev-story              # 實作故事
*workflow-status        # 查看工作流程狀態
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

#### 1. 文件更新前準備
```markdown
# ⚠️ 重要：每次更新文件前必須執行
在進行任何文件更新前，所有 Agent 必須：

1. **讀取最新內容**
   - 使用 read_file 讀取要更新的文件的最新內容
   - 確保了解當前文件的完整狀態
   - 避免基於過時的記憶進行更新

2. **確認文件狀態**
   - 檢查是否有其他 Agent 同時進行的變更
   - 確認文件的當前版本和修改歷史
   - 確保變更不會與其他進行中的工作衝突

# 範例準備步驟
@agent 先讀取 [檔案名稱] 的最新內容
確認理解當前文件狀態 ✓
準備進行安全更新 ✓
```

#### 2. 開發前準備
```markdown
# @dev 專用 - 開發前必須閱讀
@dev 開始任何開發任務前，請先閱讀 docs/architecture/coding-standards.md 並確認理解所有編碼標準。

確認已閱讀編碼標準 ✓
```

#### 3. 工作階段完成要求
```markdown
# 每個工作階段結束時必須執行
每個工作階段完成後，所有 Agent 必須：

1. **更新相關文件**
   - 記錄處理過程與完成事項
   - 更新任務狀態和進度
   - 記錄遇到的問題和解決方案

2. **更新 Change Log**
   - 在專案根目錄的 CHANGELOG.md 中記錄變更
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

#### 建立 PRD (V6 Alpha)
```markdown
# 載入 PM 代理後執行
*prd

# 或使用自然語言
"建立 PRD for [產品名稱] with the following features:
- [功能 1]
- [功能 2]
- [功能 3]"

# 工作流程會引導您完成：
# - 產品需求描述
# - 使用者故事
# - 驗收標準
# - 優先順序矩陣
# - 成功指標
```

#### 需求澄清
```markdown
@pm Help me clarify the requirements for [功能名稱].
Current understanding: [目前的理解]
Questions to resolve: [需要澄清的問題]
```

### Architect (架構師) Prompts

#### 建立架構 (V6 Alpha)
```markdown
# 載入 Architect 代理後執行
*create-architecture

# 或使用自然語言
"建立架構文件 for [系統名稱] using:
- Frontend: [技術棧]
- Backend: [技術棧]
- Database: [資料庫]
- Authentication: [認證方式]"

# 工作流程會自動：
# - 讀取 PRD 和 Epic 文件
# - 生成規模自適應架構
# - 考量效能、安全性、可維護性和擴展性
```

#### 方案門檻檢查 (V6 Alpha)
```markdown
# 架構完成後執行
*solutioning-gate-check

# 驗證所有規劃文件的一致性：
# - PRD、UX、Architecture、Epics 是否對齊
```

#### 技術選型建議
```markdown
@architect Recommend technology choices for [專案類型]:
- Current team skills: [團隊技能]
- Project constraints: [專案限制]
- Future scalability needs: [未來擴展需求]
```

### Dev (開發者) Prompts

#### 實作故事 (V6 Alpha)
```markdown
# 載入 Dev 代理後執行
*dev-story

# 工作流程會自動：
# - 讀取當前故事文件
# - 讀取相關技術上下文（story-context）
# - 實作功能並包含測試
# - 更新 sprint-status.yaml

⚠️  重要：開始前請先閱讀 docs/architecture/coding-standards.md
✅ 已閱讀編碼標準並遵循所有規範
```

#### 程式碼審查 (V6 Alpha)
```markdown
# 實作完成後執行
*code-review

# 工作流程會執行：
# - 完整的程式碼品質檢查
# - 測試覆蓋率分析
# - 安全性檢查
# - 效能優化建議
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

### SM (Scrum Master) Prompts

#### 衝刺規劃 (V6 Alpha)
```markdown
# 載入 SM 代理後執行
*sprint-planning

# 工作流程會：
# - 從 Epic 文件生成 sprint-status.yaml
# - 初始化所有故事的狀態追蹤
```

#### 建立故事 (V6 Alpha)
```markdown
# 載入 SM 代理後執行
*create-story

# 工作流程會：
# - 從 Epic 中選擇下一個待建立的故事
# - 生成故事文件
# - 更新 sprint-status.yaml
```

#### 故事技術上下文 (V6 Alpha)
```markdown
# 建立故事後執行（建議）
*story-context

# 工作流程會：
# - 組裝故事的動態技術上下文
# - 包含相關的 PRD、架構、Epic 上下文
# - 為 Dev 實作提供完整背景
```

### Analyst (分析師) Prompts

#### 工作流程初始化 (V6 Alpha)
```markdown
# 載入 Analyst 代理後執行
*workflow-init

# 工作流程會引導您：
# - 描述專案目標
# - 選擇專案類型（新專案/既有專案）
# - 選擇規劃軌跡（Quick Flow / BMad Method / Enterprise Method）
# - 建立 bmm-workflow-status.yaml 追蹤文件
```

#### 查看工作流程狀態 (V6 Alpha)
```markdown
# 載入任何代理後執行
*workflow-status

# 會顯示：
# - 當前階段
# - 已完成的工作流程
# - 下一步建議的工作流程
# - 需要的代理
```

## 🎯 任務特定 Prompt

### 完整開發流程 (V6 Alpha)

這是 BMad Method V6 Alpha 的完整開發流程，適用於 BMad Method 和 Enterprise 軌跡：

```markdown
# ============================================
# 階段 1: 專案初始化
# ============================================

# 1. 初始化工作流程
*workflow-init
# 或使用 Cursor IDE 格式：
/bmad:bmm:workflows:workflow-init

# ============================================
# 階段 2: 既有專案文件化（僅既有專案需要）
# ============================================

# 2. 如果是既有專案（Brownfield），先建立專案文件
/bmad:bmm:workflows:document-project

# ============================================
# 階段 3: 規劃階段
# ============================================

# 3. 建立產品需求文件
/bmad:bmm:workflows:prd

# ============================================
# 階段 4: 方案階段
# ============================================

# 4. 建立架構文件
/bmad:bmm:workflows:create-architecture

# 5. 方案門檻檢查（驗證規劃一致性）
/bmad:bmm:workflows:solutioning-gate-check

# ============================================
# 階段 5: 實作階段 - 初始化
# ============================================

# 6. 初始化衝刺規劃
/bmad:bmm:workflows:sprint-planning

# ============================================
# 階段 6: Epic 循環（對每個 Epic 重複）
# ============================================

# **Epic 循環開始**

# 7. 建立 Epic 技術上下文
/bmad:bmm:workflows:epic-tech-context Epic x

# ============================================
# 階段 7: Story 循環（對每個 Story 重複）
# ============================================

# **Story 循環開始**

# 8. 建立 Story x.1
/bmad:bmm:workflows:create-story 建立 Story x.1

# 9. 為 Story x.1 生成技術上下文 XML
/bmad:bmm:workflows:story-context 為 Story x.1 生成技術上下文 XML

# 10. 開始實作 Story x.1
/bmad:bmm:workflows:dev-story 開始實作 Story x.1

# 11. 程式碼審查 Story x.1
/bmad:bmm:workflows:code-review Story x.1

# **Story 循環結束**

# ============================================
# 階段 8: Epic 完成
# ============================================

# 12. Epic 回顧
/bmad:bmm:workflows:retrospective Epic x

# **Epic 循環結束**

# ============================================
# 注意事項：
# ============================================
# - 每個工作流程建議使用新對話執行
# - 使用 *workflow-name 或 /bmad:bmm:workflows:workflow-name 格式
# - 隨時使用 *workflow-status 查看進度
# - Epic 和 Story 循環會根據實際情況重複執行
```

### 新功能開發 (V6 Alpha) - 快速參考

```markdown
# 簡化流程（快速參考）：
# 1. 如果是新專案，先執行 workflow-init
*workflow-init

# 2. 建立 PRD 或技術規格
*prd              # BMad Method/Enterprise
或
*tech-spec        # Quick Flow

# 3. 建立 Epic 和故事（如果使用 PRD）
*create-epics-and-stories

# 4. 建立架構（BMad Method/Enterprise）
*create-architecture

# 5. 開始實作
*sprint-planning
*create-story
*story-context
*dev-story
*code-review
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

### 專案啟動階段 (V6 Alpha)

```markdown
# 1. 載入 Analyst 代理，執行工作流程初始化
*workflow-init

# 2. 回答引導問題：
# - 描述專案目標
# - 選擇專案類型
# - 選擇規劃軌跡

# 3. 根據選擇的軌跡執行相應工作流程：
# Quick Flow: *tech-spec
# BMad Method: *prd → *create-epics-and-stories → *create-architecture
# Enterprise: *prd → 企業規劃 → *create-architecture

# 4. 隨時查看進度
*workflow-status
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

## 📚 V6 Alpha 使用提示

### 工作流程系統最佳實踐

1. **每個工作流程使用新對話** - 避免上下文限制和幻覺
2. **使用 workflow-status** - 隨時查看進度和下一步建議
3. **遵循工作流程順序** - 讓系統引導您完成整個開發流程
4. **使用 200k+ 上下文模型** - Claude Sonnet 4.5、GPT-4 等
5. **不要跳過驗證步驟** - `solutioning-gate-check` 和 `code-review` 很重要

### 撰寫有效 Prompt 的原則

1. **使用 * 前綴格式** - `*workflow-name` 是最可靠的方式
2. **具體明確** - 清楚描述期望的輸出
3. **提供上下文** - 包含相關背景資訊
4. **指定格式** - 說明期望的回應格式
5. **設定限制** - 明確範圍和限制條件

### V6 Alpha 工作流程指令速查表

| 工作流程 | 代理 | 指令 | 說明 |
|---------|------|------|------|
| 初始化 | Analyst | `*workflow-init` | 初始化專案工作流程 |
| 查看狀態 | 任何代理 | `*workflow-status` | 查看當前進度 |
| 建立 PRD | PM | `*prd` | 產品需求文件 |
| 技術規格 | PM | `*tech-spec` | 技術規格（Quick Flow） |
| 建立 Epic | PM | `*create-epics-and-stories` | 建立 Epic 和故事 |
| 建立架構 | Architect | `*create-architecture` | 建立架構文件 |
| 方案驗證 | Architect | `*solutioning-gate-check` | 驗證規劃一致性 |
| 衝刺規劃 | SM | `*sprint-planning` | 初始化衝刺追蹤 |
| 建立故事 | SM | `*create-story` | 建立下一個故事 |
| 故事上下文 | SM | `*story-context` | 建立故事技術上下文 |
| 實作故事 | Dev | `*dev-story` | 實作故事 |
| 程式碼審查 | Dev | `*code-review` | 程式碼審查 |

### 強制要求提醒

**⚠️ 所有 Agent 必須記住：**

每完成一個工作階段，必須立即執行以下四項：

1. **📖 文件更新前準備**
   - 使用 read_file 讀取最新內容
   - 確保了解當前文件的完整狀態
   - 避免基於過時的記憶進行更新

2. **📝 更新相關文件**
   - 記錄處理過程與完成事項
   - 更新任務狀態和進度追蹤

3. **📋 更新 Change Log**
   - 在專案根目錄的 CHANGELOG.md 中記錄變更
   - 包含日期、作者、變更內容和影響範圍

4. **🔄 更新文件狀態**
   - 更新 docs/ 目錄下所有相關文件的狀態
   - 標記完成項目、進行中項目、待處理項目
   - 更新最後修改時間和負責人資訊

### 最佳實踐

- **漸進式提問** - 從高層次開始，逐步細化
- **參考既有文件** - 利用專案中的既有文件
- **包含範例** - 提供期望輸出的範例
- **指定優先順序** - 明確哪些方面最重要
- **遵循編碼標準** - @dev 必須先閱讀 coding-standards.md
- **安全文件更新** - 更新前必須讀取最新內容
- **完整記錄** - 每個階段結束都要更新文件狀態

### 常見模式

- **任務分解**: 將大任務分解為小步驟
- **條件分支**: 根據不同情境提供不同處理方式
- **品質檢查**: 包含驗證和測試要求
- **文件生成**: 指定輸出文件的格式和內容
- **狀態追蹤**: 記錄每個步驟的進度和問題

---

*此文件將持續更新，歡迎貢獻新的 prompt 模板和最佳實踐。*