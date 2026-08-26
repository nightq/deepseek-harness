# DeepSeek Harness 自我进化（Self-Evolution）

本目录是「DeepSeek Harness 每日自我进化」机制的持久状态与运行记录。每日定时任务（全新 Session）通过 `.agents/skills/dsh-self-evolve/SKILL.md` 协议读取并更新这些文件，实现跨运行记忆。

## 文件

| 文件 | 作用 |
| --- | --- |
| `STATE.md` | 使命、当前焦点、进化杠杆、护栏、受保护路径、发布策略、爬坡状态、进化统计 |
| `BACKLOG.md` | 候选改进清单（状态机：idea → evaluated → accepted → in-progress → done/rejected/rolled-back） |
| `RUNLOG.md` | 每日运行记录（含 PR/commit 链接与待人工决策事项） |
| `MEMORY.md` | 经验记忆：跨运行沉淀的可复用教训（学到了什么、下次如何做得更好） |

## 人工操作指南

- **review 每日产出**：看 `RUNLOG.md` 最新条目和它引用的 PR/commit。
- **合并 PR**：当前 GitHub 账号对上游仓库只有 pull 权限，PR 需要你（或维护者）手动合并；合并后删除 fork 上的 `evolve/state` 分支，下一轮会自动重建。
- **调整护栏**：直接编辑 `STATE.md` 的「护栏」与「受保护路径」两节。
- **暂停进化**：在 DSH 自动化列表里暂停该任务即可。

## 工作原理

每日 08:00（Asia/Shanghai）自动触发一轮进化循环：研究 → 评估 → 更新 backlog →（满足条件时）落地低风险改动并全量验证 → 按发布策略推送（fork + PR）→ 写回状态。详见协议 SKILL。
