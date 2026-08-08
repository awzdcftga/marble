# RiverMark

RiverMark 是一个面向技术团队与独立开发者的外链资产聚合与管理工具，本质上是一个轻量级的技术资源导航与元数据归档系统。它不对内容做二次分发，而是提供结构化的外链索引、状态标记与快速检索能力，帮助用户将散落在代码仓库、文档站点、设计稿、API 参考、运维面板等不同场景下的关键链接统一收纳，并赋予可维护的语义标签。项目定位为“开发者个人的外链治理中台”，适用于需要长期维护大量外部引用（如依赖文档、监控大盘、内部规范、调研材料）的团队或个人。

## 功能概览

- 批量外链导入与去重：支持从 Markdown、CSV 或纯文本列表中批量摄入 URL，自动识别重复条目并生成冲突报告。

- 多级标签与自定义分类：每个外链可绑定多个标签，支持按项目、环境、状态（待阅/常用/归档）等维度自由组合分类。

- 变更历史与回溯：记录每次链接新增、删除或元数据修改的操作日志，支持按时间点回滚至任意历史版本。

- Markdown 原生渲染：所有外链列表与注释均以 Markdown 格式存储，可直接嵌入现有文档体系，无需额外前端。

- 离线校验与可用性检查：提供本地命令行工具，定期对已收录链接进行 HTTP 状态检测，标记失效或重定向的条目。

- 模板化导出：支持按标签或分类筛选后，导出为 README 章节、HTML 书签文件或 JSON 结构化数据，便于集成至 CI/CD 或静态站点生成器。

## 应用场景

- 技术调研材料管理：当团队需要对某一技术方向（如消息队列、前端框架、数据库中间件）进行横向对比时，可将所有参考文档、官方仓库、Benchmark 报告等链接统一收入 RiverMark，并附加对比结论和优先级标记，避免调研材料散落在聊天记录或临时笔记中。

- 微服务架构下的文档聚合：在微服务部署环境中，每个服务通常拥有独立的 API 文档、健康检查面板、日志查询入口和配置中心地址。RiverMark 可为每个服务建立独立的标签空间，将所有相关外链聚合为一张可随时查阅的服务卡片，显著降低故障排查时的入口查找成本。

- 开源项目 README 外链治理：开源维护者经常需要在 README 中维护大量外部链接（贡献指南、行为准则、社区论坛、版本发布说明）。RiverMark 支持将此类链接统一托管在单独文件中，并通过模板渲染生成干净的 README 章节，避免主文档因链接膨胀而变得杂乱。

- 新人入职知识库构建：为新人准备的入职文档通常包含数十个必读链接（代码仓库、设计规范、项目管理工具、内部 Wiki）。RiverMark 可将这些链接按学习阶段（第一周、第二周、进阶）组织，并支持标注必读/选读状态，使入职引导更加结构化。

## 快速开始

以下命令演示了如何获取 RiverMark 源码、安装依赖并启动本地服务。

```bash
git clone https://github.com/fcdujqa/river.git
cd river
pip install -r requirements.txt
python scripts/init_db.py
python app.py --port 8080
```

执行完毕后，访问控制台输出的本地地址即可进入 Web 管理界面。首次启动会自动创建默认的链接分类模板和示例数据。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，用于后端 API 与 CLI 工具 |
| SQLite | 3.35 及以上 | 默认嵌入式数据库，用于存储链接元数据和操作日志 |
| Git | 2.30 及以上 | 用于版本化存储外链数据文件（可选，推荐） |
| Markdown 解析库 | markdown>=3.4.0 | 用于渲染和解析 Markdown 格式的外链列表 |
| 网络环境 | 出站 443/80 可通 | 仅在使用在线校验功能时需要，其余操作完全离线 |

## 文档导航

