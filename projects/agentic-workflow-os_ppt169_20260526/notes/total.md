# Agentic Workflow OS — Speaker Notes

## 01_封面

大家好，今天我来分享一个关于 Agent Teamwork 如何革新业务操作流程的研究总结。我们的出发点是一个数据分析 Agent，但我们想更进一步——通过中台 Agent 编排，真正改变业务的作业流程。这份报告综合了 ChatGPT、Claude、Grok、Gemini 四家 LLM 的深度分析。

---

## 02_背景与核心问题

我们的核心构想是：一个中台 Agent 通过数据分析和异常监控发现需要处理的任务，然后把任务下发给不同员工的 Agent，这些 Agent 自主完成任务，中途可能升级到员工手工处理确认，最后反馈结果给中台。

我们不关注每个员工 Agent 的内部实现，我们关注的是中台 Agent 本身：架构全流程是什么样的？如何下发任务？如何与异构 Agent 交互？这三个问题是今天的核心。

---

## 03_业界共识

四家 LLM 给出了高度一致的结论：业界已经收敛到 Supervisor-Worker 架构模式。核心范式是 "Supervisor/Orchestrator Agent + Human-owned Worker Agents + Workflow Runtime"。

重点已经不是每个 Agent 多聪明，而是编排——任务如何拆解、状态如何流转、谁负责权限、谁负责升级、谁负责审计。这个方向已经有大量企业在生产环境中验证。

---

## 04_中台本质

这是一个关键洞察：中台 Agent 不等于大脑，等于操作系统。

很多 demo 里 Supervisor 自己思考一切，但生产环境中这会导致不稳定、无法审计、难以 debug。成熟系统收敛成：中台 = Workflow Runtime + Policy Engine。LLM 只是其中一个决策组件。

真正的核心是 Workflow Engine、State Machine、Event Bus、Policy Layer、Human Escalation、Audit Log 和 Agent Registry 这些基础设施。企业更像是在做 BPM + Event Bus + Workflow Engine + AI Decision Layer，而不是聊天机器人。

---

## 05_三层架构

推荐的企业级架构分三层。

第一层是事件与信号层，负责数据分析、KPI 监控、异常检测。数据来源包括 ERP、CRM、数据仓库、日志等。这一层更多是 CEP、规则引擎和 ML 异常检测，不一定是 Agent。

第二层是编排层，也就是我们最关注的中台 Agent。它包含任务规划、策略引擎、工作流运行时、SLA 跟踪和升级机制。

第三层是执行层，各业务域的 Worker Agent 加上人类员工。Agent 是执行者，中台是操作系统。

---

## 06_编排层组件

编排层有五大核心组件。

Task Planner 负责识别需要哪些角色、是否并行、是否需要审批。Workflow State Machine 是核心中的核心，任务状态必须是 CREATED → ASSIGNED → IN_PROGRESS → COMPLETED，可恢复、可追踪、可审计。Agent Registry 维护各 Agent 的能力声明，包括 Agent Card 机制——每个 Agent 发布 JSON 格式的能力描述，实现无硬编码的动态路由。Policy Engine 处理权限、审批、合规。Human Escalation 确保关键节点有人工确认。

---

## 07_任务下发

中台下发任务有两种主要方案。

方案 A 是 Task Queue/Workflow 模式，这是目前最现实的选择。中台不直接聊天，而是发结构化任务——包含 task_id、目标、约束条件、期望输出。员工 Agent 拉取任务、执行、更新状态、提交结果。这本质上就是 Jira/Temporal/BPMN，只是执行者变成了 Agent。

方案 B 是 Agent-to-Agent Protocol，比如 Google A2A。它定义了 Agent 间如何发现能力、协商任务、传递上下文。A2A 基于 HTTP/SSE/JSON-RPC 2.0，已有 150+ 组织支持。但目前还比较早期，生产里稳定的仍然是 Workflow + API + Queue。

---

## 08_人机协同

Human-in-the-Loop 不是 fallback，是 primary design。Agent 自主完成 80%，关键节点人工确认，这才是企业现实。

升级触发有四个维度：置信度低于阈值、不可逆操作（资金变动、数据删除）、多 Agent 链条不确定性累积、以及合规硬约束。

技术实现上，当需要人工介入时，系统创建检查点快照、持久化状态、推送审核卡片给员工，员工确认后通过 Webhook 回调恢复执行。关键是要有语义缓存避免重复升级，以及主动学习持续优化升级阈值。

---

## 09_分布式事务

当多个 Agent 协同处理涉及多系统的任务时，需要 Saga 事务模式保障数据一致性。

分三个阶段：可补偿交易阶段，员工 Agent 执行并注册补偿动作；枢轴交易阶段，人类确认就是不归路点，一旦通过就不能回滚前面的操作；可重试交易阶段，后续步骤通过幂等重试确保最终一致。

如果人工拒绝，中台启动补偿流程回滚已提交的修改。SagaLLM 等新研究还在探索用 LLM 自动推导事务依赖和生成补偿载荷。

---

## 10_通信协议

异构 Agent 交互主要靠三类协议互补。

A2A 是水平层，负责跨平台 Agent 互联。它支持 Agent Card 能力发现、任务委托、状态同步、结果返回。任务状态机：submitted → working → input-required → completed/failed。

MCP 是垂直层，负责单个 Agent 与本地工具和数据源的打通。比如销售 Agent 通过 MCP 调用 ERP 系统。

传统方式——消息队列加共享状态加 API Gateway——仍然是生产中最稳定的选择。交互模式推荐 Hub-and-Spoke，所有通信通过中台，避免点对点混乱。

---

## 11_实施路线图

建议分三阶段演进。

第一阶段做核心：Workflow State Machine 是核心中的核心，加上 Human Escalation、Audit & Replay 和 Agent Registry。这四个能力决定了系统能不能上线。

第二阶段做治理：Policy Engine 处理权限审批合规，Memory & Experience Layer 让系统学习哪种任务容易失败、哪个 Agent 更擅长。

第三阶段才考虑 Agent-to-Agent Protocol。别一开始做智能对话网络。从中心化开始，逐步引入混合通信。

---

## 12_技术选型

业界正在形成的技术组合：Temporal 或 Cadence 做 Workflow Runtime，LangGraph 做 Agent Graph，CrewAI 或 AutoGen 做 Agent Team，BPMN/Camunda 做 Human Approval，Kafka/SQS 做消息队列，OPA 做策略引擎，LangSmith/OpenTelemetry 做可观测性。

推荐组合是 Temporal + LangGraph。Temporal 负责 durable execution，LangGraph 负责 agent graph 和 state 管理。此外 OpenAI Agents SDK 和 Google ADK 也是值得关注的新选项。

---

## 13_关键洞察

三个最重要的洞察：第一，企业最终会 Workflow 化而非 Swarm 化——生产里大量系统最后退回了 2-3 个 Agent；第二，稳定的模式是 Planner → Executor → Reviewer，不是 100 个 Agent 自由协作；第三，Human-in-the-Loop 是 primary design，不是 fallback。

行动建议：先做 Workflow State Machine，从小团队试点 3-5 个员工 Agent，定义清晰的角色和 escalation 规则，别一开始做智能对话网络。保持结构化日志和可观测性，这是出问题时的命脉。

---

## 14_结束页

感谢大家的时间。从一个数据分析 Agent 出发，我们看到了一条通往业务流程操作系统的路径。核心不在于 Agent 多聪明，而在于编排多可靠。欢迎提问。
