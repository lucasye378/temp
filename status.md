# status.md

## Current State

- Chain status: active
- Current phase: 日常维护单元进行中
- Current primary objective: 在 waiting-for-target 状态下完成必要维护并保持主链可恢复
- Current main task: 完成日常维护单元：GitHub 提交、今日自我反思、并准备在合适时机开启新 session 清理 context
- Current follow-up: 先完成本轮 GitHub 提交与反思落盘，再判断是否进入 session 重开准备或继续机会捕捉
- Follow-up mode: cron
- Chain count: active-via-cron
- Last completed unit: 启动新的持续工作单元，并将 active 从纯等待态切到日常维护执行态
- Last result: 已确认当前维护优先顺序为 GitHub 提交 → 今日反思 → session 重开准备；本轮先执行维护，再回到 waiting-for-target / opportunity-capture
- Recovery status: not-needed

## Dispatch Snapshot

- Active task: 总 reorg：维护 ready-to-send 池，并等待明确对象 / 授权信号
- Ready candidate 1: 决策包服务（优先级最高；已具备等待明确对象后即可外发的条件）
- Ready candidate 2: 阅读精华提炼服务（已具备等待明确对象后即可外发的条件）
- Reorg needed: no
- Blocking issue: none-immediate

## Active Cron Roles

- Follow-up cron: short one-shot follow-up should be actively scheduled during waiting state
- Hourly recovery cron: planned

## Notes

- 主链上任何时刻只允许 1 个 active 主任务。
- 新目标先进入 priority queue，再决定是否抢占 follow-up。
- 外发消息应先在 webchat/main 留痕，再由 main 执行给 Telegram 的动作。
- 每个运行单元结束后，默认必须设置下一次 follow-up cron；默认短间隔为 30–60 秒。
