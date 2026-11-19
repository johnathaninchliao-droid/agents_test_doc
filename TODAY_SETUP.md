# Herdr、Antigravity 與 OpenCode 設定紀錄

這份紀錄整理 2026-11-18 在目前 Windows 電腦確認過的安裝狀態，以及在另一台 Windows 電腦重建環境的步驟。版本和安裝路徑只代表今天這台電腦；回家安裝時請以官方網站提供的最新版為準。

## 今天這台電腦已確認的狀態

| 工具 | 目前版本／狀態 | 目前位置或命令 |
| --- | --- | --- |
| Herdr 桌面程式 | `0.1.16`；Herdr 與 herdr-core 程序正在執行 | `%LOCALAPPDATA%\Programs\herdr-app\herdr-app.exe` |
| Herdr Core | 已安裝並正在執行；檔案版本未由本機中繼資料提供 | `%LOCALAPPDATA%\Programs\herdr-core\herdr-core.exe` |
| Antigravity CLI | `agy 1.5.10` | `%LOCALAPPDATA%\agy\bin\agy.exe`；終端機命令為 `agy` |
| OpenCode CLI | `opencode v2.3.2` | `%LOCALAPPDATA%\Programs\opencode\opencode.exe`；終端機命令為 `opencode` |

Herdr 是桌面應用程式，沒有名為 `herdr` 的終端機命令。Herdr 可以在終端機面板中執行 coding agent；今天已在 VS Code 專案設定 OpenCode 和 Antigravity 兩個啟動工作。

## 在另一台 Windows 電腦建立環境

### 1. 安裝 Herdr

官方首頁：[herdr.dev](https://herdr.dev/)

官方 Windows 安裝指引提供 PowerShell 安裝程式：

```powershell
irm https://releases.herdr.dev/app/install.ps1 | iex
```

安裝程式會安裝 Herdr；若 herdr-core 尚未安裝，也會一併安裝。它會將 `%LOCALAPPDATA%\Programs\herdr-app` 加入使用者 PATH。安裝程式會下載並執行程式碼；若要先檢視內容，請參閱 [官方 PowerShell installer](https://github.com/herdrdev/herdr-app/blob/master/distribution/install.ps1)。安裝完成後開啟 Herdr，並重新開啟終端機以載入更新後的 PATH。

### 2. 安裝 Antigravity 與 CLI

從 [Antigravity 官方下載頁](https://antigravity.google/download)安裝應用程式並完成登入。今天這台電腦的 CLI 可在 PowerShell 用以下指令驗證：

```powershell
agy --version
agy --help
```

若已安裝 CLI，但需要設定環境路徑或 Shell 設定，可使用：

```powershell
agy install
```

注意：`agy install` 是 CLI 的環境設定子命令，不是下載或安裝 Antigravity 的安裝程式。今天此命令提供的用途為設定 PATH 和 Shell。

### 3. 安裝 OpenCode CLI

使用 [OpenCode 官方文件](https://opencode.ai/docs/)中的 Windows standalone CLI 下載連結，依電腦架構選 x64 或 ARM64。官方文件目前指出 Windows package manager 不受支援；請以官方文件提供的 standalone binary 為準，不要直接照搬此電腦的安裝路徑。

安裝後開啟新的 PowerShell 視窗，確認命令可用：

```powershell
opencode --version
opencode --help
```

### 4. 在 Herdr 啟動兩個代理（一對一專屬 Space 設定）

為了避免兩個代理同時修改相同檔案產生衝突，專案已劃分一對一獨立工作區：

1. **Antigravity 專屬 Space (`多重代理(antigravity)`)**：
   - 設定工作目錄為：`C:\Users\User\Documents\多重代理\antigravity`
   - 在終端機執行 `agy`。
2. **OpenCode 專屬 Space (`多重代理(opencode)`)**：
   - 設定工作目錄為：`C:\Users\User\Documents\多重代理\opencode`
   - 在終端機執行 `opencode .`。
3. 如此兩邊的檔案、終端機與操作進度即完全一對一分開，互不干擾。

這些命令要求對應 CLI 已安裝並在 PATH 中。若終端機顯示「找不到命令」，先確認安裝完成，再開啟新的終端機；也可用 `Get-Command agy` 和 `Get-Command opencode` 檢查。

## GitHub 認證

GitHub 登入不需要把 token 寫進專案或此文件。在另一台已安裝 Git for Windows 的電腦，可在互動式 PowerShell 使用 Git Credential Manager 的瀏覽器登入：

```powershell
git credential-manager github login
```

登入後，進入專案資料夾，以 `git remote -v` 確認遠端 repository，再使用 `git push` 上傳。確認 remote 是預期的 GitHub repository，避免推送至錯誤位置。

## VS Code 啟動工作注意事項

本專案的 `.vscode/tasks.json` 目前使用今天這台電腦的絕對執行檔路徑。搬到另一台電腦時，這些路徑不一定存在。若新電腦已將 CLI 加入 PATH，請把任務命令改成 `opencode` 和 `agy`；或先在新電腦確認實際執行檔位置，再更新路徑。

## 回家後快速驗證清單

在新的 PowerShell 視窗確認命令位置與版本：

```powershell
Get-Command herdr-app, agy, opencode
agy --version
opencode --version
git --version
git credential-manager --version
```

Herdr 主要從 Windows 開始功能表或 `herdr-app` 執行檔啟動，不要假設它支援 `--help` 參數。若 `agy` 或 `opencode` 找不到，請先確認相應 CLI 是否安裝並已加入 PATH，再重新開啟終端機。

## 官方參考

- [Herdr 安裝與使用說明](https://github.com/herdrdev/herdr-app)
- [Antigravity 官方下載頁](https://antigravity.google/download)
- [Antigravity 官方入門文件](https://antigravity.google/docs/getting-started)
- [OpenCode 官方文件與 Windows CLI 下載](https://opencode.ai/docs/)
