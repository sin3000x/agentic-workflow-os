# Agentic Workflow OS - Design Spec

> Human-readable design narrative. Machine-readable execution contract: `spec_lock.md`.

## I. Project Information

| Item | Value |
| ---- | ----- |
| **Project Name** | Agentic Workflow OS |
| **Canvas Format** | PPT 16:9 (1280×720) |
| **Page Count** | 14 |
| **Design Style** | B) General Consulting + 科技商务风 |
| **Target Audience** | 内部团队 / 技术管理层 |
| **Use Case** | Agent 编排系统架构方案汇报，指导产品方向决策 |
| **Created Date** | 2026-05-26 |

---

## II. Canvas Specification

| Property | Value |
| -------- | ----- |
| **Format** | PPT 16:9 |
| **Dimensions** | 1280×720 |
| **viewBox** | `0 0 1280 720` |
| **Margins** | left/right 60px, top/bottom 50px |
| **Content Area** | 1160×620 |

---

## III. Visual Theme

### Theme Style

- **Style**: General Consulting + 科技商务风
- **Theme**: Light theme
- **Tone**: 专业、创新、清晰、可信赖

### Color Scheme

| Role | HEX | Purpose |
| ---- | --- | ------- |
| **Background** | `#FFFFFF` | 页面背景 |
| **Secondary bg** | `#F5F7FA` | 卡片/区块背景 |
| **Primary** | `#1565C0` | 标题装饰、关键区块、图标 |
| **Accent** | `#FF6F00` | 数据高亮、关键信息、行动项 |
| **Secondary accent** | `#1E88E5` | 次要强调、渐变过渡 |
| **Body text** | `#1D1D1F` | 正文文字 |
| **Secondary text** | `#6B7280` | 注释、辅助说明 |
| **Tertiary text** | `#9CA3AF` | 补充信息、页脚 |
| **Border/divider** | `#E5E7EB` | 卡片边框、分割线 |
| **Success** | `#2E7D32` | 正向指标 |
| **Warning** | `#C62828` | 风险/问题标记 |

### Gradient Scheme

```xml
<linearGradient id="titleGradient" x1="0%" y1="0%" x2="100%" y2="0%">
  <stop offset="0%" stop-color="#1565C0"/>
  <stop offset="100%" stop-color="#1E88E5"/>
</linearGradient>

<radialGradient id="bgDecor" cx="85%" cy="15%" r="40%">
  <stop offset="0%" stop-color="#1565C0" stop-opacity="0.06"/>
  <stop offset="100%" stop-color="#1565C0" stop-opacity="0"/>
</radialGradient>
```

---

## IV. Typography System

### Font Plan

**Typography direction**: Modern CJK sans — 清晰专业的无衬线主导，标题用衬线制造层次对比

| Role | Chinese | English | Fallback tail |
| ---- | ------- | ------- | ------------- |
| **Title** | `"Microsoft YaHei"`, `"PingFang SC"` | `Georgia` | `serif` |
| **Body** | `"Microsoft YaHei"`, `"PingFang SC"` | `Arial` | `sans-serif` |
| **Emphasis** | `"Microsoft YaHei"` | `Georgia` | `serif` |
| **Code** | — | `Consolas`, `"Courier New"` | `monospace` |

**Per-role font stacks**:

- Title: `Georgia, "Microsoft YaHei", "PingFang SC", serif`
- Body: `"Microsoft YaHei", "PingFang SC", Arial, sans-serif`
- Emphasis: `Georgia, "Microsoft YaHei", serif`
- Code: `Consolas, "Courier New", monospace`

### Font Size Hierarchy

**Baseline**: Body font size = 18px (Dense — 内容密集型报告)

| Purpose | Ratio | Size |
| ------- | ----- | ---- |
| Cover title | 3.3x | 60px |
| Chapter opener | 2x | 36px |
| Page title | 1.67x | 30px |
| Subtitle | 1.33x | 24px |
| **Body** | **1x** | **18px** |
| Annotation | 0.78x | 14px |
| Page number | 0.61x | 11px |

---

## V. Layout Principles

### Page Structure

- **Header area**: 50px — 页面标题 + 装饰线
- **Content area**: 580px — 主体内容
- **Footer area**: 40px — 页码 + 辅助信息

### Layout Pattern Library

