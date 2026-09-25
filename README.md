# Software Engineering Workflow

面向 AI Agent 的软件工程工作流，覆盖需求分析、系统设计、Issue/PR 协作、技术文档写作与独立审阅，并提供 SVG 绘图能力。让没有历史聊天记录的新贡献者，也能通过仓库和任务记录理解目标、约束与进度。

## 安装

需要 Git，以及支持 `SKILL.md` 的 Agent 工具。克隆到工具的 skills 目录时，使用 `--recurse-submodules` 一并取得 SVG 绘图 skill。以 `~/.codex/skills` 为例；其他工具请替换目标路径：

```bash
git clone --recurse-submodules \
  https://github.com/qiudeng7/software-engineering-workflow.git \
  ~/.codex/skills/software-engineering-workflow
```

安装后，根目录和 `skills/qiudengs-svg-diagrams/` 下都应有 `SKILL.md`。重新开启 Agent 会话；支持显式 skill 调用的工具中可以使用：

```text
使用 $software-engineering-workflow 检查并完善这个仓库的贡献规范。
```

### 已克隆，但没有绘图文件

在本仓库目录执行：

```bash
git submodule update --init --recursive
```

### 更新

确认本地没有待保留的未提交改动后，在本仓库目录执行：

```bash
git pull --ff-only
git submodule sync --recursive
git submodule update --init --recursive
```

这会把绘图仓库切到主仓库记录的版本，不会自动追踪它的最新提交。

## 子 skills

- [Issue / PR 工作流](skills/issue-pr-workflow/SKILL.md)：需求、设计与执行记录。
- [技术写作与审阅](skills/technical-writing/SKILL.md)：读者视角的表达和独立审阅。
- [README 写作](skills/write-readme/SKILL.md)与 [CONTRIBUTING 写作](skills/write-contributing/SKILL.md)：项目入口和贡献指南。
- [SVG 绘图](skills/qiudengs-svg-diagrams/SKILL.md)：信息图规则与模板。

SVG skill 来自独立的 [qiudengs-svg-diagrams 仓库](https://github.com/qiudeng7/qiudengs-svg-diagrams)，以 submodule 放在 `skills/qiudengs-svg-diagrams`。它可以单独用于其他场景；使用本工作流时无需重复安装。

## 一次设计方向掉头

我最初尝试把所有的协作和沟通都放到文档里，这样项目工作者的沟通就不必绑定 git 托管平台，但是最终我还是决定部分使用的托管平台来达成项目协作。

一方面原因是，使用托管平台确实能够更高效地检索 issue，也能获得比较好的 UI 体验，更重要的原因是目前各平台对 GitHub issue 的集成度其实非常高，我们不必担心 GitHub 的数据无法迁移，gitea 相反，我们还能获得更方便的集成生态和能力，而自己定义的规范并不能获得集成生态。

## License

[MIT](LICENSE)
