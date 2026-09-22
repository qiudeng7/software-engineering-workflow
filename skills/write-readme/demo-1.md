# CSV Clean

删除 CSV 文件中的重复行，保留表头和原始顺序。适合数据导入前的简单清理。

## 快速开始

要求 Python 3.10+，无需额外依赖。在项目根目录运行：

```bash
python clean.py input.csv --output output.csv
```

清理结果写入 `output.csv`，原文件保持不变。

## 使用说明

- 仅支持 UTF-8 编码的 CSV 文件。
- 所有字段完全一致时，判定为重复行。
- 输出文件已存在时，命令报错退出。

## 许可证

[MIT](LICENSE)
