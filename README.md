# 通用协作 Skills

一个通用协作规范 skill，目标是让一个没有历史聊天记录的新贡献者，仅凭仓库和任务记录就能知道：要做什么、去哪里改、哪些约束不能破坏、当前做到哪里。



## 安装

直接 clone 到 Codex 或任意其他 harness 的 skills 目录：

```bash
git clone https://github.com/qiudeng7/common-collaboration-skills.git \
  ~/.codex/skills/common-collaboration-skills
```

新开一个 Codex 会话后即可自动发现，也可以显式调用：

```text
使用 $common-collaboration-skills 检查并完善这个仓库的贡献规范。
```

## 一次设计方向掉头

我最初尝试把所有的协作和沟通都放到文档里，这样项目工作者的沟通就不必绑定 git 托管平台，但是最终我还是决定部分使用的托管平台来达成项目协作。

一方面原因是，使用托管平台确实能够更高效地检索 issue，也能获得比较好的 UI 体验，更重要的原因是目前各平台对 GitHub issue 的集成度其实非常高，我们不必担心 GitHub 的数据无法迁移，gitea 相反，我们还能获得更方便的集成生态和能力，而自己定义的规范并不能获得集成生态。

## License

[MIT](LICENSE)