| 层面 | 目录位置 | 回答的问题 |
|------|---------|-----------|
| 用户手册 | docs/user-guide/ | 如何添加、编辑、删除外链；如何使用标签和筛选；如何导出和备份数据 |
| 运维指南 | docs/operations/ | 如何迁移数据库；如何配置自动校验任务；如何通过环境变量调整服务端口 |
| API 参考 | docs/api/ | 哪些 REST 接口可供二次开发调用；请求/响应数据结构定义 |
| 设计说明 | docs/design/ | 元数据模型设计依据；为什么选择 SQLite 而非其他数据库；标签系统的扩展性考虑 |

## 资源列表

- https://github.com/fcdujqa/river/blob/main/violetbright.md
- https://github.com/fcdujqa/river/blob/main/violetcedar.md
- https://github.com/fcdujqa/river/blob/main/violetcobalt.md
- https://github.com/fcdujqa/river/blob/main/violetcrystal.md
- https://github.com/fcdujqa/river/blob/main/violetfalcon.md
- https://github.com/fcdujqa/river/blob/main/violetfield.md
- https://github.com/fcdujqa/river/blob/main/violetgarden.md
- https://github.com/fcdujqa/river/blob/main/violetharbor.md
- https://github.com/fcdujqa/river/blob/main/violethorizon.md
- https://github.com/fcdujqa/river/blob/main/violetlantern.md
- https://github.com/fcdujqa/river/blob/main/violetmeadow.md
- https://github.com/fcdujqa/river/blob/main/violetmidnight.md
- https://github.com/fcdujqa/river/blob/main/violetquartz.md
- https://github.com/fcdujqa/river/blob/main/violetriver.md
- https://github.com/fcdujqa/river/blob/main/violetwillow.md
- https://github.com/fcdujqa/river/blob/main/wanderbridge.md
- https://github.com/fcdujqa/river/blob/main/wandercoral.md
- https://github.com/fcdujqa/river/blob/main/wanderharbor.md
- https://github.com/fcdujqa/river/blob/main/wandermeadow.md
- https://github.com/fcdujqa/river/blob/main/wanderolive.md
- https://github.com/fcdujqa/river/blob/main/wandervelvet.md
- https://github.com/fcdujqa/river/blob/main/wanderzephyr.md
- https://github.com/fcdujqa/river/blob/main/willowcrystal.md
- https://github.com/fcdujqa/river/blob/main/willowdelta.md
- https://github.com/fcdujqa/river/blob/main/willowfalcon.md
- https://github.com/fcdujqa/river/blob/main/willowlantern.md
- https://github.com/fcdujqa/river/blob/main/willowsilver.md
- https://github.com/fcdujqa/river/blob/main/zephyrbright.md
- https://github.com/fcdujqa/river/blob/main/zephyrcosmic.md
- https://github.com/fcdujqa/river/blob/main/zephyrgolden.md
- https://github.com/fcdujqa/river/blob/main/zephyrhorizon.md
- https://github.com/fcdujqa/river/blob/main/zephyrocean.md
- https://github.com/fcdujqa/river/blob/main/zephyrprairie.md
- https://github.com/fcdujqa/river/blob/main/zephyrwander.md
- https://github.com/munedrf/midnight/blob/main/amberbright.md
- https://github.com/munedrf/midnight/blob/main/ambercobalt.md
- https://github.com/munedrf/midnight/blob/main/ambermeadow.md
- https://github.com/munedrf/midnight/blob/main/ambermidnight.md
- https://github.com/munedrf/midnight/blob/main/amberpixel.md
- https://github.com/munedrf/midnight/blob/main/amberriver.md
- https://github.com/munedrf/midnight/blob/main/ambersignal.md
- https://github.com/munedrf/midnight/blob/main/amberzephyr.md
- https://github.com/munedrf/midnight/blob/main/anchoratlas.md
- https://github.com/munedrf/midnight/blob/main/anchorquartz.md
- https://github.com/munedrf/midnight/blob/main/anchorvelvet.md
- https://github.com/munedrf/midnight/blob/main/anchorzephyr.md
- https://github.com/munedrf/midnight/blob/main/atlasbloom.md
- https://github.com/munedrf/midnight/blob/main/atlasdelta.md
- https://github.com/munedrf/midnight/blob/main/atlassignal.md
- https://github.com/munedrf/midnight/blob/main/bloomquartz.md
- https://github.com/munedrf/midnight/blob/main/bridgeforest.md
- https://github.com/munedrf/midnight/blob/main/bridgemarble.md
- https://github.com/munedrf/midnight/blob/main/bridgetimber.md
- https://github.com/munedrf/midnight/blob/main/bridgezephyr.md
- https://github.com/munedrf/midnight/blob/main/brightember.md
- https://github.com/munedrf/midnight/blob/main/brightfield.md
- https://github.com/munedrf/midnight/blob/main/brightsaffron.md
- https://github.com/munedrf/midnight/blob/main/canvascloud.md
- https://github.com/munedrf/midnight/blob/main/canvasgarden.md
- https://github.com/munedrf/midnight/blob/main/canvasmeadow.md
- https://github.com/munedrf/midnight/blob/main/canvaswander.md
- https://github.com/munedrf/midnight/blob/main/cedarmaple.md
- https://github.com/munedrf/midnight/blob/main/cedarsilver.md
- https://github.com/munedrf/midnight/blob/main/cedartimber.md
- https://github.com/munedrf/midnight/blob/main/cedarvelvet.md
- https://github.com/munedrf/midnight/blob/main/cedarwillow.md
- https://github.com/munedrf/midnight/blob/main/cloudfield.md
- https://github.com/munedrf/midnight/blob/main/cloudforest.md
- https://github.com/munedrf/midnight/blob/main/cloudmirror.md
- https://github.com/munedrf/midnight/blob/main/cobaltdelta.md
- https://github.com/munedrf/midnight/blob/main/cobaltolive.md
- https://github.com/munedrf/midnight/blob/main/cobaltsilver.md
- https://github.com/munedrf/midnight/blob/main/cobaltviolet.md
- https://github.com/munedrf/midnight/blob/main/cobaltwillow.md
- https://github.com/munedrf/midnight/blob/main/cobaltzephyr.md
- https://github.com/munedrf/midnight/blob/main/coralamber.md
- https://github.com/munedrf/midnight/blob/main/coralcrystal.md
- https://github.com/munedrf/midnight/blob/main/coralgarden.md
- https://github.com/munedrf/midnight/blob/main/coralocean.md
- https://github.com/munedrf/midnight/blob/main/coralpixel.md
- https://github.com/munedrf/midnight/blob/main/cosmicatlas.md
- https://github.com/munedrf/midnight/blob/main/cosmiccedar.md
- https://github.com/munedrf/midnight/blob/main/cosmiccoral.md
- https://github.com/munedrf/midnight/blob/main/cosmichorizon.md
- https://github.com/munedrf/midnight/blob/main/cosmicmeadow.md
- https://github.com/munedrf/midnight/blob/main/cosmicolive.md
- https://github.com/munedrf/midnight/blob/main/cosmicpearl.md
- https://github.com/munedrf/midnight/blob/main/cosmicpixel.md
- https://github.com/munedrf/midnight/blob/main/cosmicriver.md
- https://github.com/munedrf/midnight/blob/main/cosmiczephyr.md
- https://github.com/munedrf/midnight/blob/main/crystalatlas.md
- https://github.com/munedrf/midnight/blob/main/crystalbloom.md
- https://github.com/munedrf/midnight/blob/main/crystaldelta.md
- https://github.com/munedrf/midnight/blob/main/crystalsignal.md
- https://github.com/munedrf/midnight/blob/main/deltacobalt.md
- https://github.com/munedrf/midnight/blob/main/deltamarble.md
- https://github.com/munedrf/midnight/blob/main/embercanvas.md
- https://github.com/munedrf/midnight/blob/main/emberquartz.md
- https://github.com/munedrf/midnight/blob/main/embervelvet.md
- https://github.com/munedrf/midnight/blob/main/falconcloud.md

