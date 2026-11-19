# Antigravity CLI (agy) 常用指令

本文件為 **Antigravity 專屬工作區** 指令指南。請在終端機先切換至本專屬目錄：

```powershell
Set-Location -LiteralPath 'C:\Users\User\Documents\多重代理\antigravity'
```

---

## 常用指令列表

| 用途 | 指令 | 說明 |
| :--- | :--- | :--- |
| **啟動互動工作階段** | `agy` | 在當前目錄開啟 Antigravity 互動終端介面 |
| **版本與說明** | `agy --version`<br>`agy --help` | 檢查 CLI 版本或取得完整參數說明 |
| **查詢代理與模型** | `agy agent`<br>`agy models` | 列出目前支援的代理類型與模型清單 |
| **帶 Prompt 啟動** | `agy --prompt-interactive "檢查此目錄的練習檔案"` | 帶初始問題開啟對話工作階段 |
| **單次執行並印出** | `agy --print "說明 exception_handling.md 核心概念"` | 執行一次指令後結束，直接輸出於終端機 |
| **接續最近的工作階段** | `agy --continue` | 繼續上一次的交談紀錄 |
| **指定模型與代理** | `agy --model "<模型名稱>" --agent "<代理名稱>"` | 使用特定配置執行 |

---

## 工作區檔案索引

- [README.md](file:///C:/Users/User/Documents/多重代理/antigravity/README.md)：Antigravity 工作區介紹
- [exception_handling.md](file:///C:/Users/User/Documents/多重代理/antigravity/exception_handling.md)：Python 例外處理學習筆記
- [分支練習.ipnb](file:///C:/Users/User/Documents/多重代理/antigravity/分支練習.ipnb)：Git 分支切換與合併指令練習
