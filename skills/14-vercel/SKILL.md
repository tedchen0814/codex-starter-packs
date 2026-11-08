---
name: codex-vercel
description: Codex 串接 Vercel（CLI + 部署；官方 MCP 選用）。說「串接 Vercel」「連接 Vercel」「部署到 Vercel」時載入。
---

# 串接 Vercel（Codex 版）

1. 檢查 `node --version`；缺少就先裝 Node.js LTS
2. 安裝 CLI：Windows（Codex Desktop 是 MSIX，避開 AppData）用 `$env:NPM_CONFIG_PREFIX="$env:USERPROFILE\.npm-global"; npm.cmd i -g vercel@latest`，之後用完整路徑 `vercel.cmd --version`；其他系統 `npm i -g vercel@latest`
3. 登入：`vercel whoami`，未登入就 `vercel login`（瀏覽器授權）；沒帳號請使用者到 https://vercel.com/signup 選 Hobby，建議用 GitHub 註冊
4. **官方 MCP 為選用，預設不加。** CLI 已登入就能列專案、部署、看紀錄，大多數人不需要 MCP；MCP 會增加每個對話的固定開銷，授權範圍也涵蓋帳號下所有專案。只有使用者明確要求，才說明這些影響並取得同意後再加：先備份 `~/.codex/config.toml` → `codex mcp add vercel --url https://mcp.vercel.com`（或在 `config.toml` 加 `[mcp_servers.vercel]` 與 `url = "https://mcp.vercel.com"`）→ 沒自動開瀏覽器就 `codex mcp login vercel` → 重啟 Codex
5. 測試：建 `vercel-test/index.html` → `vercel --yes`（新專案第一次部署會直接算正式，無法先預覽；之後的 `vercel` 才是預覽，要更新正式網址才 `vercel --prod --yes`）→ 請使用者開網址確認；再用 `vercel ls` 確認最新部署狀態為 Ready（有加 MCP 才改用 MCP 查）
6. 選配：`vercel link --yes` + `vercel git connect` 綁 GitHub repo，push 自動部署
7. 詢問是否刪除測試專案；刪前先 `vercel project ls --scope <scope>` 確認名稱與 scope，取得確認後只刪這一個：`vercel project rm vercel-test --scope <scope> --confirm-name vercel-test`（不接受 `--yes`，無法復原）

⚠️ `.vercel/` 不 commit；API Key 用 `vercel env add`，不寫進 repo；部署與刪除前保留人工確認。

回報：Vercel CLI 版本、登入帳號、MCP 是否有加（預設不加）、測試網址、是否綁定 GitHub。
