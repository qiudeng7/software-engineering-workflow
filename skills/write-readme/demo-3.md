# TaskBoard

一个个人任务看板，支持创建任务、切换状态和按状态筛选。

数据保存在当前浏览器中，刷新后保留，不支持跨设备同步。

## 本地运行

要求 Node.js 22 和 npm。在项目根目录执行：

```bash
npm ci
npm run dev
```

打开 http://localhost:5173。

## 构建与预览

```bash
npm run build
npm run preview
```

构建产物位于 `dist/`，可部署到静态网站托管服务。

## 项目结构

- `src/components/`：界面组件
- `src/store/`：任务状态与本地存储
- `src/styles/`：全局样式

## 许可证

[MIT](LICENSE)
