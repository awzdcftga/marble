# Midnight Resource Collective

Midnight Resource Collective 是一个面向开发者、技术研究人员与开源生态建设者的外链资源归集与导航项目。项目围绕 GitHub 仓库 munedrf/midnight 的内容组织结构，将分散在代码仓库各分支与目录中的外部参考链接、技术文档引用、社区教程与工具站入口进行系统化梳理，形成一份可公开访问、可机器解析、可人工审阅的技术资源索引。本项目的目标用户包括需要快速定位特定技术栈上下游资料的全栈工程师、希望从代码仓库中提取知识图谱的数据分析师，以及维护大型开源项目文档体系的技术撰稿人。

与传统的书签管理工具或个人收藏夹不同，Midnight Resource Collective 将资源列表视为一等公民，所有链接条目均以纯文本形式存储于仓库的 `/main` 分支下的对应分类目录中，并通过脚本自动校验每个 URL 的可达性与协议合规性。项目本身不提供爬虫、搜索或推荐算法，而是依赖贡献者人工筛选与维护，确保每一条收录的资源都具备明确的技术背景与实用价值。项目当前覆盖资源总数为 100 条，本批次为第 7/57 批，收录链接涵盖色彩主题命名空间下的各类技术文章、规范文档、在线工具与社区论坛。

## 功能概览

**资源条目结构化归档** 所有收录的 URL 按主题标签（如 cobalt、coral、cosmic、crystal 等）和资源类型（文档、工具、社区、规范）进行二级分类，资源列表以 Markdown 行内列表形式呈现，便于版本控制系统追踪增删改记录。

**链接可达性自动校验** 项目集成 GitHub Actions 工作流，每日定时对所有收录 URL 发起 HEAD 请求，检测返回状态码，将失效链接、重定向链接与超时链接生成报告并提交至仓库的 `/reports` 目录。

**协议与格式规范化检查** 脚本自动检测每个 URL 的协议头（http/https）、域名格式、路径结尾斜杠以及大小写敏感部分，对于不符合项目规范的条目在 Pull Request 阶段给出警告提示。

**主题标签聚合视图** 基于每个资源条目的文件名前缀（如 cobalt、ember、falcon、garden）生成标签云和分类索引页，访问者可通过项目 Wiki 查看按标签筛选的资源清单。

**贡献者归属记录** 每条资源条目在提交时需附带贡献者 GitHub ID 和收录日期，项目维护者可通过日志追溯每条链接的引入背景与审核状态。

**外部元数据扩展接口** 资源列表支持可选的 `#metadata` 后缀，贡献者可在同一行内补充资源语言、所属组织、最后更新年份等字段，供下游自动化工具解析。

**纯 Markdown 渲染与静态站点生成兼容** 资源列表完全基于标准 Markdown 语法编写，可直接被 Hugo、VuePress、MkDocs 等静态站点生成工具消费，无需额外解析器。

## 应用场景

**技术文档撰写过程中的参考资料管理** 当技术作者撰写某框架的配置指南或最佳实践时，可在 Midnight Resource Collective 中查找对应主题标签下的官方文档链接、社区案例和性能测试报告，避免重复搜索和书签散落。

**开源项目维护者的依赖文档梳理** 项目维护者可通过本索引快速找到与项目技术栈相关的依赖库主页、API 参考手册和变更日志，在升级依赖版本或处理安全漏洞时作为第一手信息来源。

**线下技术分享或培训的讲义素材库** 培训讲师或分享嘉宾可提前从资源列表中筛选与主题相关的延伸阅读链接，作为讲义附录或课后参考资料分发给学员，提高知识传递效率。

## 快速开始

```bash
# 克隆仓库到本地
git clone https://github.com/munedrf/midnight.git

# 进入项目根目录
cd midnight

# 安装依赖工具（需要 Node.js 18+ 和 npm）
npm install

# 运行资源校验脚本，检查所有 URL 可达性
npm run validate

# 生成分类索引页（输出到 /dist 目录）
npm run build
```

## 安装要求

| 依赖 | 必需 | 说明 |
|------|------|------|
| Node.js | 是 | 版本 18.17.0 或更高，用于运行校验脚本与构建工具 |
| npm | 是 | 版本 9.0.0 或更高，用于安装项目依赖包 |
| Git | 是 | 版本 2.30.0 或更高，用于克隆仓库与提交变更 |
| curl | 否 | 仅在不使用 Node.js 脚本时作为备用链接检测工具 |
| Python 3 | 否 | 仅用于运行可选的自定义解析脚本（/scripts 目录下） |
| Docker | 否 | 用于本地启动静态站点预览容器（/docker 目录提供配置） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | `/docs/usage.md` | 如何浏览资源列表、如何按标签筛选、如何查看校验报告 |
| 贡献指南 | `/CONTRIBUTING.md` | 如何提交新资源、更新失效链接、处理合并冲突 |
| 维护者手册 | `/docs/maintainers.md` | 如何管理批次、处理自动化报告、版本发布流程 |
| 架构说明 | `/docs/architecture.md` | 项目目录结构设计、脚本运行流程、CI/CD 配置详解 |
| 元数据规范 | `/docs/metadata-spec.md` | 资源条目注释格式、标签命名规则、扩展字段定义 |

## 资源列表

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

## 项目结构

