<!-- Yang Ethan 楊閔竣 · 2026 · 為公準精密建置 -->
<!-- 說明：整理 gongin 指令與旗標的使用方式。 -->

# CLI Reference

## 基本用法

```bash
gongin [options]
```

## 常用旗標

- `--host`
- `--port`
- `--test`
- `--live`
- `--lmstudio-url`
- `--lmstudio-host`
- `--lmstudio-port`

## 範例

### 預設啟動

```bash
gongin
```

### 指定 Web 綁定位址

```bash
gongin --host 0.0.0.0 --port 8000
```

### 指定 LM Studio 完整 URL

```bash
gongin --lmstudio-url http://127.0.0.1:1234/v1
```

### 只覆蓋 LM Studio host / port

```bash
gongin --lmstudio-host 192.168.1.50 --lmstudio-port 1235
```

### 切換 SQL 模式

```bash
gongin --test
```

或：

```bash
gongin --live
```

