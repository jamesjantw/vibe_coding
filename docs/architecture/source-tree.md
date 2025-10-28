# 專案結構與模組組織

## 專案總覽

本文件描述專案的目錄結構、模組組織原則和檔案命名規範。良好的專案結構有助於程式碼維護、團隊協作和專案擴展。

## 根目錄結構

```
project/
├── .bmad-core/              # BMad 框架核心檔案
├── app.py                   # 主應用程式入口
├── config.py                # 應用程式配置
├── database.py              # 資料庫初始化和配置
├── requirements.txt         # Python 依賴套件
├── README.md               # 專案說明文件
├── docs/                   # 文檔目錄
│   ├── README-alert-system.md
│   ├── prd-alert-notification-system.md
│   ├── stories/
│   └── architecture/
├── models/                 # 資料模型
│   ├── __init__.py
│   └── alert_models.py     # 警示相關模型
├── routes/                 # API 路由
│   ├── __init__.py
│   ├── alert_routes.py     # 警示管理路由
│   └── admin_routes.py     # 管理介面路由
├── services/               # 業務邏輯服務
│   ├── __init__.py
│   ├── alert_engine.py     # 警示檢查引擎
│   ├── notification_service.py  # 通知服務
│   └── scheduler_service.py     # 排程服務
├── templates/              # HTML 模板
│   ├── base.html
│   ├── admin/
│   │   ├── index.html      # 管理首頁
│   │   └── alerts.html     # 警示管理頁面
│   └── ef_templates/       # EF 系統模板
├── static/                 # 靜態檔案
│   ├── css/
│   │   └── styles.css
│   ├── js/
│   │   └── app.js
│   └── logo.svg
├── tests/                  # 測試檔案
│   ├── __init__.py
│   └── test_alert_system.py
├── utils/                  # 工具函數
│   ├── __init__.py
│   ├── cache_manager.py
│   ├── data_mapping.py
│   ├── db_eis.py
│   ├── draft_handler.py
│   ├── ef_handler.py
│   ├── error_handlers.py
│   ├── file_handlers.py
│   ├── logging_config.py
│   ├── response_helpers.py
│   ├── timesheet_ef_handler.py
│   └── validators.py
├── modules/                # 外部模組
│   ├── llm_api.py
│   ├── parser.py
│   └── pptx_generator.py
├── output/                 # 輸出檔案目錄
├── uploads/                # 上傳檔案目錄
├── misc/                   # 雜項檔案
├── .env                    # 環境變數
├── .gitignore             # Git 忽略檔案
├── .kilocodemodes         # Kilo Code 模式配置
├── .pytest_cache/         # Pytest 快取
├── COMBOBOX_DEBUG_GUIDE.md
├── COMBOBOX_FIX_SUMMARY.md
├── config.py.backup
├── debug_combobox.html
├── debug_dropdown.html
├── default_content.txt
├── default_template.pptx
├── DROPDOWN_TROUBLESHOOTING.md
├── IMPLEMENTATION_SUMMARY.md
├── LOGIC_CORRECTION_SUMMARY.md
├── models.py.backup
├── ocr.py
├── QUICK_TEST_GUIDE.md
├── REQUIRED_FIELDS_README.md
├── test_combobox_fix.html
├── test_declare_ym.html
├── test_expense_type_dropdown.html
├── test_expense_type_dropdown.md
├── test_googleapi.html
├── test_required_fields.html
├── test_tooltip.html
├── TOOLTIP_UPGRADE_README.md
├── 配置說明.md
├── .github/                # GitHub 配置
└── venv/                   # 虛擬環境
```

## 目錄說明

### 核心應用程式檔案

#### `app.py`
主應用程式入口點，負責：
- Flask 應用程式實例建立
- 藍圖註冊
- 中介軟體配置
- 應用程式工廠模式

#### `config.py`
應用程式配置管理：
- 環境變數處理
- 資料庫配置
- 安全設定
- 功能開關

#### `database.py`
資料庫初始化和遷移：
- SQLAlchemy 初始化
- 資料庫連線管理
- 表格建立和更新
- 索引優化

### 模組組織原則

#### Models 層 (`models/`)
資料模型定義：
- 每個主要實體一個檔案
- 關聯和約束定義
- 資料驗證邏輯
- 序列化方法

```python
# models/alert_models.py
class AlertRule(db.Model):
    """警示規則模型"""

class AlertHistory(db.Model):
    """警示歷史模型"""
```

#### Routes 層 (`routes/`)
API 端點定義：
- 按功能模組分檔案
- 輸入驗證和清理
- 錯誤處理
- 回應格式化

