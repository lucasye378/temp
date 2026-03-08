# SYSTEM-DESIGN.md

## Central Scheduling Model v1

### Core idea

采用“中央调度型持续运行系统”：
- **main** 作为中央调度器，维护主目标、Todo 池、当前优先级和下一步任务。
- **subagent** 作为执行单元，负责完成具体运行单元并回报结果。
- subagent 不直接拥有最终调度权；它可以提出 follow-up 建议，但由 main 统一决定是否接续、接续什么、是否并行。

## Why this model

这个模型相比“每个子单元自行决定下一步”更 clean，且更适合并行。
它的核心优势是把：
- 执行
- 汇报
- 调度
拆成不同职责层。

## Main responsibilities

- 维护主目标
- 维护 Todo 池
- 维护任务优先级
- 接收 subagent 汇报
- 吸纳新目标与新风险
- 决定下一个主任务
- 决定哪些任务可并行，哪些必须串行

## Subagent responsibilities

- 执行具体运行单元
- 在结束时提交标准汇报
- 报告：结果、状态、新 Todo、阻塞、follow-up 建议
- 不直接决定系统主线

## Report protocol (v1)

每个 subagent 完成时应尽量提供：
- Result
- Status
- New Todos
- Suggested Follow-up
- Risks / Blockers

## Main dispatch protocol (v1)

main 收到 subagent 汇报后，固定做：
1. 接收并判断结果
2. 吸纳新的 Todo
3. 判断是否需要更新主目标或优先级
4. 选择下一个主任务
5. 决定是否立即吊起下一个任务

## Main risks

### 1. Main becomes bottleneck

所有任务都回流给 main 会让 main 变成中央瓶颈。

### 2. Report overload

如果 subagent 汇报不标准，main 会被信息淹没。

### 3. Todo explosion

多个 subagent 并行会快速产生大量新目标，若无筛选机制，Todo 池会膨胀。

### 4. Dispatch timing ambiguity

什么时候应立即触发下一任务，什么时候应先收集更多结果，再统一调度，是关键难点。

### 5. Boundary blur

subagent 可以建议 follow-up，但不应侵蚀 main 的最终决策权。

### 6. Parallel consistency issues

并行执行可能带来冲突、重复、依赖不同步等问题。

## Reconsideration

经过进一步推敲，当前阶段**不适合**以 agent/subagent 作为持续运转链条的主干。
原因是：
- subagent 默认上下文不如 main 完整
- 某些高价值任务（尤其是深思考、主线判断、长期上下文整合）更适合 main 直接完成
- 如果把链条主干建立在 subagent 生命周期上，会让关键任务质量打折，并把系统复杂度提前抬高

## Current recommendation

当前阶段应回到 **main 自身维护主链条** 的方法：
- main 维护主目标
- main 维护 Todo 吸纳
- main 在每个运行单元结束后生成 follow-up
- main 吊起下一个任务，形成持续运行链条
- subagent 仅作为可选辅助工具，而不是主干调度结构

## Implementation order

1. 定义 main 主链条协议 v1
2. 定义运行单元收尾协议 v1
3. 定义 Todo 吸纳规则 v1
4. 定义 follow-up 与 chain 生成规则 v1
5. 再视情况把 subagent 作为局部执行辅助接入
