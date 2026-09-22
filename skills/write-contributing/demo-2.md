# 贡献指南

普通功能和缺陷修复请先关联 Issue。涉及公开交互、数据格式或多个应用的改动，在实现前先确认验收标准和影响范围。

## 准备环境

需要 Node.js 22 和 pnpm 10。启用项目使用的包管理器并安装依赖：

```bash
corepack enable
pnpm install --frozen-lockfile
cp .env.example .env.local
```

在仓库根目录启动开发环境：

```bash
pnpm dev
```

`.env.local` 只用于本地开发，不要提交凭据。

## 按改动范围验证

| 改动 | 必须运行 |
|---|---|
| Markdown 和文案 | `pnpm lint:docs` |
| UI 组件 | `pnpm lint`、`pnpm test:unit` |
| 页面交互 | 上述命令及 `pnpm test:e2e --project chromium` |
| 构建或依赖 | `pnpm lint`、`pnpm test`、`pnpm build` |

修复缺陷时增加能够在修改前失败、修改后通过的测试。视觉变化需要在 Pull Request 中附上修改前后的截图。

## 提交 Pull Request

Pull Request 应关联 Issue，并说明改动、测试结果、未验证部分和环境要求。修改了环境变量、用户流程或开发命令时，同步更新对应文档。

端到端测试因本地环境无法运行时，写明原因和未覆盖的风险，不要只写“测试通过”。
