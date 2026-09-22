# SlugKit

将英文标题转换为 URL slug，适用于文章链接和静态页面路径。

## 安装

要求 Python 3.10+。克隆仓库后，在项目根目录安装：

```bash
pip install .
```

## 使用

```python
from slugkit import slugify

slugify("Hello, World!")  # "hello-world"
slugify("  A   B  ")      # "a-b"
```

## API

`slugify(text: str) -> str`

- 将英文字母转为小写。
- 将连续空白替换为单个连字符。
- 移除英文字母、数字和连字符以外的字符。
- 移除首尾连字符；结果为空时返回空字符串。

## 许可证

[MIT](LICENSE)
