# WORKFLOW.md

## Current Workflow Snapshot

这份文件不再记录早期能力测试主线，而是只保留**当前最该看的一层摘要**。
详细规则看：`AGENTS.md` / `MAIN-CHAIN.md` / `RUNBOOK.md` / `status.md`。

## What matters now

### Main chain defaults
- 进入持续工作流程 → 直接开始，不等待额外指令
- 每次运行单元结束后：先收尾、更新 md、再挂下一次 follow-up cron
- follow-up cron 默认 30–60 秒
- 任何时刻只允许 1 个 active 主任务
- reorg 由状态决定，不由固定计数决定

## Current active direction
- Active task 以 `status.md` 为准
- Queue priority 以 `PRIORITY-QUEUE.md` 为准
- 日志沉淀以 `memory/YYYY-MM-DD.md` 为准

## Current operational weakness
- 最容易漏的不是思路，而是**收尾最后一步：挂下一次 cron**
- 因此每次运行单元都要把“Next cron: scheduled / none”显式写出来
