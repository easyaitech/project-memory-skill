# Project Memory Skill

为项目维护「总纲 + 分册」两层记忆结构：
- **根目录 `PROJECT-MEMORY.md`（总纲，软预算约 2,000 token）**：只放全局方向、红线边界、通用偏好与分册索引，每次开工必读全文。
- **`docs/memory/<topic>.md`（按需分册）**：项目变大后按业务模块沉淀排错事实与经验，改哪块读哪册、写哪册，避免单文件无限膨胀与多窗口并行冲突。
- **权限清晰且不卡交付**：方向、边界、偏好的增删改必须由项目负责人确认（合规代码先行交付，原则提案附在收尾汇报等确认）；帮助下次少走弯路的事实与经验遵循「三不写、两必填」直接维护。

## 安装

克隆本仓库后，在仓库根目录按你使用的工具安装（支持多工具共用同一份项目记忆）：

```sh
# Codex
mkdir -p ~/.codex/skills/project-memory
cp -R skills/project-memory/. ~/.codex/skills/project-memory/

# Claude Code（可选）
mkdir -p ~/.claude/skills/project-memory
cp -R skills/project-memory/. ~/.claude/skills/project-memory/

# Cursor（可选）
mkdir -p ~/.cursor/skills/project-memory
cp -R skills/project-memory/. ~/.cursor/skills/project-memory/
```

新项目建档或存量长文整理，可在新会话中输入：

```text
用 $project-memory 为这个项目建档（若已有旧长文则按「总纲 + 分册」分步迁移）
```

## 项目与全局接入（多工具统一口径）

建议把读写约定放进项目根目录的 `AGENTS.md`（`CLAUDE.md` 可通过 `@AGENTS.md` 共用），确保 Codex、Claude Code、Cursor 等不同工具读写同一套结构；若作为个人默认习惯，也可放入 `~/.codex/AGENTS.md` 或 `~/.claude/CLAUDE.md`：

> - **开工读取**：开发前先读根目录 `PROJECT-MEMORY.md` 总纲，再按本次涉及的模块查阅 `docs/memory/` 下的对应分册；缺少记忆文件时用 `project-memory` 建档。项目级明确约定优先于个人全局默认约定。
> - **收尾检查**：有改动的会话在提 PR、直接合并或交付前按 `project-memory` 检查（评审产生新长期结论时补查，纯问答与只读排查跳过）。日常分支只做局部增量、不顺手改写无关旧段落；代码本身符合现有边界时正常交付，将待确认的「方向 / 边界 / 偏好」提案附在汇报末尾，不因等确认卡住上线。
> - **经验准入与专门整理**：可直接维护帮下次少走弯路的事实与经验（不抄代码现状、不记流水账、写清原因与失效/重议条件、推翻旧条时显式更新）；总纲逼近 2,000 token 或分册膨胀时，单开整理任务集中压缩与拆册。
