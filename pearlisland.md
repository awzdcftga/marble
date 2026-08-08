# RiverMark

RiverMark 是一个面向技术团队与独立开发者的外链资源归集与文档索引工具。它不提供数据库后端，也不依赖任何 CMS，而是以纯 Markdown 文件为载体，将分散在多个仓库、多个文档站点、多个笔记系统中的外部链接与内部引用进行统一整理、分类和版本化管理。RiverMark 解决的核心问题是：当技术文档、API 参考、运维手册、设计规范等内容散落在不同域名和代码库中时，如何通过一个轻量级、可 Git 追踪、支持 PR 审核的资源清单来维持团队对外部依赖的可发现性与可追溯性。

RiverMark 定位为“技术资源的入口层”，适合用于微服务架构下的服务发现文档聚合、前端组件库的外部依赖清单、SRE 团队的运维链路汇总、以及开源社区的项目导航站。它不强调实时爬取或自动校验，而是强调人工维护的准确性与版本化控制的严谨性，让每一次链接的新增、变更或废弃都能通过 Git 历史追溯缘由。

## 功能概览

- **分层目录索引**：支持按主题、按项目、按环境、按阶段四个维度对资源进行任意深度的目录挂载，每个 Markdown 文件可同时归属于多个逻辑分类。

- **链接状态标记**：内置建议的链接状态字段（稳定/实验/废弃/外部依赖），便于维护者在资源变更时快速标注，消费者可据此评估引用风险。

- **全文检索友好**：所有资源描述与标签均以纯文本形式存储，配合 grep 或 IDE 全局搜索即可完成毫秒级定位，无需启动任何服务。

- **Markdown 元数据头**：每个资源条目支持 YAML Frontmatter，可记录添加人、添加日期、审核人、预期用途、关联 Issue 号等扩展信息。

- **变更历史审计**：依托 Git 原生能力，每次对资源列表的增删改均留下 commit 记录，支持回滚、blame 查询和 PR 讨论上下文关联。

- **批量导入辅助脚本**：项目提供 Python 辅助脚本，可将 CSV 或 JSON 格式的旧有链接清单批量转换为 RiverMark 标准格式，降低迁移成本。

- **Markdown 链接自动格式化**：维护时可直接书写裸 URL 或标准 Markdown 链接语法，项目自带的检查脚本会在 CI 阶段校验格式一致性。

- **资源预览静态站点生成**：可选集成简单的静态站点生成器，将资源列表渲染为带搜索框的 HTML 页面，供不熟悉 Git 的团队成员浏览。

## 应用场景

**场景一：微服务仓库的 API 文档入口聚合**  
某团队维护 20 余个微服务仓库，每个仓库的 README 中均散落着不同的外部依赖地址与内部文档链接。RiverMark 可作为顶层资源清单，集中记录所有服务的 Swagger 地址、监控面板、日志查询入口，新成员入职时仅需阅读一份资源文件即可了解全貌。

**场景二：开源社区的项目导航站**  
开源项目往往依赖多个上游项目、镜像站点、CI 服务、代码覆盖率平台。RiverMark 可为社区维护一份公开的资源索引文件，社区贡献者可提交 PR 更新链接，维护者审核合并后，项目官网可自动同步最新的资源列表。

**场景三：设计系统与组件库的外部依赖清单**  
组件库可能依赖图标库、字体服务、CDN 样式文件、设计令牌仓库等。RiverMark 可记录这些外部资源的版本建议与备用镜像地址，当主 CDN 不可用时，团队能快速从清单中找到替代方案。

**场景四：SRE 运维手册的链路拓扑记录**  
运维团队需要记录告警平台、日志系统、链路追踪 UI、容器编排面板、数据库管理界面等多个运维入口。RiverMark 可为每个环境（生产/预发布/测试）分别建立资源文件，并标注访问权限要求，降低故障时的入口寻找耗时。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/example/rivermark.git
cd rivermark

# 安装依赖（Python 3.8+ 与 pip）
pip install -r requirements.txt

# 运行本地预览服务器（可选）
python serve.py --port 8080

