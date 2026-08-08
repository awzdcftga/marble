# River

River 是一个面向开发者与研究员的技术资源聚合与导航系统，专注于对分散在开源社区、技术博客、学术仓库中的高质量外链进行结构化整理与可检索化呈现。项目本身不存储任何实际内容，而是通过索引、分类、标签与注释机制，构建一个可复用、可扩展的外部知识图谱。

River 的目标用户包括技术文档维护者、DevOps 工程师、架构师以及需要长期跟踪特定技术领域动态的研究人员。项目提供一套完整的工具链，用于从原始 URL 集合中提取元数据、生成分类索引，并以静态站点或 API 形式对外提供查询服务。River 的核心价值在于将无结构的链接清单转化为具有领域语义的导航树，从而降低信息检索成本，提升技术调研效率。

## 功能概览

- 批量外链导入与元数据解析：支持从纯文本列表、Markdown 表格或 CSV 文件中批量导入 URL，自动发起 HEAD 请求获取响应头信息，提取 Content-Type、Last-Modified、Content-Length 等基础元数据，并尝试从 HTML 标题与 meta 描述中抓取页面摘要。

- 多维度标签分类体系：允许用户为每个资源条目附加多个自定义标签，内置推荐标签库涵盖编程语言、框架名称、部署平台、文档类型（教程、参考、规范）等维度。支持标签继承与别名，便于建立层级化分类结构。

- 语义化搜索与过滤接口：基于关键词匹配与标签交集运算提供搜索功能，支持按域名、文件类型、更新时间范围进行过滤。搜索接口返回排序后的结果列表，并附带相关性评分。

- 快照与变更监控：定期对已收录的 URL 进行可用性检查与内容变更检测，当目标页面返回 4xx 或 5xx 状态码，或 Last-Modified 发生显著变动时，触发通知记录。变更历史以时间线形式存储。

- 静态站点生成器：内置模板引擎，可将索引数据渲染为纯 HTML 静态页面，支持响应式布局与深色模式。生成的站点无需后端服务即可部署到对象存储或 CDN 上，适合作为团队内部的知识门户。

- 开放 API 服务：提供基于 JSON 的 RESTful API，支持分页查询、按标签聚合统计、随机推荐等端点，方便与其他内部系统集成。API 响应包含缓存控制头，降低上游压力。

## 应用场景

技术团队内部知识库构建：团队可以将日常积累的参考链接、踩坑记录、官方文档入口统一录入 River，并按照项目模块打上标签。新成员加入时，通过 River 的分类导航即可快速了解团队常用的技术栈与学习路径。

技术调研与竞品分析：在进行选型或竞品对比时，研究员可以批量收集相关产品的官方文档、社区案例、性能测试报告等链接，利用 River 的标签系统区分维度（如性能、生态、许可证），随后通过导出功能生成结构化调研报告。

开源项目文档站的外链附录维护：开源项目维护者可以在项目仓库的 docs 目录下维护一个 links.md 文件，记录依赖项目、相关工具、拓展阅读等外链。River 提供命令行工具，可将该文件自动转换为带有存活检测标记的 HTML 附录页面，随项目站点一并发布。

个人技术阅读清单管理：开发者可将待读文章、待看视频、待研究的仓库统一收录至 River，利用标签标记阅读状态（待读、在读、已读）与优先级，通过 API 集成到本地通知脚本中，定时推送未读条目。

## 快速开始

以下操作假设您已安装 Git 与 Node.js 环境。River 采用纯 JavaScript 编写，运行时依赖 Node.js 18.0 及以上版本。

```bash
# 克隆仓库
git clone https://github.com/fcdujqa/river.git
cd river

# 安装依赖
npm install

# 构建索引并启动开发服务器
npm run build
npm start
```

执行完毕后，访问 http://localhost:3000 即可查看本地的 River 实例。默认会加载 `data/sample.json` 作为演示数据。您可以通过替换 `data/links.json` 文件来导入自己的链接集合。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | 18.0.0 或更高 | 运行时环境，用于执行核心脚本与启动服务 |
| npm | 9.0.0 或更高 | 包管理器，用于安装依赖项 |
| Git | 2.30.0 或更高 | 版本控制工具，用于克隆仓库与提交更新 |
| SQLite3 | 系统自带或通过 npm 安装 | 轻量级嵌入式数据库，用于存储元数据与索引 |
| curl | 7.68.0 或更高（可选） | 用于外部健康检查脚本，若缺失则回退为内置 http 模块 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门 | /docs/quickstart.md | 如何在一小时内完成 River 的初次配置并导入第一批链接？ |
| 配置 | /docs/configuration.md | 如何修改分类规则、自定义标签库、调整监控频率与通知渠道？ |
| 开发 | /docs/development.md | 如何扩展元数据解析器、增加新的输出格式或贡献核心代码？ |
| 运维 | /docs/operations.md | 如何部署生产环境、配置反向代理、执行数据备份与迁移？ |

## 资源列表

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

## 项目结构

