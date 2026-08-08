# Midnight Resource Atlas

Midnight Resource Atlas 是一个面向开发者、研究人员与技术爱好者的结构化外链与资源导航工具。项目定位于对互联网上分散的高质量技术文档、开源仓库、学术论文、工具站点及社区博客进行系统化归集与索引，通过统一的目录树与标签体系降低信息检索成本。本项目不存储任何第三方内容，仅提供指向原始资源的稳定引用链接，并围绕这些链接构建分类、检索、版本追踪与健康度检测等辅助能力。

目标用户包括需要频繁查阅外部参考资料的全栈工程师、运维人员、技术决策者以及开源贡献者。项目采用纯静态 Markdown 与 JSON 混合数据层设计，所有资源链接以可读文本形式维护于仓库目录中，支持通过 GitHub 原生界面或本地编辑器进行浏览、筛选与批量更新。Midnight Resource Atlas 本身不依赖数据库或后端服务，运行于任何支持 HTTPS 的静态托管环境，亦可作为本地知识管理工具使用。

## 功能概览

结构化资源索引：所有外链按主题域与功能角色划分至独立 Markdown 文件，每个文件内包含资源名称、原始 URL、简短描述与标签列表，支持人工维护与脚本自动化校验。

链接健康状态检测：内置基于 GitHub Actions 的定时任务，对收录的每一枚外链发起 HEAD 请求，检测响应状态码与重定向链，自动标记失效或迁移的链接。

快速模糊检索：通过仓库根目录的索引 JSON 文件与本地脚本，支持按关键词、标签或文件名前缀对资源进行实时过滤，无需启动额外服务。

版本化变更追踪：所有资源增删改操作均通过 Pull Request 流程提交，利用 Git 原生历史记录保留每次变更的上下文与审核记录，便于回溯与回滚。

跨平台访问兼容：资源列表以纯文本形式存储，可在命令行终端、代码编辑器、GitHub Web 界面或任何支持 Markdown 渲染的阅读器中正常显示，不依赖特定浏览器插件。

批量导入与校验工具：提供 Python 辅助脚本，支持从 CSV 或 TSV 文件批量导入新链接，并在提交前自动检查 URL 格式合法性、去重以及域名黑名单过滤。

自定义分类标签系统：每个资源可附加多个分类标签（如 `network` 、 `database` 、 `security` ），项目维护统一的标签字典，便于后续生成按标签聚合的视图。

## 应用场景

技术团队内部知识库搭建：团队可将 Midnight Resource Atlas 作为基础骨架，将常用的内部文档链接、私有仓库地址与公共技术博客统一收录，通过 Git 仓库实现全员共享与版本管理，减少因人员流动导致的知识散失。

开源项目依赖文档整理：开源维护者可将项目所引用的第三方库主页、API 参考手册、社区论坛及镜像站点整理至 Atlas 中，随项目代码一同发布，为贡献者与用户提供明确的参考资料入口。

个人开发者学习路径管理：学习者可按主题建立自己的资源收藏夹，例如将 Kubernetes 相关教程、云原生工具链、性能调优案例分别归档，利用标签与注释记录学习进度与心得体会，形成长期积累的可检索知识资产。

离线文档中心前置导航：对于部署在内网环境的文档服务器，Atlas 可作为导航首页，将内部 Wiki、Jenkins 构建地址、监控仪表板、代码审查工具等日常入口统一陈列，配合健康检测功能及时发现内网服务异常。

技术调研与竞品分析记录：在进行技术选型或竞品对比时，可将各类产品官网、技术白皮书、用户反馈论坛以及性能测试报告链接集中纳入 Atlas，附上对比维度标签与主观评价，支撑决策过程。

## 快速开始

以下步骤适用于初次克隆项目并在本地环境中完成基础配置的用户。请确保已安装 Git 及 Python 3.8 以上版本。

```bash
git clone https://github.com/munedrf/midnight.git
cd midnight
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python3 scripts/health_check.py --all
```

