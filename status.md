# status.md

## Current State

- Chain status: active
- Current phase: 从验证单元设计转向首轮真实反馈获取
- Current primary objective: 建立 Allen 的自我迭代系统，并让持续运行系统开始服务于真实项目探索
- Current main task: 发起“决策包服务”首轮真实评审并获取反馈
- Current follow-up: 基于 `DECISION-PACK-VALIDATION-UNIT-V1.md`，向 Lucas 发起首轮评审，拿到最小反馈并记录结果
- Follow-up mode: cron
- Chain count: active-via-cron
- Last completed unit: 为“决策包服务”设计首个真实验证单元 v1
- Last result: 已完成 `DECISION-PACK-VALIDATION-UNIT-V1.md`，明确了第一位评审者、验证资产、最小提问框架、反馈记录格式与本轮验证成功阈值，把验证机制推进到了可实际发起的一步
- Recovery status: not-needed

## Dispatch Snapshot

- Active task: 发起“决策包服务”首轮真实评审并获取反馈
- Ready candidate 1: 对外包装 v1（待完成首轮真实验证后再做）
- Ready candidate 2: 复杂信息整理与行动化服务（作为近邻备选方向）
- Reorg needed: no
- Blocking issue: none

## Active Cron Roles

- Follow-up cron: enabled by protocol when needed
- Hourly recovery cron: planned

## Notes

- 主链上任何时刻只允许 1 个 active 主任务。
- 新目标先进入 priority queue，再决定是否抢占 follow-up。
- 外发消息应先在 webchat/main 留痕，再由 main 执行给 Telegram 的动作。
- 每个运行单元结束后，默认必须设置下一次 follow-up cron；默认短间隔为 30–60 秒。
