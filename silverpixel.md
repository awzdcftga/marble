# River Resource Gateway

River Resource Gateway 是一个面向开发者与技术研究人员的轻量级外链资源聚合与导航系统。项目定位为“技术资源的统一索引枢纽”，通过结构化组织方式，将分散于互联网各处的优质文档、教程、代码仓库、技术博客与实验性项目汇聚于单一入口，降低信息检索成本，提升研发效率。目标用户包括开源贡献者、DevOps 工程师、后端开发人员以及技术决策者，尤其适用于需要长期跟踪多个上游仓库变更、管理大量外部参考资料的团队或个人。项目本身不存储实际内容，仅作为索引层与元数据管理工具，通过 Markdown 驱动的清单体系实现对海量外链的分类、标记与版本追踪。

## 功能概览

资源清单的声明式管理 通过 Markdown 文件定义资源条目，每条记录包含标题、标签、描述与原始 URL，支持人类可读与机器解析的双重特性。

外链健康状态监控 内置基于 HTTP 状态码的链接可用性检查，周期性验证资源端点是否可访问，并在控制台输出异常报告。

标签化分类与全文检索 每个资源可关联多个标签（如 rust、networking、distributed-system），项目提供基于标签的过滤与标题描述的模糊匹配查询。

静态站点生成输出 项目包含一套渲染管线，可将资源清单转换为单页 HTML 仪表板或静态 JSON API 端点，方便内网部署或嵌入其他系统。

仓库元数据镜像 对于来自 GitHub 的资源链接，自动提取仓库描述、星标数与最后更新时间，生成本地缓存的元数据快照。

导入与导出兼容性 支持从 CSV、YAML 或现有书签 HTML 文件批量导入链接，导出格式包括 Markdown 表格、JSON 和结构化文本，便于迁移与备份。

变更审计日志 记录每次资源清单的增删改操作，附带时间戳与操作者信息，所有变更以 Git 提交日志形式持久化。

## 应用场景

研发团队内部知识库构建 技术团队可将常用依赖库文档、内部 API 设计稿、运维手册与故障排查笔记通过本系统统一索引，替代浏览器书签的分散管理方式，新成员入职时可一次性获取全部参考资料。

开源项目依赖追踪 开源维护者利用本系统的标签与状态监控功能，跟踪上游依赖仓库的 release note、迁移指南与安全公告，当依赖仓库发生重大变更时及时获得提醒。

技术选型调研辅助 架构师在评估中间件、数据库或框架时，将候选项目的官网、GitHub 仓库、性能测试报告、社区讨论帖与竞品对比文章集中收录，形成结构化的调研材料供决策参考。

离线文档聚合门户 在受限网络环境中，通过本系统预先收录所需文档的外链，配合静态站点生成功能搭建内部文档门户，供隔离网络内的开发人员访问。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户建议使用 WSL2 或 Git Bash 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/fcdujqa/river.git
cd river

# 安装项目依赖（需要 Python 3.9+ 与 pip）
pip install -r requirements.txt

# 执行资源清单解析与链接健康检查
python river_cli.py parse --input ./manifests --output ./output

