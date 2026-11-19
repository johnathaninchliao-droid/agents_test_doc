# Antigravity 與 OpenCode 常用指令

以下指令適用於 Windows PowerShell。專案已依代理區分專屬目錄，請在終端機切換至對應工作區：

```powershell
# 切換至 Antigravity 專屬目錄
Set-Location -LiteralPath 'C:\Users\User\Documents\多重代理\antigravity'

# 或切換至 OpenCode 專屬目錄
Set-Location -LiteralPath 'C:\Users\User\Documents\多重代理\opencode'
```

## Antigravity CLI

這台電腦的命令名稱是 `agy`，不是 `antigravity`。

| 用途 | 指令 |
| --- | --- |
| 開啟互動式工作階段 | `agy` |
| 查看說明或版本 | `agy --help`、`agy --version` |
| 列出可用代理或模型 | `agy agent`、`agy models` |
| 以提示啟動互動式工作階段 | `agy --prompt-interactive "檢查這個專案並說明如何執行測試"` |
| 單次提示並輸出結果 | `agy --print "檢查這次變更是否有明顯問題"` |
| 繼續最近的工作階段 | `agy --continue` |
| 使用特定模型或代理 | `agy --model "<模型名稱>" --agent "<代理名稱>"` |

`--model` 與 `--agent` 的值請依 `agy models` 和 `agy agent` 顯示的名稱填入。

## OpenCode

| 用途 | 指令 |
| --- | --- |
| 在目前資料夾開啟互動介面 | `opencode .` |
| 查看說明或版本 | `opencode --help`、`opencode --version` |
| 列出可用模型 | `opencode models` |
| 單次提示並輸出結果 | `opencode run "檢查這個專案並說明如何執行測試"` |
| 繼續最近的工作階段 | `opencode --continue` |
| 查看或登入整合服務 | `opencode auth list`、`opencode auth login` |

完整的 CLI、TUI 快捷鍵與「專案等級」設定說明，請見 [opencode/AGENT_COMMANDS.md](./opencode/AGENT_COMMANDS.md) 與 [opencode/專案與專案等級.md](./opencode/專案與專案等級.md)。

## 從 VS Code 啟動兩個代理

在 VS Code 選擇 **Terminal → Run Task**，再執行 **雙代理（OpenCode + Antigravity）**。兩個代理會在各自的終端機中啟動。

## 將專案推送到 GitHub

此專案已設定 `origin` 指向 `agents_test_doc`。一般更新可以依序執行：

```powershell
git status
git add <要上傳的檔案>
git diff --cached
git commit -m "描述這次變更"
git push
```

確認 `git diff --cached` 只包含預期檔案後再提交。首次使用這台電腦的 GitHub 認證時，在互動式終端機登入：

```powershell
git credential-manager github login
```

如果推送被拒絕，先確認登入的 GitHub 帳號對 repository 有寫入權限。不要把 access token、密碼或其他憑證寫進程式碼、命令列歷史或提交內容；也不要用 `git push --force` 覆蓋遠端變更。
