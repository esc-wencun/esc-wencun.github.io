# esc-wencun

在学 AI 开发。这个主页目前主要展示一项实践成果：用 AI coding 的方式做工程——把需求写成可验证的 spec，让 AI 产出可验收的代码。

## 🤖 AI 实践项目：[ai-dev-lab](https://github.com/esc-wencun/ai-dev-lab)

> AI 开发学习工作区：以若依官方 Java 版为契约基准，用 Go / Python 两种语言复刻服务端，并已开展跨端增量开发

**[ai-dev-lab](https://github.com/esc-wencun/ai-dev-lab)** 是一套管理系统前后端学习工作区：以开源项目 [RuoYi-Vue](https://github.com/yangzongzhuan/RuoYi-Vue)（Spring Boot，若依官方 Java 版）为接口契约基准，分别用 **Go（Gin + GORM）** 和 **Python（FastAPI + SQLAlchemy 2.0 async）** 从零复刻出接口与其完全兼容的服务端，共用同一个 Vue 3 前端、**切换后端前端零适配**；前端与 Java 基准版也可按学习需要增量演进。

**这个项目想证明的：**

- 📋 **Spec 驱动开发**：每个模块动工前，先通读 Java 基准版的 Controller / ServiceImpl / Mapper XML，把端点路径、参数、返回 JSON 结构逐条核实写成 spec 任务书（含 API 清单、任务分解、验收 checklist），再按 spec 实现、按 checklist 验收——共 30+ 份 spec 文档全部在仓库中可查。
- 🔁 **复刻之外的跨端增量开发**：已实践"一份契约主文档管理四端改动"的模式——如平台标识模块（`GET /getPlatformInfo` 返回语言/版本/功能开关），Java / Go / Python 三版各自实现、前端数据监控等服务端特有页据此自动降级提示，一次改动四端对齐。
- 🤝 **与 AI 协作的工程纪律**：全部代码由 AI（Claude Code）编写，人工负责需求界定、spec 审核与最终验收；验收以数据库实际数据、前端实际调用与单元测试为准，不凭 AI 的自述下结论。产出：两套可运行的复刻后端（三版合计 150+ 端点）、与 Java 版 BCrypt / JWT / Redis 会话互相兼容、55+ 单元测试全绿。

**技术栈**：Spring Boot（契约基准） / Gin + GORM / FastAPI + SQLAlchemy / Vue 3 + Element Plus / Redis / MySQL / Docker

**开发流程细节**见仓库根目录的 [AGENTS.md](https://github.com/esc-wencun/ai-dev-lab/blob/main/AGENTS.md)（AI 编码规范与兼容契约）与 [readme.md](https://github.com/esc-wencun/ai-dev-lab#readme)（三版进度对照表）。

## 📚 AI 学习路线（进行中，由浅入深，有产出即上传）

1. **LLM 应用开发**（进行中）——模型 API 调用、提示词工程、结构化输出与 Function Calling
2. **RAG（检索增强生成）**——Embedding 与向量库、知识库问答、检索质量评估
3. **Agent 智能体**——流程编排、MCP / 工具调用、多智能体协作

其中 **AI Coding 工程化**（Claude Code / spec 驱动开发）已通过 ai-dev-lab 完整实践，见上。

## 🎮 小玩意

- [是男人就下一百层](https://esc-wencun.github.io/godown/index.html)
