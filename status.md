# status.md

## Current State

- Chain status: active
- Current phase: 从“能收集任务”升级到“能压缩选择、逼出执行”
- Current primary objective: 建立 Allen 的自我迭代系统，并让持续运行系统开始服务于真实项目探索
- Current main task: 用真实任务跑一次持续运行系统闭环
- Current follow-up: 基于第一版项目候选清单，选择一个最适合做下一步验证的方向，并把它作为真实闭环任务继续推进
- Follow-up mode: cron
- Chain count: 2 / 10
- Last completed unit: 为真实闭环任务选定“项目候选清单构建”作为第一步，并产出 `PROJECT-IDEAS.md`
- Last result: 已生成第一版低编程门槛、高现实价值的项目候选清单，并初步筛出 3 个优先方向
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
