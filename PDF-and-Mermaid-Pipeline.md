<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：整理 PDF 與 Mermaid 的產出流程與驗證重點。 -->

# PDF and Mermaid Pipeline

## PDF

公準AI 的正式 PDF 產出以公司樣板為核心：

- `app/templates/company_pdf.py`
- `build_company_report(...)`

### 原則

- 優先使用公司 PDF 樣板
- 不建議手刻簡化版 ReportLab 版面
- 輸出前應檢查檔案存在且非空

## Mermaid

Mermaid 圖表主要用於流程圖、架構圖、關聯圖說明。

### 原則

- 優先輸出 `.mmd`
- 只在明確需求時再轉為圖片格式
- 需避免顏色或可讀性問題

## 相關檔案

- `app/templates/company_pdf.py`
- `app/web/mermaid_validator.py`
- `UI/aisql/web_static/preview.js`

