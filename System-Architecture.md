<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：概述公準AI 的整體系統架構與主要元件。 -->

# System Architecture

## 架構概觀

公準AI 由四個主要層次構成：

- Web UI：使用者介面、會話與檔案互動
- Agent / Prompt 層：代理邏輯、規劃、提示詞
- Tool 層：搜尋、檔案、Python、終端、Mermaid、PDF 等能力
- Runtime / Sandbox 層：本機執行與隔離執行環境

## 主要目錄

- `app/web/`：Web server、routes、展示邏輯
- `app/agent/`：代理類別與行為
- `app/prompt/`：提示詞模板
- `app/tool/`：可呼叫工具
- `app/sandbox/`：隔離執行與 terminal/sandbox 管理
- `app/templates/`：公司 PDF 樣板與報表輸出
- `UI/aisql/web_static/`：實際使用中的前端介面

## 主要執行流程

1. 使用者從 Web UI 發送請求
2. Server 建立或續用 session
3. Agent 根據任務選擇工具或執行模式
4. Tool 實際操作搜尋、檔案、Python 或隔離環境
5. 驗證輸出內容與檔案
6. 回傳結果到前端

## 關鍵檔案

- `app/web/server.py`
- `app/web_launcher.py`
- `app/agent/gongin.py`
- `app/tool/tool_collection.py`
- `app/templates/company_pdf.py`

