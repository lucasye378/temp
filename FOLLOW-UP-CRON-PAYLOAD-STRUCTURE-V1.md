# FOLLOW-UP-CRON-PAYLOAD-STRUCTURE-V1.md

## Goal

定义主链短 follow-up cron 的 payload 最小结构，
让 main 被唤醒时，不只是收到一段自由文本提醒，
而是能更稳定地恢复到正确上下文。

---

## Why this matters

今天已经验证：
短 follow-up cron 是主链继续运转的核心吊起器。

问题在于，如果 payload 只有一段自然语言，
就容易出现：
- 当前 active 已经切换，但提醒文本还是旧的
- 同一句提醒里混着“规则 + 当前任务 + 上一步结果”，可读性差
- 后续难以模板化，也难以做恢复层复用

所以需要一个更固定的最小结构。

---

## Design principle

第一版不追求复杂 JSON 协议，
而是先定义：

**每个 follow-up payload 至少应稳定表达哪 4 件事。**

---

## Minimum fields

### 1. wake_intent
这次唤醒是为了什么。

候选值例如：
- continue-active-unit
- reorg-and-pick-active
- close-current-unit
- recovery-check

作用：
让 main 先知道这次不是“重新开始”，
而是哪一类恢复动作。

### 2. active_task
当前唯一 active 主任务是什么。

要求：
- 用一句话描述
- 必须可执行
- 不写抽象口号

作用：
让 main 醒来后先确认当前主线没有漂移。

### 3. next_unit
这一轮最小运行单元要做什么。

要求：
- 比 active_task 更具体
- 是这一轮真正要执行的动作

作用：
避免 main 醒来后又重新想一遍“那我现在到底先做哪一步”。

### 4. chain_state
当前链条处于什么状态。

候选值例如：
- active
- reorg
- waiting-boundary
- recovery
- closing

作用：
帮助 main 快速判断这轮是正常 continuation，还是 reorg / recovery。

---

## Optional field

### recent_result
上一个运行单元刚刚产出的关键结果。

这不是每次都必须，
但在这几类场景建议带上：
- 刚完成 reorg
- 刚切 active
- 刚完成一个阶段性收口

作用：
让 main 不用只靠 status.md 才知道“上一轮到底刚发生了什么”。

---

## v1 template

第一版 follow-up payload 可统一压成下面这个模板：

- wake_intent: <这次唤醒的目的>
- active_task: <当前唯一 active 主任务>
- next_unit: <这一轮最小运行单元>
- chain_state: <active/reorg/recovery/...>
- recent_result: <可选；上一轮关键结果>

---

## Example

- wake_intent: continue-active-unit
- active_task: 定义 follow-up cron payload 结构 v1
- next_unit: 基于今天的真实主链样本，收敛出 payload 的固定字段与最小模板
- chain_state: active
- recent_result: 已完成 reorg，并将 active 从财经报道拆解服务切到 cron 协议定义

---

## One-Sentence Rule

**follow-up cron payload 的第一目标，不是把所有上下文都塞进去，而是让 main 醒来时立刻知道“我为什么被叫醒、我现在要做什么”。**
