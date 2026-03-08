<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：說明公準AI 的安裝前提與基礎安裝方式。 -->

# Installation

這一頁說明如何準備公準AI 的基本執行環境。

## 最低需求

- Python 環境
- 可用的模型後端，例如 LM Studio 或 OpenAI-compatible API
- 可寫入的工作區
- 可正常執行 `gongin` 的 shell 環境

## 建議安裝流程

1. 建立並啟用 Python 環境
2. 安裝專案相依套件
3. 設定模型 base URL
4. 執行 `gongin`

## 最小驗證

```bash
gongin --help
```

若這一步可正常顯示旗標，代表 CLI 入口已可用。

## 常見錯誤

- `gongin: command not found`
- `ModuleNotFoundError`
- 無法連上模型 API

這些錯誤的排查方式可再搭配 [Troubleshooting](Troubleshooting.md) 一起看。

