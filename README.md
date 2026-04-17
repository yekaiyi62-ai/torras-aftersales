# 图拉斯售后价值创造系统

这是一个 Claude Code Skill，用于支持图拉斯天猫售后团队在日常接待中做三件事：

- 实时生成客服可直接复制的话术。
- 查询产品售后场景的 SOP 与红线内超预期处理方案。
- 把优秀售后处理过程提炼成价值创造案例。

核心目标：帮助售后客服从“执行 SOP”升级为“识别用户真实场景并创造服务价值”，沉淀可复用案例，服务晋升和团队复盘。

## 适用场景

### 1. 用户进线，需要马上回复

输入：

```text
用户进线：刚买的磁吸充电宝吸不住，明天要出差，对品牌很失望，坚持要退货退款。
```

Skill 会输出：

- 场景判断
- 情绪级别
- 人物情境识别
- 可直接复制的话术
- 红线内超预期动作
- 避坑提醒
- 案例价值判断

### 2. 提前查询某个问题怎么处理

输入：

```text
磁吸充电宝吸不住，超过7天不能退，红线内有什么超预期处理方案？
```

Skill 会输出：

- 常规 SOP
- 产品层面的处理
- 情绪层面的处理
- 增值层面的处理
- 推荐话术
- 可写案例的角度

### 3. 把一次处理写成价值创造案例

输入：

```text
帮我把今天这个充电宝售后写成价值创造案例：用户急用出差，坚持退款，我在不能突破红线的情况下安抚情绪、加急换新并持续跟进。
```

Skill 会按案例模板输出：

- 用户遇到的问题
- 常规流程会怎么做
- 我做了什么不一样的事
- 用户结果和反馈
- 价值创造总结

### 4. 周案例汇总

输入：

```text
帮我整理这周的案例
```

Skill 会从案例归档中整理周报，方便团队复盘和提交。

## 设计理念

### 方案固定，场景无限

售后动作通常是固定的：

- 退款
- 退货
- 换货
- 补发
- 排查
- 反馈

真正的价值创造不是突破政策，也不是给用户额外承诺，而是读懂用户背后的真实场景，再把现有方案用更合适的节奏、细节、温度和闭环组合起来。

例子：

- 用户不是单纯要退货，而是明天出差急用。
- 用户不是单纯不满意，而是老用户信任受损。
- 用户不是单纯换壳，而是宝妈担心孩子摔坏平板。
- 用户不是单纯咨询操作，而是帮父母处理，步骤需要更简单。

## 售后政策红线

所有回复和方案必须遵守红线：

- 换货只能同款、同色、同型号。
- 退货退款仅限签收后 7 天内。
- 同一订单 1-2 年内只能换一次。
- 不能承诺超出当前权限的赔偿、升级款、特殊退款。
- 不能主动邀请好评、收藏、推荐。

红线内的超预期包括：

- 节奏创新：加急处理、先发后退、减少空窗期。
- 细节创新：免运费、上门取件、步骤写清楚、灵活时间。
- 温度创新：先承认情绪，再解决问题。
- 闭环创新：记录反馈、持续跟进、减少用户重复解释。

## Skill 结构

```text
torras-aftersales/
├── SKILL.md
├── README.md
├── .gitignore
├── references/
│   ├── product-knowledge.md
│   ├── knowledge-index.md
│   ├── team-contract.md
│   ├── capability-coverage.md
│   └── distillation-plan.md
├── members/
│   ├── realtime-advisor/
│   │   ├── SKILL.md
│   │   └── references/
│   │       ├── talk-patterns.md
│   │       └── emotion-handling.md
│   ├── scenario-library/
│   │   ├── SKILL.md
│   │   └── references/
│   │       └── scenario-db.md
│   └── case-writer/
│       ├── SKILL.md
│       └── references/
│           └── case-template.md
└── shared/
    ├── case-archive.md
    ├── user-profile.md
    ├── progress.md
    └── baseline.md
```

## 模块说明

### 主入口：SKILL.md

负责识别用户意图，并路由到对应能力单元：

- 实时接待
- 方案查询
- 案例撰写
- 周案例汇总
- 产品知识查询

