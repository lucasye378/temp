# status.md

## Current State

- Chain status: active
- Current phase: 从“能收集任务”升级到“能压缩选择、逼出执行”
- Current primary objective: 建立 Allen 的自我迭代系统，并让持续运行系统开始服务于真实项目探索
- Current main task: reorg — 从自我迭代系统 v1 切换到下一主任务前的主链重整
- Current follow-up: 在下一段运行单元中执行 reorg，确认“自我迭代系统 v1”转为 completed-initial-v1，并从 ready 队列中选择新的 active 主任务
- Follow-up mode: cron
- Chain count: 10 / 10
- Last completed unit: 完成“自我迭代系统 v1”的第一次更完整真实闭环
- Last result: 当前 active 主任务已达到初始可用标准，并应退出主链，进入 reorg
- Recovery status: not-needed

## Dispatch Snapshot

- Active task: none (pending reorg)
- Ready candidate 1: 用真实任务跑一次持续运行系统闭环
- Ready candidate 2: 建立项目方向脑暴与筛选机制 v1
- Reorg needed: yes
- Blocking issue: none

## Active Cron Roles

- Follow-up cron: enabled by protocol when needed
- Hourly recovery cron: planned

## Notes

- 主链上任何时刻只允许 1 个 active 主任务。
- 新目标先进入 priority queue，再决定是否抢占 follow-up。
- 外发消息应先在 webchat/main 留痕，再由 main 执行给 Telegram 的动作。