# 启动本地开发服务器预览仪表板（默认监听 127.0.0.1:8080）
python river_cli.py serve --port 8080
```

首次运行前请确保已创建 `manifests` 目录并放置至少一个资源清单文件（示例文件参见 `examples/sample_manifest.md`）。执行 `parse` 命令后，生成的 HTML 仪表板与 JSON 数据将写入 `output` 目录，可通过浏览器直接打开 `output/index.html` 查看。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9, 3.10, 3.11, 3.12 | 核心运行环境，推荐使用 3.11 以获得最佳性能 |
| pip | 22.0 或更高 | Python 包管理器，用于安装项目依赖 |
| requests | 2.28.0 或更高 | 用于外链健康状态检查的 HTTP 客户端库 |
| markdown | 3.4.0 或更高 | 解析资源清单中的 Markdown 格式描述与元数据 |
| pyyaml | 6.0 或更高 | 支持 YAML 格式的资源清单导入与导出 |
| git | 2.30 或更高 | 用于变更审计日志的版本控制集成（可选，但强烈推荐） |
| 网络连接 | 出站 443/80 端口可达 | 执行链接检查与 GitHub 元数据镜像时需要访问公网资源 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何编写资源清单、如何添加标签、如何运行健康检查与导出仪表板 |
| 管理员指南 | /docs/admin-guide/ | 如何配置自动巡检、如何集成 Webhook 通知、如何迁移已有书签数据 |
| 开发参考 | /docs/developer-guide/ | 插件系统设计、自定义渲染器编写、API 端点扩展与单元测试策略 |
| 设计文档 | /docs/design-decisions/ | 为什么选择 Markdown 作为清单格式、元数据缓存失效策略、并发检查模型 |
| 故障排查 | /docs/troubleshooting/ | 链接检查超时处理、GitHub API 限流应对方案、常见解析错误修复 |

## 资源列表

- https://github.com/fcdujqa/river/blob/main/jadewillow.md
- https://github.com/fcdujqa/river/blob/main/lanternfield.md
- https://github.com/fcdujqa/river/blob/main/lanternorbit.md
- https://github.com/fcdujqa/river/blob/main/lanternpearl.md
- https://github.com/fcdujqa/river/blob/main/maplecloud.md
- https://github.com/fcdujqa/river/blob/main/mapleforest.md
- https://github.com/fcdujqa/river/blob/main/mapleriver.md
- https://github.com/fcdujqa/river/blob/main/maplerocket.md
- https://github.com/fcdujqa/river/blob/main/mapleshadow.md
- https://github.com/fcdujqa/river/blob/main/maplewander.md
- https://github.com/fcdujqa/river/blob/main/maplezephyr.md
- https://github.com/fcdujqa/river/blob/main/marbleforest.md
- https://github.com/fcdujqa/river/blob/main/marbleharbor.md
- https://github.com/fcdujqa/river/blob/main/marbleolive.md
- https://github.com/fcdujqa/river/blob/main/meadowcobalt.md
- https://github.com/fcdujqa/river/blob/main/meadowgarden.md
- https://github.com/fcdujqa/river/blob/main/meadowjade.md
- https://github.com/fcdujqa/river/blob/main/meadowlantern.md
- https://github.com/fcdujqa/river/blob/main/meadowpearl.md
- https://github.com/fcdujqa/river/blob/main/meadowvelvet.md
- https://github.com/fcdujqa/river/blob/main/meadowviolet.md
- https://github.com/fcdujqa/river/blob/main/midnightcedar.md
- https://github.com/fcdujqa/river/blob/main/midnightisland.md
- https://github.com/fcdujqa/river/blob/main/midnightmeadow.md
- https://github.com/fcdujqa/river/blob/main/midnightpearl.md
- https://github.com/fcdujqa/river/blob/main/midnightpixel.md
- https://github.com/fcdujqa/river/blob/main/midnightshadow.md
- https://github.com/fcdujqa/river/blob/main/mirrorcobalt.md
- https://github.com/fcdujqa/river/blob/main/mirrorolive.md
- https://github.com/fcdujqa/river/blob/main/nebulacrystal.md
- https://github.com/fcdujqa/river/blob/main/nebulafield.md
- https://github.com/fcdujqa/river/blob/main/nebulameadow.md
- https://github.com/fcdujqa/river/blob/main/nebulamirror.md
- https://github.com/fcdujqa/river/blob/main/nebulasaffron.md
- https://github.com/fcdujqa/river/blob/main/nebulatimber.md
- https://github.com/fcdujqa/river/blob/main/oceanatlas.md
- https://github.com/fcdujqa/river/blob/main/oceanbloom.md
- https://github.com/fcdujqa/river/blob/main/oceanbright.md
- https://github.com/fcdujqa/river/blob/main/oceancosmic.md
- https://github.com/fcdujqa/river/blob/main/oceanforest.md
- https://github.com/fcdujqa/river/blob/main/oceanisland.md
- https://github.com/fcdujqa/river/blob/main/oceanmaple.md
- https://github.com/fcdujqa/river/blob/main/olivebright.md
- https://github.com/fcdujqa/river/blob/main/olivecosmic.md
- https://github.com/fcdujqa/river/blob/main/olivefalcon.md
- https://github.com/fcdujqa/river/blob/main/oliveshadow.md
- https://github.com/fcdujqa/river/blob/main/olivesummit.md
- https://github.com/fcdujqa/river/blob/main/olivevelvet.md
- https://github.com/fcdujqa/river/blob/main/orbitbridge.md
- https://github.com/fcdujqa/river/blob/main/orbitbright.md
- https://github.com/fcdujqa/river/blob/main/orbitcloud.md
- https://github.com/fcdujqa/river/blob/main/orbitcobalt.md
- https://github.com/fcdujqa/river/blob/main/orbitcoral.md
- https://github.com/fcdujqa/river/blob/main/orbitfield.md
- https://github.com/fcdujqa/river/blob/main/orbitgolden.md
- https://github.com/fcdujqa/river/blob/main/orbitharbor.md
- https://github.com/fcdujqa/river/blob/main/orbitisland.md
- https://github.com/fcdujqa/river/blob/main/orbitjade.md
- https://github.com/fcdujqa/river/blob/main/orbitpearl.md
- https://github.com/fcdujqa/river/blob/main/orbitshadow.md
- https://github.com/fcdujqa/river/blob/main/pearlbright.md
- https://github.com/fcdujqa/river/blob/main/pearlcanvas.md
- https://github.com/fcdujqa/river/blob/main/pearlmaple.md
- https://github.com/fcdujqa/river/blob/main/pearlnebula.md
- https://github.com/fcdujqa/river/blob/main/pearlocean.md
- https://github.com/fcdujqa/river/blob/main/pearlpixel.md
- https://github.com/fcdujqa/river/blob/main/pearlprairie.md
- https://github.com/fcdujqa/river/blob/main/pearlviolet.md
- https://github.com/fcdujqa/river/blob/main/pixelanchor.md
- https://github.com/fcdujqa/river/blob/main/pixelisland.md
- https://github.com/fcdujqa/river/blob/main/pixelmeadow.md
- https://github.com/fcdujqa/river/blob/main/pixelnebula.md
- https://github.com/fcdujqa/river/blob/main/pixeltimber.md
- https://github.com/fcdujqa/river/blob/main/prairieatlas.md
- https://github.com/fcdujqa/river/blob/main/prairiebloom.md
- https://github.com/fcdujqa/river/blob/main/prairiecobalt.md
- https://github.com/fcdujqa/river/blob/main/prairielantern.md
- https://github.com/fcdujqa/river/blob/main/prairiemirror.md
- https://github.com/fcdujqa/river/blob/main/prairiesaffron.md
- https://github.com/fcdujqa/river/blob/main/prairievelvet.md
- https://github.com/fcdujqa/river/blob/main/prairieviolet.md
- https://github.com/fcdujqa/river/blob/main/quartzviolet.md
- https://github.com/fcdujqa/river/blob/main/riveramber.md
- https://github.com/fcdujqa/river/blob/main/riverdelta.md
- https://github.com/fcdujqa/river/blob/main/rivergarden.md
- https://github.com/fcdujqa/river/blob/main/riverquartz.md
- https://github.com/fcdujqa/river/blob/main/riversaffron.md
- https://github.com/fcdujqa/river/blob/main/rocketforest.md
- https://github.com/fcdujqa/river/blob/main/rocketgarden.md
- https://github.com/fcdujqa/river/blob/main/rocketmirror.md
- https://github.com/fcdujqa/river/blob/main/rocketocean.md
- https://github.com/fcdujqa/river/blob/main/rocketorbit.md
- https://github.com/fcdujqa/river/blob/main/rocketshadow.md
- https://github.com/fcdujqa/river/blob/main/saffronamber.md
- https://github.com/fcdujqa/river/blob/main/saffronbright.md
- https://github.com/fcdujqa/river/blob/main/saffroncloud.md
- https://github.com/fcdujqa/river/blob/main/saffroncobalt.md
- https://github.com/fcdujqa/river/blob/main/saffroncosmic.md
- https://github.com/fcdujqa/river/blob/main/saffronlantern.md
- https://github.com/fcdujqa/river/blob/main/saffronmirror.md

## 项目结构

```
river/
├── river_cli.py                # 命令行入口，注册 parse、serve、check 等子命令
├── requirements.txt            # Python 依赖列表
├── pyproject.toml              # 项目构建配置与元数据声明
├── README.md                   # 项目说明文档（即本文件）
├── LICENSE                     # MIT 许可证文本
│
├── river/                      # 核心源代码目录
│   ├── __init__.py
│   ├── parser.py               # 资源清单 Markdown 解析器，提取标题、标签与 URL
│   ├── checker.py              # 外链健康状态检查器，支持并发与超时重试
│   ├── metadata.py             # GitHub 仓库元数据镜像模块
│   ├── renderer.py             # 输出渲染器（HTML、JSON、Markdown 表格）
│   ├── indexer.py              # 标签索引与全文检索实现
│   └── utils.py                # 通用工具函数（日志、配置加载、文件操作）
│
├── manifests/                  # 用户定义的资源清单存放目录
│   ├── _template.md            # 清单编写模板与字段说明
│   ├── networking.md           # 网络与协议相关资源
│   ├── storage.md              # 存储与数据库相关资源
│   └── observability.md        # 可观测性与监控相关资源
│
├── docs/                       # 完整文档体系
│   ├── user-guide/
│   ├── admin-guide/
│   ├── developer-guide/
│   ├── design-decisions/
│   └── troubleshooting/
│
├── output/                     # 生成的仪表板与 JSON 数据（默认输出目录）
│   ├── index.html
│   ├── resources.json
│   └── health-report.json
│
├── tests/                      # 单元测试与集成测试
│   ├── test_parser.py
│   ├── test_checker.py
│   └── fixtures/
│
└── examples/                   # 示例资源清单与配置文件
    ├── sample_manifest.md
    └── sample_config.yaml
