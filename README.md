# 多重代理專案 (Multi-Agent Project)

這是一個用於測試 Antigravity 與 OpenCode 協作及 GitHub 上傳的專案。
專案已完成「代理專屬工作區（一對一分開）」架構，讓 Antigravity 與 OpenCode 各自擁有獨立工作目錄與檔案，避免多代理操作互相衝突。

---

## 專案目錄結構 (一對一劃分)

```
多重代理/
├── README.md                              # 專案總架構說明
├── TODAY_SETUP.md                         # 環境安裝與 Herdr 設定總指南
├── 對話紀錄_例外處理與Git教學.md            # 例外處理與 Git 學習紀錄
├── .vscode/                               # VS Code 工作區設定
│   └── tasks.json                         # 啟動任務配置 (含各代理獨立路徑)
│
├── antigravity/                           # 【Antigravity 專屬空間】
│   ├── README.md                          # Antigravity 空間說明
│   ├── AGENT_COMMANDS.md                  # agy 專用指令手冊
│   ├── exception_handling.md              # 例外處理學習筆記 (專屬副本)
│   └── 分支練習.ipnb                       # Git 分支練習 (專屬副本)
│
└── opencode/                              # 【OpenCode 專屬空間】
    ├── README.md                          # OpenCode 空間說明
    ├── AGENT_COMMANDS.md                  # opencode 專用指令手冊
    ├── 專案與專案等級.md                    # 專案／專案等級說明與設定範例
    ├── exception_handling.md              # 例外處理學習筆記 (專屬副本)
    └── 分支練習.ipnb                       # Git 分支練習 (專屬副本)
```

---

## 一對一對應關係表

| 代理名稱 | 命令列工具 | 專屬資料夾路徑 | Herdr Space 對應 | 專屬指令說明 |
| :--- | :--- | :--- | :--- | :--- |
| **Antigravity** | `agy` | `./antigravity` | `多重代理(antigravity)` | [antigravity/AGENT_COMMANDS.md](./antigravity/AGENT_COMMANDS.md) |
| **OpenCode** | `opencode` | `./opencode` | `多重代理(opencode)` | [opencode/AGENT_COMMANDS.md](./opencode/AGENT_COMMANDS.md) |

---

## 參考連結

- GitHub Repository: [johnathaninchliao-droid/agents_test_doc](https://github.com/johnathaninchliao-droid/agents_test_doc)
- [Herdr、Antigravity 與 OpenCode 安裝指南](./TODAY_SETUP.md)
- [對話紀錄：例外處理與 Git 操作指南](./對話紀錄_例外處理與Git教學.md)
- [OpenCode：專案與專案等級說明](./opencode/專案與專案等級.md)
