# BMad Method V6 Alpha - Agent Prompts 集合

这份文档收集了各个 BMad Method V6 Alpha Agent 常用的 prompt 模板和工作流程指令。这些 prompt 可以帮助你在不同场景下更有效地与 AI 代理互动。

**版本**: V6 Alpha (6.0.0-alpha.6)  
**重要变更**: V6 使用工作流程系统（Workflow）取代旧版任务（Tasks），指令格式为 `*workflow-name`

## 📋 文档结构

- **通用 Prompt** - 适用于所有 Agent 的基础指令
- **角色特定 Prompt** - 各个 Agent 的专用指令
- **任务特定 Prompt** - 针对特定任务的 prompt 模板
- **情境 Prompt** - 不同开发阶段的 prompt 范例

## 🔧 通用 Prompt

### 基础互动原则

```markdown
# 基本格式
@agent_name [任务描述]

# 范例
@pm 建立任务管理应用的 PRD
@architect 设计系统架构
@dev 实作用户认证
```

### 质量要求提示

```markdown
# 要求高质量输出
请提供详细、结构化的回应，包含：
- 具体的实作步骤
- 相关的程序代码范例
- 潜在的风险考量
- 测试建议
```

### 格式化要求

```markdown
# 要求结构化输出
请使用以下格式回应：
## 标题
- 要点 1
- 要点 2

## 程序代码范例
```language
// 程序代码内容
```
```

### 强制执行规则 (Mandatory Rules)

**所有 Agent 必须遵循：**

#### 1. 文件更新前准备
```markdown
# ⚠️ 重要：每次更新文件前必须执行
在进行任何文件更新前，所有 Agent 必须：

1. **读取最新内容**
    - 使用 read_file 读取要更新的文件的最新内容
    - 确保了解当前文件的完整状态
    - 避免基于过时的记忆进行更新

2. **确认文件状态**
    - 检查是否有其他 Agent 同时进行的变更
    - 确认文件的当前版本和修改历史
    - 确保变更不会与其他进行中的工作冲突

# 范例准备步骤
@agent 先读取 [档案名称] 的最新内容
确认理解当前文件状态 ✓
准备进行安全更新 ✓
```

#### 2. 开发前准备
```markdown
# @dev 专用 - 开发前必须阅读
@dev 开始任何开发任务前，请先阅读 docs/architecture/coding-standards.md 并确认理解所有编码标准。

确认已阅读编码标准 ✓
```

#### 3. 工作阶段完成要求
```markdown
# 每个工作阶段结束后必须执行
每个工作阶段完成后，所有 Agent 必须：

1. **更新相关文件**
    - 记录处理过程与完成事项
    - 更新任务状态和进度
    - 记录遇到的问題和解决方案

2. **更新 Change Log**
    - 在项目根目录的 CHANGELOG.md 中记录变更
    - 包含日期、作者、变更内容、影响范围

3. **更新文件状态**
    - 更新 docs/ 目录下相关文件的状态
    - 标记已完成、进行中、待处理的項目
    - 更新最后修改时间和负责人

# 范例更新格式
## [YYYY-MM-DD] - [Agent 名称]
### 完成事项
- [具体完成内容]
- [影响的档案/功能]

### 待处理事项
- [后续需要处理的項目]

### 问题与解决
- [遇到的问题]: [解决方案]
```

## 👥 角色特定 Prompt

### PM (Product Manager) Prompts

#### 建立 PRD
```markdown
@pm Create a comprehensive PRD for [产品名称] with the following features:
- [功能 1]
- [功能 2]
- [功能 3]

包含：用户故事、验收标准、优先顺序矩阵和成功指标。
```

#### 需求澄清
```markdown
@pm Help me clarify the requirements for [功能名称].
Current understanding: [目前的理解]
Questions to resolve: [需要澄清的问题]
```

### Architect (架构师) Prompts

#### 系统设计
```markdown
@architect Design a scalable architecture for [系统名称] using:
- Frontend: [技术栈]
- Backend: [技术栈]
- Database: [数据库]
- Authentication: [认证方式]

考虑：效能、安全性、可维护性和扩展性。
```

#### 技术选型建议
```markdown
@architect Recommend technology choices for [项目类型]:
- Current team skills: [团队技能]
- Project constraints: [项目限制]
- Future scalability needs: [未来扩展需求]
```

### Dev (开发者) Prompts

#### 功能实作
```markdown
@dev Implement [功能名称] with the following requirements:
- [需求 1]
- [需求 2]
- [需求 3]

Include: error handling, input validation, and unit tests.

⚠️  重要：开始前请先阅读 docs/architecture/coding-standards.md
✅ 已阅读编码标准并遵循所有规范
```