```

## 贡献指南

提交问题报告 在 GitHub Issues 页面选择对应的模板，清晰描述问题现象、复现步骤、预期结果与实际结果，并附上运行环境信息（Python 版本、操作系统、依赖包版本）。对于链接检查失败的情况，请提供失败 URL 与返回的 HTTP 状态码。

提交代码变更 从 main 分支创建功能分支（命名格式为 feature/功能简述 或 fix/问题简述），确保代码通过现有单元测试，并为新增功能添加对应的测试用例。提交前运行 `make lint` 与 `make test` 检查代码风格与测试覆盖率。

完善文档内容 文档位于 docs 目录，采用 Markdown 格式。修复拼写错误、补充缺失章节、更新过时示例均为有效贡献。对于新增功能，必须同步更新用户手册与开发者指南中的相关部分。

新增资源清单 在 manifests 目录下创建新的 .md 文件或更新现有文件，遵循 _template.md 中的字段约定。提交前运行 `python river_cli.py parse --manifest-path your_file.md --dry-run` 验证格式正确性。

审查与合并 所有拉取请求需要至少一位维护者批准后方可合并。大型功能变更请在拉取请求描述中附上设计思路与测试结果，以便加速审查流程。

## 常见问题

执行链接检查时出现大量超时错误如何解决
默认的超时时间为 5 秒，对于响应较慢的服务或位于网络质量不佳地区的资源，可通过命令行参数 `--timeout` 调整超时阈值，例如 `python river_cli.py check --timeout 15`。另外，检查器默认并发数为 20，可降低并发数以避免被目标服务器限流，使用 `--concurrency 5` 参数控制。

GitHub 元数据镜像提示 API 限流该怎么办
GitHub 未经认证的 API 请求限制为每小时 60 次。若资源列表中包含大量 GitHub 链接，建议配置个人访问令牌（Personal Access Token）以提高限额至每小时 5000 次。在项目根目录创建 `.env` 文件，添加 `GITHUB_TOKEN=your_token_here` 即可启用认证。

如何迁移浏览器书签或现有收藏夹数据
项目提供了 `import` 子命令，支持从 Chrome 导出的 HTML 书签文件（--from chrome-html）以及通用 CSV 文件（--from csv）进行导入。执行 `python river_cli.py import --from chrome-html --input bookmarks.html --output ./manifests/imported.md` 即可生成对应的资源清单文件。导入后建议手动检查标签映射与描述字段是否准确。

## 许可证

MIT

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
