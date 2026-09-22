# Contributing to SlugKit

感谢你参与 SlugKit。小型文档修正可以直接提交 Pull Request；功能和行为变更请先创建 Issue，确认目标和兼容性要求。

## 开发环境

需要 Python 3.11 或更高版本。在仓库根目录执行：

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -e ".[dev]"
```

Windows PowerShell 使用 `.venv\Scripts\Activate.ps1` 激活环境。

## 验证

```bash
python -m ruff check .
python -m pytest
```

只修改 Markdown 时，可以仅运行：

```bash
python -m pytest tests/test_docs_examples.py
```

新增或修改公开行为时，请增加覆盖正常输入和边界情况的测试，并同步更新 README 中的使用示例。

## 提交 Pull Request

Pull Request 请说明：

- 关联的 Issue；
- 用户可观察到的变化；
- 实际运行的验证命令和结果；
- 未运行的检查及原因；
- 是否影响公开 API 或兼容性。

保持一次 Pull Request 只解决一个清楚的问题。CI 通过后由维护者进行评审。
