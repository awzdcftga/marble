# RiverLink

RiverLink 是一个面向技术研究者和基础设施工程师的轻量级外链与文档资源聚合工具。项目定位为“技术文档的文档”，用于集中管理散布在代码仓库、技术博客、内部 Wiki 和外部知识库中的高价值引用链接，并通过结构化分类与版本化追踪，降低信息漂移和链接失效对研发效率的影响。

目标用户包括：需要维护大量外部依赖文档的 SDK 维护者、从事技术选型的架构师、编写技术周报或调研报告的研究人员，以及希望建立内部技术知识图谱的团队。RiverLink 本身不存储文档内容，只提供索引、校验、分类和快速跳转能力，配合自动化脚本可对链接集合进行定期可达性检查与元数据更新。

## 功能概览

批量链接导入：支持从 Markdown 表格、CSV 文件和纯文本列表中批量导入链接，自动提取标题或文件名作为展示名称。

链接分类标签：允许为每个链接附加多个自定义标签，例如“依赖库文档”、“设计提案”、“性能测试报告”等，便于按主题筛选。

状态标记与校验：内置基于 HEAD 请求的链接可达性检查，标记异常状态（200/404/超时）并记录最后检查时间。

版本化快照：每次更新链接列表时自动生成版本快照，支持回滚至任意历史版本，便于追溯引用变更。

全文搜索与过滤：基于链接的 URL、文件名、标签和描述字段提供轻量级全文搜索，支持正则表达式过滤。

静态站点生成：内置模板引擎可将链接列表导出为静态 HTML 目录页，适合部署为内部团队首页或项目导航站。

元数据扩展字段：允许为每个链接添加“所属项目”、“维护人”、“最后验证日期”等自定义键值对，适配不同团队的管理规范。

## 应用场景

技术选型调研：在进行中间件或存储系统选型时，工程师可将备选项目的官网、GitHub 仓库、性能测试报告、社区讨论帖等链接统一录入 RiverLink，形成可横向对比的索引表，并通过标签快速筛选出具有“生产验证”或“长期维护”标记的资源。

内部知识库构建：研发团队可将散布在 Confluence、Notion 和 Google Docs 中的设计文档、决策记录和故障复盘报告链接汇总至 RiverLink，并为每个链接标注“所属子系统”和“评审状态”，使新人能够通过该索引快速理解系统全貌。

依赖文档版本追踪：对于依赖多个开源组件的项目，可使用 RiverLink 记录每个组件的官方文档地址、API 参考和迁移指南。当组件升级时，管理员可批量更新链接并利用版本快照对比变更，确保团队文档始终指向正确的版本页面。

技术周报自动化：技术负责人可将每周关注的行业博客、新发布工具和重要 PR 链接统一录入 RiverLink，导出为带分类标题的 Markdown 列表，直接粘贴至周报中，减少重复整理工作。

## 快速开始

以下步骤将指导您在本地环境快速启动 RiverLink 服务。

```bash
# 克隆仓库
git clone https://github.com/riverlink/riverlink.git
cd riverlink

# 安装依赖（使用 pip 和 npm）
pip install -r requirements.txt
npm install --prefix frontend

# 初始化数据库并构建前端
python scripts/init_db.py
npm run build --prefix frontend

# 启动开发服务器（默认端口 8080）
python app.py --port 8080
```

启动后，访问 `http://localhost:8080` 即可进入 RiverLink 管理界面。首次运行会自动创建示例链接分类和一条欢迎链接。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 或更高 | 后端运行环境，核心逻辑与 API 服务 |
| Node.js | 18.x 或 20.x LTS | 用于构建前端静态资源与搜索索引 |
| SQLite | 3.35 或更高 | 默认嵌入式数据库，用于存储链接元数据和版本快照 |
| Git | 2.30 或更高 | 用于版本快照功能中的自动提交记录 |
| curl | 7.68 或更高 | 用于链接可达性检查的后备工具（可选，推荐） |
| make | 3.81 或更高 | 用于执行构建脚本和测试套件（开发环境） |
| redis | 6.0 或更高 | 可选，用于提升搜索并发性能（生产环境推荐） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何安装、配置并运行第一个实例，以及如何导入第一批链接 |
| 链接管理 | docs/link-management.md | 如何增删改链接、批量导入、设置标签和自定义元数据 |
| 自动化运维 | docs/automation.md | 如何配置定时校验、版本快照策略以及静态站点自动发布 |
| 扩展开发 | docs/development.md | 如何编写自定义标签插件、添加新的导入格式以及贡献前端组件 |

## 资源列表