### 实时话术顾问：members/realtime-advisor/

用于用户正在进线时快速输出话术。

能力包括：

- 情绪判断
- 人物情境识别
- 行为场景识别
- 红线检查
- 可复制回复
- 避坑提醒

### 场景方案库：members/scenario-library/

用于提前查询“产品 × 问题”的处理方式。

覆盖方向包括：

- 手机壳
- 手机膜
- 充电宝
- 充电器
- 数据线
- 散热器
- 通用售后场景
- 人物情境关怀

### 案例提炼师：members/case-writer/

用于把一次售后处理写成价值创造案例。

重点检查：

- 是否有不一样的动作
- 是否不是单纯 SOP
- 是否有用户反馈
- 是否有可量化或可证明的结果
- 是否能被团队复用

### 共享数据：shared/

用于沉淀团队数据：

- `case-archive.md`：案例归档
- `user-profile.md`：客服画像与目标
- `progress.md`：进度追踪
- `baseline.md`：能力摸底

## 安装方式

### 方法一：一键安装（推荐）

如果另一台电脑已经安装 Node.js/npm，可以像安装女娲 Skill 一样使用 `npx skills add`：

```bash
npx skills add yekaiyi62-ai/torras-aftersales -g -a claude-code
```

也可以使用完整 GitHub 地址：

```bash
npx skills add https://github.com/yekaiyi62-ai/torras-aftersales -g -a claude-code
```

参数说明：

- `-g`：安装到全局 skills 目录，所有 Claude Code 项目都能使用。
- `-a claude-code`：指定安装给 Claude Code。

安装后检查：

```bash
ls ~/.claude/skills/torras-aftersales
```

应能看到：

```text
SKILL.md
README.md
members
references
shared
```

更新 Skill：

```bash
npx skills update
```

### 方法二：从 GitHub 下载

1. 在 GitHub 上下载或 clone 本仓库。
2. 确保文件夹名为：

```text
torras-aftersales
```

3. 将整个文件夹放到 Claude Code 的 skills 目录中。
4. 打开 Claude Code，新建对话后直接使用。

### 方法三：GitHub Desktop 同步

1. 在 GitHub Desktop 中 clone 这个仓库。
2. 本地仓库目录就是完整 Skill 目录。
3. 将该目录复制或同步到 Claude Code skills 目录。
4. 后续可通过 GitHub Desktop 拉取更新。

## 使用方式

在 Claude Code 对话中直接描述需求即可。

推荐触发方式：

```text
使用 torras-aftersales。用户进线：磁吸充电宝吸不住，用户明天出差，很生气，坚持退款，怎么回？
```

或者：

```text
使用图拉斯售后 Skill。帮我查一下手机膜白边怎么红线内超预期处理。
```

或者：

```text
使用 torras-aftersales。帮我把今天这个售后处理写成价值创造案例。
```

## 输出风格

实时话术默认输出：

```text
🎯 场景判断：
😊 情绪级别：
👤 人物情境：

📝 推荐回复（可直接复制）：
---
...
---

🌟 超预期动作（红线内）：
...

💎 价值创造点：
...

⚠️ 避坑提醒：
...
```

## 维护建议

- 新增产品知识：更新 `references/product-knowledge.md`。
- 新增售后场景：更新 `members/scenario-library/references/scenario-db.md`。
- 新增话术方法：更新 `members/realtime-advisor/references/talk-patterns.md`。
- 新增情绪处理方法：更新 `members/realtime-advisor/references/emotion-handling.md`。
- 新增案例：更新 `shared/case-archive.md`。
- 调整总流程：更新 `SKILL.md`。

## 上传 GitHub 前检查

应包含：

```text
SKILL.md
README.md
.gitignore
members/
references/
shared/
```

不应包含：

```text
.DS_Store
其它 skill
旧版 .codex/agents
无关项目
本地缓存
```

## 当前版本

- 创建日期：2026-04-17
- 项目类型：Claude Code Skill
- 适用团队：图拉斯天猫售后
- 核心目标：红线内价值创造、实时接待辅助、案例沉淀
