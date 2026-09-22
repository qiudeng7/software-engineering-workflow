# 通用协作 Skills

一个面向 Codex 的通用贡献规范 skill，帮助仓库建立人类与 AI 共用、可恢复、可验证的协作流程。

它关注的不是增加文档数量，而是让一个没有历史聊天记录的新贡献者，仅凭仓库和任务记录就能知道：要做什么、去哪里改、哪些约束不能破坏、当前做到哪里，以及怎样证明完成。

## 安装

直接 clone 到 Codex skills 目录：

```bash
git clone https://github.com/qiudeng7/general-collaboration-skills.git \
  ~/.codex/skills/general-collaboration-skills
```

新开一个 Codex 会话后即可自动发现，也可以显式调用：

```text
使用 $general-collaboration-skills 检查并完善这个仓库的贡献规范。
```

## 能做什么

- 审查仓库现有的 README、贡献指南、架构文档与 GitHub 模板。
- 为每类信息指定唯一主要记录，避免状态和规范相互冲突。
- 建立可交给陌生贡献者的任务包、结构化交接与证据化 PR。
- 按风险决定是否需要 Issue、测试、设计讨论和 ADR。
- 用“空白会话”检验仓库能否真正脱离聊天记忆继续工作。

`assets/templates/` 提供可裁剪的起点。Skill 会先检查项目现状，再决定是否使用；模板不是要原样覆盖所有仓库。

## 设计原则

- 项目知识进入项目已有的共享记录，不另建只有 AI 能访问的事实库。
- 代码反映当前行为，已接受的需求和决策描述目标行为；冲突需要被发现和解决。
- 交接记录保存可恢复状态与证据，不保存聊天流水账。
- 设计已接受、代码已合并、部署已完成、运行路径已验证是不同状态。
- 流程强度与改动风险成比例。

## 仓库结构

```text
SKILL.md                           Skill 入口与核心决策规则
agents/openai.yaml                Codex 展示元数据
references/contribution-model.md  详细的文档边界与审查问题
assets/templates/                 可按项目裁剪的协作文件模板
```

## 贡献

请先阅读 [CONTRIBUTING.md](CONTRIBUTING.md)。

## License

[MIT](LICENSE)
