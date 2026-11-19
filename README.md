# Project Memory Skill

为项目维护「总纲 + 分册」两层记忆结构：
- **根目录 `PROJECT-MEMORY.md`（总纲，软预算约 2,000 token）**：只放跨模块通用的方向、红线边界、全局偏好与强触发分册索引，每次开工必读全文。
- **`docs/memory/<topic>.md`（按需分册）**：项目变大后按业务域承载置顶的「模块边界与偏好」与下方的「关键经验」，改哪块读哪册、写哪册；合入前对照最新目标分支核对同册并发，不盲套 `merge=union`。
- **权限清晰、交付不卡、迁移无空窗**：无论在总纲还是分册，方向、边界、偏好的增删改均须项目负责人确认（合规代码先行交付，原则提案附出处放在归档判定卡等固定尾行之前）；存量长文在确认前保持原位，确认后同一 PR 原子切换归档、新总纲与仓库共享规则。

## 安装

克隆本仓库后，在仓库根目录按你使用的工具安装（Cursor 会自动加载 `~/.codex/skills` 与 `~/.claude/skills`，仅使用 Cursor 时可装入 `~/.cursor/skills`）：

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

新项目建档或存量长文整理，可在新会话中输入：

```text
用 $project-memory 为这个项目建档（若已有旧长文则按「总纲 + 分册」先在会话起草，确认后再原子切换）
```

## 项目与全局接入（多工具统一口径）

建议把读写约定放进项目根目录的 `AGENTS.md`（`CLAUDE.md` 可通过 `@AGENTS.md` 共用），确保 Codex、Claude Code、Cursor 等不同工具读写同一套结构；迁移存量项目时，在切换总纲的同一个 PR 里同步替换仓库内的旧约定（如「只往后追加」）。若作为个人默认习惯，也可放入 `~/.codex/AGENTS.md` 或 `~/.claude/CLAUDE.md`：

> - **开工读取**：开发前先读根目录 `PROJECT-MEMORY.md` 总纲，再按总纲触发索引必读 `docs/memory/` 下的对应分册（未拆完的模块按索引提示回查归档旧文）；缺少记忆文件时用 `project-memory` 建档。项目级明确约定优先于个人全局默认约定。
> - **收尾与并发**：有改动的会话在提 PR、直接合并或交付前按 `project-memory` 检查（评审产生新长期结论时补查，纯问答与只读排查跳过）。日常分支只做局部增量，合入前对照最新目标分支核对触及的分册（独立经验并存，冲突或相反结论核实依据后合并，分册不盲套 `merge=union`）。代码本身符合现有边界时正常交付，将待确认的全局或模块原则提案附上 PR/任务出处，放在收尾汇报正文末尾（归档判定卡等固定尾行之前）。
> - **经验准入与专门整理**：可直接维护帮下次少走弯路的事实与经验（不抄代码现状、不记流水账、写清原因与失效/重议条件、推翻旧条时显式更新）；全局及分册内「边界与偏好」的任何增删改均须用户确认。总纲逼近 2,000 token 或分册膨胀时，单开整理任务集中压缩与拆册。