```python
# routes/alert_routes.py
@alert_bp.route('/rules', methods=['GET'])
def get_alert_rules():
    """獲取警示規則列表"""
```

#### Services 層 (`services/`)
業務邏輯實作：
- 複雜業務邏輯
- 外部服務整合
- 資料處理和轉換
- 事務管理

```python
# services/alert_engine.py
class AlertEngine:
    """警示檢查引擎"""
```

#### Utils 層 (`utils/`)
共用工具函數：
- 跨模組使用的功能
- 常數定義
- 輔助類別
- 共用演算法

```python
# utils/response_helpers.py
def success_response(data=None, message=None):
    """成功回應格式"""
```

### 前端組織

#### Templates (`templates/`)
HTML 模板結構：
- `base.html`: 基礎模板
- 按功能分目錄組織
- 模板繼承和區塊

#### Static Files (`static/`)
靜態資源組織：
- `css/`: 樣式表
- `js/`: JavaScript 檔案
- `img/`: 圖片資源

### 測試組織

#### Tests (`tests/`)
測試檔案結構：
- 對應應用程式模組
- 測試資料和模擬物件
- 整合測試和單元測試分離

```python
# tests/test_alert_system.py
class TestAlertSystem(unittest.TestCase):
    """警示系統測試"""
```

### 文檔組織

#### Docs (`docs/`)
文檔結構：
- `README.md`: 專案總覽
- `architecture/`: 架構文檔
- `stories/`: 使用者故事
- API 文檔和指南

## 檔案命名規範

### Python 檔案
```bash
# 模組檔案
module_name.py
alert_engine.py

# 測試檔案
test_module_name.py
test_alert_engine.py

# 初始化檔案
__init__.py

# 配置檔案
config.py
```

### HTML 模板
```bash
# 模板檔案
template_name.html
alerts.html
base.html

# 區塊模板
_form.html
_list.html
```

### 靜態檔案
```bash
# CSS 檔案
styles.css
alerts.css

# JavaScript 檔案
app.js
alerts.js

# 圖片檔案
logo.svg
icon.png
```

### SQL 檔案
```bash
# 遷移檔案
001_initial_schema.sql
002_add_alerts_table.sql

# 資料檔案
seed_data.sql
test_data.sql
```

## 匯入組織原則

### 絕對匯入 vs 相對匯入
```python
# 推薦：絕對匯入
from models.alert_models import AlertRule
from services.alert_engine import AlertEngine

# 避免：相對匯入（除非在同一個套件內）
from ..models.alert_models import AlertRule
```

### 匯入順序
```python
# 1. 標準庫匯入
import os
import sys
from datetime import datetime

# 2. 第三方庫匯入
import flask
from sqlalchemy import Column, Integer, String

# 3. 本地應用程式匯入
from . import models
from ..utils import helpers

# 空行分隔不同類型的匯入
```

### 迴圈匯入避免
```python
# 錯誤：迴圈匯入
# models/user.py
from services.user_service import UserService

# services/user_service.py
from models.user import User

# 正確：延遲匯入或重新組織
# services/user_service.py
def get_user_service():
    from models.user import User
    # 使用 User 類別
```

## 常數和配置管理

### 常數定義
```python
# constants.py 或在相關模組中
class AlertConstants:
    """警示相關常數"""

    # 嚴重性等級
    SEVERITY_INFO = 'info'
    SEVERITY_WARNING = 'warning'
    SEVERITY_ERROR = 'error'
    SEVERITY_CRITICAL = 'critical'

    # 狀態
    STATUS_NEW = 'new'
    STATUS_ACKNOWLEDGED = 'acknowledged'
    STATUS_RESOLVED = 'resolved'

    # 預設值
    DEFAULT_CHECK_INTERVAL = 3600  # 1 小時
    MAX_RETRY_ATTEMPTS = 3
```

### 配置階層
```python
# 1. 環境變數（最高優先級）
os.environ.get('DATABASE_URL')

# 2. 實例配置
app.config['DATABASE_URL']

# 3. 預設值（最低優先級）
DEFAULT_DATABASE_URL = 'sqlite:///app.db'
```

## 錯誤處理架構

### 自定義異常類別
```python
# exceptions.py
class AlertSystemError(Exception):
    """警示系統基礎異常"""
    pass

class AlertRuleNotFoundError(AlertSystemError):
    """警示規則不存在"""
    pass

class NotificationSendError(AlertSystemError):
    """通知發送失敗"""
    pass
```

