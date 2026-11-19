# OpenCode CLI 常用指令

本文件為 **OpenCode 專屬工作區** 指令指南。請在終端機先切換至本專屬目錄：

```powershell
Set-Location -LiteralPath 'C:\Users\User\Documents\多重代理\opencode'
```

---

## 一、終端機 CLI 指令（在 PowerShell 執行）

| 用途 | 指令 | 說明 |
| :--- | :--- | :--- |
| **啟動互動工作階段** | `opencode .` | 在目前資料開啟全螢幕 TUI |
| **版本與說明** | `opencode --version`<br>`opencode --help` | 檢查版本或取得完整參數說明 |
| **精簡介面** | `opencode mini` | 啟動精簡版互動介面 |
| **單次執行任務** | `opencode run "檢查 exception_handling.md 內容"` | 不開介面，直接輸出結果（適合腳本 / CI） |
| **接續工作階段** | `opencode --continue`<br>`opencode run --continue "..."` | 繼續最近一次的對話 |
| **查詢可用模型** | `opencode models` | 列出所有可用模型 |
| **管理工作階段** | `opencode session list`<br>`opencode session delete <id>`<br>`opencode session export <id>` | 列出、刪除、匯出對話紀錄 |
| **身分驗證** | `opencode auth list`<br>`opencode auth login` | 查看或登入服務供應商 |
| **MCP / 外掛** | `opencode mcp list`<br>`opencode plugin list` | 管理 MCP servers 與外掛 |
| **背景服務** | `opencode service status`<br>`opencode service restart` | 查看或重啟背景服務 |
| **用量統計** | `opencode stats --days 7 --models` | 查看模型使用量與成本 |
| **設定來源** | `opencode debug config` | 列出目前讀到了哪些設定檔 |
| **重新載入** | `opencode reload` | 改完設定不用重開 |
| **直接呼叫 API** | `opencode api GET /api/info` | 呼叫本地 OpenCode API |
| **升級** | `opencode upgrade` | 升級到最新版 |

`opencode run` 常用參數：`--model`、`--agent`、`--session`、`--format json`、`--file`、`--standalone`。任一指令加 `--help` 可看完整參數。

---

## 二、TUI 內的斜線指令（輸入 `/` 挑選）

| 指令 | 用途 |
| :--- | :--- |
| `/new` | 開新 session |
| `/sessions` | 切換既有 session |
| `/models`、`/agents` | 選模型或代理 |
| `/undo`、`/redo` | 撤回 / 重做上一輪 |
| `/editor` | 用外部編輯器編輯目前輸入 |
| `/btw <問題>` | 問一個不寫入對話的附帶問題 |
| `/reload` | 重新載入設定 |
| `/highlights` | 重看更新亮點 |

輸入技巧：

- `@` 附加檔案，例如 `Review @src/auth.ts#20-45`
- `!git status`：在空輸入列直接用 shell
- `Shift+Enter` / `Ctrl+Enter` / `Alt+Enter` / `Ctrl+J`：換行
- `Enter` 送出；執行中按 `Esc` 中斷

---

## 三、常用快捷鍵（預設 leader = `Ctrl+X`）

| 快捷鍵 | 功能 |
| :--- | :--- |
| `Ctrl+X` 然後 `N` / `L` | 新 session / 列出 session |
| `Ctrl+X` 然後 `M` / `A` | 選模型 / 選代理 |
| `Ctrl+X` 然後 `U` / `R` | undo / redo |
| `Ctrl+X` 然後 `C` | 壓縮 session |
| `Ctrl+X` 然後 `E` | 外部編輯器 |
| `Ctrl+X` 然後 `S` | 查看狀態 |
| `Ctrl+P` | 命令面板 |
| `Ctrl+O` | 最近 session 與專案 |
| `Ctrl+Tab` | 切換分頁 |
| `F2` | 切換最近用過的模型 |
| `Shift+Tab` | 切換代理 |
| `Ctrl+C` / `Ctrl+D` | 離開程式 |

快捷鍵可在 `C:\Users\User\.config\opencode\cli.json` 的 `keybinds` 修改；模型、代理、權限等放在 `opencode.jsonc`。

---

## 四、相關文件

- [README.md](./README.md)：OpenCode 工作區介紹
- [專案與專案等級.md](./專案與專案等級.md)：「專案」與「專案等級」完整說明（含設定範例）
- [exception_handling.md](./exception_handling.md)：Python 例外處理學習筆記
- [分支練習.ipnb](./分支練習.ipnb)：Git 分支切換與合併指令練習
- 官方文件：[CLI Commands](https://opencode.ai/docs/cli/commands/) · [TUI](https://opencode.ai/docs/cli/tui/) · [Config](https://opencode.ai/docs/config/)
