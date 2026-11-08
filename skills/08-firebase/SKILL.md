---
name: codex-firebase
description: Codex 連接 Firebase MCP。說「連接 Firebase」時載入。
---

# 連接 Firebase（Codex 版）

1. 安裝 `firebase-tools`：Windows（Codex Desktop 是 MSIX）用 `$env:NPM_CONFIG_PREFIX="$env:USERPROFILE\.npm-global"; npm.cmd install -g firebase-tools`，之後用完整路徑 `%USERPROFILE%\.npm-globalirebase.cmd`；其他系統 `npm install -g firebase-tools`。再 `firebase login`（請使用者在自己的終端機執行）
2. `firebase init` 在專案目錄
3. `codex mcp add firebase -- npx -y firebase-tools@latest mcp`
   或手動編輯 `~/.codex/config.toml`
4. 重啟後驗證

⚠️ Admin SDK 憑證不可公開，個人資料只存代號。
