# BMAD-method vs Openspec

> **版本**：v1.0
> **作者**：整合修訂 by ChatGPT（GPT-5）
> **用途**：本文件供開發團隊於 GitHub、技術簡報或開源專案文件夾中使用。
> **特色**：強調開發方法論、AI協作架構、與實務應用指引。

---

## 1. 方法概述

### 🧠 BMAD-method
BMAD（**Behavioral Multi-Agent Development**）是一種以「多智能體協作」為核心的 AI 敏捷開發方法。
它模擬完整軟體團隊（PO、PM、架構師、開發、QA、UI/UX）間的互動，透過上下文與任務分工自動化推進開發。
強調 **代理式決策、上下文工程、可重複敏捷週期**。

**最新版本特色**：
- **模組化架構**：支援擴展包系統，可應用於遊戲開發、創意寫作等任何領域
- **雙環境支援**：優化於 Web UI（規劃階段）和 IDE（開發階段）
- **智慧配置系統**：core-config.yaml 實現專案結構靈活性
- **品質保證架構**：Test Architect (Quinn) 提供專業測試策略和品質門控

**適用場景**
- 複雜跨領域專案（如ERP、Portal、AI Agent）
- 團隊分工明確、需高可追蹤性的任務
- 需要 AI 參與策略性決策的開發環境
- 任何領域的專案：軟體開發、遊戲開發、創意寫作、商業策略等
- 新專案（Greenfield）和現有專案增強（Brownfield）

### ⚙️ Openspec
OpenSpec 是以「**規範驅動開發（Specification-Driven Development）**」為核心理念的 AI 開發框架。  
它將「提案 → 審查 → 實現 → 歸檔」納入自動化週期，確保需求、設計與代碼一致。  
強調 **可審核、可追溯、可重現** 的協作模式。

**適用場景**
- SaaS / API 平台開發與維運
- 高度合規與審查需求（如企業級專案）
- 開源社群或多人協作專案

---

## 2. 核心哲學比較

| 項目 | BMAD-method | Openspec |
|:--|:--|:--|
| **設計理念** | 多智能體模擬人類團隊協作 | 規範驅動，確保一致性與可追溯性 |
| **開發流程核心** | Agent 協作 + Context-based 任務分工 | Proposal → Review → Spec → Archive |
| **強調點** | 自動化敏捷週期、上下文記錄、品質保證架構 | 文件化、規範化、自動對齊 |
| **主要產出** | 可重現的團隊決策紀錄與代碼、專業測試策略 | 標準化開發規範與版本化文檔 |
| **典型應用** | AI Agent、企業自動化平台、複雜系統、遊戲開發、創意寫作 | SaaS 平台、開源專案、合規產品 |
| **環境支援** | Web UI + IDE 雙環境優化 | 主要為規範化開發環境 |
| **擴展性** | 擴展包系統支援任何領域 | 專注於規範化開發流程 |

---

## 3. 優缺點分析

| 分類 | BMAD-method | Openspec |
|:--|:--|:--|
| **優點** | - 多智能體自動分工與回饋<br>- 支援 Scrum/Agile 節奏<br>- 有助建立上下文式決策知識庫<br>- 品質保證架構 (Test Architect)<br>- 擴展包支援任何領域 | - 文件與程式一致<br>- 開發歷程可審查<br>- 適合版本控制與自動生成文件 |
| **缺點** | - 學習曲線高<br>- Context 管理需經驗<br>- 適用中大型專案 | - 前期投入規範撰寫成本高<br>- 不利於快速原型或探索性開發<br>- 缺乏團隊協作模擬 |

---

## 4. 實務流程示例

