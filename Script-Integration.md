<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：提供腳本層級的整合方式與實務範例。 -->

# Script Integration

這一頁專門說明如何用「腳本」或「服務整合」方式使用公準AI，而不是只把它當成一個手動點擊的 Web UI。

目標讀者：

- 想用 shell script 啟動公準AI 的維運人員
- 想從 Python 程式直接啟動或嵌入公準AI 的工程師
- 想把公準AI 納入內部流程、自動化、服務管理的人

---

## 1. 整合層級總覽

公準AI 可以從三個層級整合：

### A. CLI 層

最簡單、最穩定，也最推薦。

```bash
gongin
```

適合：

- 手動啟動服務
- shell script 包裝
- systemd / supervisor / launchd 啟動
- 容器 entrypoint

### B. Python 啟動器層

如果你已經有 Python 程式，希望從程式碼裡啟動公準AI，可直接呼叫啟動器：

```python
from app.web_launcher import main

main([
    "--host", "0.0.0.0",
    "--port", "8000",
])
```

適合：

- 內部工具鏈
- 自動化平台
- 自建控制平面

### C. ASGI 應用層

如果你要把公準AI 當成 ASGI app 掛進既有 Python Web stack，可以直接使用：

```python
from app.web.server import app
```

適合：

- 自訂 Uvicorn/Gunicorn 啟動
- 進一步做反向代理、路由合併、內部平台整合

---

## 2. 最低整合前提

在整合公準AI 之前，至少要有：

- Python 環境
- 可用的模型後端
- 正確的 base URL
- 可寫入的工作區

常見模型後端是 LM Studio 或其他 OpenAI-compatible API。

---

## 3. CLI 整合方式

### 最小啟動

```bash
gongin
```

預設會：

- 啟動 Web UI
- 綁定 `0.0.0.0:8000`
- 使用目前設定檔或環境變數中的模型設定

### 指定 Web 位址

```bash
gongin --host 0.0.0.0 --port 8000
```

### 指定 LM Studio 完整位址

```bash
gongin --lmstudio-url http://127.0.0.1:1234/v1
```

### 只覆蓋 host / port

```bash
gongin --lmstudio-host 192.168.1.50 --lmstudio-port 1235
```

### 切換資料庫執行模式

```bash
gongin --test
```

或：

```bash
gongin --live
```

---

## 4. Shell Script 包裝範例

### 範例：基本啟動腳本

```bash
#!/usr/bin/env bash
set -euo pipefail

export GONGIN_BASE_URL="http://127.0.0.1:1234/v1"
export GONGIN_MODEL="qwen/qwen3-coder-next"

gongin --host 0.0.0.0 --port 8000
```

### 範例：明確覆蓋旗標

```bash
#!/usr/bin/env bash
set -euo pipefail

gongin \
  --host 0.0.0.0 \
  --port 8000 \
  --lmstudio-url http://127.0.0.1:1234/v1
```

### 範例：背景執行

```bash
nohup gongin --host 0.0.0.0 --port 8000 > gongin.log 2>&1 &
```

---

## 5. Python 整合方式

### 5.1 直接呼叫啟動器

```python
from app.web_launcher import main

main([
    "--host", "0.0.0.0",
    "--port", "8000",
    "--lmstudio-url", "http://127.0.0.1:1234/v1",
])
```

這是最接近 CLI 行為的 Python 方案。

### 5.2 直接以 subprocess 啟動 CLI

如果你想保持系統界線清楚，也可以從 Python 呼叫 CLI：

```python
import subprocess

subprocess.run(
    [
        "gongin",
        "--host", "0.0.0.0",
        "--port", "8000",
        "--lmstudio-url", "http://127.0.0.1:1234/v1",
    ],
    check=True,
)
```

這種方式適合：

- 外部 orchestrator
- 測試框架
- 需要明確進程隔離的控制腳本

### 5.3 直接使用 ASGI app

```python
import uvicorn
from app.web.server import app

uvicorn.run(app, host="0.0.0.0", port=8000)
```