### 錯誤處理裝飾器
```python
# decorators.py
def handle_errors(func):
    """錯誤處理裝飾器"""
    @wraps(func)
    def wrapper(*args, **kwargs):
        try:
            return func(*args, **kwargs)
        except AlertRuleNotFoundError as e:
            logger.warning(f"警示規則不存在: {e}")
            return error_response("警示規則不存在", 404)
        except NotificationSendError as e:
            logger.error(f"通知發送失敗: {e}")
            return error_response("通知發送失敗", 500)
        except Exception as e:
            logger.error(f"未預期的錯誤: {e}")
            return error_response("內部伺服器錯誤", 500)
    return wrapper
```

## 資料庫遷移管理

### 遷移檔案結構
```
migrations/
├── versions/
│   ├── 001_initial_schema.py
│   ├── 002_add_alert_system.py
│   └── 003_add_notification_templates.py
├── env.py          # 遷移環境配置
├── README.md       # 遷移說明
└── script.py.mako  # 遷移腳本模板
```

### 遷移命名規範
```bash
# 格式: 序號_描述.py
001_initial_schema.py
002_add_user_profiles.py
003_create_alert_tables.py
004_add_notification_support.py
```

## 日誌配置

### 日誌檔案組織
```
logs/
├── app.log          # 主應用程式日誌
├── error.log        # 錯誤日誌
├── access.log       # 存取日誌
├── alert.log        # 警示系統日誌
└── debug.log        # 除錯日誌（開發環境）
```

### 日誌器層次結構
```python
# logging_config.py
import logging
from logging.handlers import RotatingFileHandler

def setup_logging(app):
    """設定應用程式日誌"""

    # 根日誌器
    root_logger = logging.getLogger()
    root_logger.setLevel(logging.INFO)

    # 格式化器
    formatter = logging.Formatter(
        '%(asctime)s - %(name)s - %(levelname)s - %(message)s'
    )

    # 檔案處理器
    file_handler = RotatingFileHandler(
        'logs/app.log',
        maxBytes=10*1024*1024,  # 10MB
        backupCount=5
    )
    file_handler.setFormatter(formatter)
    root_logger.addHandler(file_handler)

    # 錯誤處理器
    error_handler = RotatingFileHandler(
        'logs/error.log',
        maxBytes=10*1024*1024,
        backupCount=5
    )
    error_handler.setLevel(logging.ERROR)
    error_handler.setFormatter(formatter)
    root_logger.addHandler(error_handler)

    # Flask 應用程式日誌器
    app.logger.addHandler(file_handler)
    app.logger.addHandler(error_handler)
```

## 環境特定配置

### 環境目錄結構
```
config/
├── __init__.py
├── base.py          # 基礎配置
├── development.py   # 開發環境
├── testing.py       # 測試環境
├── staging.py       # 預發環境
└── production.py    # 生產環境
```

### 配置類別設計
```python
# config/base.py
class BaseConfig:
    """基礎配置"""
    SECRET_KEY = os.environ.get('SECRET_KEY') or 'dev-key'
    DEBUG = False
    TESTING = False

    # 資料庫
    SQLALCHEMY_DATABASE_URI = os.environ.get('DATABASE_URL')
    SQLALCHEMY_TRACK_MODIFICATIONS = False

# config/development.py
class DevelopmentConfig(BaseConfig):
    """開發環境配置"""
    DEBUG = True
    SQLALCHEMY_DATABASE_URI = 'sqlite:///dev.db'

# config/production.py
class ProductionConfig(BaseConfig):
    """生產環境配置"""
    DEBUG = False
    SQLALCHEMY_DATABASE_URI = os.environ.get('DATABASE_URL')

    # 安全設定
    SESSION_COOKIE_SECURE = True
    SESSION_COOKIE_HTTPONLY = True
```

## 部署配置

### Docker 容器結構
```
Dockerfile
docker-compose.yml
.dockerignore
```

### 部署腳本
```
deploy/
├── scripts/
│   ├── deploy.sh
│   ├── rollback.sh
│   └── health_check.sh
├── config/
│   ├── nginx.conf
│   ├── gunicorn.conf.py
│   └── supervisor.conf
└── docker/
    ├── Dockerfile
    └── docker-compose.yml
```

## 總結

良好的專案結構是專案成功的重要基礎。本專案採用以下原則：

1. **關注點分離**: 清晰的模組分工
2. **可擴展性**: 易於新增功能和模組
3. **可維護性**: 一致的命名和組織規範
4. **可測試性**: 支援單元測試和整合測試
5. **部署友好**: 支援多環境部署

這些結構和規範將隨著專案發展持續優化和調整。