## 项目结构

```
river/
├── app.py                  # Web 服务主入口，注册路由与中间件
├── requirements.txt        # Python 依赖清单（Flask、markdown、requests 等）
├── config/
│   ├── default.yaml        # 默认配置（端口、数据库路径、校验间隔）
│   └── schema.json         # 外链元数据的 JSON Schema 定义
├── core/
│   ├── models.py           # SQLAlchemy 模型定义（Link、Tag、History）
│   ├── validator.py        # URL 格式校验与去重逻辑
│   └── checker.py          # 离线 HTTP 状态检测实现
├── scripts/
│   ├── init_db.py          # 首次运行时的数据库初始化脚本
│   ├── import_batch.py     # 批量导入外部链接列表的命令行工具
│   └── export_template.py  # 按模板导出 Markdown/JSON 的脚本
├── templates/
│   ├── base.html           # Web 界面基础布局模板
│   └── link_list.html      # 外链列表页渲染模板
├── static/
│   ├── style.css           # 界面样式（适配明暗主题）
│   └── app.js              # 前端交互逻辑（筛选、标签编辑）
├── storage/
│   └── river.db            # SQLite 数据库文件（默认位置，可迁移）
└── docs/                   # 完整文档子目录（见文档导航）
    ├── user-guide/
    ├── operations/
    ├── api/
    └── design/
```

