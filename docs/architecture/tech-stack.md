# 技術棧與架構決策

## 概述

本文件記錄專案的技術選型、架構決策和技術標準。這些決策基於專案需求、團隊經驗和業界最佳實踐。

## 核心技術棧

### 後端框架
```yaml
framework: Flask
version: 2.3+
language: Python 3.9+
why:
  - 輕量級且靈活，適合中小型應用
  - 豐富的擴展生態系統
  - 易於學習和維護
  - 良好的開發體驗
```

### 資料庫
```yaml
primary: SQLite
migration: SQLAlchemy
orm: Flask-SQLAlchemy
why:
  - 無需額外安裝，適合開發和小型部署
  - ACID 特性確保資料一致性
  - 支援複雜查詢和關聯
  - 易於遷移到 PostgreSQL/MySQL
```

### 前端技術
```yaml
framework: Vanilla JavaScript + Bootstrap
styling: CSS3 + Bootstrap 5
templating: Jinja2
why:
  - 減少複雜性，專注於功能
  - Bootstrap 提供一致的 UI 體驗
  - 原生 JavaScript 足夠處理互動需求
  - 易於維護和除錯
```

### 部署與容器化
```yaml
runtime: Python WSGI
server: Gunicorn (生產)
container: Docker (可選)
why:
  - Gunicorn 提供良好的並發處理
  - Docker 確保環境一致性
  - 支援水平擴展
```

## 架構模式

### 應用程式架構
```
Layered Architecture (分層架構)

┌─────────────────┐
│   Routes        │  # API 和 Web 路由
├─────────────────┤
│   Services      │  # 業務邏輯
├─────────────────┤
│   Models        │  # 資料模型
├─────────────────┤
│   Utils         │  # 工具函數
├─────────────────┤
│   Config        │  # 配置管理
└─────────────────┘
```

#### 各層責任

**Routes 層**
- HTTP 請求處理
- 輸入驗證和清理
- 回應格式化
- 錯誤處理

**Services 層**
- 業務邏輯實作
- 外部服務整合
- 資料處理和轉換
- 事務管理

**Models 層**
- 資料庫映射
- 資料驗證
- 關聯管理
- 查詢優化

**Utils 層**
- 共用工具函數
- 常數定義
- 輔助類別

### 設計模式應用

#### 工廠模式 (Factory Pattern)
```python
class NotificationServiceFactory:
    """通知服務工廠"""

    @staticmethod
    def create_service(service_type: str):
        if service_type == 'email':
            return EmailNotificationService()
        elif service_type == 'sms':
            return SMSNotificationService()
        else:
            raise ValueError(f"不支援的通知類型: {service_type}")
```

#### 策略模式 (Strategy Pattern)
```python
class AlertChecker:
    """警示檢查器"""

    def __init__(self, strategy):
        self.strategy = strategy

    def check(self, data):
        return self.strategy.check(data)

# 使用不同的檢查策略
checker = AlertChecker(OverdueInvoiceStrategy())
result = checker.check(invoice_data)
```

#### 觀察者模式 (Observer Pattern)
```python
class AlertSubject:
    """警示主題"""

    def __init__(self):
        self._observers = []

    def attach(self, observer):
        self._observers.append(observer)

    def notify(self, alert):
        for observer in self._observers:
            observer.update(alert)

# 通知服務訂閱警示事件
alert_subject = AlertSubject()
alert_subject.attach(email_service)
alert_subject.attach(logging_service)
```

## 資料庫設計原則

### 表格命名
```sql
-- 使用複數形式
users, invoices, alert_rules

-- 使用 snake_case
user_profiles, alert_history

-- 避免保留字
`order` → orders
`group` → groups
```

### 欄位設計
```sql
-- 主鍵
id INTEGER PRIMARY KEY AUTOINCREMENT

-- 外鍵
user_id INTEGER REFERENCES users(id)

-- 索引
CREATE INDEX ix_users_email ON users(email);
CREATE INDEX ix_invoices_created_at ON invoices(created_at);

-- 約束
CHECK (amount > 0)
UNIQUE (email)
```

### 關聯設計
```python
class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100), nullable=False)

    # 一對多關聯
    invoices = db.relationship('Invoice', backref='user', lazy=True)

class Invoice(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    user_id = db.Column(db.Integer, db.ForeignKey('user.id'), nullable=False)
    amount = db.Column(db.Float, nullable=False)
```

