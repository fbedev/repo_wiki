<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：整理正式部署前應注意的硬化與維運原則。 -->

# Production Hardening

## 基本原則

- 不要把 session、workspace、logs、tmp 提交到公開 repo
- 不要把真實 API 金鑰寫進公開文件
- 不要把真實內網位址寫進公開操作手冊

## 部署建議

- Gongin 綁內部 port
- 對外由 Nginx / Caddy / Traefik 代理
- TLS 與存取控制交給代理層

## 建議檢查

- 模型 API 可連線
- 工作區可寫入
- 輸出目錄權限正常
- 例外情況有基本日誌與排查路徑

