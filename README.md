# Project Memory Skill

为项目维护精简、不撞车、不卡交付的「总纲 + 分册」两层记忆：
- **根目录 `PROJECT-MEMORY.md`（总纲，约 2,000 字）**：只放跨模块通用的方向、红线边界、全局偏好与强触发分册索引，每次开工必读全文。
- **`docs/memory/<topic>.md`（按需分册，单册约 3,000 字）**：置顶放本模块的「边界与偏好」，下方放三句以内的「关键经验」；按文件是否配置 `merge=union` 自动切换原地修订或末尾追加模式。
- **权限清晰、交付不卡、迁移无空窗**：用户在任务中当场拍板的取舍直接记录，AI 自行归纳的新规矩放进「待确认的规则提案」（不写进记忆文件、不阻塞合规代码交付）；存量长文迁移参见 `skills/project-memory/references/migration.md`，原位起草确认后单 PR 原子切换。

## 安装

克隆本仓库后，按你使用的工具整目录复制安装（含 `references/` 子目录；Cursor 会自动加载 `~/.codex/skills` 与 `~/.claude/skills`）：

```sh
# Codex
mkdir -p ~/.codex/skills/project-memory
cp -R skills/project-memory/. ~/.codex/skills/project-memory/

# Claude Code
mkdir -p ~/.claude/skills/project-memory
cp -R skills/project-memory/. ~/.claude/skills/project-memory/

# 仅使用 Cursor（未装上面两项时）
mkdir -p ~/.cursor/skills/project-memory
cp -R skills/project-memory/. ~/.cursor/skills/project-memory/
```

新项目建档或点名迁移存量长文，可在新会话中输入：

```text
用 $project-memory 为这个项目建档（若已有超长旧记忆则先在会话起草迁移方案，确认后再原子切换）
```

## 项目接入（推荐放进项目 `AGENTS.md`）

建议在项目根目录的 `AGENTS.md` 中放下面两行精简指针（`CLAUDE.md` 可通过 `@AGENTS.md` 共用；详细规则留在技能内单一维护，避免多处副本脱节）：

> - **项目记忆**：开工先读根目录 `PROJECT-MEMORY.md` 总纲，并按其中触发索引读取 `docs/memory/` 下的相关分册；缺少记忆文件时用 `project-memory` 建档。
> - **收尾检查**：有改动的会话在提 PR、合并或交付前按 `project-memory` 技能检查更新（纯问答与只读排查跳过）；具体准入、并发与确认规则以该技能为准。
