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

AI 會讀取 `SKILL.md`（安裝入口），先問你想做什麼（例如「連接 Obsidian」「把網頁放上網」），提出建議的安裝方案，經你同意後**一次只裝一項**。你不需要先看懂編號；想自己挑時，選「我想自己挑」就會看到完整清單。只給網址時，AI 會從 `raw.githubusercontent.com` 讀檔，**讀檔不需要先安裝 Git**（安裝項目前會先請你裝 Git）。

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

> 只執行 `00-環境建置.md` 時，不會檢查 GitHub 帳號，也不會安裝 GitHub CLI；但會確認並安裝 Git（Git 是後續所有項目的前置條件，經你同意才裝）。

---

## 最低先備條件

- [ ] OpenAI 帳號（ChatGPT Plus / Pro / Business / Edu 訂閱，或 OpenAI API 額度）
- [ ] **Codex Desktop app** 已安裝且能登入（macOS / Windows）；或 IDE 擴充 / CLI 任一
- [ ] 電腦有網路連線

貼網址讀檔**不需要先裝 Git**；但開始安裝任何項目之前，Codex 會**先請你安裝 Git**（版本控制工具，後續幾乎都會用到）。其餘缺少的工具（Node.js、uv 等）也會先說明用途、經你同意才安裝。

---

## 懶人包清單

編號與技能、檔名一致（檔名前面的數字就是編號）。

| 編號 | 名稱 | 說明 |
|------|------|------|
| 00 | [環境建置](00-環境建置.md) | 確認並補裝 Git、Node.js LTS、uv；Codex CLI 選用；不處理 GitHub CLI 與登入 |
| 01 | [連接 NotebookLM](01-連接-NotebookLM.md) | NotebookLM MCP（Codex 版） |
| 02 | [初學者必裝外掛程式與技能](02-Codex必裝Skills與Plugins.md) | 基礎工具快篩、GitHub、Browser Use、Office 文件、生圖、官方文件與技能工具檢查 |
| 03 | [連接 GitHub](03-連接-GitHub.md) | GitHub CLI + 網頁端登入 + GitHub Pages 驗證 |
| 04 | [連接 GitHub 與 Obsidian 第二大腦](04-連接GitHub與Obsidian.md) | 整合版：GitHub CLI commit / push + Obsidian MCPVault（等於 03＋05） |
| 05 | [連接 Obsidian 第二大腦](05-建立第二大腦-Obsidian.md) | 先找 vault，再設定全域 AGENTS.md；跨專案讀寫可走資料夾授權或 MCPVault |
| 06 | [第二大腦設定指南](06-第二大腦設定指南.md) | 三層結構 + AGENTS.md + 模板（先完成 05） |
| 07 | [連接 Supabase 資料庫](07-連接-Supabase-資料庫.md) | Supabase MCP（Codex 版） |
| 08 | [連接 Firebase 資料庫](08-連接-Firebase-資料庫.md) | Firebase MCP（Codex 版） |
| 09 | [安裝本地 AI Ollama](09-安裝本地AI-Ollama.md) | 本地模型，網頁工具用 |
| 10 | [設定 Gemini 免費 API](10-設定Gemini免費API.md) | Gemini 免費 API，網頁工具用 |
| 11 | [開始你的專案](11-初始化研發工具工作模式.md) | AGENTS.md + Obsidian 駕駛艙 + GitHub repo + 開工/收工/新專案初始化 skills |
| 12 | [用 Image Gen Skill 在 Codex 生圖](12-用Image Gen Skill在Codex生圖.md) | 新手用內建 Image Gen Skill；進階再用 API Key / CLI |
| 13 | [用 chezmoi 同步 Codex 設定](13-用chezmoi同步Codex設定.md) | 跨電腦同步 `~/.codex/AGENTS.md` 與全域 skills |
| 14 | [串接 Vercel](14-串接-Vercel.md) | Vercel CLI + 官方 MCP（選用），一句話部署網頁、讀建置 log |
| 00A | 狀態盤點 | 只檢查哪些已完成、哪些還沒，並給建議；不安裝、不登入 |

### 不知道從哪開始？

- **只想先確認電腦準備好**：00
- **想讓 AI 幫你管理程式碼、備份到 GitHub**：00 → 03
- **想連接 Obsidian 筆記**：00 → 05（想要資料夾分層再加 06）
- **想把網頁放上網**：00 → 03 → 14
- **想知道自己電腦現在裝到哪**：說「做狀態盤點」（00A）

---

## Repo 結構

```
codex-starter-packs/
├── 00-環境建置.md … 14-串接-Vercel.md             ← 完整版懶人包（含說明、步驟、FAQ）
├── SKILL.md                                      ← 給 AI 讀的安裝入口（目標選單、通用規則、編號對照）
├── skills/<編號-名稱>/SKILL.md                    ← 每份懶人包的精簡版步驟（00-install-all 為狀態盤點）
└── workflow-skills/                               ← 編號 11 會安裝的三個技能：project-init-sync、startup-sync、shutdown-sync
```

- 想了解原理、自己看步驟：讀根目錄的完整版 MD 檔。
- 交給 AI 安裝：AI 會從 `SKILL.md` 進入，依序讀 `skills/` 裡的精簡版步驟。

---

## 不通用、需特別注意的章節

- **09 / 10**：跟 Codex / Claude 都無關，是「讓你做的網頁工具有 AI 能力」，兩邊通用。
- **11 / 13 收工同步**：Codex 可用全域 skill + `~/.codex/AGENTS.md` 觸發詞；跨電腦同步時用 chezmoi 管理安全項目。
- **12 生圖**：Codex Desktop 新手優先使用內建 Image Gen Skill；API Key / CLI 腳本只作為進階大量產圖與自動化路線。
- **06 第二大腦設定指南**：每週知識重整優先使用 Codex 自動化；CLI 排程只作為進階備援。

---

## 常見問題與復原

| 問題 | 解法 |
|------|------|
| 安裝到一半中斷了 | 重新跑同一份懶人包即可，每一步都會先檢查是否已完成 |
| 裝完技能或 MCP，Codex 卻說找不到 | 完全關閉 Codex 再重新開啟，並開**新的對話** |
| 想還原設定 | 改過 `~/.codex/config.toml` 之前都會先備份成 `config.toml.bak-<日期時間>`（同一個資料夾），把備份檔複製回 `config.toml` 即可 |
| 想移除某個技能 | 刪掉 `~/.codex/skills/` 底下對應的 `codex-…` 資料夾，再重開 Codex |
| 直接打 `vercel`、`firebase` 指令失敗（Windows） | 改打 `vercel.cmd`、`firebase.cmd`；公司或群組原則常擋未簽章的 `.ps1` |
| 讀 raw 檔案中文變亂碼（Windows PowerShell 5.1） | 改用 UTF-8 解碼重抓；不要根據亂碼的內容行動 |

---

## ⚠️ 使用提醒

- 個資與機敏資料不要放進公開的 GitHub repo 或免費雲端資料庫。
- API Key、Token 只存在本機，不要寫進 repo，也不要貼進對話。
- 每個 MCP 都會讓每個對話多載入一批工具、增加固定開銷，裝之前先確認真的需要。
- 免費方案的額度與規則可能變動，以各服務官網為準。

---
## 授權

MIT License。沿用上游授權，原版權聲明保留於 [LICENSE](LICENSE)。
