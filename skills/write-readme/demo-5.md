# TaskHub

一个用于个人任务管理的 HTTP API，支持创建任务、修改状态和按状态查询。

数据保存在本地 SQLite 数据库中。项目适合个人工具集成和小型应用原型，
目前按单用户、单实例运行设计。

## 功能

- 创建、查询和删除任务。
- 在 `todo`、`doing`、`done` 三种状态之间切换。
- 按状态筛选任务。
- 通过数据库文件保留任务数据。

当前不提供账户系统、权限控制或定时提醒。

## 本地运行

需要 Python 3.11 或更高版本。以下命令在项目根目录执行。

安装依赖并创建配置文件：

```bash
python -m pip install -r requirements.txt
cp .env.example .env
```

初始化数据库并启动服务：

```bash
python -m taskhub init-db
python -m taskhub serve
```

`init-db` 会创建所需的数据表；已有数据库中的任务会被保留。

服务默认监听 `http://127.0.0.1:8000`。检查是否启动成功：

```bash
curl http://127.0.0.1:8000/health
```

预期返回：

```json
{"status":"ok"}
```

## 配置

程序启动时读取项目根目录下的 `.env` 文件。同名环境变量优先于文件中的配置。

| 配置项 | 说明 | 默认值 |
| --- | --- | --- |
| `TASKHUB_HOST` | 监听地址 | `127.0.0.1` |
| `TASKHUB_PORT` | 监听端口 | `8000` |
| `TASKHUB_DB_PATH` | SQLite 数据库路径 | `./data/tasks.db` |
| `TASKHUB_LOG_LEVEL` | 日志级别 | `INFO` |

数据库的相对路径以项目根目录为基准。修改配置后需要重启服务。

例如，将服务端口改为 `8080`：

```dotenv
TASKHUB_PORT=8080
```

## API 示例

创建任务：

```bash
curl -X POST http://127.0.0.1:8000/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":"整理项目文档"}'
```

成功时返回 `201 Created`：

```json
{
  "id": 1,
  "title": "整理项目文档",
  "status": "todo"
}
```

新任务默认使用 `todo` 状态。示例中的 `id` 由服务生成，
后续请求应使用实际返回的值。

将任务标记为完成：

```bash
curl -X PATCH http://127.0.0.1:8000/tasks/1 \
  -H "Content-Type: application/json" \
  -d '{"status":"done"}'
```

查询已完成的任务：

```bash
curl "http://127.0.0.1:8000/tasks?status=done"
```

## 相关文档

- [API 参考](docs/api.md)：完整接口、请求字段、响应结构和错误码。
- [配置参考](docs/configuration.md)：全部配置项、默认值和覆盖顺序。
- [部署指南](docs/deployment.md)：生产部署、升级和回退步骤。
- [数据运维](docs/data-operations.md)：数据库备份、恢复和迁移流程。
- [架构说明](docs/architecture.md)：模块职责、依赖边界和关键执行链路。
- [贡献指南](CONTRIBUTING.md)：开发环境、测试命令和提交规范。

## 接口约定

| 方法 | 路径 | 作用 |
| --- | --- | --- |
| `POST` | `/tasks` | 创建任务 |
| `GET` | `/tasks` | 查询任务，支持 `status` 参数 |
| `GET` | `/tasks/{id}` | 获取单个任务 |
| `PATCH` | `/tasks/{id}` | 修改标题或状态 |
| `DELETE` | `/tasks/{id}` | 删除任务 |

请求体和响应体使用 JSON，删除成功时返回 `204 No Content`，不包含响应体。

任务标题去除首尾空白后，长度必须为 1–200 个字符。
状态只接受 `todo`、`doing` 和 `done`。

错误响应使用统一格式：

```json
{
  "error": {
    "code": "TASK_NOT_FOUND",
    "message": "Task 42 does not exist."
  }
}
```

参数不合法时返回 `400`，任务不存在时返回 `404`，
服务内部错误返回 `500`。

## 数据保存与运行限制

任务数据保存在 `TASKHUB_DB_PATH` 指向的文件中。重启服务不会清空数据；
删除数据库文件会丢失全部任务。

本地备份时，先停止服务，再复制数据库文件。恢复时替换该文件并重新启动。

项目尚未实现身份认证，默认只监听本机地址。需要开放给其他用户访问时，
应先补充认证和访问控制。

当前运行方式不支持多个服务实例共享同一个数据库文件。

## 开发与测试

安装开发依赖并运行测试：

```bash
python -m pip install -r requirements-dev.txt
python -m pytest
```

测试使用临时数据库，不会读写 `.env` 中配置的数据库。

主要目录：

- `taskhub/api/`：路由、请求校验和响应转换。
- `taskhub/services/`：任务管理逻辑。
- `taskhub/storage/`：数据库连接与查询。
- `tests/`：接口测试和业务逻辑测试。

新增接口时，请同时补充请求示例、参数校验和错误响应测试。

## 许可证

[MIT](LICENSE)