| Pattern | Used On |
| ------- | ------- |
| Single column centered | P01 封面, P14 结束页 |
| Asymmetric split (3:7) | P02, P04 — 左侧核心概念 + 右侧展开 |
| Center-radiating | P06 — 核心组件辐射 |
| Three-column cards | P07, P10 — 方案对比 |
| Top-bottom split | P08 — 流程 + 说明 |
| Z-pattern / waterfall | P09 — Saga 三阶段 |
| Matrix grid | P12 — 技术选型表 |

### Spacing Specification

**Universal**:

| Element | Value |
| ------- | ----- |
| Safe margin | 60px (left/right), 50px (top/bottom) |
| Content block gap | 30px |
| Icon-text gap | 10px |

**Card-based layouts**:

| Element | Value |
| ------- | ----- |
| Card gap | 24px |
| Card padding | 24px |
| Card border radius | 12px |

---

## VI. Icon Usage Specification

### Source

- **Library**: `tabler-outline`
- **Stroke width**: 2
- **Style**: 线条风格，与科技商务主题搭配

### Recommended Icon List

| Purpose | Icon Path | Page |
| ------- | --------- | ---- |
| 网络/架构 | `tabler-outline/network` | P03, P05 |
| 机器人/Agent | `tabler-outline/robot` | P03, P04 |
| 用户/员工 | `tabler-outline/users` | P03, P08 |
| 盾牌/安全 | `tabler-outline/shield-check` | P06, P09 |
| 数据库 | `tabler-outline/database` | P05, P12 |
| 闪电/触发 | `tabler-outline/bolt` | P05, P07 |
| 图表/数据 | `tabler-outline/chart-bar` | P02, P05 |
| 层级/架构 | `tabler-outline/layers-intersect` | P05 |
| 锁/权限 | `tabler-outline/lock` | P06 |
| 检查/审计 | `tabler-outline/checklist` | P06, P09 |
| 消息/通信 | `tabler-outline/message-2` | P07, P10 |
| 时钟/SLA | `tabler-outline/clock` | P06 |
| 目标 | `tabler-outline/target` | P11, P13 |
| 服务器 | `tabler-outline/server` | P07, P12 |
| 拼图/模块 | `tabler-outline/puzzle` | P04 |
| 层级树 | `tabler-outline/hierarchy` | P08 |
| 警告 | `tabler-outline/alert-triangle` | P02 |
| 灯泡/洞察 | `tabler-outline/bulb` | P13 |
| 云/平台 | `tabler-outline/cloud` | P12 |
| 列表 | `tabler-outline/list-check` | P11 |
| 大脑 | `tabler-outline/brain` | P04 |
| Git分支 | `tabler-outline/git-branch` | P10 |

---

## VII. Visualization Reference List

Catalog read: 71 templates

| Page | Template | Path | Summary-quote (verbatim) | Usage |
| ---- | -------- | ---- | ------------------------ | ----- |
| P05 | layered_architecture | `templates/charts/layered_architecture.svg` | "Pick for 3-4 horizontal architecture layers (presentation/service/data), 2-4 module cards per layer, each card = title + bullets — fits 'Feature X contains 3 pillars each with sub-modules'." | 三层架构（事件层/编排层/执行层）展示 |
| P06 | hub_spoke | `templates/charts/hub_spoke.svg` | "Pick for 1 core capability + 4-8 surrounding capabilities (platform/ecosystem); each spoke = title or title + 1-2 line description." | 中台编排层五大核心组件辐射图 |
| P11 | numbered_steps | `templates/charts/numbered_steps.svg` | "Pick for 3-6 horizontal sequential steps with numeric emphasis — how-it-works section, getting-started guide, methodology stages." | 三阶段实施路线图 |
| P12 | basic_table | `templates/charts/basic_table.svg` | "Pick for plain tabular text/number grid, 3-8 columns. Skip if cells need visual bars (use consulting_table) or qualitative scoring (use harvey_balls_table)." | 技术选型对照表 |

**Runners-up considered**:

- `process_flow` | rejected for P05: 三层架构强调层级关系而非线性流程，layered_architecture 更贴合
- `icon_grid` | rejected for P06: 五大组件有明确的中心-辐射关系，不是平行并列
- `chevron_process` | rejected for P11: 三阶段有时间递进但重点是阶段内容而非箭头连接
- `roadmap_vertical` | rejected for P11: 水平展示更适合三阶段的并列对比

