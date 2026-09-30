## 你好 👋

我是江裕文，计算机科学与技术专业在读，方向是 **Java 后端**。

喜欢把项目做完、做扎实——比起"跑起来了"，更在意"为什么这样设计、出问题会不会兜住"。

---

### 技术栈

**后端**：Java · Spring Boot · Spring Cloud Alibaba · MyBatis-Plus · Sa-Token
**数据与中间件**：MySQL · Redis · RocketMQ · Elasticsearch · PostgreSQL / pgvector
**AI 应用**：Spring AI · Function Calling · RAG · Agent 编排（LangGraph）
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

`Java 17` `Spring Boot 3` `Redis` `RocketMQ` `MySQL` `Docker`

#### [UniTrade](https://github.com/Evan7J/UniTrade) · 校园二手交易平台

校园闲置交易平台，含商品、订单、实时聊天和后台管理，并集成了基于大模型的 AI 助手模块。

- WebSocket 长连接实时聊天，消息先落库再推送，离线消息下次登录可见
- 商品搜索支持关键词与语义两路召回，向量服务异常时自动降级为纯关键词检索
- 基于 Spring AI 实现工具调用（商品搜索、分类查询、发布草稿生成）
- JWT 认证 + 拦截器校验，接口按读写维度分级限流

`Java 17` `Spring Boot 3` `Spring AI` `MySQL` `Redis` `Vue 3`

#### [rag-agent](https://github.com/Evan7J/rag-agent) · 文档问答

把 RAG 和 Function Calling 从底层到框架走了一遍的练习项目——从裸调 API 到基础 RAG 链，再到 Agent 化和服务化，最后不依赖框架手写一遍工具调用循环。

`Python` `LangChain` `LangGraph` `FAISS` `FastAPI`

---

### 最近在学

Spring AI Alibaba 的 Agent 编排实践、Java 并发底层原理、高可用架构设计。

---

### 联系我

📮 15297903669@163.com