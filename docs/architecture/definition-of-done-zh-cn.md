# BMad Method - 通用完成定义 (Definition of Done)

**版本:** 1.0
**适用于:** 所有项目类型
**日期:** 2025-10-15

---

## 介绍

本文档定义了使用 BMad Method 进行开发时，一个用户故事 (User Story) 或任务被视为「完成」所需满足的通用标准清单。这些标准适用于所有程序语言和项目类型，确保交付的质量与一致性。

---

## 通用标准 (General Criteria)

- [ ] **代码完成 (Code Complete):** 所有相关的代码都已撰写完成。
- [ ] **符合编码标准 (Coding Standards):** 代码遵循 `docs/architecture/coding-standards.md` 中定义的所有规范。
- [ ] **同侪审核 (Peer Reviewed):** 代码已经过至少一位其他开发人员的审核 (Code Review)，并已处理所有反馈。
- [ ] **没有已知的错误 (No Known Bugs):** 在交付当下，没有任何与此 Story 相关的已知错误。
- [ ] **文档更新 (Documentation Updated):** 相关的 API 文件、使用指南已同步更新。
- [ ] **版本控制 (Version Control):** 变更已提交到适当的分支，并遵循提交讯息规范。

---

## 开发标准 (Development Standards)

- [ ] **单元测试通过 (Unit Tests Pass):** 针对新或修改的业务逻辑，已撰写单元测试，且所有测试案例皆已通过。
- [ ] **代码质量检查通过 (Code Quality Checks Pass):** 所有代码都已通过 Linter 和格式化工具检查。
- [ ] **安全性检查 (Security Review):** 已检查常见的安全漏洞（如输入验证、认证、授权等）。
- [ ] **效能考量 (Performance Considerations):** 已评估新功能的效能影响，并确保符合效能标准。

---

## 测试与质量 (Testing & Quality)

- [ ] **测试覆盖率符合标准 (Test Coverage Meets Standards):** 代码覆盖率达到项目规定的最低标准。
- [ ] **整合测试通过 (Integration Tests Pass):** 相关的模块互动和 API 端点已有整合测试覆盖，且所有测试案例皆已通过。
- [ ] **手动测试完成 (Manual Testing Completed):** 关键功能已通过手动测试验证。
- [ ] **无回归错误 (No Regression Bugs):** 现有功能未受到新变更的影响。

---

## 部署与交付 (Deployment & Delivery)

- [ ] **构建成功 (Build Successful):** 项目可以成功构建/打包，没有任何错误。
- [ ] **环境相容性 (Environment Compatibility):** 在目标环境中功能正常运作。
- [ ] **部署准备完成 (Deployment Ready):** 所有必要的部署配置和脚本已准备完成。
- [ ] **回滚计划 (Rollback Plan):** 存在有效的回滚策略，以防部署失败。

---

## 项目特定标准 (Project-Specific Criteria)

根据项目类型，可能需要额外的完成标准：

### Web 应用程序
- [ ] **跨浏览器测试 (Cross-Browser Testing):** 在支持的浏览器中功能正常。
- [ ] **响应式设计 (Responsive Design):** 在不同屏幕尺寸下正确显示。
- [ ] **无障碍性 (Accessibility):** 符合 WCAG 基本标准。

### API 服务
- [ ] **API 文档更新 (API Documentation Updated):** OpenAPI/Swagger 文件已更新。
- [ ] **向后相容性 (Backward Compatibility):** 不破坏现有 API 契约。
- [ ] **速率限制测试 (Rate Limiting Tested):** API 速率限制功能正常。

### 行动应用程序
- [ ] **装置相容性 (Device Compatibility):** 在目标装置上正常运作。
- [ ] **离线功能测试 (Offline Functionality Tested):** 离线功能按预期运作。
- [ ] **应用程序商店要求 (App Store Requirements):** 符合应用程序商店的发布标准。