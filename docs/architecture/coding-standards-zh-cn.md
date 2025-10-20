# BMad Method - 通用编码标准 (Coding Standards)

**版本:** 1.0
**适用于:** 所有程序语言和框架
**日期:** 2025-10-15

## 1. 介绍 (Introduction)

本文档定义了使用 BMad Method 进行软件开发的通用编码标准、风格指南与最佳实践。这些标准适用于所有程序语言和框架，旨在确保代码的可读性、一致性与可维护性。

---

## 2. 通用原则 (General Principles)

*   **清晰优于简洁:** 代码首先是写给人看的，其次才是给机器执行的。
*   **遵守 The Zen of Python:** 在终端机输入 `import this`。
*   **DRY (Don't Repeat Yourself):** 避免重复的代码，尽可能地将它们抽象化为可重用的函数或类。
*   **KISS (Keep It Simple, Stupid):** 除非有充分的理由，否则应选择最简单直接的解决方案。
*   **请以正体中文回复与文件撰写**
*   **内部工具** 请使用 read_file 取代 read_many_files, write_file 取代 replace
*   **修改前请请重新读取档案** 更新记忆 确保原有的功能不会被影响
*   **注解** 请加上 日期 agent人员 story task
*   **OS环境** Windows
*   **所有 Agent 角色** 请参考 docs/architecture/definition-of-done.md 理解 & align 相关定义
*   **处理方式与结果** 请详实记录  并更新文件状态

---

### 2.1 开发者执行清单（Mandatory for Developers）

以下清单为开发者在进行任何变更时「必须」遵循的具体步骤，确保可追踪、可回溯、不中断既有功能：

1) 准备阶段
    - 读取将被修改的文件与相关依赖文件（避免猜测）。
    - 若需查找位置，先使用搜寻工具定位，再读取文件。
    - 记录关键决策点和设计考量。

2) 依循规范
    - 遵循各程序语言的官方编码标准。
    - 使用适当的格式化工具和 Linter。

3) 变更实施
    - 变更前加入注解（日期/作者/Story/Task）。
    - 使用最小化编辑；避免无关变更。
    - 追踪待办事项，完成时更新状态。

4) 验证与一致性
    - 执行 Lint 和格式检查，修正发现的问题。

5) 文件同步
    - 更新相关文件和注解。

6) 提交说明
    - 使用清晰的提交讯息描述变更。

---

## 3. 通用程序语言标准

### 3.1. 风格与格式化

*   **语言特定标准:** 遵循各程序语言的官方编码标准和惯例。
*   **自动格式化:** 使用适当的代码格式化工具（如 Prettier、Black、gofmt 等）。
*   **Linter:** 使用语言特定的静态分析工具来捕捉潜在错误和不符合规范的写法。

### 3.2. 通用命名惯例 (Naming Conventions)

不同程序语言有不同的命名惯例，但应保持一致性：

| 元素 | 常见惯例 | 范例 |
|------|----------|------|
| 变量 | camelCase 或 snake_case | `userName`, `user_name` |
| 函数/方法 | camelCase 或 snake_case | `calculateTotal()`, `calculate_total()` |
| 类/类型 | PascalCase | `UserService`, `ProjectManager` |
| 常量 | UPPER_SNAKE_CASE | `MAX_RETRY_COUNT`, `DEFAULT_TIMEOUT` |
| 私有成员 | 前缀底线 | `_privateField`, `_internalMethod()` |

### 3.3. 文件与注解 (Documentation & Comments)

*   **公开 API:** 所有公开的函数、类和模块都必须有完整文件。
*   **复杂逻辑:** 为复杂的业务逻辑和算法加上注解。
*   **文件格式:** 使用各语言标准的文件格式（如 JSDoc、docstrings、XML comments）。

```javascript
/**
 * 验证用户认证信息
 * @param {string} username - 用户名称
 * @param {string} password - 密码
 * @returns {Promise<boolean>} 验证结果
 */
async function validateCredentials(username, password) {
    // 实作验证逻辑
}
```

---

## 4. 安全性 (Security)

*   **敏感信息管理:** 所有敏感信息（API 密钥、数据库密码、证书等）都必须储存在环境变量或安全的配置管理系统中，绝不提交到版本控制。
*   **输入验证:** 始终验证和清理用户输入，防止注入攻击。
*   **认证与授权:** 实作适当的身份验证和权限检查机制。
*   **数据加密:** 敏感数据在储存和传输时应进行加密。
*   **依赖更新:** 定期更新第三方依赖以修补已知的安全漏洞。

---

## 5. 测试 (Testing)

*   **测试框架:** 根据程序语言选择适当的测试框架（如 JUnit、pytest、Jest、Vitest 等）。
*   **测试组织:** 将测试文件与原始程序代码放在相应的目录结构中。
*   **单元测试:** 测试个别函数、方法或类的逻辑，使用模拟对象隔离外部依赖。
*   **整合测试:** 测试元件间互动和数据流。
*   **测试覆盖率:** 维持合理的程序代码覆盖率，通常至少 70-80%。

---

## 6. 版本控制 (Version Control)

### 6.1. 分支策略

我们采用 `GitFlow` 的简化版：
*   `main`: 代表稳定、可随时发布的版本。只接受来自 `develop` 分支的合并。
*   `develop`: 开发分支，整合所有已完成的功能。
*   `feature/<feature-name>`: 开发新功能的分支，基于 `develop` 建立，完成后再合并回 `develop`。

### 6.2. 版本控制实践

*   **提交讯息:** 使用清晰、描述性的提交讯息，说明变更的内容和原因。
*   **分支策略:** 根据项目规模采用适当的分支策略（如 Git Flow、GitHub Flow）。
*   **代码审查:** 重要的变更应经过代码审查。
*   **变更追踪:** 使用议题追踪系统来追踪功能请求和错误修复。