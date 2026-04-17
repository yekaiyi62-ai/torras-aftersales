# Team Contract

## 角色责任

| 角色 | 负责能力 | 输入 | 输出 | 上游 | 下游 |
|------|----------|------|------|------|------|
| 协调器 | 意图识别与路由 | 用户的任意输入 | 路由到对应成员 | 用户 | 各成员 |
| scenario-library | 场景方案匹配 | 产品+问题描述 | 超预期方案+话术 | 协调器 | 用户/case-writer |
| realtime-advisor | 实时话术生成 | 用户进线情况描述 | 分步话术+情感动作 | 协调器 | 用户/case-writer |
| case-writer | 案例撰写提炼 | 处理过程描述 | 结构化价值创造案例 | 协调器 | 用户提交 |

## 路由契约

| 用户意图 | 负责人 | 必读知识 | 必读记忆 | 输出 |
|---------|--------|----------|----------|------|
| "这个产品XX问题怎么处理能超预期" | scenario-library | scenario-db.md, product-knowledge.md | — | 方案+话术 |
| "用户进线了，情况是XX" | realtime-advisor | talk-patterns.md, emotion-handling.md | — | 分步话术 |
| "帮我把这个case写成案例" | case-writer | case-template.md | shared/case-archive.md | 结构化案例 |
| "这周的案例帮我整理" | case-writer | case-template.md | shared/case-archive.md | 周案例汇总 |
| "XX产品有什么卖点" | 协调器 | product-knowledge.md | — | 产品信息 |

## 记忆写入契约

| 角色 | 任务完成后必须写入 | 条件写入 | 禁止写入 |
|------|------------------|----------|----------|
| scenario-library | — | — | 不修改references |
| realtime-advisor | — | — | 不修改references |
| case-writer | shared/case-archive.md（追加新案例） | — | 不修改references |
| 协调器 | shared/session-log.md | — | — |

## 冲突处理
- 静态知识 `references/` 和 `members/*/references/` 不在日常使用中改写
- 用户积累的案例只追加写入 `shared/case-archive.md`
- session-log 保留最近7天
