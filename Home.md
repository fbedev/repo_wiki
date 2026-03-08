<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：Wiki 首頁，概覽公準AI 系統與文件入口。 -->

# 公準AI Wiki

公準AI 是為公準精密建置的本地代理系統，主要用途是把研究、檔案處理、程式生成、PDF 報告、Mermaid 圖表、Web UI 工作流整合成同一套操作平台。

## 核心能力

- Web UI 操作與會話管理
- LM Studio 模型整合
- 本機模式與隔離模式執行
- 檔案建立、編輯、驗證
- PDF 報告與 Mermaid 圖表產出
- 搜尋、研究、資料整理

## 主要入口

- Web 啟動：`gongin`
- 預設 Web 位址：`0.0.0.0:8000`
- 主伺服器：`app/web/server.py`
- 啟動器：`app/web_launcher.py`

## 閱讀順序

1. [System Architecture](System-Architecture)
2. [Web UI](Web-UI)
3. [Installation](Installation)
4. [CLI Reference](CLI-Reference)
5. [Python Embedding](Python-Embedding)
6. [ASGI and Uvicorn](ASGI-and-Uvicorn)
7. [Runtime Modes](Runtime-Modes)
8. [Configuration](Configuration)
9. [Script Integration](Script-Integration)
10. [Production Hardening](Production-Hardening)
11. [Tools and Agents](Tools-and-Agents)
12. [PDF and Mermaid Pipeline](PDF-and-Mermaid-Pipeline)
13. [Operations and Deployment](Operations-and-Deployment)
14. [Troubleshooting](Troubleshooting)

## 安全原則

- 不在公開文件放入實際密鑰、真實帳密、內網敏感位址、真實使用者 session 路徑
- 不記錄工作區內部 session 檔或歷史封存內容
- 只保留系統結構、操作方式與公開級別說明

## 整合導讀

如果你的重點是「如何從腳本或程式整合」，請優先閱讀：

- [Installation](Installation)
- [CLI Reference](CLI-Reference)
- [Python Embedding](Python-Embedding)
- [ASGI and Uvicorn](ASGI-and-Uvicorn)
- [Script Integration](Script-Integration)
- [Configuration](Configuration)
- [Runtime Modes](Runtime-Modes)