执行上述命令后，项目即完成基础环境准备。健康检测脚本会遍历 `resources/` 目录下所有 Markdown 文件，提取其中包含的外链并输出状态报告。若希望启动本地预览服务，可运行 `python3 -m http.server 8000` ，随后在浏览器中访问 `http://localhost:8000` 查看索引页面。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Git | 2.25.0 或更高 | 用于克隆仓库及提交变更记录 |
| Python | 3.8.0 或更高 | 运行辅助脚本与健康检测工具 |
| pip | 20.0.0 或更高 | 安装 Python 依赖包 |
| requests | 2.25.0 或更高 | 用于发送 HTTP 请求检测链接状态 |
| markdown | 3.3.0 或更高 | 用于解析 Markdown 文件提取链接 |
| PyYAML | 5.4.0 或更高 | 用于读取配置文件中的元数据 |
| 网络环境 | 可访问公网 | 健康检测及访问外链资源所需 |
| 静态托管服务 | 任意 | 部署阶段需要，本地运行无需 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide.md | 如何浏览资源列表、使用搜索功能、理解标签体系 |
| 维护者手册 | docs/maintainer-guide.md | 如何新增/编辑/删除资源链接、处理失效链接、审核 PR |
| 脚本参考 | docs/scripts-reference.md | 各辅助脚本的参数说明、输出格式、定时任务配置方法 |
| 设计文档 | docs/design-philosophy.md | 为何采用纯静态结构、目录划分逻辑、标签设计原则 |
| 常见问题 | docs/faq.md | 链接失效如何处理、如何请求添加新资源、如何报告错误 |
| 变更日志 | CHANGELOG.md | 每个版本的资源增减列表与脚本功能更新记录 |

## 资源列表

