# Midnight Resource Collective

Midnight Resource Collective 是一个面向开发者、技术研究者与内容创作者的轻量化外链资源汇总工具。该项目以 GitHub 仓库作为底层数据存储媒介，通过结构化的 Markdown 文档索引与分类机制，将分散在网络各处的技术文章、工具站点、代码示例与设计素材进行集中管理和快速检索。项目定位为个人或小团队使用的内部资源导航辅助系统，不依赖数据库或外部服务，所有资源链接以纯文本形式保存在仓库目录中，支持通过 Git 进行版本追踪与协作更新。

项目主要解决三类问题：第一，技术从业者在日常工作中需要频繁查找各类文档与依赖库入口，但浏览器书签管理方式缺乏分类层级与跨设备同步的灵活性；第二，团队内部积累的优质外链资源难以形成可共享、可维护的知识库，现有商业方案通常需要付费或受限于平台生态；第三，个人开发者希望拥有一个完全自主可控、可随时迁移的资源索引体系，避免因浏览器更换或账号丢失导致收藏数据不可用。Midnight Resource Collective 通过将资源链接与描述信息写入 Markdown 文件，利用 GitHub 的 Web 界面与本地编辑器即可完成增删改查操作，同时借助 GitHub Actions 实现链接可用性的定时检查。

## 功能概览

- 基于 Markdown 的纯文本存储：所有资源条目以 Markdown 文件格式保存于仓库目录，无需数据库环境，支持任意文本编辑器直接修改。

- 多维度资源分类索引：资源按主题类别划分至不同目录，同一资源可被多个索引文件引用，实现灵活的多标签检索逻辑。

- 链接状态自动化检查：通过 GitHub Actions 工作流定时检测所有记录 URL 的可访问性，并在检出异常时生成报告文件，便于维护者及时清理失效链接。

- 模糊搜索与快速过滤：项目提供简单的 Shell 脚本与 Python 辅助工具，支持按关键词、分类名或文件标签对资源列表进行快速筛选与输出。

- 版本控制与变更追溯：所有资源增删改操作均通过 Git 提交记录完整保存，支持回滚至任意历史版本，适合团队协作场景下的变更审核。

- 静态站点生成适配：资源数据可被静态站点生成器（如 Hugo、Jekyll）直接读取，用于构建对外公开或内部部署的资源导航页面。

- 导入导出兼容性：支持从标准 CSV 与 JSON 格式批量导入资源条目，也支持将现有索引导出为通用数据交换格式，便于迁移至其他工具。

## 应用场景

开发团队内部文档中心补充模块：技术团队可将 Midnight Resource Collective 作为现有内部文档站点的外链补充模块，存放各类第三方依赖官方文档、社区讨论帖、问题排查参考链接。团队成员通过 Pull Request 提交新资源，经过审核合并后自动更新至团队共享的资源池。

个人知识库的外链管理插件：使用 Obsidian、Logseq 等双向链接笔记软件的用户，可将本项目的资源索引目录挂载为笔记库的子目录，在撰写技术笔记时直接引用资源文件中的链接，无需切换浏览器查找。

开源项目 README 与 Wiki 的外部参考维护：开源项目维护者可以利用本项目组织项目周边生态的链接集合，包括插件列表、扩展工具、社区教程等，避免这些内容散落在 Issue 或 Discussions 中难以查找。

技术社区内容聚合与定期分享：技术博客作者或社区运营人员可将项目作为素材暂存池，按月或按主题整理值得推荐的阅读材料与工具，并借助自动化脚本生成分享摘要。

## 快速开始

以下命令演示了从克隆项目到启动本地辅助工具的标准流程。请确保系统已安装 Git 与 Python 3.8 及以上版本。

```bash
git clone https://github.com/munedrf/midnight.git
cd midnight
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python3 scripts/init_index.py
```

执行上述命令后，项目将在本地完成初始化，创建必要的目录结构与索引模板文件。用户随后可通过编辑 `resources/` 目录下的 Markdown 文件来添加或修改资源条目。

## 安装要求

