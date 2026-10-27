---
name: codex-obsidian
description: Codex 連接 Obsidian。說「連接 Obsidian」時載入。
---

# 連接 Obsidian（Codex 版）

## 先確認

1. 找 vault 路徑（搜尋含 `.obsidian` 子資料夾的位置），列出候選**請使用者確認**，不要自己挑。
2. 問使用者：這個 vault 有沒有不想讓 AI 讀取的私密資料夾？有的話，先把規則寫進 `~/.codex/AGENTS.md`（例如「不讀取、不搜尋、不引用 `<私密資料夾>/`，也不要透過任何工具對它做列出、讀取、寫入、移動、刪除」）。這是規則，不是技術鎖，請如實告知使用者。

## 方式一：資料夾授權（推薦）
在 Codex 設定中授權 vault 資料夾讀寫，不需 MCP。

## 方式二：MCPVault（需要用 MCP 工具時）

1. **不要做全域安裝**（不要 `npm install -g`），改用 `npx` 直接啟動並**鎖定版本**，避免新版本悄悄改變行為。
2. 改設定檔之前，先備份：`~/.codex/config.toml` → `config.toml.bak-<日期時間>`。
3. 加入設定（二選一）：
   - 指令（Windows）：`codex mcp add obsidian -- npx.cmd -y @bitbonsai/mcpvault@0.15.0 "<VAULT_PATH>"`
   - 指令（macOS／Linux）：`codex mcp add obsidian -- npx -y @bitbonsai/mcpvault@0.15.0 "<VAULT_PATH>"`
   - 或手動編輯 `~/.codex/config.toml`：
     ```toml
     [mcp_servers.obsidian]
     command = "npx.cmd"   # macOS／Linux 用 "npx"
     args = ["-y", "@bitbonsai/mcpvault@0.15.0", "<VAULT_PATH>"]
     ```
   - Windows 一律用 `npx.cmd`；路徑含中文或空白時要加引號。
4. 重啟 Codex 後驗證：**只列出 vault 最上層資料夾**，確認讀得到；再做一次讀取與一次寫入測試（寫入前先告知要建立哪個測試筆記，測完詢問是否刪除）。
5. 載入失敗時，**把完整錯誤訊息貼給使用者，不要自己換方案**，也不要改成全域安裝。

> 版本號 `0.15.0` 是撰寫時驗證過的版本；要升級時先告知使用者，不要自動用 `@latest`。

## 進階
全文檢索：安裝 Obsidian Local REST API plugin + `cli-hub install obsidian`（需要使用者同意）。

回報：授權方式、vault 路徑、私密資料夾規則是否已寫入、讀取／寫入測試結果。
