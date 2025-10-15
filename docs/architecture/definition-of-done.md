# BMad Method - 通用完成定義 (Definition of Done)

**版本:** 1.0
**適用於:** 所有專案類型
**日期:** 2025-10-15

---

## 介紹

本文件定義了使用 BMad Method 進行開發時，一個使用者故事 (User Story) 或任務被視為「完成」所需滿足的通用標準清單。這些標準適用於所有程式語言和專案類型，確保交付的品質與一致性。

---

## 通用標準 (General Criteria)

- [ ] **程式碼完成 (Code Complete):** 所有相關的程式碼都已撰寫完成。
- [ ] **符合編碼標準 (Coding Standards):** 程式碼遵循 `docs/architecture/coding-standards.md` 中定義的所有規範。
- [ ] **同儕審核 (Peer Reviewed):** 程式碼已經過至少一位其他開發人員的審核 (Code Review)，並已處理所有回饋。
- [ ] **沒有已知的錯誤 (No Known Bugs):** 在交付當下，沒有任何與此 Story 相關的已知錯誤。
- [ ] **文件更新 (Documentation Updated):** 相關的 API 文件、使用指南已同步更新。
- [ ] **版本控制 (Version Control):** 變更已提交到適當的分支，並遵循提交訊息規範。

---

## 開發標準 (Development Standards)

- [ ] **單元測試通過 (Unit Tests Pass):** 針對新或修改的業務邏輯，已撰寫單元測試，且所有測試案例皆已通過。
- [ ] **程式碼品質檢查通過 (Code Quality Checks Pass):** 所有程式碼都已通過 Linter 和格式化工具檢查。
- [ ] **安全性檢查 (Security Review):** 已檢查常見的安全漏洞（如輸入驗證、認證、授權等）。
- [ ] **效能考量 (Performance Considerations):** 已評估新功能的效能影響，並確保符合效能標準。

---

## 測試與品質 (Testing & Quality)

- [ ] **測試覆蓋率符合標準 (Test Coverage Meets Standards):** 程式碼覆蓋率達到專案規定的最低標準。
- [ ] **整合測試通過 (Integration Tests Pass):** 相關的模組互動和 API 端點已有整合測試覆蓋，且所有測試案例皆已通過。
- [ ] **手動測試完成 (Manual Testing Completed):** 關鍵功能已通過手動測試驗證。
- [ ] **無迴歸錯誤 (No Regression Bugs):** 現有功能未受到新變更的影響。

---

## 部署與交付 (Deployment & Delivery)

- [ ] **建置成功 (Build Successful):** 專案可以成功建置/打包，沒有任何錯誤。
- [ ] **環境相容性 (Environment Compatibility):** 在目標環境中功能正常運作。
- [ ] **部署準備完成 (Deployment Ready):** 所有必要的部署配置和腳本已準備完成。
- [ ] **回滾計劃 (Rollback Plan):** 存在有效的回滾策略，以防部署失敗。

---

## 專案特定標準 (Project-Specific Criteria)

根據專案類型，可能需要額外的完成標準：

### Web 應用程式
- [ ] **跨瀏覽器測試 (Cross-Browser Testing):** 在支援的瀏覽器中功能正常。
- [ ] **響應式設計 (Responsive Design):** 在不同螢幕尺寸下正確顯示。
- [ ] **無障礙性 (Accessibility):** 符合 WCAG 基本標準。

### API 服務
- [ ] **API 文件更新 (API Documentation Updated):** OpenAPI/Swagger 文件已更新。
- [ ] **向後相容性 (Backward Compatibility):** 不破壞現有 API 契約。
- [ ] **速率限制測試 (Rate Limiting Tested):** API 速率限制功能正常。

### 行動應用程式
- [ ] **裝置相容性 (Device Compatibility):** 在目標裝置上正常運作。
- [ ] **離線功能測試 (Offline Functionality Tested):** 離線功能按預期運作。
- [ ] **應用商店要求 (App Store Requirements):** 符合應用商店的發佈標準。
