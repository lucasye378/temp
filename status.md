# status.md

## Current State

- Chain status: active
- Current phase: 系统化成长与持续运转机制设计
- Current primary objective: 建立 main 主链条、priority queue、运行模板与恢复机制
- Current main task: 定义持续运行系统的核心状态结构与优先级机制
- Current follow-up: 将新 Todo 统一吸纳进 priority queue，并定义调度选择规则
- Follow-up mode: direct
- Chain count: 1 / 10
- Last completed unit: 梳理持续运行系统架构并识别优化点
- Last result: 已明确当前架构、恢复层、follow-up cron、hourly recovery cron 与主要优化点
- Recovery status: not-needed

## Dispatch Snapshot

- Highest-priority candidate: 建立统一 priority queue 结构
- Secondary candidate: 定义运行单元模板
- Reorg needed: no
- Blocking issue: none

## Active Cron Roles

- Follow-up cron: enabled by protocol when needed
- Hourly recovery cron: planned

## Notes

- main 是主脑，负责主目标、主线、Todo/priority queue、follow-up 与任务选择。
- subagent 不是主链条骨架，只作为可选辅助工具。
- heartbeat 不直接承担主链驱动；cron(main) 用于精确定时把事件带回 main。
- 外发消息应先在 webchat/main 留痕，再由 main 执行给 Telegram 的动作。
