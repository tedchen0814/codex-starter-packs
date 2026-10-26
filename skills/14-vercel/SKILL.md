---
name: codex-vercel
description: Codex 串接 Vercel（CLI + MCP + 部署）。說「串接 Vercel」「連接 Vercel」「部署到 Vercel」時載入。
---

# 串接 Vercel（Codex 版）

1. 檢查 `node --version`；缺少就先裝 Node.js LTS
2. 安裝 CLI：`npm i -g vercel@latest` → `vercel --version`（PowerShell 被擋就用 `vercel.cmd`）
3. 登入：`vercel whoami`，未登入就 `vercel login`（瀏覽器授權）；沒帳號請使用者到 https://vercel.com/signup 選 Hobby，建議用 GitHub 註冊
4. 註冊 MCP：`codex mcp add vercel --url https://mcp.vercel.com`（或在 `~/.codex/config.toml` 加 `[mcp_servers.vercel]` 與 `url = "https://mcp.vercel.com"`）→ 沒自動開瀏覽器就 `codex mcp login vercel` → 重啟 Codex
5. 測試：建 `vercel-test/index.html` → `vercel --yes`（預覽）→ `vercel --prod --yes`（正式）→ 請使用者開網址確認；再用 MCP 查最新部署狀態為 READY
6. 選配：`vercel link --yes` + `vercel git connect` 綁 GitHub repo，push 自動部署
7. 詢問是否刪除測試專案：`vercel project rm vercel-test`

⚠️ `.vercel/` 不 commit；API Key 用 `vercel env add`，不寫進 repo；部署與刪除前保留人工確認。

回報：Vercel CLI 版本、登入帳號、MCP 授權狀態、測試網址、是否綁定 GitHub。
