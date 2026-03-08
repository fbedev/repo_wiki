<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：說明如何從 Python 程式嵌入與啟動公準AI。 -->

# Python Embedding

## 直接呼叫啟動器

```python
from app.web_launcher import main

main([
    "--host", "0.0.0.0",
    "--port", "8000",
    "--lmstudio-url", "http://127.0.0.1:1234/v1",
])
```

這是最接近 CLI 行為的 Python 嵌入方式。

## 使用 subprocess 啟動

```python
import subprocess

subprocess.run(
    [
        "gongin",
        "--host", "0.0.0.0",
        "--port", "8000",
    ],
    check=True,
)
```

這種方式適合把公準AI 當成獨立進程管理。

## 直接匯入 ASGI app

```python
from app.web.server import app
```

如果你的平台本身就是 Python Web stack，這是最自然的整合點。