這種做法適合：

- 已經有既有 Python server stack
- 想自己控制 Uvicorn lifecycle
- 想加額外 middleware 或部署邏輯

---

## 6. 設定策略

### 建議優先順序

整合時建議採用這個順序：

1. 先用 `config/config.toml` 或環境變數定預設值
2. 再用 CLI flag 做部署環境覆蓋

原因：

- 預設設定集中管理
- 部署層可以局部覆蓋
- 比直接把所有位址寫死在腳本裡更容易維護

### 常見變數

```bash
export GONGIN_MODEL="qwen/qwen3-coder-next"
export GONGIN_BASE_URL="http://127.0.0.1:1234/v1"
export GONGIN_SQL_MODE="live"
```

---

## 7. PDF 與 Mermaid 腳本整合

### 7.1 直接使用公司 PDF 樣板

```python
from app.templates.company_pdf import build_company_report, ReportSection

build_company_report(
    output_path="outputs/report.pdf",
    company_name="公準精密",
    report_title="整合測試報告",
    sections=[
        ReportSection(
            title="摘要",
            body="這是整合測試輸出的 PDF 範例。",
        ),
        ReportSection(
            title="建議",
            bullets=[
                "確認輸出檔存在",
                "確認圖表與段落格式正確",
            ],
        ),
    ],
)
```

### 7.2 直接寫出 Mermaid 檔

```python
from pathlib import Path

diagram = \"\"\"flowchart LR
    A[需求] --> B[分析]
    B --> C[產出]
    C --> D[驗證]
\"\"\"

Path("outputs/system_flow.mmd").write_text(diagram, encoding="utf-8")
```

### 7.3 整合原則

- 一般圖表優先保留為 `.mmd`
- 若使用者沒有要求圖片格式，不要主動轉成 PNG/JPEG/SVG
- PDF 盡量走公司樣板，不建議另外手刻報表版面

---

## 8. Runtime 選擇建議

### 什麼時候用本機模式

- 一般研究
- 文件整理
- Mermaid
- PDF 報告
- 小型 Python 腳本

### 什麼時候用隔離模式

- 需要 Docker
- 有特殊系統依賴
- 要做較高風險驗證
- 有附件分析或複雜多步驟工程流程

### 實務建議

若只是腳本整合與文件產出，先用本機模式即可，不要一開始就把所有東西丟進容器。

---

## 9. 服務化部署範例

### systemd 範例概念

```ini
[Unit]
Description=GonginAI Web Service
After=network.target

[Service]
WorkingDirectory=/opt/gongin
ExecStart=/usr/local/bin/gongin --host 0.0.0.0 --port 8000
Restart=always
RestartSec=3

[Install]
WantedBy=multi-user.target
```

### 反向代理概念

常見做法：

- Gongin 綁定內部 port
- 外部由 Nginx / Caddy / Traefik 做反向代理
- TLS、存取控制、對外域名交給代理層處理

---

## 10. 常見整合錯誤

### `gongin: command not found`

通常表示：

- 啟動器不在 PATH
- shell 快取尚未刷新

### `ModuleNotFoundError`

通常表示：

- entrypoint 指向了錯誤的 top-level 模組
- 或安裝環境與執行環境不一致

### LM Studio 連不上

請先檢查：

- `GONGIN_BASE_URL`
- `--lmstudio-url`
- `--lmstudio-host`
- `--lmstudio-port`

### 產出檔存在但內容不正確

請檢查：

- 是否真的用到了公司 PDF builder
- 是否真的寫出了 `.mmd`
- 是否在結尾做了 `file_exists` / 檔案非空驗證

---

## 11. 實務建議

如果你的目標是穩定整合，建議採用以下原則：

- 人工使用：直接 `gongin`
- shell automation：用 CLI + 環境變數
- Python 平台整合：用 `app.web_launcher.main(...)`
- 已有 ASGI 架構：直接掛 `app.web.server:app`

這樣可以避免把公準AI 綁死在單一部署方式，也比較容易維護。