- https://github.com/fcdujqa/river/blob/main/cobaltvelvet.md
- https://github.com/fcdujqa/river/blob/main/cobaltwillow.md
- https://github.com/fcdujqa/river/blob/main/coralhorizon.md
- https://github.com/fcdujqa/river/blob/main/coralmirror.md
- https://github.com/fcdujqa/river/blob/main/coralprairie.md
- https://github.com/fcdujqa/river/blob/main/coralriver.md
- https://github.com/fcdujqa/river/blob/main/coralsilver.md
- https://github.com/fcdujqa/river/blob/main/coraltimber.md
- https://github.com/fcdujqa/river/blob/main/cosmicdelta.md
- https://github.com/fcdujqa/river/blob/main/cosmicfalcon.md
- https://github.com/fcdujqa/river/blob/main/cosmicgarden.md
- https://github.com/fcdujqa/river/blob/main/cosmicgolden.md
- https://github.com/fcdujqa/river/blob/main/cosmicorbit.md
- https://github.com/fcdujqa/river/blob/main/cosmicquartz.md
- https://github.com/fcdujqa/river/blob/main/cosmicsilver.md
- https://github.com/fcdujqa/river/blob/main/cosmicwillow.md
- https://github.com/fcdujqa/river/blob/main/crystalamber.md
- https://github.com/fcdujqa/river/blob/main/crystalharbor.md
- https://github.com/fcdujqa/river/blob/main/crystalmaple.md
- https://github.com/fcdujqa/river/blob/main/crystalocean.md
- https://github.com/fcdujqa/river/blob/main/crystalorbit.md
- https://github.com/fcdujqa/river/blob/main/crystalpearl.md
- https://github.com/fcdujqa/river/blob/main/crystalsummit.md
- https://github.com/fcdujqa/river/blob/main/crystaltimber.md
- https://github.com/fcdujqa/river/blob/main/crystalwillow.md
- https://github.com/fcdujqa/river/blob/main/deltacedar.md
- https://github.com/fcdujqa/river/blob/main/deltagarden.md
- https://github.com/fcdujqa/river/blob/main/deltamarble.md
- https://github.com/fcdujqa/river/blob/main/deltaocean.md
- https://github.com/fcdujqa/river/blob/main/deltawander.md
- https://github.com/fcdujqa/river/blob/main/emberbridge.md
- https://github.com/fcdujqa/river/blob/main/emberfield.md
- https://github.com/fcdujqa/river/blob/main/emberforest.md
- https://github.com/fcdujqa/river/blob/main/embergolden.md
- https://github.com/fcdujqa/river/blob/main/embernebula.md
- https://github.com/fcdujqa/river/blob/main/falconbright.md
- https://github.com/fcdujqa/river/blob/main/falconcoral.md
- https://github.com/fcdujqa/river/blob/main/falconcosmic.md
- https://github.com/fcdujqa/river/blob/main/falcongarden.md
- https://github.com/fcdujqa/river/blob/main/falconharbor.md
- https://github.com/fcdujqa/river/blob/main/falconmidnight.md
- https://github.com/fcdujqa/river/blob/main/falconmirror.md
- https://github.com/fcdujqa/river/blob/main/falconquartz.md
- https://github.com/fcdujqa/river/blob/main/falconriver.md
- https://github.com/fcdujqa/river/blob/main/falconsignal.md
- https://github.com/fcdujqa/river/blob/main/fieldbright.md
- https://github.com/fcdujqa/river/blob/main/fieldember.md
- https://github.com/fcdujqa/river/blob/main/fieldfalcon.md
- https://github.com/fcdujqa/river/blob/main/fieldgolden.md
- https://github.com/fcdujqa/river/blob/main/fieldhorizon.md
- https://github.com/fcdujqa/river/blob/main/fieldnebula.md
- https://github.com/fcdujqa/river/blob/main/forestmeadow.md
- https://github.com/fcdujqa/river/blob/main/forestshadow.md
- https://github.com/fcdujqa/river/blob/main/forestsummit.md
- https://github.com/fcdujqa/river/blob/main/forestvelvet.md
- https://github.com/fcdujqa/river/blob/main/forestwillow.md
- https://github.com/fcdujqa/river/blob/main/gardencobalt.md
- https://github.com/fcdujqa/river/blob/main/gardencoral.md
- https://github.com/fcdujqa/river/blob/main/gardennebula.md
- https://github.com/fcdujqa/river/blob/main/gardenocean.md
- https://github.com/fcdujqa/river/blob/main/gardenolive.md
- https://github.com/fcdujqa/river/blob/main/gardenquartz.md
- https://github.com/fcdujqa/river/blob/main/gardenriver.md
- https://github.com/fcdujqa/river/blob/main/gardensaffron.md
- https://github.com/fcdujqa/river/blob/main/gardensilver.md
- https://github.com/fcdujqa/river/blob/main/gardentimber.md
- https://github.com/fcdujqa/river/blob/main/gardenwillow.md
- https://github.com/fcdujqa/river/blob/main/goldenatlas.md
- https://github.com/fcdujqa/river/blob/main/goldenember.md
- https://github.com/fcdujqa/river/blob/main/goldenharbor.md
- https://github.com/fcdujqa/river/blob/main/goldenhorizon.md
- https://github.com/fcdujqa/river/blob/main/goldenmirror.md
- https://github.com/fcdujqa/river/blob/main/goldenviolet.md
- https://github.com/fcdujqa/river/blob/main/harborbridge.md
- https://github.com/fcdujqa/river/blob/main/harborcloud.md
- https://github.com/fcdujqa/river/blob/main/harbormarble.md
- https://github.com/fcdujqa/river/blob/main/harborprairie.md
- https://github.com/fcdujqa/river/blob/main/horizoncoral.md
- https://github.com/fcdujqa/river/blob/main/horizoncrystal.md
- https://github.com/fcdujqa/river/blob/main/islandcosmic.md
- https://github.com/fcdujqa/river/blob/main/islandfield.md
- https://github.com/fcdujqa/river/blob/main/islandgolden.md
- https://github.com/fcdujqa/river/blob/main/islandwander.md
- https://github.com/fcdujqa/river/blob/main/islandwillow.md
- https://github.com/fcdujqa/river/blob/main/jadecanvas.md
- https://github.com/fcdujqa/river/blob/main/jadehorizon.md
- https://github.com/fcdujqa/river/blob/main/jadelantern.md
- https://github.com/fcdujqa/river/blob/main/jadepearl.md
- https://github.com/fcdujqa/river/blob/main/jadepixel.md
- https://github.com/fcdujqa/river/blob/main/jadetimber.md
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

