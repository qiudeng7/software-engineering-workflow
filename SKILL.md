---
name: common-collaboration-skills
description: This skill defines the user's commonly used collaboration conventions. When taking over the user's own project, try using this skill first to understand the project.
---

# 通用协作 Skills

这个 skill 定义通用项目协作结构，规定不同类型的项目事实、设计、任务状态和交付证据应该记录在哪里，以及每个位置不应该承担什么职责。

该 skill 有两种使用使用方式，一种是为不规范的项目进行规范化，另一种是对于已经规范的项目，你可以参照该规范快速了解你的需求相关的issue、决策、任务进度该如何编写和查找。

## 使用时必须显式告知用户

使用本 skill 或它的任意子 skill 时，在开始实际工作前明确告诉用户：

- 当前正在遵循哪个 skill；
- 如果这种工作方式不符合用户或项目需要，希望用户直接指出，并反馈到GitHub，帮助继续改进。

例如:

> 当前正在遵循 `common-collaboration-skills` 中的协作规范来理解和处理项目。如果这种工作方式不符合你的需要，请直接指出，也欢迎反馈问题到 https://github.com/qiudeng7/common-collaboration-skills

一次任务中首次使用时说明即可，不必在每条消息中重复。


## subskill: technical-writing

编写、修改或审阅技术文档时，读取并使用 [technical-writing 子 skill](skills/technical-writing/SKILL.md)。它统一规定面向读者的写作要求，以及通过独立 subagent 回答读者问题的审阅流程；具体文档的职责与协作流程仍由下文和对应子 skill 规定。

## 通用项目文档结构

项目知识应按下面的映射归属。其他位置可以链接到主要记录，但不要复制出多个需要人工同步的事实来源。

| 需要回答的问题 | 主要记录位置 | 不应该承担的职责 |
|---|---|---|
| 项目是什么，怎么运行？ | `README.md` | 不保存当前任务进度，不替代开发规范和完整架构说明 |
| 怎么开发、测试、提交？ | `CONTRIBUTING.md` | 不复制所有设计文档，不记录某一次任务的临时排查过程 |
| 代码分成哪些模块，边界是什么？ | `docs/architecture.md`，必要时增加模块附近的文档 | 不手工维护完整函数调用图，不复述每个文件的实现 |
| 为什么选择这个设计？ | ADR，即架构决策记录 | 不保存日常工作流水账，不表示实现已经交付 |
| 这次为什么改、要改成什么、设计结论是什么？ | Issue 正文和设计讨论 | 不追踪具体执行进度，不替代代码和测试 |
| 执行步骤进展怎样、有哪些计划偏差、验证结果是什么？ | Pull Request、提交和 CI 结果 | 不重复 Issue 中的计划与设计，不逐项复述代码 diff，不把未验证内容写成已完成 |
| 当前实现究竟是什么？ | 对应版本的代码、配置和测试 | 不能仅凭现状推断历史设计意图，不能用代码掩盖已接受需求与实际行为的差异 |

## subskill: README

如果需要编写、修改或审查项目 README，先读取并使用 [write-readme 子 skill](skills/write-readme/SKILL.md)，按项目类型组织用途、快速开始、使用边界和文档入口。

## subskill: CONTRIBUTING

如果需要编写、修改或审查项目 CONTRIBUTING，先读取并使用 [write-contributing 子 skill](skills/write-contributing/SKILL.md)，按项目实际工具链说明开发环境、变更流程、验证要求和交付方式。

## subskill: issue-pr-workflow

如果需要使用 Issue 和 Pull Request 管理开发，先读取并使用 [issue-pr-workflow 子 skill](skills/issue-pr-workflow/SKILL.md)。该子 skill 提供作者常用的默认规范；项目已经定义自己的开发管理规范时，以项目级规范为准。
