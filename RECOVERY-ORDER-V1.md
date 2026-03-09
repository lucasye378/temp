# RECOVERY-ORDER-V1.md

## Goal

定义 hourly recovery cron 在唤醒 main 后的最小恢复顺序。

它的任务不是“重做所有工作”，
而是：

**在主链断掉、follow-up 漏掉、或状态混乱时，把 main 稳定拉回正确轨道。**

---

## Core principle

recovery 的第一目标不是继续旧文本，
而是先判断：

**旧 active 还值不值得恢复？**

如果值得，就恢复。
如果不值得，就立刻 reorg 并选新的唯一 active。

---

## Recovery order v1

### Step 1 — Read state files
先读取：
1. `status.md`
2. `PRIORITY-QUEUE.md`
3. `RUNBOOK.md`

作用：
先恢复主链显式状态，
而不是靠记忆猜。

---

### Step 2 — Determine recovery type
判断当前属于哪种情况：

- **normal continuation**：旧 active 仍有效，只是 follow-up 漏了
- **reorg needed**：旧 active 已完成、失效、或 queue 与 status 不一致
- **state confusion**：status / queue / follow-up 信息互相冲突

如果是 `state confusion`，
直接进入 reorg 单元，
不要硬续旧 active。

---

### Step 3 — Check whether old active is still valid
旧 active 只有在同时满足下面条件时才继续恢复：

- 当前仍是唯一主任务
- 还没阶段性完成
- 下一步动作仍然具体
- 没有更高优先级任务抢占

只要有一条不满足，
就不要强行恢复旧 active。

---

### Step 4 — Choose the branch

#### Branch A — Continue old active
如果旧 active 仍有效：
- 沿用旧 active
- 明确这一轮 `next_unit`
- 执行一个最小运行单元

#### Branch B — Reorg and pick a new active
如果旧 active 无效：
- 把当前状态收口写清
- 从 priority queue 中选出新的唯一 active
- 明确新的 `next_unit`

---

### Step 5 — Close the unit
无论走哪条 branch，
都要完成：
- 写结果
- 更新 `status.md`
- 更新 `PRIORITY-QUEUE.md`
- 更新当天 `memory/YYYY-MM-DD.md`

作用：
避免 recovery 本身又制造新的状态漂移。

---

### Step 6 — Schedule the next short follow-up
recovery 单元结束后，
默认仍应：
- 先获取当前本地时间
- 程序化计算 `now + 30s` 或 `+60s`
- 真正写入下一次 short follow-up cron

作用：
避免恢复一次后又再次断链。

---

## What recovery should not do

hourly recovery cron 不应：
- 默认重跑旧任务全文
- 无视 queue 直接继续旧 active
- 只留一句“已恢复”但不更新状态
- 恢复后不挂下一次 short follow-up

---

## v1 decision rule

**Recovery 不是为了忠于旧 active，而是为了尽快恢复“唯一 active + 下一步明确 + 短 follow-up 已挂上”的健康主链状态。**
