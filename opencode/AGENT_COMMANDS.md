# OpenCode CLI 常用指令

本文件為 **OpenCode 專屬工作區** 指令指南。請在終端機先切換至本專屬目錄：

```powershell
Set-Location -LiteralPath 'C:\Users\User\Documents\多重代理\opencode'
```

---

## 常用指令列表

| 用途 | 指令 | 說明 |
| :--- | :--- | :--- |
| **啟動互動工作階段** | `opencode .` | 在當前目錄開啟 OpenCode 互動終端介面 |
| **版本與說明** | `opencode --version`<br>`opencode --help` | 檢查 CLI 版本或取得完整參數說明 |
| **查詢可用模型** | `opencode models` | 列出 OpenCode 支援的所有模型清單 |
| **單次執行任務** | `opencode run "檢查 exception_handling.md 內容"` | 執行一次性任務指令並輸出結果 |
| **接續最近的工作階段** | `opencode --continue` | 繼續上一次的對話工作階段 |
| **身分驗證與服務整合** | `opencode auth list`<br>`opencode auth login` | 查看或進行服務身分登入 |

---

## 工作區檔案索引

- [README.md](file:///C:/Users/User/Documents/多重代理/opencode/README.md)：OpenCode 工作區介紹
- [exception_handling.md](file:///C:/Users/User/Documents/多重代理/opencode/exception_handling.md)：Python 例外處理學習筆記
- [分支練習.ipnb](file:///C:/Users/User/Documents/多重代理/opencode/分支練習.ipnb)：Git 分支切換與合併指令練習
