<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：說明本機模式、隔離模式與任務路由原則。 -->

# Runtime Modes

## 執行模式

公準AI 目前有兩個主要執行路徑：

- `host-tools`
  - 使用本機或共享 Python 環境
  - 適合研究、檔案生成、Mermaid、PDF、一般腳本任務

- `isolated`
  - 使用 Docker/隔離環境
  - 適合依賴較重、容器需求、系統驗證、附件分析或高風險任務

## 路由原則

- 一般研究與文件產出優先走本機模式
- 複雜工程或需要隔離時才切換到容器
- 有附件、需要特殊依賴、需要系統級驗證時會偏向隔離模式

## 路徑觀念

- 本機模式使用工作區實際路徑
- 隔離模式必須使用容器內路徑，例如 `/workspace`

## 相關檔案

- `app/web/server.py`
- `app/sandbox/session_runtime.py`
- `app/tool/bash.py`
- `app/session_policy.py`

