<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：整理常見錯誤與排查方向。 -->

# Troubleshooting

## `gongin: command not found`

- 檢查啟動器是否已安裝到可執行路徑
- 檢查 shell 是否已刷新快取

## `ModuleNotFoundError`

- 通常是 console entrypoint 指向了錯誤的 top-level 模組
- 目前應以 `app.cli` / `app.web_launcher` 作為入口

## LM Studio 無法連線

- 檢查 `GONGIN_BASE_URL`
- 或使用：
  - `--lmstudio-url`
  - `--lmstudio-host`
  - `--lmstudio-port`

## Mermaid 不可讀

- 檢查 theme 與文字顏色
- 檢查是否被自定義 classDef 覆蓋

## PDF 樣板不正確

- 確認有使用 `build_company_report`
- 確認輸出不是 generic fallback PDF

