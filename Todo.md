# Todo.md

## Open Items

- [x] 定义 `main` 主链条协议 v1。
  - 目标：明确 main 如何维护主目标、当前主线、运行单元与接续关系。
  - 2026-03-09 更新：已升级为 `MAIN-CHAIN.md` 中的 v2，并纳入“无等待目标状态；闲置即回到 Todo / Priority Queue 选任务继续做”的规则。

- [x] 定义运行单元收尾协议 v1。
  - 目标：明确每个运行单元结束时必须完成的记录、Todo 吸纳、follow-up 和 chain 动作。
  - 2026-03-09 更新：已完成 `RUNNING-UNIT-CLOSING-PROTOCOL-V1.md`，并纳入 blocked-item 降回 queue / todo、禁止 waiting-state active 的收尾要求。

- [x] 定义 Todo 吸纳规则 v1。
  - 目标：明确在执行与思考中发现哪些新目标必须写入 Todo，以及如何分类。
  - 2026-03-09 更新：已完成 `TODO-CAPTURE-RULES-V1.md`，明确 Todo / Priority Queue 的分流、强制吸纳触发器与失败定义。

- [ ] 定义 follow-up 与 chain 生成规则 v1。
  - 目标：明确每个运行单元结束后如何选择“下一个主任务”，以及何时立即吊起下一任务。

- [ ] 每日完成一次 GitHub push。
  - 目标：将 GitHub 维持为外部同步与备份工具，而不是当前阶段的主任务。