# 执行资源链接格式检查
python scripts/check_links.py --path ./resources
```

执行上述命令后，项目会启动一个本地静态预览服务，访问 http://localhost:8080 即可查看 resources 目录下的所有 Markdown 资源文件渲染结果。检查脚本会输出每个文件中的链接格式警告与错误，建议在提交前运行。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 用于运行辅助脚本与静态站点生成器 |
| Git | 2.25 及以上 | 版本控制与变更历史管理 |
| Markdown 解析器 | Python-markdown 3.3+ | 用于预览服务渲染 |
| PyYAML | 6.0+ | 解析资源条目中的 YAML Frontmatter |
| pytest | 7.0+ | 可选，用于运行单元测试套件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 概念 | docs/concepts/architecture.md | RiverMark 的设计理念、目录规范与资源生命周期定义 |
| 使用 | docs/usage/daily-maintenance.md | 日常如何新增、修改、废弃一条资源链接，如何书写描述 |
| 集成 | docs/integration/ci-setup.md | 如何在 GitHub Actions 或 GitLab CI 中配置链接检查步骤 |
| 扩展 | docs/extension/custom-theme.md | 如何替换预览站点的主题模板，增加自定义前端搜索逻辑 |

## 资源列表

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
- https://github.com/fcdujqa/river/blob/main/saffronprairie.md
- https://github.com/fcdujqa/river/blob/main/saffronzephyr.md
- https://github.com/fcdujqa/river/blob/main/shadowember.md
- https://github.com/fcdujqa/river/blob/main/shadowlantern.md
- https://github.com/fcdujqa/river/blob/main/shadowmidnight.md
- https://github.com/fcdujqa/river/blob/main/shadoworbit.md
- https://github.com/fcdujqa/river/blob/main/shadowtimber.md
- https://github.com/fcdujqa/river/blob/main/signalcosmic.md
- https://github.com/fcdujqa/river/blob/main/signaldelta.md
- https://github.com/fcdujqa/river/blob/main/signalharbor.md
- https://github.com/fcdujqa/river/blob/main/signalshadow.md
- https://github.com/fcdujqa/river/blob/main/signalsummit.md
- https://github.com/fcdujqa/river/blob/main/silvercanvas.md
- https://github.com/fcdujqa/river/blob/main/silverfield.md

## 项目结构

```
rivermark/
├── resources/                      # 核心资源目录，存放所有 Markdown 资源清单文件
│   ├── infrastructure/             # 基础设施类资源（数据库面板、消息队列控制台等）
│   ├── services/                   # 微服务 API 文档与内部接口地址
│   ├── frontend/                   # 前端组件库、设计系统、图标库等前端相关资源
│   ├── operations/                 # SRE 运维工具、监控告警、日志平台入口
│   └── community/                  # 社区项目、论坛、邮件列表、社交媒体账号
├── scripts/                        # 辅助工具脚本
│   ├── check_links.py              # 链接格式与可达性检查（CI 集成用）
│   ├── import_from_csv.py          # 从 CSV 批量导入旧链接清单
│   └── generate_index.py           # 根据资源文件生成汇总索引页
├── docs/                           # 项目文档
│   ├── concepts/                   # 设计概念与架构说明
│   ├── usage/                      # 日常使用与维护指南
│   ├── integration/                # 第三方集成与 CI 配置示例
│   └── extension/                  # 自定义扩展开发文档
├── templates/                      # 静态预览站点的 HTML 模板文件
│   ├── base.html                   # 基础布局模板
│   └── resource_list.html          # 资源列表渲染模板
├── tests/                          # 单元测试与集成测试用例
│   ├── test_check_links.py         # 链接检查函数的测试
│   └── test_import.py              # 导入脚本的测试数据与断言
├── serve.py                        # 本地预览服务的入口脚本
├── requirements.txt                # Python 依赖声明
└── README.md                       # 项目主说明文档（当前文件）
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆到本地开发环境。确保本地 Python 版本符合安装要求，且已安装所有开发依赖。

2. 在 resources 目录下找到与待添加资源最匹配的子目录。若不存在合适子目录，可先通过 Issue 讨论新建目录的必要性，避免目录层级过深。

3. 新建或编辑 Markdown 资源文件，每条资源使用标准列表语法 `- [描述](URL)` 或 `- URL` 格式。若资源存在有效期或访问限制，请在条目后以括号注明。

4. 本地运行 `python scripts/check_links.py --path ./resources` 检查格式无误，确保没有语法警告或链接格式错误。

5. 提交 Pull Request，在 PR 描述中说明本次新增或变更的资源用途、来源以及预期受众。等待维护者审核，合并后资源即正式纳入项目索引。

## 常见问题

**问：RiverMark 是否会自动检测链接是否可访问或是否已失效？**  
答：项目本身不强制自动检测，但提供了 `check_links.py` 脚本，该脚本支持可选的网络请求模式以验证链接可达性。CI 流程中默认仅执行格式检查，不会自动发起外部请求，避免网络环境差异导致的误报。团队可根据自身 CI 环境配置定期触发的完全检测任务。

**问：如何管理同一资源在不同文件中的重复引用？**  
答：RiverMark 允许同一 URL 在不同上下文中出现，不强制去重。建议在资源描述中明确区分引用场景，例如“生产环境 API 网关”与“测试环境 API 网关”虽然指向同一域名，但路径不同或用途不同时应分别记录。若确认为完全重复的冗余条目，可通过 PR 移除并合并描述。

**问：静态预览站点是否支持搜索与标签过滤？**  
答：基础预览站点提供了简单的浏览器端关键词搜索，基于 JavaScript 对页面渲染内容进行过滤。标签过滤功能需要额外配置，可通过扩展模板目录中的 JavaScript 文件自行增强，项目文档的扩展章节提供了具体指引。

## 许可证

MIT

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
