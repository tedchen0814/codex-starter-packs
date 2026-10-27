---
name: codex-starter-packs
description: Codex 懶人包全集 — 環境建置、MCP 串接、技能安裝、設定同步。說「Codex 懶人包」「安裝 Codex 懶人包」時載入。
---

# Codex 懶人包 — AI Agent 自動安裝入口

當使用者給你這個 repo 網址並說要安裝時，照下面流程。**假設使用者完全不懂技術**：不要要求他看編號，不要用 MCP、`config.toml`、CLI 這類詞而不解釋；每次只做一件事，做之前先說明、等他同意。

## 通用規則（全程適用）

1. 使用者回覆之前，**不安裝、不登入、不修改任何東西**。
2. 一次只裝一項；裝完用白話回報「做了什麼、怎麼確認成功」，再問是否繼續下一項。**不要連續安裝**。
3. 要改 `~/.codex/config.toml`（Codex 的設定檔）之前，先說明要加什麼，並備份成 `config.toml.bak-<日期時間>`，再改。
4. 需要登入帳號、輸入密碼或 API key 時，**請使用者自己在瀏覽器或自己的終端機完成**；不要把 token、key 貼進對話，也不要寫進 repo。
5. 會在網路上建立東西（GitHub repo、Vercel 部署）或需要下載大檔案時，先說明並等同意；repo 預設建立為**私有**。
6. 缺少前置條件（例如沒有 Git、Node.js）時，說明缺什麼、為什麼需要，經同意才安裝，不要直接跳過或自己猜。
7. 不確定的事先問，不要猜。
8. **使用者看不到這份檔案，也看不到你的內部步驟。** 凡是標示「原文貼給使用者」的選單、清單、提示，都要完整輸出在對話裡；不要用「請看上方」「依流程進行」帶過。
9. **Git 是前置條件。** 進入任何項目（00A 盤點除外）之前，先檢查 `git --version`。沒有就先停下來說明：「Git 是版本控制工具，後續幾乎所有項目都會用到，需要先裝好」，經使用者同意用 winget 安裝（Windows：`winget install --id Git.Git -e`；macOS：`brew install git`；安裝過程可能跳出系統管理員確認，要使用者自己按），裝完請使用者**開新的終端機**再檢查。使用者不同意就停在這裡，不繼續其他項目。

## 步驟一：問目標，不問編號

**你的第一則回覆必須把下面這段選單「原文貼給使用者」，一個字都不要改、不要摘要、不要只說「請選 1～5」或「等你選擇」。** 使用者看不到這份檔案，他唯一能看到的就是你貼出來的選單。貼完選單就停下來，等使用者回覆數字。

```
你想用 Codex 做什麼？（回覆數字就好）

1. 剛開始用，先確認電腦準備好
2. 想讓 AI 幫我管理程式碼，並備份到 GitHub
3. 想連接我的 Obsidian 筆記
4. 想把做好的網頁放到網路上（有網址可分享）
5. 我想自己挑（顯示完整清單）

回覆前我不會安裝或修改任何東西。
```

收到使用者的回答後，依回答提出「建議安裝方案」，**先告訴使用者會依序安裝哪幾項、各做什麼，等他說「好」才開始**：

| 目標 | 建議方案（依序） |
|---|---|
| 1. 先確認電腦準備好 | 00 |
| 2. 程式碼與備份 | 00 → 03 |
| 3. Obsidian 筆記 | 00 → 05（想要資料夾分層再加 06） |
| 4. 網頁上線 | 00 → 03 → 14 |
| 5. 自己挑 | 顯示下方完整清單，讓使用者選編號 |

使用者說「全部」「都裝」「全包」：**不要照做**。回：「一次全裝會要求你登入很多服務、修改很多設定，我建議先做狀態盤點（只檢查、不改任何東西），再挑你需要的。」然後執行 `skills/00-install-all`（00A）。

## 步驟二：完整清單（方案 5 時顯示；其他方案可按需查閱）

呈現時**直接把下面第一張表貼給使用者**，每一列都要出現，欄位（項目、白話說明、會改動什麼、需要登入？）也都要保留；其後的「編號對照」是給你轉換資料夾用的，不要貼給使用者；不要只說「共 16 項」、不要改寫成摘要、不要只列編號與名稱。使用者看不到這份檔案。

