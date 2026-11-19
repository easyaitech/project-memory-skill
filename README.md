# Project Memory Skill

让 Codex 在项目根目录维护一份精简的 `PROJECT-MEMORY.md`。方向、边界和偏好由项目负责人确认，事实与可复用经验可以直接维护。默认篇幅目标约 2,000 token。

## 安装

克隆本仓库后，在仓库根目录执行以下命令，将 Skill 安装到当前用户的 Codex 技能目录。目标目录应为空或尚未创建。

```sh
mkdir -p ~/.codex/skills/project-memory
cp -R skills/project-memory/. ~/.codex/skills/project-memory/
```

在新的 Codex 会话中输入 `用 $project-memory 为这个项目建档`。已有长文档也可以从同一入口整理。

## 全项目接入

在用户级 Codex 指令文件 `~/.codex/AGENTS.md` 中加入下列约定。仅想在一个项目使用时，放进该项目的 `AGENTS.md`。

> 项目开发开工时读取简短的 PROJECT-MEMORY.md，旧长文按主题查阅。缺少记忆文件时用 $project-memory 建档。有改动的会话在提 PR、直接合并或交付前用该 Skill 检查，评审引入长期决定时补查。方向、边界和偏好的任何增删改都须由用户确认，事实和经验可直接维护，无新增则跳过。

已有项目采用只追加等旧约定时，先协调项目级指令。首次建档可由用户审阅一批草案，日常只需确认实际变化的条目。
