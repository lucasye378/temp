# status.md

## Current State

- Chain status: active
- Current phase: 主链规则纠偏进行中
- Current primary objective: 修正“waiting-for-target”误设，并把闲置即转 queue/todo 执行写入主链协议
- Current main task: 定义 follow-up 与 chain 生成规则 v1
- Current follow-up: 本轮已完成 Todo 吸纳规则 v1；下一轮继续把 follow-up / chain 选择逻辑写硬，减少“知道该续链但没稳定接上”的错误
- Follow-up mode: cron
- Chain count: active-via-cron
- Last completed unit: 完成 Todo 吸纳规则 v1
- Last result: 已产出 `TODO-CAPTURE-RULES-V1.md`，明确长期待办 vs 调度项的分流规则、必须入池的触发条件，以及 Todo capture 的失败定义；当前 active 已切到 `定义 follow-up 与 chain 生成规则 v1`
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
