# BMAD-method vs Openspec

> **版本**：v1.0
> **作者**：整合修订 by ChatGPT（GPT-5）
> **用途**：本文件供开发团队于 GitHub、技术简报或开源项目文件夹中使用。
> **特色**：强调开发方法论、AI协作架构、与实务应用指引。

---

## 1. 方法概述

### 🧠 BMAD-method
BMAD（**Behavioral Multi-Agent Development**）是一种以「多智能体协作」为核心的 AI 敏捷开发方法。
它模拟完整软件团队（PO、PM、架构师、开发、QA、UI/UX）间的互动，透过上下文与任务分工自动化推进开发。
强调 **代理式决策、上下文工程、可重复敏捷周期**。

**最新版本特色**：
- **模块化架构**：支持扩展包系统，可应用于游戏开发、创意写作等任何领域
- **双环境支持**：优化于 Web UI（规划阶段）和 IDE（开发阶段）
- **智慧配置系统**：core-config.yaml 实现项目结构灵活性
- **质量保证架构**：Test Architect (Quinn) 提供专业测试策略和质量门控

**适用场景**
- 复杂跨领域项目（如ERP、Portal、AI Agent）
- 团队分工明确、需高可追踪性的任务
- 需要 AI 参与策略性决策的开发环境
- 任何领域项目：软件开发、游戏开发、创意写作、商业策略等
- 新项目（Greenfield）和现有项目增强（Brownfield）

### ⚙️ Openspec
OpenSpec 是以「**规范驱动开发（Specification-Driven Development）**」为核心理念的 AI 开发框架。
它将「提案 → 审查 → 实现 → 归档」纳入自动化周期，确保需求、设计与代码一致。
强调 **可审查、可追溯、可重现** 的协作模式。

**适用场景**
- SaaS / API 平台开发与运维
- 高度合规与审查需求（如企业级项目）
- 开源社区或多人协作项目

---

## 2. 核心哲学比较

| 项目 | BMAD-method | Openspec |
|:--|:--|:--|
| **设计理念** | 多智能体模拟人类团队协作 | 规范驱动，确保一致性与可追溯性 |
| **开发流程核心** | Agent 协作 + Context-based 任务分工 | Proposal → Review → Spec → Archive |
| **强调点** | 自动化敏捷周期、上下文记录、质量保证架构 | 文件化、规范化、自动对齐 |
| **主要产出** | 可重现的团队决策纪录与代码、专业测试策略 | 标准化开发规范与版本化文档 |
| **典型应用** | AI Agent、企业自动化平台、复杂系统、游戏开发、创意写作 | SaaS 平台、开源项目、合规产品 |
| **环境支持** | Web UI + IDE 双环境优化 | 主要为规范化开发环境 |
| **扩展性** | 扩展包系统支持任何领域 | 专注规范化开发流程 |

---

## 3. 优缺点分析

| 分类 | BMAD-method | Openspec |
|:--|:--|:--|
| **优点** | - 多智能体自动分工与反馈<br>- 支持 Scrum/Agile 节拍<br>- 有助建立上下文式决策知识库<br>- 质量保证架构 (Test Architect)<br>- 扩展包支持任何领域 | - 文档与程序一致<br>- 开发历程可审查<br>- 适合版本控制与自动生成文档 |
| **缺点** | - 学习曲线高<br>- Context 管理需经验<br>- 适用中大型项目 | - 前期投入规范撰写成本高<br>- 不利快速原型或探索性开发<br>- 缺乏团队协作模拟 |

---

## 4. 实务流程示例