- https://github.com/munedrf/midnight/blob/main/jadecosmic.md
- https://github.com/munedrf/midnight/blob/main/jadefield.md
- https://github.com/munedrf/midnight/blob/main/jadeocean.md
- https://github.com/munedrf/midnight/blob/main/jadeolive.md
- https://github.com/munedrf/midnight/blob/main/jadetimber.md
- https://github.com/munedrf/midnight/blob/main/jadevelvet.md
- https://github.com/munedrf/midnight/blob/main/jadewander.md
- https://github.com/munedrf/midnight/blob/main/lanternamber.md
- https://github.com/munedrf/midnight/blob/main/lanternfield.md
- https://github.com/munedrf/midnight/blob/main/lanternforest.md
- https://github.com/munedrf/midnight/blob/main/lanternmaple.md
- https://github.com/munedrf/midnight/blob/main/lanternrocket.md
- https://github.com/munedrf/midnight/blob/main/lanternwander.md
- https://github.com/munedrf/midnight/blob/main/mapleatlas.md
- https://github.com/munedrf/midnight/blob/main/maplecloud.md
- https://github.com/munedrf/midnight/blob/main/mapleember.md
- https://github.com/munedrf/midnight/blob/main/maplejade.md
- https://github.com/munedrf/midnight/blob/main/maplesaffron.md
- https://github.com/munedrf/midnight/blob/main/marblecoral.md
- https://github.com/munedrf/midnight/blob/main/marbleforest.md
- https://github.com/munedrf/midnight/blob/main/marbleisland.md
- https://github.com/munedrf/midnight/blob/main/marbleprairie.md
- https://github.com/munedrf/midnight/blob/main/meadowcloud.md
- https://github.com/munedrf/midnight/blob/main/meadowgarden.md
- https://github.com/munedrf/midnight/blob/main/midnightanchor.md
- https://github.com/munedrf/midnight/blob/main/midnightcedar.md
- https://github.com/munedrf/midnight/blob/main/midnightjade.md
- https://github.com/munedrf/midnight/blob/main/midnightpixel.md
- https://github.com/munedrf/midnight/blob/main/midnightquartz.md
- https://github.com/munedrf/midnight/blob/main/mirrorcanvas.md
- https://github.com/munedrf/midnight/blob/main/mirrororbit.md
- https://github.com/munedrf/midnight/blob/main/mirrorrocket.md
- https://github.com/munedrf/midnight/blob/main/mirrorsummit.md
- https://github.com/munedrf/midnight/blob/main/mirrortimber.md
- https://github.com/munedrf/midnight/blob/main/mirrorwander.md
- https://github.com/munedrf/midnight/blob/main/nebulabloom.md
- https://github.com/munedrf/midnight/blob/main/nebulacanvas.md
- https://github.com/munedrf/midnight/blob/main/nebulacrystal.md
- https://github.com/munedrf/midnight/blob/main/nebulafalcon.md
- https://github.com/munedrf/midnight/blob/main/nebulagolden.md
- https://github.com/munedrf/midnight/blob/main/nebulajade.md
- https://github.com/munedrf/midnight/blob/main/nebulameadow.md
- https://github.com/munedrf/midnight/blob/main/nebulashadow.md
- https://github.com/munedrf/midnight/blob/main/nebulasummit.md
- https://github.com/munedrf/midnight/blob/main/oceanbloom.md
- https://github.com/munedrf/midnight/blob/main/oceancloud.md
- https://github.com/munedrf/midnight/blob/main/oceanhorizon.md
- https://github.com/munedrf/midnight/blob/main/oceanpearl.md
- https://github.com/munedrf/midnight/blob/main/oceansummit.md
- https://github.com/munedrf/midnight/blob/main/olivemaple.md
- https://github.com/munedrf/midnight/blob/main/olivemidnight.md
- https://github.com/munedrf/midnight/blob/main/olivenebula.md
- https://github.com/munedrf/midnight/blob/main/orbitamber.md
- https://github.com/munedrf/midnight/blob/main/orbitember.md
- https://github.com/munedrf/midnight/blob/main/orbitgarden.md
- https://github.com/munedrf/midnight/blob/main/orbitmeadow.md
- https://github.com/munedrf/midnight/blob/main/orbitnebula.md
- https://github.com/munedrf/midnight/blob/main/orbitsaffron.md
- https://github.com/munedrf/midnight/blob/main/pearlcanvas.md
- https://github.com/munedrf/midnight/blob/main/pearlharbor.md
- https://github.com/munedrf/midnight/blob/main/pearlmarble.md
- https://github.com/munedrf/midnight/blob/main/pearlmirror.md
- https://github.com/munedrf/midnight/blob/main/pearlsilver.md
- https://github.com/munedrf/midnight/blob/main/pixelcloud.md
- https://github.com/munedrf/midnight/blob/main/pixelfield.md
- https://github.com/munedrf/midnight/blob/main/pixelrocket.md
- https://github.com/munedrf/midnight/blob/main/pixelsaffron.md
- https://github.com/munedrf/midnight/blob/main/pixelwander.md
- https://github.com/munedrf/midnight/blob/main/prairienebula.md
- https://github.com/munedrf/midnight/blob/main/quartzanchor.md
- https://github.com/munedrf/midnight/blob/main/quartzcoral.md
- https://github.com/munedrf/midnight/blob/main/quartzgolden.md
- https://github.com/munedrf/midnight/blob/main/quartzlantern.md
- https://github.com/munedrf/midnight/blob/main/quartzocean.md
- https://github.com/munedrf/midnight/blob/main/quartzwillow.md
- https://github.com/munedrf/midnight/blob/main/riverbright.md
- https://github.com/munedrf/midnight/blob/main/riverdelta.md
- https://github.com/munedrf/midnight/blob/main/rivergolden.md
- https://github.com/munedrf/midnight/blob/main/riverorbit.md
- https://github.com/munedrf/midnight/blob/main/riverrocket.md
- https://github.com/munedrf/midnight/blob/main/riverzephyr.md
- https://github.com/munedrf/midnight/blob/main/rocketfalcon.md
- https://github.com/munedrf/midnight/blob/main/rocketmidnight.md
- https://github.com/munedrf/midnight/blob/main/rocketnebula.md
- https://github.com/munedrf/midnight/blob/main/saffronbloom.md
- https://github.com/munedrf/midnight/blob/main/saffroncrystal.md
- https://github.com/munedrf/midnight/blob/main/saffronforest.md
- https://github.com/munedrf/midnight/blob/main/saffronlantern.md
- https://github.com/munedrf/midnight/blob/main/saffronnebula.md
- https://github.com/munedrf/midnight/blob/main/shadowbloom.md
- https://github.com/munedrf/midnight/blob/main/shadowbright.md
- https://github.com/munedrf/midnight/blob/main/shadowfalcon.md
- https://github.com/munedrf/midnight/blob/main/shadowgolden.md
- https://github.com/munedrf/midnight/blob/main/shadowlantern.md
- https://github.com/munedrf/midnight/blob/main/shadowmaple.md
- https://github.com/munedrf/midnight/blob/main/shadowsummit.md
- https://github.com/munedrf/midnight/blob/main/signalcobalt.md
- https://github.com/munedrf/midnight/blob/main/signalfield.md
- https://github.com/munedrf/midnight/blob/main/signalmarble.md
- https://github.com/munedrf/midnight/blob/main/signalmeadow.md

## 项目结构

