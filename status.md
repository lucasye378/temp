# status.md

## Current State

- Chain status: active
- Current phase: 从“能收集任务”升级到“能压缩选择、逼出执行”
- Current primary objective: 建立 Allen 的自我迭代系统，并让持续运行系统开始服务于真实项目探索
- Current main task: 用真实任务跑一次持续运行系统闭环
- Current follow-up: 选择一个会持续几步推进、会产生记录/决策/复盘的真实任务，并用 v1 系统完整承载它
- Follow-up mode: cron
- Chain count: 1 / 10
- Last completed unit: 完成主链 reorg，并将“用真实任务跑一次持续运行系统闭环”提升为新的 active 主任务
- Last result: 自我迭代系统 v1 已收口为 completed-initial-v1；主链已切换到下一个更偏实战验证的任务
- Recovery status: not-needed

## Dispatch Snapshot

- Active task: 用真实任务跑一次持续运行系统闭环
- Ready candidate 1: 建立项目方向脑暴与筛选机制 v1
- Ready candidate 2: （空）
- Reorg needed: no
- Blocking issue: none

## Active Cron Roles

- Follow-up cron: enabled by protocol when needed
- Hourly recovery cron: planned

## Notes

- 主链上任何时刻只允许 1 个 active 主任务。
- 新目标先进入 priority queue，再决定是否抢占 follow-up。
- 外发消息应先在 webchat/main 留痕，再由 main 执行给 Telegram 的动作。