## 项目结构

```
riverlink/
├── app.py                     # 主入口，Flask 应用实例与路由注册
├── config/
│   ├── default.py             # 默认配置（端口、数据库路径、校验间隔）
│   └── production.py          # 生产环境覆盖配置（外部 Redis、日志级别）
├── core/
│   ├── link_manager.py        # 链接增删改查、标签管理核心逻辑
│   ├── checker.py             # 异步链接可达性检查器（基于 aiohttp）
│   └── snapshot.py            # 版本快照生成与回滚（基于 Git 和 SQLite）
├── frontend/
│   ├── src/
│   │   ├── components/        # Vue.js 组件（链接列表、搜索栏、标签过滤器）
│   │   ├── stores/            # Pinia 状态管理（链接列表、筛选条件、UI 状态）
│   │   └── assets/            # 静态资源（CSS 变量、字体、图标）
│   └── dist/                  # 构建输出（由 npm run build 生成，不纳入版本库）
├── scripts/
│   ├── init_db.py             # 初始化 SQLite 表结构及索引
│   ├── import_csv.py          # 从 CSV 批量导入链接（支持自定义列映射）
│   └── export_static.py       # 导出静态 HTML 目录页
├── tests/
│   ├── unit/                  # 单元测试（pytest 框架，覆盖链接管理逻辑）
│   └── integration/           # 集成测试（含 Flask 客户端与测试数据库）
├── docs/                      # 详细文档（入门、运维、开发指南）
├── requirements.txt           # Python 依赖清单（Flask, aiohttp, jinja2 等）
├── package.json               # Node.js 依赖清单（Vue, Vite, Pinia）
└── Makefile                   # 常用命令封装（install, test, build, run）
```

## 贡献指南

1. 阅读贡献手册：在提交代码或文档前，请先阅读 `CONTRIBUTING.md`，了解编码规范、提交信息格式和分支命名规则。

2. 选择未认领 Issue：从 GitHub Issues 中筛选带有 `help wanted` 或 `good first issue` 标签的任务，在评论中声明认领，避免重复工作。

3. 开发环境准备：运行 `make install` 安装所有依赖，并执行 `make test` 确保本地环境通过全部单元测试后再进行修改。

4. 提交变更并创建 PR：使用 `feature/` 或 `fix/` 前缀创建分支，提交时遵循语义化提交信息（`feat:`, `fix:`, `docs:` 等），随后发起 Pull Request 并至少请求一名维护者 Review。

5. 更新资源列表：如需新增或移除外部链接，请通过 `scripts/import_csv.py` 或管理界面操作，不可直接手动编辑资源列表章节，以确保版本快照的一致性。

## 常见问题

**问：RiverLink 是否支持 HTTPS 和私有仓库中的链接？**

答：支持。RiverLink 仅存储链接字符串并调用系统网络库进行校验，不依赖任何特定的协议或权限模型。对于需要认证的私有仓库链接，可通过配置 `checker.py` 中的自定义请求头或环境变量注入访问令牌，但系统本身不会保存任何凭证。

**问：如何迁移已有的链接收藏夹或书签文件？**

答：RiverLink 提供了 `scripts/import_csv.py` 脚本，可将标准的 CSV 格式（列：URL, title, tags, description）导入系统。对于浏览器导出的 HTML 书签文件，建议先使用第三方工具转换为 CSV，或自行编写简单的解析脚本。社区已有人贡献了 Chrome 书签转换脚本，可在 `contrib/` 目录下找到。

**问：大规模链接（超过 5000 条）时性能如何？**

答：默认 SQLite 配置在 10000 条以内查询响应时间小于 50ms，搜索功能基于 FTS5 全文索引，性能线性可接受。若链接数量超过 50000 条或并发查询超过 50 QPS，建议启用 Redis 缓存（配置 `production.py` 中的 `CACHE_ENABLED` 选项）并将数据库迁移至 PostgreSQL。详细的性能调优参数请参阅 `docs/performance.md`。

## 许可证

MIT

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
