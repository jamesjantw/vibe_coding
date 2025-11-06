# BMad Method V6 Alpha - 通用测试策略

**BMad Method 版本:** V6 Alpha (6.0.0-alpha.6)

## 测试金字塔 (Testing Pyramid)

```
E2E 测试
    /  \
  整合测试
    /    \
  单元测试
```

## 测试组织 (Test Organization)

### 通用测试结构

```
tests/
├── unit/                    # 单元测试
│   ├── components/          # UI 元件测试
│   ├── services/            # 服务层测试
│   ├── models/              # 数据模型测试
│   └── utils/               # 工具函数测试
├── integration/             # 整合测试
│   ├── api/                 # API 整合测试
│   └── workflows/           # 业务流程测试
├── e2e/                     # 端到端测试
│   ├── user-journeys/       # 用户旅程测试
│   └── critical-paths/      # 关键路径测试
└── performance/             # 效能测试
```

## 测试范例 (Test Examples)

### 单元测试范例 (Unit Test Example)

```javascript
// JavaScript/TypeScript 单元测试
import { calculateTotal } from '../utils/calculator';

describe('calculateTotal', () => {
  test('should return correct sum for valid inputs', () => {
    expect(calculateTotal([1, 2, 3])).toBe(6);
  });

  test('should handle empty array', () => {
    expect(calculateTotal([])).toBe(0);
  });
});
```

### 整合测试范例 (Integration Test Example)

```python
# Python 整合测试
import pytest
from services.user_service import UserService
from repositories.user_repository import UserRepository

def test_user_creation_flow():
    repo = UserRepository()
    service = UserService(repo)

    user = service.create_user("john@example.com", "John Doe")
    assert user.email == "john@example.com"
    assert user.name == "John Doe"
    assert user.id is not None
```

### E2E 测试范例 (E2E Test Example)

```typescript
// Playwright E2E 测试
import { test, expect } from '@playwright/test';

test('user can create and view tasks', async ({ page }) => {
  await page.goto('/tasks');

  // 建立新任务
  await page.click('[data-testid="new-task-button"]');
  await page.fill('[data-testid="task-title"]', 'Test Task');
  await page.click('[data-testid="save-task"]');

  // 验证任务已建立
  await expect(page.locator('[data-testid="task-list"]')).toContainText('Test Task');
});
```

## 测试策略 (Testing Strategy)

### 测试目标
- **单元测试**：验证个别模块与函数的正确性
- **整合测试**：验证模块间互动与数据流
- **E2E 测试**：验证完整用户工作流程
- **效能测试**：确保系统回应时间符合需求

### 测试框架选择
根据程序语言选择适当的测试框架：

| 语言 | 单元测试框架 | 整合/E2E 测试 | 模拟工具 |
|------|-------------|---------------|----------|
| JavaScript/TypeScript | Jest, Vitest | Playwright, Cypress | Jest mocks |
| Python | pytest, unittest | pytest, Selenium | unittest.mock |
| Java | JUnit, TestNG | Selenium, RestAssured | Mockito |
| C# | NUnit, xUnit | Selenium, SpecFlow | Moq |
| Go | testing (标准库) | - | - |

### 测试覆盖率目标
- **单元测试**：80% 以上程序代码覆盖率
- **整合测试**：涵盖所有关键互动路径
- **E2E 测试**：涵盖主要用户工作流程
- **错误情境**：涵盖常见错误与异常处理

## 测试执行环境

### 本地测试环境
根据使用的测试框架执行测试：

```bash
# JavaScript/TypeScript (Jest)
npm test                    # 执行所有测试
npm test -- --watch         # 监视模式
npm test -- --coverage      # 产生覆盖率报告

# Python (pytest)
pytest tests/               # 执行所有测试
pytest tests/unit/ -v       # 详细输出
pytest --cov=src tests/     # 覆盖率报告

# Java (Maven)
mvn test                    # 单元测试
mvn verify                  # 整合测试
mvn surefire-report:report  # 测试报告
```

