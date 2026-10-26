---
name: codex-starter-packs
description: Codex 懶人包全集 — 環境建置、MCP 串接、技能安裝、設定同步。說「Codex 懶人包」「安裝 Codex 懶人包」時載入。
---

# Codex 懶人包 — AI Agent 自動安裝入口

當使用者給你這個 repo 網址並說要安裝時：

## 步驟一：列出可用懶人包

| 編號 | Skill 名稱 | 資料夾 | 說明 |
|------|-----------|--------|------|
| 00 | `codex-env-setup` | `skills/00-env-setup` | Codex Desktop、Node.js LTS、uv；CLI 選用，不處理 GitHub |
| 01 | `codex-notebooklm` | `skills/01-notebooklm` | 連接 NotebookLM MCP |
| 02 | `codex-essentials` | `skills/02-essentials` | 初學者必裝 Skills 與 Plugins |
| 03 | `codex-github` | `skills/03-github` | 連接 GitHub CLI |
| 04 | `codex-github-obsidian` | `skills/04-github-obsidian` | GitHub + Obsidian 整合 |
| 05 | `codex-obsidian` | `skills/05-obsidian` | 連接 Obsidian（資料夾授權 / MCPVault） |
| 06 | `codex-second-brain` | `skills/06-second-brain` | 第二大腦三層結構 |
| 07 | `codex-supabase` | `skills/07-supabase` | 連接 Supabase |
| 08 | `codex-firebase` | `skills/08-firebase` | 連接 Firebase |
| 09 | `codex-ollama` | `skills/09-ollama` | 本地 AI Ollama |
| 10 | `codex-gemini` | `skills/10-gemini` | Gemini 免費 API |
| 11 | `codex-workspace` | `skills/11-workspace` | 專案初始化工作模式 |
| 12 | `codex-draw` | `skills/12-draw` | 生圖指引（內建 + API） |
| 13 | `codex-chezmoi` | `skills/13-chezmoi` | 跨電腦同步 Codex 設定 |
| 14 | `codex-install-all` | `skills/00-install-all` | 一次安裝全部 |

## 步驟二：讓使用者選擇

問：「你要安裝哪些？輸入全部或編號組合（例如 00, 01, 03, 05）。」

將編號轉成上表的資料夾。若使用者只選 00，不得順便執行 GitHub 安裝或帳號檢查。

## 步驟三：依序安裝

讀取對應資料夾內的 `SKILL.md`，照裡面的步驟執行；需要完整說明時，改讀 repo 根目錄同編號的 `.md` 檔（例如 `00-環境建置.md`）。

- 已 clone 到本機：直接讀本機資料夾。
- 只拿到網址、沒有 clone：從 `https://raw.githubusercontent.com/tedchen0814/codex-starter-packs/main/` 加上檔案路徑讀取（例如 `.../main/skills/00-env-setup/SKILL.md`）。檔名含中文時，路徑要做 URL 編碼。

## 步驟四：回報

每項回報 ✅/⚠️/❌，最後列總表。