#### 程序代码重构
```markdown
@dev Refactor [档案/函数名称] to improve:
- Readability
- Performance
- Maintainability

Current issues: [现有问题]

⚠️  重要：开始前请先阅读 docs/architecture/coding-standards.md
✅ 已阅读编码标准并遵循所有规范
```

### QA (测试架构师) Prompts

#### 风险评估
```markdown
@qa *risk [故事名称]
评估实作风险并提供缓解策略。
```

#### 测试策略设计
```markdown
@qa *design [故事名称]
建立完整的测试情境，包括：
- 单元测试
- 整合测试
- 端到端测试
- 边界情况
```

#### 质量审核
```markdown
@qa *review [故事名称]
执行全面的质量评估并提供：
- 测试覆盖率分析
- 程序代码质量反馈
- 安全性考量
```

## 🎯 任务特定 Prompt

### 新功能开发

```markdown
@dev Implement a new feature for [功能描述]

Requirements:
- [具体需求]
- [技术限制]
- [质量标准]

请包含：
- 实作计划
- 程序代码结构
- 错误处理
- 单元测试
```

### 错误修复

```markdown
@dev Fix the bug in [功能/档案名称]

问题描述：[问题描述]
预期行为：[预期行为]
目前行为：[目前行为]

重现步骤：
1. [步骤 1]
2. [步骤 2]
3. [步骤 3]
```

### 程序代码审查

```markdown
@qa Review the following code changes:

Files changed: [档案列表]
Key changes: [主要变更]

重点关注：
- 程序代码质量
- 安全性漏洞
- 效能影响
- 测试覆盖率
```

## 📝 情境 Prompt

### 项目启动阶段

```markdown
@pm We're starting a new project: [项目描述]

Initial requirements:
- [需求 1]
- [需求 2]

请建立：
- 高层次项目愿景
- 初始史诗分解
- 技术建议
- 时间表估計
```

### 开发中期检查

```markdown
@sm Review our current progress on [故事名称]

Completed work: [已完成项目]
Remaining tasks: [待完成任务]
Blockers: [阻碍因素]

后续步骤建议：[建议下一步]
```

### 项目收尾阶段

```markdown
@po Prepare for project closure: [项目名称]

Deliverables checklist:
- [交付项目 1]
- [交付项目 2]

Documentation needed:
- [文件 1]
- [文件 2]

部署计划：[部署计划]
```

## 🔄 迭代优化 Prompt

### 反馈收集

```markdown
根据最近实作的 [功能名称]，请分析：

运作良好的部分：[优点]
可以改进的地方：[改进点]
学到的经验教训：[经验教训]

针对未来类似任务的建议：[未来建议]
```

### 流程改进

```markdown
@sm Review our development process for [项目阶段]

Current workflow: [现有流程]
Pain points identified: [痛点]
Proposed improvements: [改进建议]

请建议流程优化方案。
```

## 📚 使用提示

### 撰写有效 Prompt 的原则

1. **具体明确** - 清楚描述期望的输出
2. **提供上下文** - 包含相关背景信息
3. **指定格式** - 说明期望的回应格式
4. **设定限制** - 明确范围和限制条件

### 强制要求提醒

**⚠️ 所有 Agent 必须记住：**

每完成一个工作阶段，必须立即执行以下四项：

1. **📖 文件更新前准备**
    - 使用 read_file 读取最新内容
    - 确保了解当前文件的完整状态
    - 避免基于过时记忆进行更新

2. **📝 更新相关文件**
    - 记录处理过程与完成事项
    - 更新任务状态和进度追踪

3. **📋 更新 Change Log**
    - 在项目根目录的 CHANGELOG.md 中记录变更
    - 包含日期、作者、变更内容和影响范围

4. **🔄 更新文件状态**
    - 更新 docs/ 目录下所有相关文件的状态
    - 标记完成项目、进行中项目、待处理项目
    - 更新最后修改时间和负责人信息

### 最佳实践

- **渐进式提问** - 从高层次开始，逐步细化
- **参考既有文件** - 利用项目中的既有文件
- **包含范例** - 提供期望输出范例
- **指定优先顺序** - 明确哪些方面最重要
- **遵循编码标准** - @dev 必须先阅读 coding-standards.md
- **安全文件更新** - 更新前必须读取最新内容
- **完整记录** - 每个阶段结束都要更新文件状态

### 常见模式

- **任务分解**: 将大任务分解为小步骤
- **条件分支**: 根据不同情境提供不同处理方式
- **质量检查**: 包含验证和测试要求
- **文件生成**: 指定输出文件的格式和内容
- **状态追踪**: 记录每个步骤的进度和问题

---

*此文档将持续更新，欢迎贡献新的 prompt 模板和最佳实践。*