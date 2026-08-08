# River Mark

River Mark 是一个面向开发者与技术研究人员的轻量化外链资源汇总工具，基于 GitHub 仓库 `fcdujqa/river` 下的 Markdown 文件构建，将分散在不同分支与目录中的技术笔记、参考链接、项目文档与学习资源统一聚合为可检索、可分类、可导出的结构化数据。项目本身不依赖数据库，不存储用户数据，只提供对公开 Markdown 文件的解析、索引与展示能力。

项目定位为“技术外链的静态门户”，目标用户包括正在整理个人知识库的开发者、需要维护团队技术周报的工程效率负责人、以及希望从零快速搭建资源导航站的开源爱好者。通过将链接、摘要、标签与阅读状态固化在 Markdown 文件的 frontmatter 或正文首段中，River Mark 能够在构建时生成按主题、时间或热度排序的导航页面，同时保留原始文件的 GitHub 编辑路径，使维护者可以直接在浏览器中完成增删改操作，无需登录额外后台。

## 功能概览

自动扫描指定 GitHub 仓库目录下的 Markdown 文件，提取标题、标签、描述与外部链接

支持基于文件名前缀与目录结构的自动分类，如 `wander` 系列、`willow` 系列、`zephyr` 系列

生成静态 HTML 索引页，按更新时间倒序排列，并提供全文关键词搜索

提供链接状态标记，包括“未读”、“已读”、“待整理”、“归档”四种状态，状态存储在文件尾部自定义注释块中

支持一键导出当前筛选结果为纯文本 URL 列表，方便批量导入其他工具

提供 RSS feed 输出，订阅者可获知新增或更新资源的通知

内置简单的链接可用性检查，在构建时对每个外链发送 HEAD 请求并记录状态码

## 应用场景

个人技术阅读清单管理：开发者将每周阅读的博客、论文、官方文档链接整理为 Markdown 文件，存入 `river` 仓库，River Mark 自动生成可公开访问的阅读列表，支持按状态过滤，避免链接丢失或遗忘。

团队周报汇总：技术团队每周将组内成员分享的工程实践、故障复盘、性能优化案例以固定格式写入 Markdown，River Mark 聚合后生成周报门户页面，新成员可快速回溯历史内容。

开源文档外链维护：开源项目维护者将项目依赖的规范、教程、参考实现等外链集中存放在 `river` 仓库的子目录中，River Mark 提供干净的导航界面，避免 README 过度臃肿，同时保留版本历史。

离线知识库镜像：用户可将所有引用的外链通过脚本批量存档至本地或 IPFS，River Mark 生成的索引文件可作为目录卡片，配合离线浏览器实现无网络查阅。

## 快速开始

以下命令可在本地启动 River Mark 开发实例，默认使用仓库 `fcdujqa/river` 的 main 分支作为数据源。

```bash
git clone https://github.com/yourname/river-mark.git
cd river-mark
npm install
npm run build -- --repo fcdujqa/river --path /main
npm start
```

执行完成后，访问 `http://127.0.0.1:8080` 即可看到索引页面。如需指定分支或子目录，可在 `--path` 后追加，例如 `--path /main/docs/links`。构建产物默认输出到 `./dist` 目录，可直接部署至静态托管服务。

## 安装要求

| 依赖 | 必需 | 说明 |
|---|---|---|
| Node.js 20.x 或更高 | 是 | 运行时环境，用于执行构建脚本与开发服务器 |
| npm 9.x 或更高 | 是 | 包管理器，用于安装依赖与执行脚本命令 |
| git 2.30 或更高 | 是 | 用于克隆仓库以及后续增量更新时拉取最新内容 |
| 网络访问 github.com | 是 | 构建过程需要读取 fcdujqa/river 仓库的 raw 内容 |
| 内存 512 MB 以上 | 否 | 大型仓库（超过 2000 个 Markdown 文件）建议 1 GB 以上 |
| 可选：curl 或 wget | 否 | 用于外部链接可用性检查（默认使用 Node.js http 模块） |
| 可选：jq | 否 | 若需要解析 JSON 格式的配置文件，可安装用于命令行过滤 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide.md | 如何浏览索引、搜索资源、查看状态、导出链接列表 |
| 维护指南 | /docs/maintainer-guide.md | 如何添加或删除 Markdown 文件、如何修改分类规则、如何更新状态标记 |
| 配置参考 | /docs/config-reference.md | 环境变量与命令行参数的完整列表，包括端口、分支、缓存策略等 |
| 设计说明 | /docs/design-notes.md | 索引数据结构、构建流程、缓存失效机制、扩展点说明 |
| 部署示例 | /docs/deployment-examples.md | 如何部署到 Vercel、Netlify、Cloudflare Pages 或自建 Nginx 服务器 |
| 故障排查 | /docs/troubleshooting.md | 常见构建错误、网络超时处理、文件解析异常的解决办法 |

