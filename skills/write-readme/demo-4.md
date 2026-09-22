# LinkCheck

检查 Markdown 文档中的本地文件链接，找出文件移动、重命名或删除后留下的失效引用。

适合用于项目文档、知识库和静态网站源码检查。支持命令行执行，也可以接入 CI。

## 检查范围

- 递归扫描指定目录中的 `.md` 文件。
- 检查普通链接和图片引用中的本地文件路径。
- 支持排除目录，以及文本和 JSON 两种输出格式。

当前不检查 HTTP 链接是否可访问，也不验证页面内的标题锚点。

## 安装

需要 Python 3.11 或更高版本。

克隆仓库后，在项目根目录执行：

```bash
python -m pip install .
```

确认安装成功：

```bash
linkcheck --version
```

建议在 Python 虚拟环境中安装，避免与其他项目的依赖混用。

## 快速开始

检查 `docs/` 目录：

```bash
linkcheck docs/
```

发现失效链接时，输出文件位置、行号和目标路径：

```text
docs/setup.md:24  missing target: ./images/settings.png
docs/api.md:61    missing target: ../reference/auth.md

Checked 42 files, found 2 broken links.
```

相对路径以链接所在文件的目录为基准解析。例如，`docs/setup.md`
中的 `./images/settings.png` 指向 `docs/images/settings.png`。

未发现问题时，命令返回退出码 `0`。

## 相关文档

- [命令行参考](docs/cli-reference.md)：全部选项、默认值和组合用法。
- [CI 集成指南](docs/ci.md)：不同 CI 平台的配置示例和结果归档方式。
- [架构说明](docs/architecture.md)：解析、路径解析和输出模块的边界。
- [贡献指南](CONTRIBUTING.md)：开发环境、测试命令和提交规范。

## 常用选项

| 选项 | 作用 | 默认值 |
| --- | --- | --- |
| `--root` | 解析以 `/` 开头的链接时使用的根目录 | 当前工作目录 |
| `--exclude` | 排除匹配的文件，可重复传入 | 不排除 |
| `--format` | 输出格式，支持 `text` 和 `json` | `text` |

排除草稿和归档目录：

```bash
linkcheck docs/ \
  --exclude 'drafts/**' \
  --exclude 'archive/**'
```

排除规则以扫描目录为基准。上例中的 `drafts/**` 对应 `docs/drafts/`。

将检查结果保存为 JSON：

```bash
linkcheck docs/ --format json > link-report.json
```

## 在 CI 中使用

安装完成后，直接执行检查命令：

```bash
linkcheck docs/
```

命令通过退出码区分检查结果：

| 退出码 | 含义 |
| --- | --- |
| `0` | 检查完成，未发现失效链接 |
| `1` | 检查完成，发现失效链接 |
| `2` | 检查未完成，例如参数错误或文件无法读取 |

CI 应将非零退出码视为失败。退出码为 `2` 时，应先解决运行问题，
再判断文档链接是否有效。

## 开发

安装开发依赖并运行测试：

```bash
python -m pip install -e ".[dev]"
python -m pytest
```

主要代码位置：

- `src/linkcheck/parser.py`：提取 Markdown 中的链接。
- `src/linkcheck/resolver.py`：解析路径并检查目标文件。
- `src/linkcheck/cli.py`：处理命令行参数和输出。
- `tests/fixtures/`：用于测试的文档与目录结构。

修改链接解析规则时，请同时添加能够复现问题的测试样例。

## 许可证

[MIT](LICENSE)
