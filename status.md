# status.md

## Current State

- Chain status: active
- Current phase: 从“能收集任务”升级到“能压缩选择、逼出执行”
- Current primary objective: 建立 Allen 的自我迭代系统，并让持续运行系统开始服务于真实项目探索
- Current main task: 用真实任务跑一次持续运行系统闭环
- Current follow-up: 复盘这次真实闭环样例，判断 v1 系统在哪些地方顺手、哪些地方还粗糙，并决定是否将该真实任务视为闭环完成
- Follow-up mode: cron
- Chain count: 5 / 10
- Last completed unit: 产出第一版最小决策包交付物
- Last result: 真实任务已从‘选方向’推进到‘形成可交付样例’，v1 系统已被用于承载一次真实产出
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