## 资源列表

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

## 项目结构

```
river-mark/
├── bin/                           # 可执行脚本入口
│   └── river-mark.js              # CLI 主程序，处理参数解析与命令分发
├── src/                           # 核心源码目录
│   ├── core/                      # 核心逻辑模块
│   │   ├── scanner.js             # 扫描 GitHub 文件列表，过滤 Markdown
│   │   ├── parser.js              # 解析 frontmatter、标题、正文首段与尾部注释
│   │   ├── indexer.js             # 构建倒排索引与分类映射
│   │   └── checker.js             # 外链可用性检查（HEAD 请求）
│   ├── adapters/                  # 适配器层，对接不同数据源
│   │   ├── github.js              # 通过 GitHub REST API 获取文件内容
│   │   └── local.js               # 读取本地文件系统，用于离线调试
│   ├── output/                    # 输出生成器
│   │   ├── html.js                # 生成静态 HTML 索引页与详情页
│   │   ├── rss.js                 # 生成 RSS 2.0 订阅源
│   │   └── plain.js               # 导出纯文本 URL 列表
│   ├── server/                    # 开发服务器与热重载
│   │   ├── dev.js                 # 启动 Express 服务器，提供实时预览
│   │   └── watcher.js             # 监听文件变化并触发增量构建
│   └── utils/                     # 通用工具函数
│       ├── cache.js               # 内存缓存与文件缓存管理
│       ├── logger.js              # 分级日志输出（info/warn/error）
│       └── config.js              # 读取 .env 与默认配置合并
├── templates/                     # HTML 模板文件（EJS 格式）
│   ├── layout.ejs                 # 全局布局模板
│   ├── index.ejs                  # 资源列表页模板
│   └── detail.ejs                 # 单个资源详情页模板
├── dist/                          # 构建输出目录（git 忽略）
├── test/                          # 单元测试与集成测试
│   ├── unit/                      # 针对 parser、scanner 的独立测试
│   └── integration/               # 端到端测试，模拟真实 GitHub 请求
├── docs/                          # 项目文档（用户手册、维护指南等）
├── .env.example                   # 环境变量示例文件
├── package.json                   # npm 依赖与脚本声明
├── README.md                      # 项目说明（本文档）
└── LICENSE                        # MIT 许可证文件
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，并克隆到本地开发环境。建议在 dev 分支上进行修改，避免直接操作 main 分支。

2. 运行 `npm install` 安装所有开发依赖，包括测试框架与代码检查工具。安装完成后执行 `npm run lint` 检查代码风格是否符合项目 ESLint 配置。

3. 修改或新增功能时，请同步更新对应的单元测试，确保测试覆盖率达到 80% 以上。测试命令为 `npm run test`。

4. 提交前执行 `npm run build` 确认构建可通过，并手动检查生成的 `dist/index.html` 在浏览器中显示正常。

5. 提交 Pull Request 时，请在描述中说明变更动机、影响范围以及是否包含破坏性改动。项目维护者会在 3 个工作日内完成 Review。

## 常见问题

问：项目启动后页面显示“No data found”，可能是什么原因？

答：最常见的原因是网络无法访问 GitHub API，或者仓库名、分支名、路径参数填写错误。请先确认 `fcdujqa/river` 仓库是公开状态，且 `main` 分支下存在至少一个 `.md` 文件。可以在浏览器中直接访问 `https://raw.githubusercontent.com/fcdujqa/river/main/wanderbridge.md` 测试连通性。若使用代理，请检查 `HTTP_PROXY` 环境变量是否设置正确。

问：构建日志中出现“Rate limit exceeded”错误，如何解决？

答：GitHub 对未认证的 API 请求限制为每小时 60 次。可通过设置 `GITHUB_TOKEN` 环境变量提供个人访问令牌，将限制提升至每小时 5000 次。在项目根目录下创建 `.env` 文件，写入 `GITHUB_TOKEN=ghp_xxxxxx` 即可。注意不要将 `.env` 提交到公共仓库。

问：如何添加自定义分类，例如按“前端/后端/运维”来组织资源？

答：在 Markdown 文件的 frontmatter 中添加 `category` 字段，例如 `category: 前端`，构建器会自动识别并按该字段分组。若希望基于文件名前缀分类，可修改 `src/core/scanner.js` 中的 `classifyByPrefix` 函数，增加新的映射规则，然后重新运行 `npm run build`。

## 许可证

MIT

> 外链数量: 20 | 生成时间: 2026-08-09 00:01:36