## API 設計原則

### RESTful API 設計
```
資源導向設計

GET    /api/users          # 獲取所有使用者
GET    /api/users/123      # 獲取特定使用者
POST   /api/users          # 建立新使用者
PUT    /api/users/123      # 更新使用者
DELETE /api/users/123      # 刪除使用者

GET    /api/users/123/invoices  # 獲取使用者的發票
```

### API 回應格式
```json
{
  "status": "success",
  "data": {
    "id": 123,
    "name": "使用者名稱",
    "email": "user@example.com"
  },
  "pagination": {
    "page": 1,
    "per_page": 20,
    "total": 100
  }
}
```

### 錯誤處理
```json
{
  "status": "error",
  "message": "請求參數無效",
  "errors": {
    "email": "Email 格式無效",
    "name": "名稱不能為空"
  },
  "code": "VALIDATION_ERROR"
}
```

## 安全性設計

### 認證與授權
```python
# JWT 認證
from flask_jwt_extended import JWTManager, jwt_required

app.config['JWT_SECRET_KEY'] = 'your-secret-key'
jwt = JWTManager(app)

@app.route('/api/protected')
@jwt_required()
def protected_route():
    return {'message': '這是受保護的端點'}
```

### 輸入驗證
```python
from marshmallow import Schema, fields, ValidationError

class UserSchema(Schema):
    name = fields.Str(required=True, validate=lambda x: len(x) > 0)
    email = fields.Email(required=True)
    age = fields.Int(validate=lambda x: x > 0)

@app.route('/api/users', methods=['POST'])
def create_user():
    schema = UserSchema()
    try:
        data = schema.load(request.get_json())
        # 處理驗證通過的資料
    except ValidationError as err:
        return {'errors': err.messages}, 400
```

### SQL 注入防護
```python
# 使用參數化查詢
user = User.query.filter_by(email=email).first()

# 使用 SQLAlchemy 表達式
query = db.session.query(User).filter(User.age > 18)

# 避免字串拼接
# BAD: f"SELECT * FROM users WHERE id = {user_id}"
# GOOD: db.session.query(User).filter_by(id=user_id).first()
```

## 效能優化策略

### 資料庫優化
```python
# 選擇性載入
user = User.query.options(db.joinedload(User.invoices)).get(user_id)

# 分頁查詢
page = User.query.paginate(page=1, per_page=20)

# 查詢優化
users = User.query.with_entities(User.name, User.email).all()
```

### 快取策略
```python
from flask_caching import Cache

cache = Cache(app, config={'CACHE_TYPE': 'simple'})

@app.route('/api/users')
@cache.cached(timeout=300)  # 快取 5 分鐘
def get_users():
    return User.query.all()
```

### 非同步處理
```python
from concurrent.futures import ThreadPoolExecutor
import asyncio

# 線程池執行
executor = ThreadPoolExecutor(max_workers=4)

@app.route('/api/heavy-task')
def heavy_task():
    future = executor.submit(process_heavy_task, request.args)
    return future.result()
```

## 測試策略

### 單元測試
```python
import unittest
from unittest.mock import patch

class TestUserService(unittest.TestCase):
    def setUp(self):
        self.service = UserService()

    def test_create_user(self):
        with patch('services.user_service.db') as mock_db:
            mock_db.add.return_value = None
            mock_db.commit.return_value = None

            result = self.service.create_user({'name': 'Test', 'email': 'test@example.com'})

            self.assertTrue(result['success'])
            mock_db.add.assert_called_once()
```

### 整合測試
```python
import pytest

@pytest.fixture
def client():
    app = create_app('testing')
    with app.test_client() as client:
        yield client

def test_create_user_api(client):
    response = client.post('/api/users', json={
        'name': 'Test User',
        'email': 'test@example.com'
    })

    assert response.status_code == 201
    data = response.get_json()
    assert data['name'] == 'Test User'
```

### 端到端測試
```python
def test_user_registration_flow(client):
    # 註冊使用者
    response = client.post('/register', data={
        'email': 'test@example.com',
        'password': 'password123'
    })
    assert response.status_code == 302  # 重定向到登入頁面

    # 登入
    response = client.post('/login', data={
        'email': 'test@example.com',
        'password': 'password123'
    })
    assert response.status_code == 302  # 重定向到儀表板

    # 檢查登入狀態
    response = client.get('/dashboard')
    assert b'歡迎' in response.data
```

