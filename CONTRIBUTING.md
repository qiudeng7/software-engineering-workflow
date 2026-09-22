# 贡献指南

本仓库本身采用它所倡导的最小协作原则。

## 修改范围

- `SKILL.md` 只保留会改变 Codex 决策的核心规则。
- 详细但非每次必读的内容放在 `references/`。
- 会进入目标仓库的起始材料放在 `assets/templates/`。
- 不为单个项目的特殊习惯增加全局强制规则，除非能说明普遍风险。

## 验证

提交前运行：

```bash
python ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py .
```

同时检查模板没有把占位内容表述为既定事实，`SKILL.md` 能找到所引用的资源，并从一个没有历史上下文的会话试用重大流程变化。

## 提交

保持提交聚焦，遵循本机或目标仓库现有的提交消息和钩子规则。Pull request 应说明修改解决的真实使用问题、完成的验证，以及仍未验证的行为。