项目对运行环境的要求较低，主要依赖通用的命令行工具与 Python 运行时。下表列出了必要的依赖项及其说明。

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Git | 2.25.0 或更高 | 用于克隆仓库和提交变更记录，所有版本管理操作均基于 Git 命令行 |
| Python | 3.8.0 或更高 | 运行辅助脚本与自动化工具的核心解释器，需确保 pip 同时可用 |
| Bash | 4.0 或更高 | 执行快速筛选与统计 Shell 脚本，macOS 与 Linux 系统默认自带 |
| curl | 7.68.0 或更高 | 用于链接状态检查脚本中的 HTTP 请求发送，支持 HTTPS 协议 |
| GNU Make | 3.81 或更高 | 可选依赖，用于简化常用任务命令的调用，非必需但建议安装 |

## 文档导航

项目文档按照使用者的不同需求层面进行划分，从入门概览到进阶定制均有覆盖。下表可帮助用户快速定位所需文档。

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指引 | `docs/quick_start.md` | 如何在一分钟内完成项目克隆与初次运行，如何添加第一条资源记录 |
| 资源管理 | `docs/resource_management.md` | 资源文件的命名规范、分类目录结构、标签使用建议以及批量导入方法 |
| 自动化配置 | `docs/automation.md` | 如何配置 GitHub Actions 定时检查，如何修改检查频率与通知方式 |
| 高级定制 | `docs/customization.md` | 如何调整辅助脚本的输出格式，如何适配静态站点生成器的数据格式 |

## 资源列表

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
- https://github.com/munedrf/midnight/blob/main/falconshadow.md
- https://github.com/munedrf/midnight/blob/main/falconviolet.md
- https://github.com/munedrf/midnight/blob/main/fieldcanvas.md
- https://github.com/munedrf/midnight/blob/main/fieldriver.md
- https://github.com/munedrf/midnight/blob/main/forestcoral.md
- https://github.com/munedrf/midnight/blob/main/forestharbor.md
- https://github.com/munedrf/midnight/blob/main/forestsignal.md
- https://github.com/munedrf/midnight/blob/main/gardencanvas.md
- https://github.com/munedrf/midnight/blob/main/gardenharbor.md
- https://github.com/munedrf/midnight/blob/main/gardenmaple.md
- https://github.com/munedrf/midnight/blob/main/gardenorbit.md
- https://github.com/munedrf/midnight/blob/main/gardenriver.md
- https://github.com/munedrf/midnight/blob/main/gardenrocket.md
- https://github.com/munedrf/midnight/blob/main/gardenshadow.md
- https://github.com/munedrf/midnight/blob/main/goldencanvas.md
- https://github.com/munedrf/midnight/blob/main/goldengarden.md
- https://github.com/munedrf/midnight/blob/main/goldenlantern.md
- https://github.com/munedrf/midnight/blob/main/goldenmaple.md
- https://github.com/munedrf/midnight/blob/main/goldenmidnight.md
- https://github.com/munedrf/midnight/blob/main/goldenocean.md
- https://github.com/munedrf/midnight/blob/main/goldenolive.md
- https://github.com/munedrf/midnight/blob/main/goldenorbit.md
- https://github.com/munedrf/midnight/blob/main/goldenwillow.md
- https://github.com/munedrf/midnight/blob/main/harborcrystal.md
- https://github.com/munedrf/midnight/blob/main/harborgolden.md
- https://github.com/munedrf/midnight/blob/main/harborisland.md
- https://github.com/munedrf/midnight/blob/main/harbormarble.md
- https://github.com/munedrf/midnight/blob/main/harbormirror.md
- https://github.com/munedrf/midnight/blob/main/harborwillow.md
- https://github.com/munedrf/midnight/blob/main/horizondelta.md
- https://github.com/munedrf/midnight/blob/main/islandbridge.md
- https://github.com/munedrf/midnight/blob/main/islanddelta.md
- https://github.com/munedrf/midnight/blob/main/islandpixel.md
- https://github.com/munedrf/midnight/blob/main/islandsignal.md
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

## 项目结构

项目采用分层目录设计，将源代码、文档、资源配置与自动化脚本明确分离，便于后续维护与扩展。

