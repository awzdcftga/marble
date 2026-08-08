# River Canon

River Canon 是一个面向技术文档与知识库管理的外部资源聚合与规范化索引工具。该项目定位于帮助开发者、技术写作团队以及开源项目维护者，以系统化的方式管理和引用分布在不同仓库、不同目录下的结构化 Markdown 资源文件。

River Canon 不提供新的文档存储方案，而是基于现有 Git 仓库的文件组织结构，生成稳定的引用索引，并提供可视化的目录树与分类概览，便于在团队内部或跨项目间共享资源定位信息。目标用户包括需要维护大量技术规格说明、设计文档或 API 参考的工程团队，以及希望建立统一资源查找入口的开源项目社区。

## 功能概览

资源索引自动生成 基于上游仓库的文件扫描结果，自动生成包含文件路径、命名模式与分类标签的索引清单。

目录树可视化 以 ASCII 树形结构展示仓库的层级目录布局，每行附带文件类型或功能注释，便于快速理解仓库组织逻辑。

命名规范校验 自动识别资源文件名中是否包含项目约定的颜色或主题词（如 Cobalt、Coral、Cosmic、Crystal、Delta、Ember、Falcon、Field、Forest、Garden、Golden、Harbor 等），辅助维护者检查命名一致性。

多层级筛选视图 支持按目录前缀（如 canvas、cedar、cloud、cobalt 等）进行资源分组筛选，减少人工遍历时间。

Markdown 引用输出 将资源列表以纯 Markdown 无序列表形式输出，无额外 HTML 标签或链接包裹，保证粘贴到文档、Issue 或 Wiki 后格式不丢失。

静态依赖与低运行时开销 仅依赖 Python 3.9+ 标准库与 Git 命令行工具，无需额外数据库或服务进程，适合 CI/CD 流水线集成。

路径可追溯性 每条索引记录均可回溯至源仓库的原始文件路径，便于进行版本对比或内容审计。

## 应用场景

技术文档仓库的入口索引维护 当技术文档团队需要为包含数百个 Markdown 文件的仓库提供一个稳定的目录入口时，River Canon 可定期扫描并生成索引文件，避免人工维护表格或列表的重复劳动。

开源项目的资源引用聚合 开源项目维护者可在 README 中引用 River Canon 生成的资源列表，使社区贡献者能够快速定位设计草图、协议定义或示例配置文件的位置，无需逐一翻阅目录。

内部知识库的合规性检查 在金融或医疗领域的内部知识库中，文件命名通常需要包含特定的主题词或环境标识。River Canon 的命名校验功能可辅助管理员发现不符合规范的新增文件。

跨仓库依赖的资源映射 当多个微服务仓库共用同一套接口定义文件时，River Canon 可生成统一的映射表，帮助架构师追踪各仓库引用的外部资源路径。

CI 流程中的文档完整性验证 在持续集成流水线中加入 River Canon 的扫描步骤，若发现新增资源未纳入索引或命名不符合约定，可输出警告或中断构建，确保文档资产始终可控。

## 快速开始

以下命令演示如何从 GitHub 克隆 River Canon 项目仓库，安装基础依赖，并执行首次索引生成。

```bash
git clone https://github.com/fcdujqa/river.git
cd river
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
python canon.py --scan --output INDEX.md
```

执行成功后，当前目录将生成 INDEX.md 文件，其中包含对仓库内所有 Markdown 资源的分类索引与目录树。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 或更高 | 核心运行环境，用于执行扫描与索引生成脚本 |
| Git | 2.30 或更高 | 用于克隆目标仓库以及获取文件变更日志 |
| pip | 22.0 或更高 | Python 包管理工具，用于安装依赖库 |
| PyYAML | 6.0 | 用于解析可选的配置文件，支持自定义索引规则 |
| markdown-it-py | 2.2 | 用于解析 Markdown 文件头部元数据，提取标题与标签 |
| pytest | 7.0 | 仅开发与测试需要，用于运行单元测试 |
| flake8 | 5.0 | 仅开发需要，用于代码风格检查 |
| pre-commit | 2.20 | 仅开发需要，用于提交前自动执行校验钩子 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide/ | 如何配置扫描路径、如何自定义输出模板、如何集成到 CI 中 |
| 管理员指南 | docs/admin/ | 如何管理多仓库索引、如何设定命名规范白名单、如何处理冲突文件 |
| 开发者文档 | docs/developer/ | 核心模块职责、扩展插件接口、单元测试编写规范 |
| 设计决策记录 | docs/adr/ | 为何选择 YAML 作为配置格式、为何不自动拉取远程仓库最新提交 |
| 常见任务速查 | docs/cheatsheet.md | 最常用的 10 条命令示例以及输出格式调整参数 |
| 故障排除 | docs/troubleshooting.md | 扫描超时、编码异常、Git 权限问题的常见解决办法 |

## 资源列表

