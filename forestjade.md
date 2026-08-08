# River Link Index

River Link Index 是一个面向技术团队与开源项目维护者的结构化外链资产整理工具。该项目将分散在代码仓库、文档站点与协作空间中的参考链接、资源引用和外部依赖纳入统一的索引框架，通过约定式目录与可编码的元数据描述，降低链接漂移与资源不可用带来的维护成本。River Link Index 适用于需要长期维护大量外部引用的项目，例如技术文档站、API 网关说明、SDK 使用指南或多仓库联合构建系统。

本项目的核心定位并非通用书签管理器，而是为仓库级别的外链提供版本可追踪、校验可自动化、迁移可批量处理的工程化方案。River Link Index 通过单文件描述与脚本化检查，帮助维护者快速定位失效链接、归类资源类型并生成面向阅读者或下游工具的索引视图。

## 功能概览

- **链接分类标注** 每条链接可附加类型标识，例如标准文档、API 端点、社区讨论或依赖镜像地址，便于按类别筛选与审计。

- **指纹校验与状态检查** 项目提供轻量级脚本，对链接对应的目标资源执行可达性探测与内容摘要比对，辅助识别内容变更或页面移除。

- **多级目录索引生成** 支持按主题标签、目标域名或引用仓库生成多维度索引表格，供 README 或独立文档页面嵌入使用。

- **版本差异对比** 基于 Git 历史记录，可对比不同提交之间外链集合的增删改变化，便于代码审查时关注外部依赖变动。

- **批量迁移辅助** 当上游资源调整 URL 结构时，项目提供正则映射表与批处理建议，帮助维护者一次性更新全部引用。

- **JSON 与 YAML 导出** 索引数据可导出为结构化格式，供 CI 流程、静态站点生成器或其他分析工具消费。

- **自定义元数据扩展** 用户可在索引文件中添加业务相关字段，例如负责团队、更新周期或访问权限要求，无需修改核心解析逻辑。

## 应用场景

- **技术文档站的外链审计** 当文档包含数百个指向第三方库、规范或工具的链接时，维护者可定期运行 River Link Index 的检查命令，生成失效链接报告，并在发版前完成修复。

- **微服务仓库的依赖资源追溯** 在包含多个服务配置文件的仓库中，不同服务可能引用不同的配置中心地址、日志收集端点或监控面板。River Link Index 可将这些外链统一登记，避免配置变更时遗漏更新。

- **开源项目 README 与贡献指南的链接规范化** 开源项目通常需要在 README、CONTRIBUTING 和 ISSUE_TEMPLATE 中引用外部资源。使用 River Link Index 可确保这些引用保持同步，降低新贡献者因访问无效链接而产生的困惑。

- **离线文档包的资源映射** 部分企业环境需要将文档打包为离线版本。River Link Index 可输出所有外链清单，帮助打包工具提前下载或替换为内部镜像地址。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户建议通过 WSL 或 Git Bash 执行。

