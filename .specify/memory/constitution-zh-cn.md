# Speckit Constitution

## 核心原则 (Core Principles)

### I. 高质量与干净代码 (High Quality & Clean Code)
代码首先是为人类编写的，其次才是为机器执行的。遵循 DRY (Don't Repeat Yourself) 原则，避免重复代码。采用 KISS (Keep It Simple, Stupid) 原则，除非有充分理由，否则选择最简单直接的解决方案。

### II. 可测试性 (Testability)
所有代码必须是可测试的。采用测试驱动开发 (TDD) 方法：先写测试 → 测试失败 → 实现功能 → 测试通过 → 重构。维持合理的代码覆盖率，通常至少 70-80%。

### III. 最小可行产品 (Minimum Viable Product)
避免过度设计。从最简单的解决方案开始，根据实际需求逐步迭代。遵循 YAGNI (You Aren't Gonna Need It) 原则。

### IV. 繁体中文优先 (Traditional Chinese First)
所有文档、注释和回复均使用繁体中文。确保团队沟通一致性。

### V. 开发者执行清单 (Developer Execution Checklist)
开发者在进行任何变更时必须遵循以下步骤：
1. 准备阶段：读取将被修改的文件与相关依赖文件，避免猜测。若需要查找位置，先使用搜索工具定位，再读取文件。记录关键决策点和设计考虑。
2. 遵循规范：遵循各编程语言的官方编码标准。使用适当的格式化工具和 Linter。
3. 变更实施：变更前加入注释（日期/作者/Story/Task）。使用最小化编辑；避免无关变更。跟踪待办事项，完成时更新状态。
4. 验证与一致性：执行 Lint 和格式检查，修正发现的问题。
5. 文档同步：更新相关文档和注释。
6. 提交说明：使用清晰的提交消息描述变更。

## 编码标准 (Coding Standards)

### 风格与格式化
- 遵循各编程语言的官方编码标准和惯例。
- 使用自动格式化工具（如 Prettier、Black、gofmt 等）。
- 使用语言特定的静态分析工具 (Linter) 来捕捉潜在错误。

### 命名惯例
保持一致的命名惯例：

| 元素 | 常见惯例 | 示例 |
|------|----------|------|
| 变量 | camelCase 或 snake_case | `userName`, `user_name` |
| 函数/方法 | camelCase 或 snake_case | `calculateTotal()`, `calculate_total()` |
| 类/类型 | PascalCase | `UserService`, `ProjectManager` |
| 常量 | UPPER_SNAKE_CASE | `MAX_RETRY_COUNT`, `DEFAULT_TIMEOUT` |
| 私有成员 | 前缀下划线 | `_privateField`, `_internalMethod()` |

### 文档与注释
- 所有公开 API 必须有完整文档。
- 复杂逻辑需加上注释。
- 使用标准文档格式（如 JSDoc、docstrings、XML comments）。

## 安全性 (Security)
- 敏感信息管理：所有敏感信息存储在环境变量或安全配置系统中，绝不提交到版本控制。
- 输入验证：始终验证和清理用户输入，防止注入攻击。
- 认证与授权：实现适当的身份验证和权限检查机制。
- 数据加密：敏感数据在存储和传输时进行加密。
- 依赖更新：定期更新第三方依赖以修补安全漏洞。

## 测试策略 (Testing Strategy)
- 根据编程语言选择适当测试框架（如 JUnit、pytest、Jest、Vitest 等）。
- 测试文件与原始代码放在相应目录结构中。
- 单元测试：测试个别函数、方法或类别的逻辑，使用模拟对象隔离外部依赖。
- 集成测试：测试组件间互动和数据流。
- 测试覆盖率：维持 70-80% 以上。

## 版本控制 (Version Control)
采用 GitFlow 简化版：
- `main`: 稳定可发布版本，只接受来自 `develop` 的合并。
- `develop`: 开发分支，整合所有完成功能。
- `feature/<feature-name>`: 新功能分支，基于 `develop` 建立，完成后合并回 `develop`。

实践：
- 清晰描述性提交消息。
- 重要变更经过代码审查。
- 使用议题跟踪系统跟踪功能请求和错误修复。

## 开发工作流程 (Development Workflow)

### 代码审查
所有变更必须经过代码审查。审查重点包括：
- 符合编码标准
- 测试覆盖率
- 安全性考虑
- 性能影响

### 质量门槛
- 所有测试必须通过
- Lint 检查无错误
- 代码覆盖率达标
- 安全扫描通过

## 治理 (Governance)
宪法优于所有其他实践。所有 PR/审查必须验证合规性。复杂性必须有正当理由。使用相关指导文档进行开发指导。

**版本**: 1.0 | **通过日期**: 2025-10-28 | **最后修订**: 2025-10-28