### CI/CD 整合测试
- **触发条件**：程序代码推送、PR 建立、排程执行
- **测试范围**：单元测试、整合测试、E2E 测试
- **质量闸门**：测试通过率 > 95%，覆盖率符合项目标准
- **报告产出**：测试结果、覆盖率报告、效能基准

## 测试数据管理

### 测试数据策略
- **模拟数据**：建立逼真的测试数据集
- **数据隔离**：确保测试间数据不会互相影响
- **数据清理**：测试后自动清理测试数据
- **边界条件**：涵盖正常、边界与异常数据情境

### 测试数据库设置
- **开发环境**：使用内存数据库进行快速测试
- **测试环境**：使用专用测试数据库
- **数据库迁移**：支援测试环境的结构迁移

## 质量保证流程

### 程序代码审查标准
- **测试需求**：新功能必须包含对应测试案例
- **测试质量**：测试案例必须明确且易于维护
- **边界测试**：涵盖正常与异常情境
- **效能考量**：避免测试案例影响系统效能

### 持续整合流程
1. **程序代码提交**：触发自动语法检查
2. **测试执行**：自动执行完整测试套件
3. **质量验证**：确认测试通过率与覆盖率
4. **部署准备**：仅允许通过测试的程序代码部署

## 测试类型详细说明

### 单元测试 (Unit Tests)
- **目标**：验证个别函数与方法的正确性
- **范围**：隔离测试，不依赖外部资源
- **工具**：语言特定的单元测试框架
- **执行时间**：快速，通常在数秒内完成

### 整合测试 (Integration Tests)
- **目标**：验证模块间互动与数据流
- **范围**：测试模块整合点与介面契约
- **工具**：测试框架 + 测试数据库/服务
- **执行时间**：中等，通常在数十秒内完成

### 端到端测试 (E2E Tests)
- **目标**：验证完整用户工作流程
- **范围**：从用户操作到系统回应的完整流程
- **工具**：Selenium、Playwright、Cypress 等
- **执行时间**：较长，通常需要数分钟

### 效能测试 (Performance Tests)
- **目标**：验证系统效能指标符合需求
- **范围**：回应时间、资源使用率、负载处理
- **工具**：JMeter、k6、负载测试工具
- **执行时间**：依测试规模而定

## 测试自动化

### 自动化测试管线
- **触发机制**：程序代码提交、排程执行、手动触发
- **平行执行**：支援多执行绪测试执行
- **结果报告**：自动产生测试报告与趋势分析
- **失败通知**：测试失败时自动通知相关人员

### 测试环境管理
- **环境隔离**：开发、测试、生产环境分离
- **环境复制**：支援测试环境快速复制与还原
- **资源监控**：追踪测试环境资源使用状况

## 测试结果分析

### 测试指标追踪
- **通过率**：整体测试通过率统计
- **执行时间**：测试执行时间趋势分析
- **覆盖率**：程序代码覆盖率追踪与改进
- **错误率**：测试失败率与原因分析

### 测试报告
- **详细报告**：包含测试结果、错误详情、效能指标
- **趋势分析**：长期测试结果趋势追踪
- **改进建议**：基于测试结果的质量改进建议

## 测试团队角色

### 开发工程师
- 负责撰写与维护单元测试
- 确保新功能包含对应测试案例
- 参与测试失败问题诊断与修复

### QA 工程师
- 负责整合测试与 E2E 测试设计
- 执行测试验证与质量评估
- 提供测试结果分析与改进建议

### 架构师
- 定义测试架构与策略方向
- 审查测试案例设计与覆盖率
- 指导测试技术选型与工具使用

## 测试文档标准

### 测试案例文档
- **明确描述**：清楚说明测试目的与验证点
- **前置条件**：列出测试执行必要条件
- **测试步骤**：详细的操作步骤说明
- **期望结果**：明确的验证标准与成功条件
- **测试数据**：提供测试数据范例与准备方式

### 测试报告文档
- **执行摘要**：测试结果概览与关键指标
- **详细结果**：每个测试案例的执行结果与错误详情
- **趋势分析**：长期测试结果趋势与改进建议
- **问题追踪**：测试发现问题的记录与状态追踪