```bash
# 克隆仓库到本地
git clone https://github.com/fcdujqa/river.git
cd river

# 安装基础依赖（Python 3.8+ 与 pip）
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# 执行索引构建与链接检查
python scripts/build_index.py --input ./links --output ./dist
python scripts/check_links.py --source ./dist/index.json --report ./reports
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心脚本运行环境，用于解析索引文件与执行网络检查 |
| Git | 2.25 及以上 | 用于版本历史对比与提交钩子集成 |
| pip | 20.0 及以上 | 安装 Python 依赖包，包括 requests、pyyaml、jsonschema |
| 网络连接 | 出站 HTTPS 可达 | 检查外链可达性时需要访问目标域名，部分内网环境需配置代理 |
| 磁盘空间 | 至少 50 MB | 用于存放索引文件、报告及临时缓存 |
| 操作系统 | Linux / macOS / Windows WSL | 脚本基于 POSIX 路径设计，Windows 原生命令行未全面测试 |
| 可选依赖 | Graphviz | 若需生成链接关系可视化图表，建议安装 dot 工具 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何安装、初始化索引目录并生成第一份链接清单 |
| 索引格式规范 | docs/schema.md | 索引文件支持哪些字段、如何扩展自定义属性及类型约束 |
| 命令行工具参考 | docs/cli-reference.md | 每个脚本的详细参数、环境变量与退出码含义 |
| 最佳实践 | docs/best-practices.md | 如何组织大量链接、设定检查频率及处理上游资源变更 |

## 资源列表

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
- https://github.com/fcdujqa/river/blob/main/maplezephyr.md
- https://github.com/fcdujqa/river/blob/main/marbleforest.md
- https://github.com/fcdujqa/river/blob/main/marbleharbor.md
- https://github.com/fcdujqa/river/blob/main/marbleolive.md

## 项目结构

```
river/
├── links/                          # 索引源文件目录，每个类别一个子目录
│   ├── core/                       # 核心依赖与基础组件链接
│   │   ├── index.yaml              # 核心层外链列表
│   │   └── checksums.txt           # 目标资源的指纹快照
│   ├── docs/                       # 文档相关外链，如规范、教程、API参考
│   │   ├── api_references.yaml
│   │   ├── community_guides.yaml
│   │   └── internal_standards.yaml
│   ├── tools/                      # 构建工具、CI插件、辅助脚本来源
│   │   ├── build_systems.yaml
│   │   ├── linters.yaml
│   │   └── codegen_tools.yaml
│   └── archive/                    # 历史归档链接，保留旧版引用
│       ├── v1_deprecated.yaml
│       └── migration_maps.yaml
├── scripts/                        # 可执行脚本
│   ├── build_index.py              # 解析 links 目录并生成合并索引
│   ├── check_links.py              # 执行链接可达性与摘要校验
│   ├── diff_versions.py            # 对比两次提交间的链接变化
│   └── export_formats.py           # 输出 JSON、YAML 或 Markdown 表格
├── tests/                          # 单元测试与集成测试
│   ├── test_parser.py
│   ├── test_checker.py
│   └── fixtures/                   # 测试用的示例索引文件
├── docs/                           # 项目自身文档
│   ├── getting-started.md
│   ├── schema.md
│   ├── cli-reference.md
│   └── best-practices.md
├── reports/                        # 检查报告输出目录（gitignore）
│   ├── latest_report.json
│   └── history/                    # 历史报告存档
├── config/                         # 全局配置
│   ├── default_settings.yaml       # 超时时间、重试策略、忽略列表
│   └── user_overrides.yaml.example # 用户自定义配置模板
├── .github/                        # GitHub 工作流与模板
│   └── workflows/
│       └── link_check_cron.yaml    # 定期执行链接检查的 CI 配置
├── requirements.txt                # Python 依赖声明
├── LICENSE                         # MIT 许可文件
└── README.md                       # 项目入口文档（当前文件）
```

## 贡献指南

欢迎各类贡献，包括但不限于新增索引条目、改进检查脚本、完善文档或报告问题。请遵循以下步骤提交变更。

1. 在 GitHub 上 fork 本仓库，并将 fork 后的仓库克隆到本地开发环境。
2. 创建独立的特性分支，分支名使用 `feat/` 或 `fix/` 前缀，后接简短描述，例如 `feat/add-java-sdk-links`。
3. 若新增或修改索引文件，请确保遵循 `docs/schema.md` 中定义的字段规范，并执行本地构建与检查脚本验证格式正确性。
4. 提交代码时使用清晰的 commit message，遵循常规提交格式，并在 PR 描述中说明变更动机、影响范围及测试结果。
5. 提交 Pull Request 至主仓库的 main 分支，等待维护者审查。CI 流水线将自动执行链接检查与单元测试，请确保所有检查通过。

## 常见问题

**Q: 链接检查脚本返回超时或连接拒绝，但目标网站实际可访问，应如何处理？**

A: 可能原因包括网络代理设置、目标站点的限流策略或脚本默认超时时间过短。请检查 `config/default_settings.yaml` 中的 `timeout` 与 `retry` 参数，适当增大超时值。若位于企业内网，可在 `user_overrides.yaml` 中配置 `proxy` 字段。若目标站点明确限制自动化访问，可将其加入 `ignore_list` 并备注原因，改为人工定期复核。

**Q: 索引文件中的链接数量较多时，构建和检查速度明显下降，有无优化建议？**

A: 建议使用 `--parallel` 参数启用并发检查，默认并发数为 8，可根据机器性能调整。此外，`check_links.py` 支持 `--cache` 选项，对状态码稳定的链接缓存结果，减少重复网络请求。对于内容摘要校验，可关闭 `--verify-content` 以仅检查可达性。

**Q: 如何将现有仓库中散落的链接迁移到 River Link Index 格式？**

A: 项目提供了 `scripts/migrate_from_markdown.py` 辅助脚本（位于 contrib 目录），可解析 README 或文档中的 Markdown 链接并生成初始 YAML 条目。对于更复杂的迁移需求，建议使用 `export_formats.py --input ./dist/index.json --output ./migration/` 导出为 CSV 格式，在电子表格中批量整理后再重新导入。

## 许可证

MIT

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
