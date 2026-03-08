<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：介紹公準AI 的 Web UI 結構、入口與畫面組成。 -->

# Web UI

## 主 UI

目前實際使用中的主 UI 位於：

- `UI/aisql/web_static/index.html`
- `UI/aisql/web_static/app.js`
- `UI/aisql/web_static/style.css`

## UI 功能

- 對話列表與會話切換
- 模型選擇
- 檔案/工作區瀏覽
- 工具執行紀錄
- thinking / terminal / browser stage 顯示
- 管理頁與登入頁

## 相關頁面

- 主頁：`index.html`
- 管理頁：`admin.html`
- 登入頁：`login.html`
- 預覽頁：`preview.html`
- 除錯頁：`debug.html`

## 前端責任

- 顯示對話狀態與工具執行過程
- 管理 session 與檔案開啟
- 顯示 Mermaid、PDF、terminal、browser 內容
- 讓使用者在同一介面完成研究與輸出任務

## 後端責任

- 路由與身份驗證
- session 執行與狀態更新
- 會話歷史與工具結果保存
- 模型與 runtime 管理