---

## VIII. Image Resource List

无图片 — 本 deck 以架构图、流程图、对比表为主，通过 SVG 原生绘制充分表达。

---

## IX. Content Outline

### Part 1: 开场与背景

#### Slide 01 - 封面

- **Layout**: Single column centered
- **Title**: Agentic Workflow OS
- **Subtitle**: 中台 Agent 编排架构 — 从数据分析到业务流程革新
- **Info**: 研究总结 | 2026.05

#### Slide 02 - 背景与核心问题

- **Layout**: Asymmetric split (3:7)
- **Title**: 我们的构想与核心问题
- **Content**:
  - 左侧：核心构想图示（中台Agent → 员工Agent → Human）
  - 右侧：
    - 构想：中台Agent通过数据分析发现任务 → 下发给员工Agent → 自主完成/升级人工 → 反馈结果
    - 三个核心问题：架构全流程？如何下发任务？如何与异构Agent交互？

### Part 2: 业界洞察

#### Slide 03 - 业界共识：Supervisor-Worker 架构

- **Layout**: Top-bottom split
- **Title**: 业界收敛方向：Supervisor-Worker 架构
- **Content**:
  - 上部：架构示意（Supervisor → Worker Agents → Humans）
  - 下部：四家LLM一致认同的核心范式
    - "Supervisor / Orchestrator Agent + Human-owned Worker Agents + Workflow Runtime"
    - 重点不在单个Agent多聪明，而在编排

#### Slide 04 - 中台 Agent 的本质

- **Layout**: Asymmetric split (3:7)
- **Title**: 中台 Agent ≠ 大脑，= 操作系统
- **Content**:
  - 左侧：核心洞察 — LLM 只是 decision component
  - 右侧：中台本质组成
    - Workflow Engine + State Machine
    - Event Bus + Policy Layer
    - Human Escalation + Audit Log
    - Agent Registry
  - 关键反思：生产里问题不在 prompt，在 orchestration

### Part 3: 架构设计

#### Slide 05 - 三层架构总览

- **Layout**: layered_architecture
- **Visualization**: layered_architecture
- **Title**: 企业级 Agent Teamwork 三层架构
- **Content**:
  - Layer 1 — Event & Signal Layer：数据分析/KPI监控/异常检测/风险识别
  - Layer 2 — Orchestrator / Supervisor：任务规划/策略引擎/工作流运行时/SLA跟踪/升级
  - Layer 3 — Worker Agents + Humans：Sales/Support/Finance Agent → Human

#### Slide 06 - 编排层五大核心组件

- **Layout**: Center-radiating (hub_spoke)
- **Visualization**: hub_spoke
- **Title**: Orchestrator 核心组件
- **Content**:
  - 中心：Orchestrator Agent
  - 五个辐射节点：
    - A. Task Planner — 任务规划（角色识别/并行判断/审批需求）
    - B. Workflow State Machine — 状态机（CREATED→ASSIGNED→IN_PROGRESS→COMPLETED）
    - C. Agent Registry — 注册中心（能力/SLA/权限/endpoint）
    - D. Policy Engine — 策略层（金额阈值/PII保护/VIP响应）
    - E. Human Escalation — 人工升级（80%自主 + 关键节点确认）

#### Slide 07 - 任务下发机制

- **Layout**: Three-column comparison
- **Title**: 中台如何下发任务
- **Content**:
  - 方案A — Task Queue/Workflow（最现实）：结构化JSON任务 → Agent拉取/执行/反馈
  - 方案B — Agent-to-Agent Protocol（未来）：A2A/MCP 标准协议，discover/negotiate/handoff
  - 现实选择：Workflow + API + Queue，不是自由Agent对话

#### Slide 08 - 人机协同设计

- **Layout**: Top-bottom split
- **Title**: Human-in-the-Loop：不是 Fallback，是 Primary Design
- **Content**:
  - 上部：升级触发条件（置信度/不可逆操作/链条衰减/合规硬约束）
  - 下部：检查点持久化流程
    - 员工Agent检测需人工 → 中台挂起+快照 → 推送审核卡片 → 人类确认 → 恢复执行
  - 闭环优化：语义缓存避免重复升级 + 主动学习持续强化

