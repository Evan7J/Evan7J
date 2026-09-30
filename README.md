## 你好 👋

我是江裕文，计算机科学与技术专业在读，方向是 **Java 后端**。

喜欢把项目做完、做扎实——比起"跑起来了"，更在意"为什么这样设计、出问题会不会兜住"。

---

### 技术栈

**后端**：Java · Spring Boot · Spring Cloud Alibaba · MyBatis-Plus · Sa-Token
**数据与中间件**：MySQL · Redis · RocketMQ · Elasticsearch · PostgreSQL / pgvector
**AI 应用**：Spring AI · Spring AI Alibaba Graph · Function Calling · RAG · Agent 编排（LangGraph）
**前端**：Vue 3 + Element Plus（能独立完成页面和联调，主力还是后端）
**工具**：Git · Docker Compose · Maven · Linux

---

### 项目

#### [LiveTix](https://github.com/Evan7J/LiveTix) · 演出选座秒杀平台

覆盖选座、下单、支付、超时关单全链路的票务系统，主要解决高并发下的库存一致性和座位并发冲突。

- 库存校验与扣减合并为单条 Lua 脚本在 Redis 内原子执行，500 并发压测零超卖
- 座位级细粒度锁（`SET NX EX`），避免整场一把大锁拖垮并发
- RocketMQ 异步下单削峰 + 延迟消息关单，配定时任务扫库兜底
- 双层缓存防护：布隆过滤器挡不存在的 ID、缓存空值防穿透、互斥锁防击穿

`Java 17` `Spring Boot 3.2` `Redis` `RocketMQ` `MySQL` `Docker`

#### [UniTrade](https://github.com/Evan7J/UniTrade) · 校园二手交易平台

校园闲置交易平台，含商品、订单、实时聊天和后台管理，核心是一个**能自己议价的 Agent**——替卖家谈，但拿不到卖家的底价。

- 议价链路用 Spring AI Alibaba Graph 做状态图编排：意图识别 → 报价计算 → 风控闸门 → 话术生成，节点不碰数据库，只做内存计算
- 报价全部由代码算，模型不参与任何数值；几何衰减保证单调递减，锚点抖动让底价无法被一行算式反解
- 越界出价不直接拒绝而是挂起转人工，放行由卖家确认并留痕；Agent 自主轮次上限 5 轮
- 四重防重（Redis `SET NX` / 轮次 CAS / 会话级串行化 / 数据库唯一索引），Redis 不可用时放行而不是报错
- 评测可复现：意图识别 130 条 Macro-F1 91.2%；对抗 70 条中 33 条构成越界，全部拦下、误放 0
- 模型分级路由 + 内容哈希缓存压成本，报价绝不缓存（依赖会话状态，命中旧值会击穿单调性）

`Java 21` `Spring Boot 3.4` `Spring AI` `Milvus` `MySQL` `Redis` `Vue 3`

#### [rag-agent](https://github.com/Evan7J/rag-agent) · 文档问答

把 RAG 和 Function Calling 从底层到框架走了一遍的练习项目——从裸调 API 到基础 RAG 链，再到 Agent 化和服务化，最后不依赖框架手写一遍工具调用循环。

`Python` `LangChain` `LangGraph` `FAISS` `FastAPI`

---

### 最近在学

Spring AI Alibaba 的 Agent 编排实践、Java 并发底层原理、高可用架构设计。

---

### 联系我

📮 15297903669@163.com