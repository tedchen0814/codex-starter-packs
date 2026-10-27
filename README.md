# Codex 懶人包（OpenAI Codex 版）

> 給 OpenAI Codex 使用的安裝懶人包（研發／個人學習版）。
> 把每份 MD 檔丟給 Codex，它會自動執行。
>
> ✅ **適用三種 Codex**：**Codex Desktop app（macOS/Windows）**、**Codex IDE 擴充（VSCode / Cursor / JetBrains）**、**Codex CLI**。三者**共用同一份** `~/.codex/config.toml` 與 `AGENTS.md`，所以設定做一次就好。

---

## 我用的是哪一種？

| 你的工具 | 怎麼裝 / 怎麼開 |
|---|---|
| **Codex Desktop app** | 從 [OpenAI 官網](https://developers.openai.com/codex/app)下載 macOS / Windows 安裝檔（**本懶人包預設場景**） |
| Codex IDE 擴充 | VSCode / Cursor / Windsurf → Marketplace 搜尋「ChatGPT」（OpenAI 官方）；JetBrains 系列也有對應 |
| Codex CLI | `npm install -g @openai/codex` |

**MCP 與 AGENTS.md 設定的三條路（任選）**：
1. **Desktop**：`設定 → Integrations & MCP` 介面新增 server；`設定 → Personalization` 編輯 AGENTS.md
2. **IDE**：齒輪 → MCP settings → Open config.toml
3. **CLI**：`codex mcp add <name> -- <command>`

> 設定動了一邊，三邊都會吃到。本懶人包以 **Desktop app GUI** 為主寫，每個 MCP 章節都附「手動編輯 `~/.codex/config.toml`」的 TOML 範例供 IDE / CLI 用戶或 Desktop 進階使用者參考。

---

## 為什麼有這份？

同一套工作流程另有 Claude Code 版。這份是**改寫成 Codex 看得懂的版本**，兩者主要差異如下：

| 差異 | Claude Code | OpenAI Codex |
|---|---|---|
| 全域指令檔 | `~/.claude/CLAUDE.md` | `~/.codex/AGENTS.md` |
| 專案指令檔 | `./CLAUDE.md` | `./AGENTS.md` |
| 設定檔 | `~/.claude/settings.json`（JSON） | `~/.codex/config.toml`（TOML） |
| MCP 安裝指令 | `claude mcp add ...` | `codex mcp add ...` |
| Skill 機制 | 原生支援 | ✅ Codex Desktop 支援 skills；CLI / 舊環境可用 prompt 模板或 shell 腳本備援 |
| Slash command | 原生支援 | ❌ 沒有 |
| 排程任務 | `mcp__scheduled-tasks__*` | ❌ 沒有，用系統 cron / Task Scheduler |

---

## 使用方式

### 方式一：直接叫 AI 幫你裝（最簡單）

把這行貼給你的 AI agent：

```
這是 Codex 懶人包全集 https://github.com/tedchen0814/codex-starter-packs
請讀取 repo 內容的 SKILL.md，依它的流程帶我安裝：先問我想做什麼，每次只做一項，做之前先跟我說明。
```

AI 會讀取 `SKILL.md`（安裝入口），先問你想做什麼（例如「連接 Obsidian」「把網頁放上網」），提出建議的安裝方案，經你同意後**一次只裝一項**。你不需要先看懂編號；想自己挑時，選「我想自己挑」就會看到完整清單。只給網址時，AI 會從 `raw.githubusercontent.com` 讀檔，**不需要先安裝 Git**。

> 不建議一次全部安裝：多項會要求登入或修改設定。想先知道目前裝了哪些，請 AI 做「狀態盤點（00A）」，它只檢查、不改任何東西。

### 方式二：clone 到本機

```powershell
git clone https://github.com/tedchen0814/codex-starter-packs
```

再請 Codex 讀取資料夾裡的 `SKILL.md` 並依步驟安裝。

### 方式三：只裝單一份

1. 下載對應的懶人包（MD 檔）
2. 打開 Codex，把檔案內容貼進去
3. AI 自動執行，遇到需要手動操作的地方會暫停指示你

> 只執行 `00-環境建置.md` 時，不會檢查 GitHub 帳號，也不會安裝 Git 或 GitHub CLI。

---

## 最低先備條件

- [ ] OpenAI 帳號（ChatGPT Plus / Pro / Business / Edu 訂閱，或 OpenAI API 額度）
- [ ] **Codex Desktop app** 已安裝且能登入（macOS / Windows）；或 IDE 擴充 / CLI 任一
- [ ] 電腦有網路連線

---

## 懶人包清單

| 編號 | 名稱 | 說明 |
|------|------|------|
| 00 | [環境建置](00-環境建置.md) | Codex Desktop、Node.js LTS、uv；Codex CLI 選用，不處理 GitHub |
| 01 | [連接 NotebookLM](01-連接-NotebookLM.md) | NotebookLM MCP（Codex 版） |
| 01.5 | [初學者必裝外掛程式與技能](01.5-Codex必裝Skills與Plugins.md) | 基礎工具快篩、GitHub、Browser Use、Office 文件、生圖、官方文件與技能工具檢查 |
| 02 | [連接 GitHub](02-連接-GitHub.md) | GitHub CLI + 網頁端登入 + GitHub Pages 驗證 |
| 02.5 | [連接 GitHub 與 Obsidian 第二大腦](02.5-連接GitHub與Obsidian.md) | 整合版：GitHub CLI commit / push + Obsidian MCPVault |
| 03 | [連接 Obsidian 第二大腦](03-建立第二大腦-Obsidian.md) | 先找 vault，再設定全域 AGENTS.md；跨專案讀寫可走資料夾授權或 MCPVault |
| 03+ | [第二大腦設定指南](04-第二大腦設定指南.md) | 三層結構 + AGENTS.md + 模板 |
| 04 | [連接 Supabase 資料庫](04-連接-Supabase-資料庫.md) | Supabase MCP（Codex 版） |
| 04.5 | [連接 Firebase 資料庫](04.5-連接-Firebase-資料庫.md) | Firebase MCP（Codex 版） |
| 05 | [安裝本地 AI Ollama](05-安裝本地AI-Ollama.md) | 本地模型，網頁工具用 |
| 06 | [設定 Gemini 免費 API](06-設定Gemini免費API.md) | Gemini 免費 API，網頁工具用 |
| 07 | [開始你的專案](07-初始化研發工具工作模式.md) | AGENTS.md + Obsidian 駕駛艙 + GitHub repo + 開工/收工/新專案初始化 skills |
| 08 | [用 Image Gen Skill 在 Codex 生圖](08-用Image Gen Skill在Codex生圖.md) | 新手用內建 Image Gen Skill；進階再用 API Key / CLI |
| 09 | [用 chezmoi 同步 Codex 設定](09-用chezmoi同步Codex設定.md) | 跨電腦同步 `~/.codex/AGENTS.md` 與全域 skills |
| 10 | [串接 Vercel](10-串接-Vercel.md) | Vercel CLI + 官方 MCP，一句話部署網頁、讀建置 log |

---

## 不通用、需特別注意的章節

- **05 / 06**：跟 Codex / Claude 都無關，是「讓你做的網頁工具有 AI 能力」，兩邊通用。
- **07 / 09 收工同步**：Codex 可用全域 skill + `~/.codex/AGENTS.md` 觸發詞；跨電腦同步時用 chezmoi 管理安全項目。
- **08 生圖**：Codex Desktop 新手優先使用內建 Image Gen Skill；API Key / CLI 腳本只作為進階大量產圖與自動化路線。
- **04 第二大腦設定指南**：每週知識重整優先使用 Codex 自動化；CLI 排程只作為進階備援。

---

## 授權

MIT License。沿用上游授權，原版權聲明保留於 [LICENSE](LICENSE)。