```
midnight/
├── resources/                 # 核心资源索引目录，存放所有 Markdown 资源文件
│   ├── design/                # 设计类资源，包含 UI/UX 相关工具与素材链接
│   ├── development/           # 开发类资源，涵盖编程语言、框架与库的官方文档
│   ├── infrastructure/        # 基础设施类资源，包括云服务、运维工具与监控方案
│   ├── community/             # 社区类资源，收录技术论坛、博客聚合与讨论区链接
│   └── misc/                  # 综合类资源，暂未归类的链接存放于此
├── scripts/                   # 辅助脚本目录
│   ├── check_links.py         # 链接可用性检查主脚本，调用 curl 进行批量检测
│   ├── init_index.py          # 项目初始化脚本，创建目录结构与模板文件
│   └── search_filter.sh       # 基于 grep 的快速关键词筛选脚本
├── docs/                      # 项目文档目录
│   ├── quick_start.md         # 快速入门指南
│   ├── resource_management.md # 资源管理操作手册
│   ├── automation.md          # 自动化配置说明
│   └── customization.md       # 高级定制与扩展开发指南
├── .github/                   # GitHub 专用配置目录
│   └── workflows/             # Actions 工作流定义
│       └── link_check.yml     # 定时链接检查工作流配置文件
├── templates/                 # 资源文件模板目录
│   └── resource_template.md   # 新建资源条目的推荐格式模板
├── Makefile                   # GNU Make 任务聚合文件，简化常用命令调用
├── requirements.txt           # Python 依赖清单，供 pip 安装使用
└── README.md                  # 项目总体说明文档，即本文件
```

## 贡献指南

项目欢迎所有类型的贡献，包括新增资源条目、改进脚本逻辑、完善文档内容以及报告问题。请遵循以下步骤参与贡献。

第一步，在 GitHub 上 Fork 本仓库至个人账户，并克隆至本地开发环境。建议在新建分支上进行所有修改，分支名称应反映修改类型，例如 `feat/add-resources` 或 `fix/link-check-script`。

第二步，根据 `templates/resource_template.md` 的格式要求，在 `resources/` 下对应的分类目录中新增或修改 Markdown 文件。每个资源文件必须包含标题、原始链接、分类标签和至少一段用途描述。修改完成后，请使用 `scripts/check_links.py` 验证所有链接的有效性。

第三步，编写清晰的提交信息，说明本次修改的目的与范围。提交信息格式建议采用约定式提交规范，例如 `feat(resources): add five new design tool links`。推送分支至个人远程仓库后，在 GitHub 上发起 Pull Request 至主仓库的 main 分支。

第四步，等待项目维护者的评审反馈。若 Pull Request 被接受，维护者将进行合并操作；若存在需要调整的内容，维护者会在 Pull Request 下留言说明修改建议，贡献者需根据建议更新代码并重新推送。

## 常见问题

Q: 项目是否支持在 Windows 系统上运行？
A: 项目核心脚本基于 Python 开发，可在 Windows 系统上通过 Git Bash 或 WSL 环境正常运行。但部分 Shell 脚本依赖 Bash 特性，在原生 PowerShell 中可能无法直接执行，建议安装 Git for Windows 附带的 Git Bash 终端，或使用 Windows Subsystem for Linux 子系统。链接检查脚本所需的 curl 命令在 Windows 下可通过安装 cURL for Windows 或使用 WSL 内置版本解决。

Q: 如何批量添加大量现有书签中的链接？
A: 项目提供了 `scripts/import_from_csv.py` 辅助脚本（需额外安装 pandas 依赖），支持将符合指定列格式的 CSV 文件转换为多个 Markdown 资源文件。用户可先从浏览器导出书签为 HTML 格式，再使用在线工具或 Python 脚本将 HTML 书签转换为 CSV 格式，最后调用导入脚本完成批量生成。对于小于五十条的资源新增，建议直接复制模板手动创建文件以保持描述质量。

Q: 链接状态检查脚本报告了大量的超时错误，应该如何处理？
A: 链接检查脚本默认超时时间为 10 秒，若大量链接位于网络条件受限的地区或站点本身响应较慢，可能导致误报。用户可编辑 `scripts/check_links.py` 文件中的 `TIMEOUT` 变量值，将其调整为 30 或 60 秒后再运行。此外，部分站点会针对自动化请求返回 403 或 429 状态码，此时可在脚本中添加自定义 User-Agent 头部或增加请求间隔延迟来规避限制。

## 许可证

MIT

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
