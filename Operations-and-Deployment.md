<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：提供部署、啟動與維運層面的概要指引。 -->

# Operations and Deployment

## 本機啟動

```bash
gongin
```

## Docker 相關

系統包含隔離執行與容器相關元件：

- `Dockerfile`
- `docker/ubuntu-session.Dockerfile`
- `app/sandbox/`

## 維運重點

- 確保 LM Studio 或相容 API 可連線
- 確保工作區與輸出權限正常
- 避免把 session / logs / 本地設定提交到版本控制
- 使用 `.gitignore` 排除本地敏感內容

## 建議發布方式

- 私有主 repo：放完整系統程式碼
- 公開文件站：放經過清理的 wiki/doc 頁面

