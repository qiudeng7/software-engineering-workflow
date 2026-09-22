# 贡献指南

非安全问题请先创建或关联 Issue。疑似漏洞不要公开提交 Issue，请按照 [安全策略](SECURITY.md) 中的渠道报告。

## 本地环境

需要 Python 3.11、Docker 和 Docker Compose。在仓库根目录执行：

```bash
cp .env.example .env.test
docker compose up -d postgres redis
python -m pip install -r requirements-dev.txt
python -m taskhub migrate --env test
```

测试配置只连接 `taskhub_test` 数据库。运行命令前确认 `TASKHUB_ENV=test`，测试和迁移不得连接生产数据库。

## 验证

```bash
python -m ruff check .
python -m pytest tests/unit
python -m pytest tests/integration
```

修改数据库结构时，同时提交迁移和回退测试。修改 HTTP 接口时，更新请求校验、成功响应、错误响应测试和 API 文档。

## Pull Request

Pull Request 应说明关联任务、数据和接口兼容性、迁移方式、已运行的检查及未验证部分。需要外部服务才能完成的验证，应写明使用的测试环境和数据范围。

合并只表示代码进入目标分支；部署和数据迁移按照发布流程单独验收。