```
river/
├── bin/                           # 可执行脚本入口
│   └── cli.js                     # 命令行交互入口，处理 build/start/check 子命令
├── src/                           # 核心源代码
│   ├── core/                      # 核心逻辑模块
│   │   ├── indexer.js             # 索引构建器，负责遍历链接、调用解析器并写入数据库
│   │   ├── parser.js              # 元数据解析器，封装对 URL 的 HEAD/GET 请求与 HTML 解析
│   │   ├── monitor.js             # 变更监控调度器，定时执行可用性与内容变更检查
│   │   └── tags.js                # 标签系统，管理标签别名、继承关系与推荐逻辑
│   ├── api/                       # RESTful API 实现
│   │   ├── routes.js              # 路由定义，挂载查询、统计、导出等端点
│   │   └── handlers.js            # 请求处理器，含参数校验、数据库查询与响应格式化
│   ├── render/                    # 静态站点渲染引擎
│   │   ├── template.js            # 模板编译与渲染函数，支持布局与组件复用
│   │   ├── assets/                # 静态资源（CSS、JavaScript、字体）
│   │   └── pages/                 # 页面级模板（首页、分类页、详情页）
│   ├── db/                        # 数据库层
│   │   ├── schema.sql             # SQLite 建表语句（links、tags、snapshots、config）
│   │   └── client.js              # 数据库连接池与 CRUD 操作封装
│   └── utils/                     # 通用工具函数
│       ├── http.js                # 封装 axios 与重试策略，处理超时与状态码判断
│       ├── logger.js              # 分级日志记录器，支持文件输出与控制台彩色打印
│       └── validator.js           # URL 校验、标签名合法性检查、日期格式解析
├── data/                          # 数据存储目录
│   ├── links.json                 # 用户导入的原始链接清单（JSON 数组格式）
│   └── river.db                   # SQLite 数据库文件（运行时生成）
├── docs/                          # 项目文档
│   ├── quickstart.md
│   ├── configuration.md
│   ├── development.md
│   └── operations.md
├── config/                        # 配置文件目录
│   ├── default.yaml               # 默认配置（端口、监控间隔、标签库路径）
│   └── custom.yaml.example        # 自定义配置示例，用户可复制后修改
├── test/                          # 单元测试与集成测试
│   ├── unit/                      # 单元测试（针对 parser、tags、validator 等）
│   └── integration/               # 集成测试（端到端 API 测试、数据库迁移测试）
├── .github/                       # GitHub 相关配置
│   └── workflows/                 # CI 流水线定义（测试覆盖率检查、构建验证）
│       └── ci.yml
├── package.json                   # npm 包描述文件，定义依赖与脚本命令
├── README.md                      # 项目介绍与使用指南（本文件）
└── LICENSE                        # MIT 许可证文本
```

## 贡献指南

1. 查阅 issue 列表与项目看板，确认当前迭代周期内的待办事项。选择未被认领且与自身技能匹配的任务，在 issue 下留言说明认领意向，等待维护者确认以避免重复工作。

2. 从主分支派生个人副本，在本地新建特性分支进行开发。分支命名遵循 `feature/功能简述` 或 `fix/问题编号` 格式。提交信息采用约定式提交规范（Conventional Commits），以便于自动生成变更日志。

3. 编写或修改代码时，同步更新对应的单元测试与文档说明。新增的解析器逻辑需附带测试用例覆盖主流场景与边界情况。文档更新需确保 `docs/` 目录下的 Markdown 文件与代码行为保持一致。

4. 提交前运行完整的测试套件与代码检查工具。执行 `npm run lint` 与 `npm test`，确保所有检查项通过且测试覆盖度不低于现有基线。若引入破坏性变更，需在请求正文中明确标注并说明迁移方案。

5. 发起拉取请求至主分支，在请求描述中引用相关 issue 编号，简要说明实现思路与测试结果。维护者将在三个工作日内进行审查，提出修改意见或合并。合并后特性分支将被删除。

## 常见问题

问：River 是否支持对需要登录或带有反爬机制的页面进行检测？

答：当前版本仅支持公开可访问的 URL，不提供表单登录、Cookie 维持或 JavaScript 渲染能力。对于需要登录的页面，建议使用监控模块的忽略规则跳过检测，或通过配置代理头（如 User-Agent、Referer）来降低被拦截概率。若目标页面为 GitHub 仓库下的 Markdown 文件，可直接使用 Raw 链接以获取稳定响应。

问：如何迁移已有的链接收藏夹或书签导出文件到 River？

答：River 内置了一个轻量转换脚本，位于 `bin/import.js`。该脚本支持解析 Netscape 格式的书签导出文件（HTML）、CSV 列文件以及 JSON 键值对格式。执行 `node bin/import.js --format=csv --path=bookmarks.csv` 即可将数据导入 `data/links.json`。导入后运行 `npm run build` 重新构建索引即可生效。对于自定义格式，可参考 `data/links.json` 的结构编写简单转换脚本。

问：静态站点生成后的页面能否部署到 GitHub Pages 或 Cloudflare Pages？

答：完全可以。生成的静态文件全部位于 `dist/` 目录下，包含 index.html、分类页、详情页以及 assets 子目录。将 `dist/` 目录下的所有文件推送至任意静态托管服务的根目录即可。站点内部所有链接均采用相对路径，无需额外配置。若需要自定义域名，可在托管服务商处添加 CNAME 记录，并在 `config/default.yaml` 中修改 `siteBaseUrl` 字段以确保 RSS 订阅链接正确生成。

## 许可证

MIT

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