| 編號 | 項目 | 白話說明 | 會改動什麼 | 需要登入？ |
|---|---|---|---|---|
| 00 | 環境準備 | 確認電腦有 Codex、Git、Node.js、uv，缺的才補（Git 是後續所有項目的前置） | 缺工具時安裝軟體 | 不用 |
| 01 | NotebookLM | 讓 Codex 能查你的 NotebookLM 筆記本 | 安裝 1 個工具、改設定檔 | 要（Google） |
| 02 | 新手工具包 | 檢查並建議新手必備的技能與外掛 | 可能安裝套件 | 不用 |
| 03 | GitHub 備份 | 讓 Codex 能把程式碼備份到 GitHub | 設定 Git 姓名與信箱；測試會建立測試 repo（要你同意） | 要（GitHub） |
| 04 | GitHub＋Obsidian | 把 Obsidian 筆記與程式碼備份串起來（等於 03＋05） | 同 03、05 | 要（GitHub） |
| 05 | Obsidian 筆記 | 讓 Codex 讀寫你的 Obsidian 筆記 | 授權資料夾，或安裝工具並改設定檔 | 不用 |
| 06 | 第二大腦資料夾 | 在筆記庫建立「每日筆記／創作庫／知識庫」三層資料夾 | 新增資料夾與說明筆記 | 不用 |
| 07 | Supabase 資料庫 | 連接 Supabase 雲端資料庫 | 安裝工具、改設定檔 | 要（API key） |
| 08 | Firebase | 連接 Firebase | 安裝工具、改設定檔 | 要（Google） |
| 09 | Ollama 本機 AI | 在自己電腦上跑 AI 模型 | 下載安裝 Ollama 與模型（檔案大） | 不用 |
| 10 | Gemini API | 設定 Gemini 免費 API | 只教你取得 key，不改電腦 | 要（Google、key） |
| 11 | 新專案工作區 | 替新專案建立資料夾、說明檔與版本控制 | 新增檔案；要建 GitHub repo 需同意 | 建 repo 時要（GitHub） |
| 12 | AI 生圖 | 用內建生圖功能做圖 | 不改設定（進階 API 路線才需要 key） | 不用 |
| 13 | 同步 Codex 設定 | 多台電腦之間同步 Codex 設定 | 安裝工具 | 視需求 |
| 14 | Vercel 網頁上線 | 把網頁部署成可分享的網址 | 安裝工具、改設定檔；測試會真的上線一個網頁（要你同意） | 要（Vercel） |
| 00A | 狀態盤點 | **狀態盤點**：只檢查哪些已完成、哪些還沒，並給建議 | 不改任何東西 | 不用 |

### 編號對照（給 AI 用，**不要貼給使用者**）

| 編號 | Skill 名稱 | 資料夾 |
|---|---|---|
| 00 | `codex-env-setup` | `skills/00-env-setup` |
| 01 | `codex-notebooklm` | `skills/01-notebooklm` |
| 02 | `codex-essentials` | `skills/02-essentials` |
| 03 | `codex-github` | `skills/03-github` |
| 04 | `codex-github-obsidian` | `skills/04-github-obsidian` |
| 05 | `codex-obsidian` | `skills/05-obsidian` |
| 06 | `codex-second-brain` | `skills/06-second-brain` |
| 07 | `codex-supabase` | `skills/07-supabase` |
| 08 | `codex-firebase` | `skills/08-firebase` |
| 09 | `codex-ollama` | `skills/09-ollama` |
| 10 | `codex-gemini` | `skills/10-gemini` |
| 11 | `codex-workspace` | `skills/11-workspace` |
| 12 | `codex-draw` | `skills/12-draw` |
| 13 | `codex-chezmoi` | `skills/13-chezmoi` |
| 14 | `codex-vercel` | `skills/14-vercel` |
| 00A | `codex-install-all` | `skills/00-install-all` |

## 步驟三：處理相依性

**除 00A 盤點外，所有項目都要先完成 00（環境準備，含 Git）**；使用者沒選 00 也要自動補上並告知。其餘相依如下，**自動補上並告知**，不要讓使用者猜：

| 選了 | 要先有 |
|---|---|
| 01、05、07、08、14 | 00（需要 Node.js 或 uv） |
| 03、13 | 00 |
| 04 | 03 與 05 |
| 06 | 05（需要知道筆記庫位置） |
| 11 | 03（建 GitHub repo 時）；有 Obsidian 筆記才加 05 |
| 14 | 00、03（建議用 GitHub 帳號註冊與綁定） |

只選 00 時，不得順便執行 GitHub CLI 安裝或帳號檢查（Git 屬於 00，會安裝；GitHub CLI 與登入屬於 03）。

## 步驟四：逐項安裝

對每一項重複：

1. 用白話說明這項要做什麼、會改動什麼，**等使用者同意**。
2. 讀取對應資料夾內的 `SKILL.md`，照步驟執行；需要完整說明時，改讀 repo 根目錄同主題的 `.md` 檔（例如 `00-環境建置.md`）。
   - 已 clone 到本機：直接讀本機資料夾。
   - 只拿到網址、沒有 clone：從 `https://raw.githubusercontent.com/tedchen0814/codex-starter-packs/main/` 加上檔案路徑讀取（例如 `.../main/skills/00-env-setup/SKILL.md`）。檔名含中文時，路徑要做 URL 編碼。這個做法**不需要先安裝 Git**，適合全新的電腦。讀到的中文若是亂碼（Windows PowerShell 5.1 的 `Invoke-WebRequest` 常見），改用 UTF-8 解碼重抓：`[Text.Encoding]::UTF8.GetString((Invoke-WebRequest <網址> -UseBasicParsing).RawContentStream.ToArray())`；不要根據亂碼的內容行動。
3. 把技能檔案安裝到 `~/.codex/skills/`（Windows：`C:\Users\<使用者>\.codex\skills\`），技能資料夾名稱用上表的 Skill 名稱（例如 `codex-env-setup`）。
4. 用白話回報結果，並說明新技能要在**下一個新對話**才會載入。
5. 問：「要繼續下一項嗎？」使用者說不用就停。

## 步驟五：收尾

每項回報 ✅ 完成／⏭️ 使用者跳過／⚠️ 需手動處理／❌ 失敗，最後列總表，並建議使用者：

- 開新對話，確認新技能有載入。
- 若有改設定檔，告知備份檔位置。
- 下一步可以做什麼（最多給兩個建議）。
