---
name: codex-workspace
description: Codex 專案初始化工作模式。說「初始化專案」「建專案」時載入。
---

# 專案初始化（Codex 版）

## 步驟一：安裝三個工作流程技能（只裝缺的）

本 repo 的 `workflow-skills/` 資料夾附了三個技能，先檢查 `~/.codex/skills/` 是否已有同名資料夾；**已有的不要覆蓋**，有差異時請使用者決定。

| 技能 | 用途 | repo 內路徑 |
|---|---|---|
| `project-init-sync` | 新專案初始化 | `workflow-skills/project-init-sync/SKILL.md` |
| `startup-sync` | 開工接續 | `workflow-skills/startup-sync/SKILL.md` |
| `shutdown-sync` | 收工同步 | `workflow-skills/shutdown-sync/SKILL.md` |

- 已 clone：直接複製對應資料夾到 `~/.codex/skills/<技能名稱>/`。
- 只拿到網址：從 `https://raw.githubusercontent.com/tedchen0814/codex-starter-packs/main/workflow-skills/<技能名稱>/SKILL.md` 下載，存成 `~/.codex/skills/<技能名稱>/SKILL.md`。
- 安裝前先說明要裝哪三個，等使用者同意。裝完提醒：新技能要在下一個新對話才會載入。

## 步驟二：初始化專案

使用 `project-init-sync` 流程：

1. 問：名稱、用途、資料夾；GitHub repo（預設不建，要建一律私有）、是否登錄到 Obsidian。
2. 建立：`AGENTS.md`、`README.md`、`工作筆記.md`、`.gitignore`、本機 Git repo。
3. 建 GitHub repo、登錄 Obsidian 都要使用者同意，且需先完成對應的 `codex-github`、`codex-obsidian`。

## 開工／收工

- 開工：使用 `startup-sync`，讀 `工作筆記.md` → `git status` → 回報上次做到哪與下一步。
- 收工：使用 `shutdown-sync`，檢查敏感資料 → 更新 `工作筆記.md` → 明確檔案 `git commit` → 有 origin 時 push。
- 有安裝 `codex-chezmoi` 才需要同步設定（見 13-chezmoi）；沒有就略過，不要自行安裝。

回報：檔案清單、已安裝的技能、（若有）GitHub 網址與 Obsidian 筆記路徑。
