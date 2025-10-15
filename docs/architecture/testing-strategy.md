# BMad Method - 通用測試策略

## 測試金字塔 (Testing Pyramid)

```
E2E 測試
   /  \
 整合測試
   /    \
 單元測試
```

## 測試組織 (Test Organization)

### 通用測試結構

```
tests/
├── unit/                    # 單元測試
│   ├── components/          # UI 元件測試
│   ├── services/            # 服務層測試
│   ├── models/              # 資料模型測試
│   └── utils/               # 工具函式測試
├── integration/             # 整合測試
│   ├── api/                 # API 整合測試
│   └── workflows/           # 業務流程測試
├── e2e/                     # 端到端測試
│   ├── user-journeys/       # 使用者旅程測試
│   └── critical-paths/      # 關鍵路徑測試
└── performance/             # 效能測試
```

## 測試範例 (Test Examples)

### 單元測試範例 (Unit Test Example)

```javascript
// JavaScript/TypeScript 單元測試
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

### 整合測試範例 (Integration Test Example)

```python
# Python 整合測試
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

### E2E 測試範例 (E2E Test Example)

```typescript
// Playwright E2E 測試
import { test, expect } from '@playwright/test';

test('user can create and view tasks', async ({ page }) => {
  await page.goto('/tasks');

  // 建立新任務
  await page.click('[data-testid="new-task-button"]');
  await page.fill('[data-testid="task-title"]', 'Test Task');
  await page.click('[data-testid="save-task"]');

  // 驗證任務已建立
  await expect(page.locator('[data-testid="task-list"]')).toContainText('Test Task');
});
```

## 測試策略 (Testing Strategy)

### 測試目標
- **單元測試**：驗證個別模組與函數的正確性
- **整合測試**：驗證模組間互動與資料流
- **E2E 測試**：驗證完整使用者工作流程
- **效能測試**：確保系統回應時間符合需求

### 測試框架選擇
根據程式語言選擇適當的測試框架：

| 語言 | 單元測試框架 | 整合/E2E 測試 | 模擬工具 |
|------|-------------|---------------|----------|
| JavaScript/TypeScript | Jest, Vitest | Playwright, Cypress | Jest mocks |
| Python | pytest, unittest | pytest, Selenium | unittest.mock |
| Java | JUnit, TestNG | Selenium, RestAssured | Mockito |
| C# | NUnit, xUnit | Selenium, SpecFlow | Moq |
| Go | testing (標準庫) | - | - |

### 測試覆蓋率目標
- **單元測試**：80% 以上程式碼覆蓋率
- **整合測試**：涵蓋所有關鍵互動路徑
- **E2E 測試**：涵蓋主要使用者工作流程
- **錯誤情境**：涵蓋常見錯誤與異常處理

## 測試執行環境

### 本地測試環境
根據使用的測試框架執行測試：

```bash
# JavaScript/TypeScript (Jest)
npm test                    # 執行所有測試
npm test -- --watch         # 監視模式
npm test -- --coverage      # 產生覆蓋率報告

# Python (pytest)
pytest tests/               # 執行所有測試
pytest tests/unit/ -v       # 詳細輸出
pytest --cov=src tests/     # 覆蓋率報告

# Java (Maven)
mvn test                    # 單元測試
mvn verify                  # 整合測試
mvn surefire-report:report  # 測試報告
```

### CI/CD 整合測試
- **觸發條件**：程式碼推送、PR 建立、排程執行
- **測試範圍**：單元測試、整合測試、E2E 測試
- **品質閘門**：測試通過率 > 95%，覆蓋率符合專案標準
- **報告產出**：測試結果、覆蓋率報告、效能基準

## 測試資料管理

### 測試資料策略
- **模擬資料**：建立逼真的測試資料集
- **資料隔離**：確保測試間資料不會互相影響
- **資料清理**：測試後自動清理測試資料
- **邊界條件**：涵蓋正常、邊界與異常資料情境

### 測試資料庫設定
- **開發環境**：使用記憶體資料庫進行快速測試
- **測試環境**：使用專用測試資料庫
- **資料庫遷移**：支援測試環境的結構遷移

## 品質保證流程

### 程式碼審查標準
- **測試需求**：新功能必須包含對應測試案例
- **測試品質**：測試案例必須明確且易於維護
- **邊界測試**：涵蓋正常與異常情境
- **效能考量**：避免測試案例影響系統效能

### 持續整合流程
1. **程式碼提交**：觸發自動語法檢查
2. **測試執行**：自動執行完整測試套件
3. **品質驗證**：確認測試通過率與覆蓋率
4. **部署準備**：僅允許通過測試的程式碼部署

## 測試類型詳細說明

### 單元測試 (Unit Tests)
- **目標**：驗證個別函數與方法的正確性
- **範圍**：隔離測試，不依賴外部資源
- **工具**：語言特定的單元測試框架
- **執行時間**：快速，通常在數秒內完成

### 整合測試 (Integration Tests)
- **目標**：驗證模組間互動與資料流
- **範圍**：測試模組整合點與介面契約
- **工具**：測試框架 + 測試資料庫/服務
- **執行時間**：中等，通常在數十秒內完成

### 端到端測試 (E2E Tests)
- **目標**：驗證完整使用者工作流程
- **範圍**：從使用者操作到系統回應的完整流程
- **工具**：Selenium、Playwright、Cypress 等
- **執行時間**：較長，通常需要數分鐘

### 效能測試 (Performance Tests)
- **目標**：驗證系統效能指標符合需求
- **範圍**：回應時間、資源使用率、負載處理
- **工具**：JMeter、k6、負載測試工具
- **執行時間**：依測試規模而定

## 測試自動化

### 自動化測試管線
- **觸發機制**：程式碼提交、排程執行、手動觸發
- **平行執行**：支援多執行緒測試執行
- **結果報告**：自動產生測試報告與趨勢分析
- **失敗通知**：測試失敗時自動通知相關人員

### 測試環境管理
- **環境隔離**：開發、測試、生產環境分離
- **環境複製**：支援測試環境快速複製與還原
- **資源監控**：追蹤測試環境資源使用狀況

## 測試結果分析

### 測試指標追蹤
- **通過率**：整體測試通過率統計
- **執行時間**：測試執行時間趨勢分析
- **覆蓋率**：程式碼覆蓋率追蹤與改進
- **錯誤率**：測試失敗率與原因分析

### 測試報告
- **詳細報告**：包含測試結果、錯誤詳情、效能指標
- **趨勢分析**：長期測試結果趨勢追蹤
- **改進建議**：基於測試結果的品質改進建議

## 測試團隊角色

### 開發工程師
- 負責撰寫與維護單元測試
- 確保新功能包含對應測試案例
- 參與測試失敗問題診斷與修復

### QA 工程師
- 負責整合測試與 E2E 測試設計
- 執行測試驗證與品質評估
- 提供測試結果分析與改進建議

### 架構師
- 定義測試架構與策略方向
- 審查測試案例設計與覆蓋率
- 指導測試技術選型與工具使用

## 測試文件標準

### 測試案例文件
- **明確描述**：清楚說明測試目的與驗證點
- **前置條件**：列出測試執行必要條件
- **測試步驟**：詳細的操作步驟說明
- **期望結果**：明確的驗證標準與成功條件
- **測試資料**：提供測試資料範例與準備方式

### 測試報告文件
- **執行摘要**：測試結果概覽與關鍵指標
- **詳細結果**：每個測試案例的執行結果與錯誤詳情
- **趨勢分析**：長期測試結果趨勢與改進建議
- **問題追蹤**：測試發現問題的記錄與狀態追蹤