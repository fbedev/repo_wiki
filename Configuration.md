<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：整理公準AI 的設定檔、環境變數與啟動旗標。 -->

# Configuration

## 主要設定檔

- `config/config.example.toml`
- `config/config.example-model-anthropic.toml`
- `config/config.example-model-azure.toml`
- `config/config.example-model-google.toml`
- `config/config.example-model-ollama.toml`

本地實際設定通常使用 `config/config.toml`，不建議公開。

## 重要環境變數

- `GONGIN_MODEL`
- `GONGIN_BASE_URL`
- `LMSTUDIO_URL`
- `GONGIN_SQL_MODE`

## 啟動旗標

`gongin` 支援：

- `--host`
- `--port`
- `--test`
- `--live`
- `--lmstudio-url`
- `--lmstudio-host`
- `--lmstudio-port`

## 預設啟動

```bash
gongin
```

預設會啟動 Web UI，並綁定：

- `0.0.0.0:8000`

