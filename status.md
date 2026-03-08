# status.md

## Current State

- Chain status: active
- Current phase: 目标梳理与优先级系统建设
- Current primary objective: 建立 Allen 的自我迭代系统，并让持续运行系统开始服务于真实项目探索
- Current main task: 构建可指导后续工作的 priority queue
- Current follow-up: 依据最新共识重写 priority queue，使其同时承载 Allen 目标、公司目标、每日固定工作与项目方向脑暴池
- Follow-up mode: direct
- Chain count: 2 / 10
- Last completed unit: 完成主链状态、priority queue 与模板系统的第一版搭建
- Last result: 已具备 status / queue / templates / runbook 等骨架，现进入目标与方向整理阶段
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