#### Slide 09 - 分布式事务一致性

- **Layout**: Z-pattern / waterfall
- **Title**: Saga 事务模式 — 保障多Agent数据一致性
- **Content**:
  - 三阶段设计：
    - 可补偿交易（Compensable）：员工Agent执行 + 注册补偿动作
    - 枢轴交易（Pivot）：人类确认 = 不归路点
    - 可重试交易（Retryable）：幂等重试直到成功
  - SagaLLM：LLM自动推导事务依赖树、生成补偿载荷

### Part 4: 通信与实施

#### Slide 10 - 通信协议对比

- **Layout**: Three-column comparison
- **Title**: 异构 Agent 交互协议
- **Content**:
  - A2A（水平层）：跨平台Agent互联，任务委托/状态同步/结果返回
  - MCP（垂直层）：Agent与本地工具/数据源打通
  - 传统方式：消息队列 + 共享状态 + API Gateway
  - 交互模式：Hub-and-Spoke（中心辐射，避免点对点混乱）

#### Slide 11 - 实施路线图

- **Layout**: numbered_steps
- **Visualization**: numbered_steps
- **Title**: 三阶段演进路径
- **Content**:
  - 第一阶段（核心）：Workflow State Machine + Human Escalation + Audit & Replay + Agent Registry
  - 第二阶段（治理）：Policy Engine + Memory & Experience Layer
  - 第三阶段（协议）：Agent-to-Agent Protocol
  - 原则：从中心化开始，逐步引入混合通信

#### Slide 12 - 技术选型参考

- **Layout**: basic_table
- **Visualization**: basic_table
- **Title**: 业界技术选型组合
- **Content**:
  - 表格：层 → 常见技术
    - Workflow Runtime: Temporal / Cadence / Airflow
    - Agent Graph: LangGraph
    - Agent Team: CrewAI / AutoGen
    - Human Approval: BPMN / Camunda
    - Queue: Kafka / SQS
    - Policy: OPA
    - Observability: LangSmith / OpenTelemetry
    - Memory: Postgres + Vector DB
    - Tool Access: MCP
  - 推荐组合：Temporal + LangGraph

### Part 5: 总结

#### Slide 13 - 关键洞察与行动建议

- **Layout**: Asymmetric split (4:6)
- **Title**: 关键洞察与下一步
- **Content**:
  - 左侧 — 三大洞察：
    - 企业最终会 Workflow 化，而非 Swarm 化
    - 生产里稳定的是 2-3 Agent，不是 100 个自由协作
    - Human-in-the-loop 是 primary design，不是 fallback
  - 右侧 — 行动建议：
    - 先做 Workflow State Machine（核心中的核心）
    - 从小团队试点（3-5 员工Agent）
    - 定义清晰角色和 escalation 规则
    - 别一开始做"智能对话网络"

#### Slide 14 - 结束页

- **Layout**: Single column centered
- **Title**: Thank You
- **Subtitle**: 从数据分析 Agent 到业务流程操作系统
- **Info**: Q&A

---

## X. Speaker Notes Requirements

- **Filename**: match SVG name (e.g., `01_cover.md`)
- **Total duration**: 20-25 minutes
- **Notes style**: Professional conversational — 结论先行，数据支撑
- **Purpose**: Inform + Persuade（传达研究发现，推动架构决策）

---

## XI. Technical Constraints Reminder

### SVG Generation Must Follow:

1. viewBox: `0 0 1280 720`
2. Background uses `<rect>` elements
3. Text wrapping uses `<tspan>` (`<foreignObject>` FORBIDDEN)
4. Transparency uses `fill-opacity` / `stroke-opacity`; `rgba()` FORBIDDEN
5. FORBIDDEN: `mask`, `<style>`, `class`, `foreignObject`
6. FORBIDDEN: `textPath`, `animate*`, `script`
7. Text characters: raw Unicode; HTML named entities FORBIDDEN; XML reserved chars escaped
8. `marker-start` / `marker-end` conditionally allowed with `<marker>` in `<defs>`
9. `clipPath` conditionally allowed only on `<image>` elements

### PPT Compatibility Rules:

- `<g opacity="...">` FORBIDDEN; set on each child individually
- Image transparency uses overlay mask layer
- Inline styles only; external CSS and `@font-face` FORBIDDEN