## 部署架構

### 開發環境
```
Local Development
├── Python 3.9+
├── SQLite
├── Flask Dev Server
└── Local File System
```

### 生產環境
```
Production Deployment
├── Docker Container
├── Gunicorn WSGI Server
├── Nginx Reverse Proxy
├── PostgreSQL Database
├── Redis Cache (Optional)
└── Cloud Storage (Optional)
```

### 容器化配置
```dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "app:create_app()"]
```

## 監控與日誌

### 應用程式監控
```python
from flask import g, request
import time

@app.before_request
def start_timer():
    g.start = time.time()

@app.after_request
def log_request(response):
    if hasattr(g, 'start'):
        duration = time.time() - g.start
        logger.info(f"{request.method} {request.path} - {response.status_code} - {duration:.3f}s")
    return response
```

### 健康檢查
```python
@app.route('/health')
def health_check():
    return {
        'status': 'healthy',
        'timestamp': datetime.utcnow().isoformat(),
        'version': '1.0.0'
    }

@app.route('/health/database')
def database_health():
    try:
        db.session.execute(text('SELECT 1'))
        return {'database': 'healthy'}
    except Exception as e:
        return {'database': 'unhealthy', 'error': str(e)}, 503
```

### 錯誤追蹤
```python
import sentry_sdk
from sentry_sdk.integrations.flask import FlaskIntegration

sentry_sdk.init(
    dsn="your-sentry-dsn",
    integrations=[FlaskIntegration()],
    traces_sample_rate=1.0
)
```

## 擴展性考量

### 水平擴展
- **無狀態設計**: 應用程式不依賴本地狀態
- **外部會話儲存**: 使用 Redis 儲存會話
- **資料庫連接池**: 適當的連接池配置
- **負載均衡**: 多實例部署支援

### 垂直擴展
- **快取層**: Redis/Memcached 快取
- **讀寫分離**: 資料庫讀寫分離
- **CDN**: 靜態資源分發
- **資料庫分片**: 大資料量處理

### 微服務遷移路徑
```
單體應用 → API 分離 → 資料分離 → 服務拆分

階段 1: 保持單體，提供清晰的 API 邊界
階段 2: 將複雜功能拆分為獨立服務
階段 3: 實作服務間通訊
階段 4: 容器化部署和服務網格
```

## 決策記錄

### 技術選型理由

| 技術 | 選用理由 | 替代方案 | 權衡 |
|------|----------|----------|------|
| Flask | 輕量、靈活、學習成本低 | Django, FastAPI | Django 過於重量級，FastAPI 生態較新 |
| SQLite | 零配置、開發友好 | PostgreSQL, MySQL | 生產環境可輕鬆遷移 |
| Bootstrap | 快速開發、一致 UI | Tailwind, Material | 自定義需求不高時合適 |
| SQLAlchemy | 強大 ORM、靈活查詢 | Peewee, PonyORM | 學習曲線適中，功能完整 |

### 架構決策

#### 分層架構採用
**決定**: 使用傳統的分層架構 (Routes → Services → Models)
**理由**:
- 清晰的關注點分離
- 易於測試和維護
- 團隊熟悉度高
- 符合業務需求複雜度

**替代方案**: 洋蔥架構 (Onion Architecture)
**權衡**: 對於中小型專案，分層架構已足夠；未來可視需求演進

#### API 設計選擇
**決定**: RESTful API with JSON responses
**理由**:
- 業界標準，易於理解
- 良好的工具支援
- 適合 CRUD 操作
- 易於版本化

**替代方案**: GraphQL
**權衡**: REST 對當前需求足夠；GraphQL 在複雜查詢場景更優

## 總結

這些技術選型和架構決策基於以下原則：

1. **適度設計**: 不過度設計，但為未來擴展留出空間
2. **團隊能力**: 選擇團隊熟悉的技術棧
3. **業務需求**: 滿足當前和預期的業務需求
4. **維護性**: 易於維護、測試和部署
5. **成本效益**: 平衡開發成本和運營成本

這些決策將定期檢視，根據專案發展和團隊反饋進行調整。