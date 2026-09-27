# esc-wencun

在学 AI 开发。这个主页目前主要展示一项实践成果：**如何用工程纪律驱动 AI 做真实的工程**——不是"AI 生成了代码"，而是人制定纪律、AI 执行、数据验收。

## 🤖 AI 实践项目：[ai-dev-lab](https://github.com/esc-wencun/ai-dev-lab)

> 用 spec 任务书、checklist 验收纪律和数据实证，驱动 AI（Claude Code）跨四个技术栈交付一套接口一致的管理系统——包括 AI 在哪跌倒、靠什么机制抓住的，全部过程文档在仓库可查。

载体：源于开源项目若依（RuoYi）——以官方 Java 版为接口契约基准，用 Go 和 Python 从零复刻出接口完全兼容的服务端（切换后端前端零适配）；前端有 Vue 3 与 React 两个实现（React 版功能等价复刻 Vue3、服务三版后端），Java 基准版与前端均按学习需要增量演进（如跨四端的平台标识模块）。

**实践主线（每个点在仓库有第一手记录可验证）：**

1. **方法论——spec 驱动，验收以数据为准**：动工前先对着 Java 基准源码逐条核实端点契约写成 spec（不凭 AI 记忆）；模块配 spec/tasks/checklist 三件套；AI 说"做完了"不算数，要扫数据库实际数据、抓前端实际调用、跑测试。量化：57 份 spec 文档、491 项已勾验收记录、178 个单元测试全绿（Python 55 + Go 123）。

2. **AI 在哪跌倒，我怎么抓住的**（差异化重点，可讲故事）：
   - AI 凭记忆写错数据库列名 → 端到端暴露 → "契约先行、不凭记忆"成为动工检查单条款
   - AI 的 checklist 出现"状态头标完成、勾选框全空"的虚勾 → 人工核对发现 → 立了 checklist 纪律五条，按新纪律扫库复查又抓出两处漏实现和一个"暂停任务永远无法启用"的真 bug
   - AI 初版方案"缓存解析失败就删键"会砸掉共享 Redis 里 Java 侧的登录会话 → 复审抓住 → 改为永不删除的保守策略
   - 异步日志落库失败但接口返回 200，curl 测不出 → 浏览器级验收抓到 → 沉淀"别只看接口响应"的排查方法论

3. **跨技术栈一致性**：三版后端严守同一套响应信封/字段命名/Redis 键前缀/密码哈希兼容契约；无法对齐的行为全部登记进 deviations.md（20 条），规则是"影响前端契约的差异一律不允许"；跨四端增量功能用一份契约主文档管理，前端按能力开关降级而非硬编码语言判断。

4. **AI 操作 GitHub 本身**：分支、提交信息、PR 均由 AI 完成（提交元数据 `Co-Authored-By` 联署可查），人工只做审查与合并——协作流程本身也是实践的一部分。

**技术栈**：Spring Boot（契约基准） / Gin + GORM / FastAPI + SQLAlchemy / Vue 3 + Element Plus / React 19 + TypeScript + Ant Design 5 / Redis / MySQL / Docker

**入口**：仓库 [readme](https://github.com/esc-wencun/ai-dev-lab#readme)（叙事主线 + 进度与技术栈对照）、[AGENTS.md](https://github.com/esc-wencun/ai-dev-lab/blob/main/AGENTS.md)（AI 编码规范权威源）；跌倒案例的第一手记录在仓库 specs 里可查（如 [GO 11.0.0](https://github.com/esc-wencun/ai-dev-lab/tree/main/RuoYi-Vue-GO/specs/11.0.0-代码生成器/spec.md)、[spec-09](https://github.com/esc-wencun/ai-dev-lab/blob/main/RuoYi-Vue-FastApi/specs/spec-09-job.md)）。

## 📚 AI 学习路线（进行中，由浅入深，有产出即上传）

1. **LLM 应用开发**（进行中）——模型 API 调用、提示词工程、结构化输出与 Function Calling / Tool Use
2. **RAG（检索增强生成）**——Embedding 与向量库、知识库问答、检索质量评估
3. **Agent 智能体**——流程编排、MCP / 工具调用、多智能体协作、企业智能体工程化
4. **Java 生态 AI 集成**——LangChain4j / Spring AI（陆续补充）

其中 **AI Coding 工程化**（Claude Code / spec 驱动开发）已通过 ai-dev-lab 完整实践，见上。

## 🎮 小玩意

- [是男人就下一百层](https://esc-wencun.github.io/godown/index.html) —— 基于 LayaAir 引擎的 HTML5 小游戏，2023 年部署于本站（游戏的构建发布包，非工程源码）