### BMAD-method 实作步骤
1. **规划阶段 (Web UI)**：使用 Gemini 等大上下文模型建立 PRD 和架构文档
2. **环境转换**：将文档复制到项目的 `docs/prd.md` 和 `docs/architecture.md`
3. **文档分片**：使用 PO agent 将大型文档分片为可管理的部分
4. **开发周期**：SM → Dev → QA 的顺序开发流程，每个故事一个完整周期
5. **质量保证**：Test Architect (Quinn) 提供专业测试策略和质量门控
📺 [YouTube 完整教学影片](https://www.youtube.com/watch?v=5mhjgwTWAPA)

### Openspec 实作步骤
1. 撰写功能提案 (Proposal Draft)
2. 经由 Review/Alignment 反复修正
3. AI 根据规范产出代码与测试
4. 自动归档与版本控制
📺 [Openspec 概念教学](https://www.youtube.com/watch?v=ANjiJQQIBo0)

---

## 5. 实际应用建议

| 开发需求类型 | 建议采用方法 |
|:--|:--|
| 构建 AI 自动开发团队、代理模拟项目 | **BMAD-method** |
| 高度流程化、需审查或规范追踪的系统 | **Openspec** |
| 教学 / 实验性项目 | **Openspec（易入门）** |
| 大型企业级项目或多角色整合 | **BMAD-method（高扩展）** |
| 游戏开发、创意写作、商业策略等非技术领域 | **BMAD-method（扩展包支持）** |
| 需要专业质量保证和测试策略的项目 | **BMAD-method（Test Architect）** |
| Brownfield 项目增强和重构 | **BMAD-method（专用工作流程）** |

---

## 6. 热门影音与教学资源

### 🎥 BMAD-method 教学精选
- [打造 AI 敏捷团队完整指南 (YouTube)](https://www.youtube.com/watch?v=5mhjgwTWAPA)
- [多智能体实战示范 (YouTube)](https://www.youtube.com/watch?v=31wPd03ZOJ0)
- [Gemini 实作 BMad 团队示例](https://www.youtube.com/watch?v=Coo4tfJsL7k)

### 🎬 Openspec 教学精选
- [OpenSpec 开发规范与实作教学 (YouTube)](https://www.youtube.com/watch?v=ANjiJQQIBo0)
- [AI 编码规范革命工具 (YouTube)](https://www.youtube.com/watch?v=NexwdkKrcUU)
- [从 Spec 到 Code 完整流程 (YouTube)](https://www.youtube.com/watch?v=xTOY6ryjHSE)

---

## 7. 参考与延伸阅读

| 主题 | 参考资源 |
|:--|:--|
| BMAD 官方文件 | [BMAD User Guide](docs/user-guide.md) |
| BMAD 核心架构 | [Core Architecture](docs/core-architecture.md) |
| BMAD Framework 解析 | [GMO Engineering Blog](https://recruit.gmo.jp/engineer/jisedai/blog/the-bmad-method-a-framework-for-spec-oriented-ai-driven-development/) |
| BMAD 社区与支持 | [Discord Community](https://discord.gg/gk8jAdXWmj) |
| Openspec 规范解读 | [CSDN 技术文章](https://blog.csdn.net/m0_71165399/article/details/153475459) |
| 规范化开发趋势 | [从Spec-Kit到OpenSpec趋势分析](https://www.53ai.com/news/LargeLanguageModel/2025101896725.html) |
| BMAD 扩展包指南 | [Expansion Packs Guide](docs/expansion-packs.md) |

---

## 8. 技术趋势与展望

- **BMAD-method**：
  正迈向「多智能体协作 + 自动敏捷规划」主流框架，预期将整合 GitOps、LLM CodeOps、与 Agentic Orchestration。最新 v4 版本已实现模块化架构、双环境支持、智慧配置系统和专业质量保证架构。

- **Openspec**：
  将成为「AI 开发治理」核心机制，未来与 Lint、CI/CD、API Schema 自动同步化整合，是企业开源项目治理的重点工具。

---

> 💡 **建议整合策略：**
> 若团队需快速起步，可采「OpenSpec 撰写规范 → BMAD method 自动执行与管理」的混合模式，兼具灵活与严谨。
> 对于复杂项目，建议优先使用 BMAD-method 的规划阶段建立完整文档，然后利用其质量保证架构确保开发质量。

---

## 9. 实做范例与快速开始指南

### 🚀 BMAD-method 快速开始指南

#### 第一步：环境准备
```bash
# 安装 BMAD-method 到你的项目
npx bmad-method install
```

#### 第二步：选择适合的团队
根据你的项目类型选择团队，并按照以下步骤设置：

**新项目开发（推荐）**：
```bash
# 下载 team-fullstack.txt
curl -O https://raw.githubusercontent.com/bmadcode/bmad-method/main/dist/teams/team-fullstack.txt

# 在 Gemini 中建立新 Gem
# 1. 前往 https://gemini.google.com/app
# 2. 建立新的 Gemini Gem
# 3. 上传 team-fullstack.txt 文件
# 4. 设置指令："Your critical operating instructions are attached, do not break character as directed"
```

**后端项目**：
```bash
# 下载 team-no-ui.txt
curl -O https://raw.githubusercontent.com/bmadcode/bmad-method/main/dist/teams/team-no-ui.txt

# 在 ChatGPT 中建立 Custom GPT
# 1. 前往 https://chat.openai.com/gpts
# 2. 建立新的 Custom GPT
# 3. 上传 team-no-ui.txt 作为知识文件
# 4. 设置系统提示："You are part of a BMAD-method development team focused on backend development"
```

**完整功能（进阶用户）**：
```bash
# 下载 team-all.txt
curl -O https://raw.githubusercontent.com/bmadcode/bmad-method/main/dist/teams/team-all.txt

# 在 Claude 中使用
# 1. 前往 https://claude.ai
# 2. 建立新对话
# 3. 复制粘贴 team-all.txt 的内容
# 4. 开始使用 /help 命令
```

**团队文件位置**：所有团队文件都可以在项目的 `dist/teams/` 目录中找到，或从 GitHub 直接下载。

#### 第三步：开始规划（Web UI 或 IDE 阶段）

**选项A：Web UI 规划（推荐新手，成本效益高）**
在 Gemini 或其他 Web UI 中：

**初始提示语示例**：
```
我想要建立一个[项目类型，例如：任务管理应用程序]。

项目目标：[简要描述你的想法]
主要功能：[列出3-5个核心功能]
目标用户：[描述目标用户群]
技术偏好：[提及你喜欢的技栈，如果有的话]

请帮我使用 BMAD-method 的团队来规划这个项目。
```

**具体的规划提示语**：
```
@pm 我需要为一个任务管理应用程序建立 PRD。这个应用程序应该让用户能够建立、编辑和跟踪任务，支持团队协作，并有基本的报告功能。请引导我完成 PRD 的建立过程。
```

```
@architect 基于这个 PRD，请设计一个可扩展的系统架构。考虑到用户可能会增长到 10,000 人，并需要支持移动应用程序。
```

**选项B：IDE 直接规划（适合有经验的开发者）**
在 Kilo Code 或其他支持 BMAD 的 IDE 中：

**安装并启动**：
```bash
# 安装 BMAD 到项目
npx bmad-method install

# 启动规划模式
@pm create-doc prd
```

**IDE 规划提示语示例**：
```
@pm 我想建立一个任务管理应用程序。请帮我建立完整的 PRD，包括用户故事、功能需求和接受标准。

项目背景：一个支持团队协作的任务管理工具
主要功能：
- 任务建立、编辑、删除
- 团队成员分配
- 进度跟踪和报告
- 通知系统

请一步步引导我完成 PRD 的建立。
```

```
@architect 现在 PRD 已经完成，请为这个任务管理系统设计技术架构。

技术要求：
- 前端：React 或 Vue
- 后端：Node.js 或 Python
- 数据库：PostgreSQL 或 MongoDB
- 支持 1000+ 并发用户
- 需要 RESTful API

请建立完整的架构文档。
```

**IDE 规划优势**：
- 直接在开发环境中工作
- 文档自动保存到项目结构
- 可立即进行开发阶段转换
- 无需在不同环境间复制文档

#### 第四步：开发阶段（IDE 阶段）
切换到你的 IDE 后：

**故事开发提示语**：
```
@sm 请为用户认证功能建立下一个开发故事。参考 PRD 中的安全需求和架构文档中的认证设计。
```

```
@dev 请实现这个用户登入功能。记得包含密码验证、session 管理，以及错误处理。参考架构文档中的安全设计。
```

```
@qa 请检查这个登入功能的实现，确保符合安全标准并有适当的测试覆盖。
```

### 📋 Openspec 快速开始指南

#### 第一步：建立规范结构
```yaml
# 建立 specs/ 目录结构
specs/
├── features/
│   ├── user-management/
│   └── task-management/
└── api/
    ├── v1/
    └── v2/
```

#### 第二步：撰写第一个功能提案
**初始提示语示例**：
```
我需要为用户管理系统建立规范。

功能需求：
- 用户注册和登入
- 密码重设功能
- 基本资料管理

请帮我撰写规范提案。
```

**规范提案范本**：
```yaml
proposal:
  id: "user-registration-v1"
  title: "用户注册功能"
  version: "1.0"
  author: "开发团队"
  date: "2025-10-20"

  description: |
    实现完整用户注册流程，包含验证和资料储存

  requirements:
    functional:
      - 电子邮件验证
      - 密码强度检查
      - 用户资料储存
    non-functional:
      - 响应时间 < 2秒
      - 支持 1000 并发用户
      - GDPR 合规

  acceptance-criteria:
    - 用户可以成功注册账号
    - 收到验证邮件
    - 密码符合安全标准
```

#### 第三步：审查与迭代
**审查提示语**：
```
请审查这个用户注册规范提案。检查是否涵盖了所有必要的安全考量，并确保规范足够详细以供开发使用。
```

#### 第四步：产生实作规范
**实作提示语**：
```
基于已审核通过的用户注册提案，请产生详细的 API 规范和数据库设计规范。
```

### 💡 实务运用范例

#### 范例 1：简单的待办事项应用程序

**BMAD-method 方式**：
1. **规划阶段**：`@pm 建立一个简单的待办事项应用程序的 PRD`
2. **架构设计**：`@architect 设计前端使用 React，后端使用 Node.js 的架构`
3. **开发阶段**：`@sm 建立第一个故事 - 任务建立功能`
4. **实作**：`@dev 实现任务 CRUD 操作`

**Openspec 方式**：
1. **提案**：撰写任务管理的规范提案
2. **审查**：团队审查功能完整性
3. **实作**：根据规范产生代码和测试

#### 范例 2：企业级用户管理系统

**BMAD-method 方式**：
- 使用完整团队（PM、Architect、Dev、QA、UX）
- 分阶段开发：认证 → 用户管理 → 权限控制 → 审计日志
- 每个阶段都有完整的测试和质量检查

**Openspec 方式**：
- 先建立完整的安全和合规规范
- 规范驱动开发，确保每项功能都符合企业标准
- 版本控制所有规范变更

### 🔧 常见问题与解决方法

#### BMAD-method 常见问题
**Q：第一次使用，应该从哪里开始？**
A：从 Web UI 开始，使用 `/help` 命令了解可用功能，然后说 `/pm 我想建立一个[你的项目想法]`。

**Q：如何在不同环境间切换？**
A：在 Web UI 完成规划后，将产生的文档复制到项目的 `docs/` 文件夹，然后在 IDE 中继续开发。

#### Openspec 常见问题
**Q：规范应该多详细？**
A：规范应该详细到开发者能够直接根据规范写代码，但不要过度设计。包含输入输出格式、错误处理和边界情况。

**Q：如何处理规范变更？**
A：所有规范变更都要通过审查流程，建立新版本，并记录变更原因。

### 📈 进阶技巧

#### BMAD-method 进阶运用
- **扩展包**：探索 `expansion-packs/` 目录，找到适合你领域的扩展
- **客制化**：修改 `core-config.yaml` 以适应你的项目结构
- **团队优化**：根据项目规模选择适当的团队大小

#### Openspec 进阶运用
- **自动化**：整合到 CI/CD 流程中自动验证规范一致性
- **版本管理**：使用语意化版本控制规范变更
- **跨项目重用**：建立共用规范库以提高开发效率

---

**文档更新纪录**
- 2025-10-20：v1.0 更新 - 加入 BMAD-method 最新特色、质量保证架构、扩展包支持等信息
- 2025-10-20：加入实做范例章节，提供 BMAD-method 和 Openspec 的具体应用范本

---

<div align="center">© 2025 Team Insight – AI Collaborative Development Framework</div>