```
midnight/
├── .github/                          # GitHub 自动化工作流配置
│   └── workflows/
│       ├── health-check.yml          # 定时执行链接健康检测
│       └── index-update.yml          # 资源变更时自动重建索引
├── resources/                        # 核心资源分类目录
│   ├── network/                      # 网络基础设施相关链接
│   │   ├── cdn.md
│   │   ├── dns.md
│   │   └── load-balancer.md
│   ├── database/                     # 数据库与存储技术
│   │   ├── relational.md
│   │   ├── nosql.md
│   │   └── cache.md
│   ├── security/                     # 安全工具与最佳实践
│   │   ├── authentication.md
│   │   ├── encryption.md
│   │   └── auditing.md
│   ├── devops/                       # 运维与持续交付
│   │   ├── ci-cd.md
│   │   ├── monitoring.md
│   │   └── infrastructure.md
│   └── languages/                    # 编程语言与框架
│       ├── go.md
│       ├── rust.md
│       └── python.md
├── scripts/                          # 辅助工具脚本
│   ├── health_check.py               # 批量检测链接状态
│   ├── import_csv.py                 # 从 CSV 导入新资源
│   ├── dedup.py                      # 检测并移除重复链接
│   └── generate_index.py             # 生成全局索引 JSON
├── docs/                             # 项目文档
│   ├── user-guide.md
│   ├── maintainer-guide.md
│   ├── scripts-reference.md
│   └── design-philosophy.md
├── config/                           # 配置文件
│   ├── tags.yaml                     # 标签字典与分类映射
│   └── blacklist.yaml                # 域名黑名单与规则
├── data/                             # 运行时生成的数据
│   ├── index.json                    # 全量资源索引
│   └── health-report.json            # 最近一次健康检测结果
├── tests/                            # 单元测试与验证
│   ├── test_health_check.py
│   └── test_import.py
├── README.md                         # 项目入口文档（本文件）
├── CHANGELOG.md                      # 版本与变更记录
├── CONTRIBUTING.md                   # 贡献指南详细版
├── LICENSE                           # MIT 许可证
├── requirements.txt                  # Python 依赖列表
└── .gitignore                        # Git 忽略规则
```

## 贡献指南

欢迎各类形式的贡献，包括新增资源链接、修复失效链接、改进文档、提交脚本优化建议等。请遵循以下步骤确保协作流程顺畅。

第一步：查阅现有资源列表与标签体系，确认拟新增或修改的链接尚未被收录，且其内容与已有分类不存在冲突。若涉及新增分类标签，需同步更新 `config/tags.yaml` 文件。

第二步：从主仓库派生副本至个人账户，并在派生仓库中创建独立的功能分支，分支名称应简要描述变更目的，例如 `add-network-tools` 或 `fix-broken-links` 。

第三步：在对应分类目录下的 Markdown 文件中执行编辑操作。每个资源条目需包含资源名称、原始 URL、简短描述（不超过一行）及至少一个标签。使用标准格式 `- [名称](URL) - 描述 #标签1 #标签2` 以便脚本解析。

第四步：本地执行健康检测脚本与索引生成脚本，确保新增链接可达且格式无误。运行 `python3 scripts/health_check.py --changed-only` 仅检查本次变更的文件，以节约时间。

第五步：提交变更并推送至派生仓库，随后通过 GitHub Web 界面发起 Pull Request 至主仓库的 main 分支。PR 描述中应列明变更动机、涉及链接数量及任何需要特别说明的事项。项目维护者将在三个工作日内完成审核。

## 常见问题

问：如果发现资源列表中的某个链接已经失效，应该如何处理？

答：请先访问该链接确认其状态。若确认失效，可参照贡献指南提交 Pull Request，将该链接从对应 Markdown 文件中移除，或在描述中标注 `[失效]` 前缀并保留作为历史记录。若原站点迁移至新地址，欢迎同时提供新链接及必要的说明。

问：能否请求添加不在当前列表中的新资源？

答：可以。请通过 GitHub Issues 提交请求，标题格式为 `[资源请求] 资源名称` ，并在正文中提供完整 URL、简短描述以及推荐归属的分类与标签。项目维护者会根据资源质量、相关性及许可证兼容性进行评估。若资源符合收录标准，将随下一批次更新合并。

问：健康检测脚本报告链接状态异常，但我手动访问正常，如何排查？

答：这种情况通常源于网络环境差异或请求头限制。首先检查脚本发出的请求是否携带了 `User-Agent` 头，部分站点对非浏览器请求返回不同状态。可尝试在命令行中执行 `curl -I <URL>` 进行对比。若确认是误报，可在 `config/whitelist.yaml` 中为该域名添加例外规则，后续检测将跳过该链接的状态校验。

## 许可证

本项目采用 MIT 许可证进行分发。详细信息请查阅仓库根目录下的 LICENSE 文件。您被允许自由使用、复制、修改、合并、发布、分发、再授权及销售本项目的副本，但需保留原始版权声明与许可声明。本软件按“现状”提供，不提供任何明示或暗示的担保，包括但不限于适销性、特定用途适用性及非侵权性担保。

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