### BMAD-method 實作步驟
1. **規劃階段 (Web UI)**：使用 Gemini 等大上下文模型建立 PRD 和架構文檔
2. **環境轉換**：將文檔複製到專案的 `docs/prd.md` 和 `docs/architecture.md`
3. **文檔分片**：使用 PO agent 將大型文檔分片為可管理的部分
4. **開發週期**：SM → Dev → QA 的順序開發流程，每個故事一個完整週期
5. **品質保證**：Test Architect (Quinn) 提供專業測試策略和品質門控
📺 [YouTube 完整教學影片](https://www.youtube.com/watch?v=5mhjgwTWAPA)

### Openspec 實作步驟
1. 撰寫功能提案 (Proposal Draft)  
2. 經由 Review/Alignment 反覆修正  
3. AI 根據規範產出代碼與測試  
4. 自動歸檔與版本控制  
📺 [Openspec 概念教學](https://www.youtube.com/watch?v=ANjiJQQIBo0)

---

## 5. 實際應用建議

| 開發需求類型 | 建議採用方法 |
|:--|:--|
| 建構 AI 自動開發團隊、代理模擬專案 | **BMAD-method** |
| 高度流程化、需審核或規範追蹤的系統 | **Openspec** |
| 教學 / 實驗性專案 | **Openspec（易入門）** |
| 大型企業級專案或多角色整合 | **BMAD-method（高擴展）** |
| 遊戲開發、創意寫作、商業策略等非技術領域 | **BMAD-method（擴展包支援）** |
| 需要專業品質保證和測試策略的專案 | **BMAD-method（Test Architect）** |
| Brownfield 專案增強和重構 | **BMAD-method（專用工作流程）** |

---

## 6. 熱門影音與教學資源

### 🎥 BMAD-method 教學精選
- [打造 AI 敏捷團隊完整指南 (YouTube)](https://www.youtube.com/watch?v=5mhjgwTWAPA)  
- [多智能體實戰示範 (YouTube)](https://www.youtube.com/watch?v=31wPd03ZOJ0)  
- [Gemini 實作 BMad 團隊示例](https://www.youtube.com/watch?v=Coo4tfJsL7k)

### 🎬 Openspec 教學精選
- [OpenSpec 開發規範與實作教學 (YouTube)](https://www.youtube.com/watch?v=ANjiJQQIBo0)  
- [AI 編碼規範革命工具 (YouTube)](https://www.youtube.com/watch?v=NexwdkKrcUU)  
- [從 Spec 到 Code 完整流程 (YouTube)](https://www.youtube.com/watch?v=xTOY6ryjHSE)

---

## 7. 參考與延伸閱讀

| 主題 | 參考資源 |
|:--|:--|
| BMAD 官方文件 | [BMAD User Guide](docs/user-guide.md) |
| BMAD 核心架構 | [Core Architecture](docs/core-architecture.md) |
| BMAD Framework 解析 | [GMO Engineering Blog](https://recruit.gmo.jp/engineer/jisedai/blog/the-bmad-method-a-framework-for-spec-oriented-ai-driven-development/) |
| BMAD 社群與支援 | [Discord Community](https://discord.gg/gk8jAdXWmj) |
| Openspec 規範解說 | [CSDN 技術文章](https://blog.csdn.net/m0_71165399/article/details/153475459) |
| 規範化開發趨勢 | [從Spec-Kit到OpenSpec趨勢分析](https://www.53ai.com/news/LargeLanguageModel/2025101896725.html) |
| BMAD 擴展包指南 | [Expansion Packs Guide](docs/expansion-packs.md) |

---

## 8. 技術趨勢與展望

- **BMAD-method**：
  正邁向「多智能體協作 + 自動敏捷計畫」主流框架，預期將整合 GitOps、LLM CodeOps、與 Agentic Orchestration。最新 v4 版本已實現模組化架構、雙環境支援、智慧配置系統和專業品質保證架構。

- **Openspec**：
  將成為「AI 開發治理」核心機制，未來與 Lint、CI/CD、API Schema 自動同步化整合，是企業開源專案治理的重點工具。

---

> 💡 **建議整合策略：**
> 若團隊需快速起步，可採「OpenSpec 撰寫規範 → BMAD method 自動執行與管理」的混合模式，兼具靈活與嚴謹。
> 對於複雜專案，建議優先使用 BMAD-method 的規劃階段建立完整文檔，然後利用其品質保證架構確保開發品質。

---

## 9. 實做範例與快速開始指南

### 🚀 BMAD-method 快速開始指南

#### 第一步：環境準備
```bash
# 安裝 BMAD-method 到你的專案
npx bmad-method install
```

#### 第二步：選擇適合的團隊
根據你的專案類型選擇團隊，並按照以下步驟設定：

**新專案開發（推薦）**：
```bash
# 下載 team-fullstack.txt
curl -O https://raw.githubusercontent.com/bmadcode/bmad-method/main/dist/teams/team-fullstack.txt

# 在 Gemini 中建立新 Gem
# 1. 前往 https://gemini.google.com/app
# 2. 建立新的 Gemini Gem
# 3. 上傳 team-fullstack.txt 檔案
# 4. 設定指令："Your critical operating instructions are attached, do not break character as directed"
```

**後端專案**：
```bash
# 下載 team-no-ui.txt
curl -O https://raw.githubusercontent.com/bmadcode/bmad-method/main/dist/teams/team-no-ui.txt

# 在 ChatGPT 中建立 Custom GPT
# 1. 前往 https://chat.openai.com/gpts
# 2. 建立新的 Custom GPT
# 3. 上傳 team-no-ui.txt 作為知識檔案
# 4. 設定系統提示："You are part of a BMAD-method development team focused on backend development"
```

**完整功能（進階用戶）**：
```bash
# 下載 team-all.txt
curl -O https://raw.githubusercontent.com/bmadcode/bmad-method/main/dist/teams/team-all.txt

# 在 Claude 中使用
# 1. 前往 https://claude.ai
# 2. 建立新對話
# 3. 複製貼上 team-all.txt 的內容
# 4. 開始使用 /help 命令
```

**團隊檔案位置**：所有團隊檔案都可以在專案的 `dist/teams/` 目錄中找到，或從 GitHub 直接下載。

#### 第三步：開始規劃（Web UI 或 IDE 階段）

**選項A：Web UI 規劃（推薦新手，成本效益高）**
在 Gemini 或其他 Web UI 中：

**初始提示語示例**：
```
我想要建立一個[專案類型，例如：任務管理應用程式]。

專案目標：[簡要描述你的想法]
主要功能：[列出3-5個核心功能]
目標用戶：[描述目標用戶群]
技術偏好：[提及你喜歡的技術棧，如果有的話]

請幫我使用 BMAD-method 的團隊來規劃這個專案。
```

**具體的規劃提示語**：
```
/pm 我需要為一個任務管理應用程式建立 PRD。這個應用程式應該讓用戶能夠建立、編輯和追蹤任務，支持團隊協作，並有基本的報告功能。請引導我完成 PRD 的建立過程。
```

```
/architect 基於這個 PRD，請設計一個可擴展的系統架構。考慮到用戶可能會增長到 10,000 人，並需要支援移動應用程式。
```

**選項B：IDE 直接規劃（適合有經驗的開發者）**
在 Kilo Code 或其他支援 BMAD 的 IDE 中：

**安裝並啟動**：
```bash
# 安裝 BMAD 到專案
npx bmad-method install

# 啟動規劃模式
@pm create-doc prd
```

**IDE 規劃提示語示例**：
```
@pm 我想建立一個任務管理應用程式。請幫我建立完整的 PRD，包括用戶故事、功能需求和接受標準。

專案背景：一個支援團隊協作的任務管理工具
主要功能：
- 任務建立、編輯、刪除
- 團隊成員分配
- 進度追蹤和報告
- 通知系統

請一步步引導我完成 PRD 的建立。
```

```
@architect 現在 PRD 已經完成，請為這個任務管理系統設計技術架構。

技術要求：
- 前端：React 或 Vue
- 後端：Node.js 或 Python
- 資料庫：PostgreSQL 或 MongoDB
- 支援 1000+ 並發用戶
- 需要 RESTful API

請建立完整的架構文檔。
```

**IDE 規劃優勢**：
- 直接在開發環境中工作
- 文檔自動儲存到專案結構
- 可立即進行開發階段轉換
- 無需在不同環境間複製文檔

#### 第四步：開發階段（IDE 階段）
切換到你的 IDE 後：

**故事開發提示語**：
```
@sm 請為用戶認證功能建立下一個開發故事。參考 PRD 中的安全需求和架構文檔中的認證設計。
```

```
@dev 請實現這個用戶登入功能。記得包含密碼驗證、session 管理，以及錯誤處理。參考架構文檔中的安全設計。
```

```
@qa 請檢查這個登入功能的實現，確保符合安全標準並有適當的測試覆蓋。
```

### 📋 Openspec 快速開始指南

#### 第一步：建立規範結構
```yaml
# 建立 specs/ 目錄結構
specs/
├── features/
│   ├── user-management/
│   └── task-management/
└── api/
    ├── v1/
    └── v2/
```

#### 第二步：撰寫第一個功能提案
**初始提示語示例**：
```
我需要為用戶管理系統建立規範。

功能需求：
- 用戶註冊和登入
- 密碼重設功能
- 基本資料管理

請幫我撰寫規範提案。
```

**規範提案範本**：
```yaml
proposal:
  id: "user-registration-v1"
  title: "用戶註冊功能"
  version: "1.0"
  author: "開發團隊"
  date: "2025-10-20"

  description: |
    實現完整用戶註冊流程，包含驗證和資料儲存

  requirements:
    functional:
      - 電子郵件驗證
      - 密碼強度檢查
      - 用戶資料儲存
    non-functional:
      - 響應時間 < 2秒
      - 支援 1000 並發用戶
      - GDPR 合規

  acceptance-criteria:
    - 用戶可以成功註冊帳號
    - 收到驗證郵件
    - 密碼符合安全標準
```

#### 第三步：審查與迭代
**審查提示語**：
```
請審查這個用戶註冊規範提案。檢查是否涵蓋了所有必要的安全考量，並確保規範足夠詳細以供開發使用。
```

#### 第四步：產生實作規範
**實作提示語**：
```
基於已審核通過的用戶註冊提案，請產生詳細的 API 規範和資料庫設計規範。
```

### 💡 實務運用範例

#### 範例 1：簡單的待辦事項應用程式

**BMAD-method 方式**：
1. **規劃階段**：`/pm 建立一個簡單的待辦事項應用程式的 PRD`
2. **架構設計**：`/architect 設計前端使用 React，後端使用 Node.js 的架構`
3. **開發階段**：`@sm 建立第一個故事 - 任務建立功能`
4. **實作**：`@dev 實現任務 CRUD 操作`

**Openspec 方式**：
1. **提案**：撰寫任務管理的規範提案
2. **審查**：團隊審查功能完整性
3. **實作**：根據規範產生代碼和測試

#### 範例 2：企業級用戶管理系統

**BMAD-method 方式**：
- 使用完整團隊（PM、Architect、Dev、QA、UX）
- 分階段開發：認證 → 用戶管理 → 權限控制 → 審計日誌
- 每個階段都有完整的測試和品質檢查

**Openspec 方式**：
- 先建立完整的安全和合規規範
- 規範驅動開發，確保每項功能都符合企業標準
- 版本控制所有規範變更

### 🔧 常見問題與解決方案

#### BMAD-method 常見問題
**Q：第一次使用，應該從哪裡開始？**
A：從 Web UI 開始，使用 `/help` 命令了解可用功能，然後說 `/pm 我想建立一個[你的專案想法]`。

**Q：如何在不同環境間切換？**
A：在 Web UI 完成規劃後，將產生的文檔複製到專案的 `docs/` 資料夾，然後在 IDE 中繼續開發。

#### Openspec 常見問題
**Q：規範應該多詳細？**
A：規範應該詳細到開發者能夠直接根據規範寫代碼，但不要過度設計。包含輸入輸出格式、錯誤處理和邊界情況。

**Q：如何處理規範變更？**
A：所有規範變更都要通過審查流程，建立新版本，並記錄變更原因。

### 📈 進階技巧

#### BMAD-method 進階運用
- **擴展包**：探索 `expansion-packs/` 目錄，找到適合你領域的擴展
- **客製化**：修改 `core-config.yaml` 以適應你的專案結構
- **團隊優化**：根據專案規模選擇適當的團隊大小

#### Openspec 進階運用
- **自動化**：整合到 CI/CD 流程中自動驗證規範一致性
- **版本管理**：使用語意化版本控制規範變更
- **跨專案重用**：建立共用規範庫以提高開發效率

---

**文件更新紀錄**
- 2025-10-20：v1.0 更新 - 加入 BMAD-method 最新特色、品質保證架構、擴展包支援等資訊
- 2025-10-20：加入實做範例章節，提供 BMAD-method 和 Openspec 的具體應用範本

---

<div align="center">© 2025 Team Insight – AI Collaborative Development Framework</div>
