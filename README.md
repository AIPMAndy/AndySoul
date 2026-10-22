<div align="center">

# AndySoul

**一份放进项目根目录的规则文件，让 Claude Code、Codex、Cursor 少犯常见错误。**

先想清楚再写代码 · 只改该改的地方 · 每一步都验收 · 不确定就直说

[![License: MIT](https://img.shields.io/badge/License-MIT-111827?style=flat-square)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/AIPMAndy/AndySoul?style=flat-square&color=111827)](https://github.com/AIPMAndy/AndySoul/stargazers)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-111827?style=flat-square)](https://github.com/AIPMAndy/AndySoul/pulls)

简体中文 · [English](./README_EN.md) · [模板](./TEMPLATES.md) · [前后对比示例](./EXAMPLES.md)

</div>

**在找 CLAUDE.md / AGENTS.md 规则模板？** AndySoul 是一份可以直接放进项目根目录的规则文件。Claude Code 读 `CLAUDE.md`，Codex 读 `AGENTS.md`，Cursor 读 `.cursorrules`，同一份内容下载成对应的文件名就能用。

*English: a drop-in CLAUDE.md / AGENTS.md / .cursorrules rules template that helps Claude Code, Codex and Cursor make fewer mistakes.*

## 30 秒装上

```bash
# Claude Code
curl -o CLAUDE.md https://raw.githubusercontent.com/AIPMAndy/AndySoul/main/CLAUDE.md

# OpenAI Codex（读取 AGENTS.md）
curl -o AGENTS.md https://raw.githubusercontent.com/AIPMAndy/AndySoul/main/CLAUDE.md

# Cursor
curl -o .cursorrules https://raw.githubusercontent.com/AIPMAndy/AndySoul/main/CLAUDE.md
```

其他 Agent：把 [`CLAUDE.md`](./CLAUDE.md) 的内容贴进它的系统提示词或项目指令文件。

## 装上之后有什么不同

**之前**（常见的 LLM 行为）：

```
用户："给登录表单添加验证"
AI：[添加验证 + 重构表单 + 更新样式 + 添加没用到的错误状态]
```

**之后**（用 AndySoul）：

```
用户："给登录表单添加验证"
AI："我会添加邮箱/密码验证。计划：
1. 添加验证规则 → 用无效输入测试
2. 显示错误消息 → 测试错误显示
3. 无效时阻止提交 → 测试提交拦截

空字符串这类边界情况要一起处理吗，还是只做基本格式验证？"
[只改请求的部分，沿用现有代码风格]
```

[EXAMPLES.md](./EXAMPLES.md) 里有 5 组详细的前后对比：加登录、修接口超时、数据分析、重构等。

## 规则从哪来

1. **9 条认知公理**：熵增、还原论、概率与不确定性等
2. **马斯克 5 步工程法**：质疑 → 删除 → 简化 → 加速 → 自动化
3. **Karpathy 4 条编码原则**：先想再写、简单优先、外科手术式修改、目标驱动执行

落到 Agent 身上，就是这几条：

- **先质疑需求**，确认真要做再动手
- **只改必须改的**，每一行改动都能对应到你的要求，不顺手"优化"旁边的代码
- **每一步有验收标准**，做完自己检查
- **数据不美化**：看不清的不猜，算的过程写出来，错了马上承认
- **不确定就问**，不替你拍板

## 6 个场景模板

[TEMPLATES.md](./TEMPLATES.md) 里按场景准备好了：极简版、全栈版、数据密集型、创业 MVP 等。保留适合你的部分，再加上你自己的技术栈、项目规则、团队 git 习惯和领域知识。

## 适合谁

- 希望 AI Agent 少出错、推理过程透明
- 在乎改动小而准
- 做的项目对数据准确性要求高

**它不包含**项目脚手架、CI/CD、技术栈，也替代不了你项目自己的规则。

**取舍**：这套规则偏谨慎，适合正式功能、生产系统、长期维护和多人协作的代码。改个错别字这类小事，按你的判断来。

## 社区

- 分享你的使用效果：[成功案例模板](./.github/ISSUE_TEMPLATE/success_story.md)
- 报告问题：[Bug 模板](./.github/ISSUE_TEMPLATE/bug_report.md)
- 提改进建议：[改进模板](./.github/ISSUE_TEMPLATE/improvement.md)

这是一份持续更新的文档。欢迎提 Issue 说说你的场景、哪些有效哪些没用，或直接发 PR。

## 相关工作

- Karpathy：[关于 LLM 编码常见错误的推文](https://x.com/karpathy/status/2015883857489522876)
- 马斯克的工程方法：来自 SpaceX / Tesla 制造的第一性原理思维
- BMAD-METHOD：完整的研发流程（PM → 架构 → 开发 → QA）
- claude-code-bmad-foundation：结合 Karpathy 和 BMAD 的模板

[![Star History Chart](https://api.star-history.com/svg?repos=AIPMAndy/AndySoul&type=Date)](https://star-history.com/#AIPMAndy/AndySoul&Date)

## 常见问题 FAQ

### CLAUDE.md 和 AGENTS.md 有什么区别？

Claude Code 读取 `CLAUDE.md`，OpenAI Codex 读取 `AGENTS.md`，Cursor 读取 `.cursorrules`。AndySoul 三处用的是同一份内容，按上面的命令下载成对应的文件名就行。

### 装上以后 AI 会有什么变化？

它会先说计划，只改你要求的部分，每一步都验收，不确定就问你。[EXAMPLES.md](./EXAMPLES.md) 里有 5 组前后对比。

### 这些规则的依据是什么？

9 条认知公理、马斯克 5 步工程法和 Karpathy 4 条编码原则。

### 能按我自己的项目改吗？

能。[TEMPLATES.md](./TEMPLATES.md) 里有极简版、全栈版、数据密集型、创业 MVP 等场景模板。保留适合你的部分，再加上你自己的技术栈和项目规则。

### 免费吗？

免费，MIT 许可，可以自由使用和修改。

<!-- andy-author-card:start -->
## 作者 / About the author

**AI 酋长 Andy（Andy Liu，GitHub/X @AIPMAndy）**：前腾讯/百度 AI 产品专家，大模型独角兽前 VP，现专注 AI + 产品方法论创业。

可以找我聊求职咨询、AI 增长和副业陪跑，服务范围和费用先沟通确认。

微信 `AIPMAndy`（备注「AndySoul」）· [X @AIPMAndy](https://x.com/AIPMAndy) · [Telegram @AIPMAndy](https://t.me/AIPMAndy) · [个人官网 metaver.vip](https://metaver.vip/) · [Grok Bot 中文攻略](https://aipmandy.github.io/grok-bot-handbook/)

*AI Chief Andy (Andy Liu, @AIPMAndy on GitHub and X) is a former Tencent and Baidu AI product expert and former VP at an LLM unicorn, now a serial entrepreneur focused on AI and product methodology.*

### 作者的其他项目

- [DNA Memory](https://github.com/AIPMAndy/dna-memory)：Claude Code、Codex 共用的本地 AI Agent 记忆 MCP
- [goskill](https://github.com/AIPMAndy/goskill)：长任务执行助手：先定成功标准，再按标准验收
- [SafeSkill](https://github.com/AIPMAndy/safeskill)：装 AI Skill 之前，先扫危险命令、提示注入和密钥泄露
- [Grok Bot 中文攻略](https://github.com/AIPMAndy/grok-bot-handbook)：Grok Bot / AI Agent 中文教程，26 章加 40 套任务指令
- [OpenClaw Skills 中文精选](https://github.com/AIPMAndy/awesome-openclaw-skills-CN)：2868 个 OpenClaw Skills 分类整理，附国产模型接入指南

<!-- andy-author-card:end -->

## 许可证

MIT，可自由使用、修改，无需署名。与 Anthropic、OpenAI、Cursor 或任何 AI 公司无关。

如果对你有用，点个 Star，或在 [X 上分享](https://twitter.com/intent/tweet?text=推荐%20AndySoul%20-%20适用于%20AI%20编码%20Agent（Claude、Codex、Cursor）的通用指令%20-%20结合认知公理、马斯克方法论和%20Karpathy%20原则&url=https://github.com/AIPMAndy/AndySoul)。