## 贡献指南

1. 阅读设计说明文档（docs/design/ 目录下）以了解 RiverMark 的核心数据模型和设计取舍，确保新增功能与现有架构保持一致。

2. 在 GitHub 上 fork 本项目，并基于 main 分支创建新的 feature 分支，分支命名采用 feature/功能简述 的格式，避免直接在主分支上提交。

3. 代码改动需附带对应的单元测试，测试文件放置在 tests/ 目录下，并确保所有现有测试用例通过（执行 pytest 命令验证）。

4. 若新增或修改了对外接口（包括 REST API 和 CLI 命令），请同步更新 docs/api/ 或 docs/operations/ 中的相关文档，并补充使用示例。

5. 提交 Pull Request 时，请在描述中清晰说明改动目的、影响范围以及是否涉及数据迁移，维护者会在 48 小时内给予反馈。

## 常见问题

Q: RiverMark 是否支持 PostgreSQL 作为生产环境数据库？

A: 项目默认使用 SQLite 以降低起步门槛，但核心模型层基于 SQLAlchemy 编写，理论上支持 PostgreSQL、MySQL 等多种关系型数据库。如需切换，请修改 config/default.yaml 中的数据库连接字符串，并安装对应的数据库驱动（如 psycopg2）。需要留意的是，部分 SQLite 特有的查询优化在 PostgreSQL 上可能需微调索引策略。

Q: 离线校验功能会占用大量网络带宽吗？

A: 默认校验模式下，RiverMark 仅对每个链接发送一个 HEAD 请求，不下载响应体，因此单次校验的流量消耗极小（约几百字节/链接）。对于数量超过 1000 条的大规模数据集，建议通过命令行工具设置 --interval 参数，将校验任务分散到多天执行，避免瞬时并发过高。

Q: 如何将现有书签文件（如 Chrome 导出的 HTML）迁移到 RiverMark？

A: RiverMark 提供了 scripts/import_batch.py 脚本，支持传入包含链接列表的纯文本或 CSV 文件。对于 Chrome 书签 HTML 格式，建议先使用第三方工具将其转换为每行一个 URL 的简单列表，再执行导入。后续版本计划增加对 Netscape 书签格式的直接支持。

## 许可证

MIT

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
