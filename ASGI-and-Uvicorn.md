<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：說明如何以 ASGI 與 Uvicorn 方式部署公準AI。 -->

# ASGI and Uvicorn

## 直接使用 Uvicorn

```bash
uvicorn app.web.server:app --host 0.0.0.0 --port 8000
```

## 從 Python 啟動

```python
import uvicorn
from app.web.server import app

uvicorn.run(app, host="0.0.0.0", port=8000)
```

## 適用情境

- 你已有 Python 服務框架
- 你想自己控制 server lifecycle
- 你想在外層加 middleware 或反向代理