```
midnight/
├── .github/
│   └── workflows/                 # GitHub Actions 自动化流水线
│       ├── validate.yml           # 每日 URL 校验与报告生成
│       └── build.yml              # 静态站点构建与部署
├── main/                          # 资源列表主目录
│   ├── cobalt/                    # 钴色主题资源（含 violet/willow/zephyr）
│   ├── coral/                     # 珊瑚色主题资源（含 amber/crystal/garden/ocean/pixel）
│   ├── cosmic/                    # 宇宙主题资源（含 atlas/cedar/coral/horizon/meadow/olive/pearl/pixel/river/zephyr）
│   ├── crystal/                   # 水晶主题资源（含 atlas/bloom/delta/signal）
│   ├── delta/                     # 三角洲主题资源（含 cobalt/marble）
│   ├── ember/                     # 余烬主题资源（含 canvas/quartz/velvet）
│   ├── falcon/                    # 猎鹰主题资源（含 cloud/shadow/violet）
│   ├── field/                     # 田野主题资源（含 canvas/river）
│   ├── forest/                    # 森林主题资源（含 coral/harbor/signal）
│   ├── garden/                    # 花园主题资源（含 canvas/harbor/maple/orbit/river/rocket/shadow）
│   ├── golden/                    # 金色主题资源（含 canvas/garden/lantern/maple/midnight/ocean/olive/orbit/willow）
│   ├── harbor/                    # 港湾主题资源（含 crystal/golden/island/marble/mirror/willow）
│   ├── horizon/                   # 地平线主题资源（含 delta）
│   ├── island/                    # 岛屿主题资源（含 bridge/delta/pixel/signal）
│   ├── jade/                      # 玉色主题资源（含 cosmic/field/ocean/olive/timber/velvet/wander）
│   ├── lantern/                   # 灯笼主题资源（含 amber/field/forest/maple/rocket/wander）
│   ├── maple/                     # 枫叶主题资源（含 atlas/cloud/ember/jade/saffron）
│   ├── marble/                    # 大理石主题资源（含 coral/forest/island/prairie）
│   ├── meadow/                    # 草地主题资源（含 cloud/garden）
│   ├── midnight/                  # 午夜主题资源（含 anchor/cedar/jade/pixel/quartz）
│   └── mirror/                    # 镜面主题资源（含 canvas/orbit/rocket/summit/timber/wander）
├── scripts/                       # 本地工具脚本
│   ├── validate.js                # URL 可达性校验主脚本
│   ├── generate-index.js          # 分类索引页生成器
│   └── metadata-parser.py         # 可选元数据解析脚本（Python）
├── reports/                       # 自动化报告输出目录（gitignore）
│   ├── broken-links-$(date).json  # 失效链接明细
│   └── redirects-$(date).json     # 重定向链接明细
├── dist/                          # 静态站点构建输出目录
│   ├── index.html                 # 资源总览页
│   └── tags/                      # 按标签聚合的子页面
├── docs/                          # 项目文档
│   ├── usage.md                   # 用户使用手册
│   ├── maintainers.md             # 维护者操作指南
│   ├── architecture.md            # 架构设计说明
│   └── metadata-spec.md           # 元数据规范定义
├── docker/                        # Docker 配置
│   ├── Dockerfile                 # 静态站点预览容器镜像
│   └── nginx.conf                 # Nginx 服务配置
├── .gitignore                     # Git 忽略规则
├── package.json                   # Node.js 项目配置与依赖
├── package-lock.json              # 依赖锁定文件
├── README.md                      # 项目入口文档（当前文件）
└── LICENSE                        # MIT 许可证
```

## 贡献指南

1. 复刻本仓库至个人 GitHub 账户，从 `main` 分支创建新的功能分支，分支命名格式为 `feature/add-<资源主题>-<日期>` 或 `fix/update-<资源名称>-<日期>`。

2. 在对应主题子目录下新增或修改 Markdown 文件，每个文件仅收录一个 URL，文件名为资源主题加描述性后缀（如 `cobaltviolet.md`）。文件内容需包含原始链接以及可选的 `#metadata` 注释行，注释中注明贡献者 ID 和收录日期。

3. 提交前本地运行 `npm run validate` 确保新增或修改的 URL 可达且协议合规，若校验失败请根据终端输出的错误提示调整条目内容。校验通过后提交 commit，commit message 需遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:` 等前缀。

4. 向本仓库发起 Pull Request，在 PR 描述中说明新增资源的背景、所属标签以及预期用途。项目维护者将在 48 小时内进行审核，如有修改意见将通过 PR 评论反馈。

5. 审核通过后 PR 将被合并至 `main` 分支，合并后 GitHub Actions 将自动触发构建流水线，更新静态站点并重新生成所有分类索引页。合并后如发现链接失效，维护者将在下一批次的报告中标记并联系贡献者处理。

## 常见问题

**问：如果我发现某个已收录的链接已经失效，应该如何处理？**

答：请按照贡献指南的流程，从 `main` 分支创建修复分支，定位到对应的主题子目录下的 Markdown 文件，将失效链接更新为有效的新链接，或移除该条目并在 commit message 中说明移除原因。如果无法找到替代链接，可以在文件中将 URL 替换为 `#DEPRECATED` 占位符，并添加注释说明失效日期，维护者会在定期清理时统一归档此类条目。

**问：资源列表中的主题标签是如何确定的？我可以新增自定义标签吗？**

答：当前的主题标签主要来源于文件名前缀，由初始贡献者根据资源内容的技术领域或视觉主题进行命名。新增自定义标签需要在项目的元数据规范文档中先行提案，经过维护者讨论并更新 `/docs/metadata-spec.md` 后方可正式使用。在提案通过之前，建议将新资源放入现有最接近的标签目录下，并在文件内部注释中标注建议的新标签。

**问：项目是否会收录非技术类或商业推广类链接？**

答：Midnight Resource Collective 明确只收录与技术开发、系统设计、开源生态、学术研究直接相关的资源链接。商业产品主页、付费课程推广页面、个人博客中无技术内容的文章均不在收录范围内。贡献者在提交前请自行判断资源内容的技术含量，维护者审核时会拒绝明显不符合定位的条目。

## 许可证

MIT

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