- https://github.com/fcdujqa/river/blob/main/canvasdelta.md
- https://github.com/fcdujqa/river/blob/main/canvashorizon.md
- https://github.com/fcdujqa/river/blob/main/canvaslantern.md
- https://github.com/fcdujqa/river/blob/main/canvasquartz.md
- https://github.com/fcdujqa/river/blob/main/canvastimber.md
- https://github.com/fcdujqa/river/blob/main/cedarcanvas.md
- https://github.com/fcdujqa/river/blob/main/cedarfalcon.md
- https://github.com/fcdujqa/river/blob/main/cedarharbor.md
- https://github.com/fcdujqa/river/blob/main/cedarpixel.md
- https://github.com/fcdujqa/river/blob/main/cedartimber.md
- https://github.com/fcdujqa/river/blob/main/cedarwander.md
- https://github.com/fcdujqa/river/blob/main/cloudamber.md
- https://github.com/fcdujqa/river/blob/main/cloudatlas.md
- https://github.com/fcdujqa/river/blob/main/cloudcrystal.md
- https://github.com/fcdujqa/river/blob/main/cloudember.md
- https://github.com/fcdujqa/river/blob/main/cloudforest.md
- https://github.com/fcdujqa/river/blob/main/cloudhorizon.md
- https://github.com/fcdujqa/river/blob/main/cobaltatlas.md
- https://github.com/fcdujqa/river/blob/main/cobaltbloom.md
- https://github.com/fcdujqa/river/blob/main/cobaltcloud.md
- https://github.com/fcdujqa/river/blob/main/cobaltisland.md
- https://github.com/fcdujqa/river/blob/main/cobaltpixel.md
- https://github.com/fcdujqa/river/blob/main/cobaltrocket.md
- https://github.com/fcdujqa/river/blob/main/cobaltsaffron.md
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

## 项目结构

```
river/
├── canon.py                # 主入口脚本，负责解析命令行参数并调度扫描流程
├── config.yaml             # 可选配置文件，定义白名单、黑名单及输出格式偏好
├── requirements.txt        # 生产环境依赖列表
├── README.md               # 项目说明文档（即本文档）
├── LICENSE                 # MIT 许可证文件
├── .gitignore              # Git 忽略规则，排除虚拟环境与临时输出文件
├── .pre-commit-config.yaml # 预提交钩子配置，用于代码格式化与静态检查
│
├── core/                   # 核心功能模块目录
│   ├── __init__.py
│   ├── scanner.py          # 目录扫描与文件收集逻辑，支持递归遍历和路径过滤
│   ├── parser.py           # Markdown 文件头部元数据解析（YAML Front Matter 或 HTML 注释）
│   ├── indexer.py          # 索引构建与分类聚合，生成结构化数据对象
│   └── validator.py        # 文件名规范性校验，匹配预定义的主题词列表
│
├── output/                 # 输出渲染模块
│   ├── __init__.py
│   ├── markdown_renderer.py # 将索引数据渲染为 Markdown 无序列表与标题
│   ├── tree_builder.py     # 构建 ASCII 目录树，并附加注释说明
│   └── formatter.py        # 统一处理缩进、换行与特殊字符转义
│
├── utils/                  # 通用辅助工具
│   ├── __init__.py
│   ├── git_helper.py       # 封装 Git 命令，用于获取文件最后修改人及提交哈希
│   ├── logger.py           # 日志记录器，支持不同级别输出到控制台或文件
│   └── exceptions.py       # 自定义异常类，区分配置错误、扫描错误与渲染错误
│
├── tests/                  # 单元测试与集成测试目录
│   ├── test_scanner.py     # 测试文件扫描逻辑，覆盖空目录、深层嵌套与符号链接情况
│   ├── test_parser.py      # 测试元数据解析，验证不同格式的 Front Matter 能否正确提取
│   ├── test_indexer.py     # 测试索引聚合的正确性，包括重复文件与重命名场景
│   └── fixtures/           # 测试用固定样本数据（模拟目录与 Markdown 文件）
│
└── docs/                   # 项目自身文档
    ├── user-guide/         # 用户手册（分章节）
    ├── admin/              # 管理员指南
    ├── developer/          # 开发者文档
    ├── adr/                # 架构决策记录
    ├── cheatsheet.md       # 命令速查表
    └── troubleshooting.md  # 故障排除指南
```

## 贡献指南

1. 阅读开发者文档 首先参考 docs/developer/ 目录下的模块概述和编码规范，了解核心类的职责划分和命名约定，避免重复工作。

2. 创建功能分支 从 main 分支签出新的特性分支，分支命名格式为 feature/简短描述 或 fix/问题编号，例如 feature/support-csv-output。

3. 编写单元测试 在 tests/ 目录下为新增功能或修复编写对应的测试用例，确保测试覆盖率达到 90% 以上。运行 pytest 确认全部现有测试通过。

4. 提交代码前执行预检查 使用 pre-commit 运行所有钩子，包括 flake8 静态检查、black 代码格式化和 isort 导入排序。如未安装 pre-commit，可手动执行相应工具。

5. 发起拉取请求 推送分支至远程仓库，在 GitHub 上发起 Pull Request，并在描述中写明改动动机、影响范围以及测试结果摘要。等待至少一名维护者审核后合并。

## 常见问题

Q: 扫描大型仓库时脚本执行时间过长或内存占用过高怎么办？

A: 可以通过配置文件中的 max_files 选项限制单次扫描的最大文件数，默认值为 2000。同时，可以启用增量扫描模式，仅检查自上次扫描以来发生变更的文件，该模式需要配置持久化缓存文件路径。

Q: 输出列表中的文件路径为何是相对路径而非绝对路径？

A: River Canon 默认输出相对于扫描起始目录的路径，以保证索引的可移植性。若需要输出完整绝对路径，可在配置文件中将 absolute_path 设置为 true，但请注意这会导致索引在不同机器间不可用。

Q: 如何支持私有 Git 仓库或需要 SSH 认证的仓库？

A: River Canon 本身不处理认证逻辑，所有 Git 操作均依赖系统自带的 Git 命令行。请预先在本地配置好 SSH 密钥或 HTTPS 凭证，确保 git clone 或 git fetch 能够正常执行。若仓库需要特定访问令牌，可通过环境变量 GIT_TOKEN 传递。

## 许可证

MIT

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
