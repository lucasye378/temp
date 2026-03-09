# status.md

## Current State

- Chain status: active
- Current phase: 从“能收集任务”升级到“能压缩选择、逼出执行”
- Current primary objective: 建立 Allen 的自我迭代系统，并让持续运行系统开始服务于真实项目探索
- Current main task: 建立 Allen 的自我迭代系统 v1
- Current follow-up: 启动“自我迭代系统 v1”的最小构成设计，并定义第一条真实日常流程
- Follow-up mode: direct
- Chain count: 4 / 10
- Last completed unit: 完成 priority queue 清洗，引入执行闸门与状态分流
- Last result: 系统已从“会收集任务”升级到“会压缩选择、保留唯一 active 项”阶段
- Recovery status: not-needed

## Dispatch Snapshot

- Active task: 建立 Allen 的自我迭代系统 v1
- Ready candidate 1: 用真实任务跑一次持续运行系统闭环
- Ready candidate 2: 建立项目方向脑暴与筛选机制 v1
- Reorg needed: no
- Blocking issue: none

## Active Cron Roles

- Follow-up cron: enabled by protocol when needed
- Hourly recovery cron: planned

## Notes

- 主链上任何时刻只允许 1 个 active 主任务。
- 新目标先进入 priority queue，再决定是否抢占 follow-up。
- 外发消息应先在 webchat/main 留痕，再由 main 执行给 Telegram 的动作。
