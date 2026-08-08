# Midnight Resource Catalog

Midnight Resource Catalog 是一个面向开发者与技术研究者的外链资源归集与导航系统。该项目定位于对分散在多个仓库、多个分支中的技术文档、配置文件、示例代码及研究笔记进行统一的索引、分类与快速检索。目标用户包括基础架构工程师、DevOps 运维人员、技术文档撰写者以及需要频繁查阅外部技术参考资料的研发团队。Midnight Resource Catalog 通过结构化的资源清单与轻量化的元数据标记，解决了跨仓库资源查找困难、引用路径模糊以及外部链接失效率高等实际问题。

## 功能概览

**跨仓库资源统一索引**：支持对多个源仓库下的 Markdown 文档进行批量扫描与路径归集，生成可浏览的资源清单。

**多维标签分类体系**：每个资源条目可关联多个分类标签，支持按主题、按仓库来源、按文件命名模式进行快速筛选。

**轻量化本地部署**：无需外部数据库依赖，基于静态文件目录结构与 JSON 索引文件即可运行完整的资源导航服务。

**资源状态健康检查**：内置链接可达性探测模块，定时检测外部引用资源是否可访问，自动标记失效链接。

**全文模糊搜索**：基于标题、文件名及摘要内容构建倒排索引，支持中英文混合关键词的快速定位。

**索引快照版本管理**：每次索引构建生成带时间戳的快照文件，支持回滚至任意历史索引状态。

**原始引用直出模式**：所有资源链接以原始格式呈现，不附加额外修饰符或跳转包装，确保引用路径的准确性与可追溯性。

## 应用场景

**技术文档中心资源聚合**：企业内部技术文档中心使用 Midnight Resource Catalog 将分散在多个代码仓库中的设计文档、API 说明与运维手册进行统一归集，文档撰写人员可通过分类标签快速定位相关参考资料。

**开源项目外部依赖梳理**：开源项目维护者利用该目录系统梳理项目所依赖的外部资源链接，包括上游参考实现、协议定义文件与社区讨论帖，确保所有外部引用均有据可查。

**个人知识库外链管理**：研究人员或高级开发者将个人笔记仓库中的外链资源导出至 Midnight Resource Catalog，配合健康检查功能定期验证收藏链接的有效性，及时发现并替换失效资源。

## 快速开始

以下命令演示了从克隆仓库到启动本地索引服务的完整流程。

```bash
git clone https://github.com/munedrf/midnight.git
cd midnight
pip install -r requirements.txt
python build_index.py --source ./ --output ./index.json
python server.py --port 8080 --index ./index.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心索引构建与服务器运行环境 |
| pip | 22.0 及以上 | Python 依赖包管理工具 |
| Markdown | 3.4.0 及以上 | 用于解析 .md 文件中的标题与链接 |
| PyYAML | 6.0 及以上 | 解析可选的自定义元数据配置文件 |
| requests | 2.28.0 及以上 | 用于外部链接可达性健康检查 |
| click | 8.1.0 及以上 | 命令行交互接口框架 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/getting-started.md | 如何首次部署并生成可浏览的资源索引页面 |
| 索引配置 | /docs/index-config.md | 如何自定义扫描路径、排除规则与标签映射 |
| 健康检查 | /docs/health-check.md | 如何配置定时检测任务以及处理失效链接报告 |
| 搜索语法 | /docs/search-syntax.md | 支持哪些搜索运算符以及如何组合关键词提高查准率 |

## 资源列表

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
- https://github.com/munedrf/midnight/blob/main/signalpearl.md
- https://github.com/munedrf/midnight/blob/main/signalprairie.md
- https://github.com/munedrf/midnight/blob/main/silveramber.md
- https://github.com/munedrf/midnight/blob/main/silvernebula.md
- https://github.com/munedrf/midnight/blob/main/summitcanvas.md
- https://github.com/munedrf/midnight/blob/main/summitcobalt.md
- https://github.com/munedrf/midnight/blob/main/summitcosmic.md
- https://github.com/munedrf/midnight/blob/main/summitmarble.md
- https://github.com/munedrf/midnight/blob/main/summitprairie.md
- https://github.com/munedrf/midnight/blob/main/summitsignal.md
- https://github.com/munedrf/midnight/blob/main/summittimber.md
- https://github.com/munedrf/midnight/blob/main/timberatlas.md
- https://github.com/munedrf/midnight/blob/main/timberbright.md
- https://github.com/munedrf/midnight/blob/main/timberlantern.md
- https://github.com/munedrf/midnight/blob/main/timbermarble.md
- https://github.com/munedrf/midnight/blob/main/timberriver.md
- https://github.com/munedrf/midnight/blob/main/timbersilver.md
- https://github.com/munedrf/midnight/blob/main/timberwillow.md
- https://github.com/munedrf/midnight/blob/main/velvetatlas.md
- https://github.com/munedrf/midnight/blob/main/velvetcanvas.md
- https://github.com/munedrf/midnight/blob/main/velvetgarden.md
- https://github.com/munedrf/midnight/blob/main/violetatlas.md
- https://github.com/munedrf/midnight/blob/main/violetcobalt.md
- https://github.com/munedrf/midnight/blob/main/violetmaple.md
- https://github.com/munedrf/midnight/blob/main/violetmeadow.md
- https://github.com/munedrf/midnight/blob/main/violetsaffron.md
- https://github.com/munedrf/midnight/blob/main/violettimber.md
- https://github.com/munedrf/midnight/blob/main/violetwillow.md
- https://github.com/munedrf/midnight/blob/main/wandercosmic.md
- https://github.com/munedrf/midnight/blob/main/wanderdelta.md
- https://github.com/munedrf/midnight/blob/main/wanderfield.md
- https://github.com/munedrf/midnight/blob/main/wanderriver.md
- https://github.com/munedrf/midnight/blob/main/wandersummit.md
- https://github.com/munedrf/midnight/blob/main/willowbridge.md
- https://github.com/munedrf/midnight/blob/main/willowdelta.md
- https://github.com/munedrf/midnight/blob/main/willowgolden.md
- https://github.com/munedrf/midnight/blob/main/zephyrfield.md
- https://github.com/munedrf/midnight/blob/main/zephyrmarble.md
- https://github.com/munedrf/midnight/blob/main/zephyrocean.md
- https://github.com/munedrf/midnight/blob/main/zephyrsignal.md
- https://github.com/munedrf/midnight/blob/main/zephyrtimber.md
- https://github.com/fcdujqa/river/blob/main/ambercoral.md
- https://github.com/fcdujqa/river/blob/main/ambercrystal.md
- https://github.com/fcdujqa/river/blob/main/amberfalcon.md
- https://github.com/fcdujqa/river/blob/main/amberharbor.md
- https://github.com/fcdujqa/river/blob/main/amberprairie.md
- https://github.com/fcdujqa/river/blob/main/amberriver.md
- https://github.com/fcdujqa/river/blob/main/amberrocket.md
- https://github.com/fcdujqa/river/blob/main/anchorbridge.md
- https://github.com/fcdujqa/river/blob/main/anchorisland.md
- https://github.com/fcdujqa/river/blob/main/anchorlantern.md
- https://github.com/fcdujqa/river/blob/main/anchorolive.md
- https://github.com/fcdujqa/river/blob/main/anchorpearl.md
- https://github.com/fcdujqa/river/blob/main/atlasbloom.md
- https://github.com/fcdujqa/river/blob/main/atlascedar.md
- https://github.com/fcdujqa/river/blob/main/atlasorbit.md
- https://github.com/fcdujqa/river/blob/main/atlasprairie.md
- https://github.com/fcdujqa/river/blob/main/atlasrocket.md
- https://github.com/fcdujqa/river/blob/main/atlassummit.md
- https://github.com/fcdujqa/river/blob/main/bloomamber.md
- https://github.com/fcdujqa/river/blob/main/bloomatlas.md
- https://github.com/fcdujqa/river/blob/main/bloomcloud.md
- https://github.com/fcdujqa/river/blob/main/bloomgolden.md
- https://github.com/fcdujqa/river/blob/main/bloomnebula.md
- https://github.com/fcdujqa/river/blob/main/bloomquartz.md
- https://github.com/fcdujqa/river/blob/main/bridgecanvas.md
- https://github.com/fcdujqa/river/blob/main/bridgecobalt.md
- https://github.com/fcdujqa/river/blob/main/bridgeember.md
- https://github.com/fcdujqa/river/blob/main/bridgefalcon.md
- https://github.com/fcdujqa/river/blob/main/bridgenebula.md
- https://github.com/fcdujqa/river/blob/main/bridgeprairie.md
- https://github.com/fcdujqa/river/blob/main/brightbloom.md
- https://github.com/fcdujqa/river/blob/main/brightfalcon.md
- https://github.com/fcdujqa/river/blob/main/brightgolden.md
- https://github.com/fcdujqa/river/blob/main/brightjade.md
- https://github.com/fcdujqa/river/blob/main/brightpearl.md
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

## 项目结构

```
midnight/
├── build_index.py          # 索引构建主脚本，扫描指定目录生成 JSON 索引
├── server.py               # 基于 Flask 的轻量级 Web 导航服务入口
├── requirements.txt        # Python 依赖声明文件
├── index.json              # 默认输出索引文件，包含所有资源条目元数据
├── config/
│   ├── default.yaml        # 默认扫描规则与标签映射配置
│   └── custom.yaml         # 用户自定义覆盖配置示例
├── docs/
│   ├── getting-started.md  # 新手入门教程
│   ├── index-config.md     # 索引配置参数详解
│   ├── health-check.md     # 健康检查模块使用说明
│   └── search-syntax.md    # 搜索语法完整参考
├── scanners/
│   ├── md_parser.py        # Markdown 文档解析器，提取标题与内部链接
│   └── link_extractor.py   # 通用链接提取工具，支持多种文本格式
├── checkers/
│   ├── reachability.py     # HTTP 可达性探测模块
│   └── reporter.py         # 生成健康检查报告
├── templates/
│   ├── index.html          # 资源清单首页模板
│   └── detail.html         # 单个资源详情页模板
└── tests/
    ├── test_parser.py      # 解析器单元测试
    └── test_checker.py     # 健康检查模块单元测试
```

## 贡献指南

1. 在 GitHub 仓库页面点击 Fork 按钮，将本仓库复制至个人账户下，然后克隆该副本至本地开发环境。

2. 新建一个以 feature/ 或 fix/ 为前缀的分支，例如 feature/add-custom-tag-support，在该分支上完成代码修改或文档更新。

3. 遵循项目现有的代码风格与提交信息规范，提交信息首行应概括变更内容，第二行开始详细描述修改动机与影响范围。

4. 将本地分支推送至个人远程仓库，随后通过 GitHub 页面发起 Pull Request 至本仓库的 main 分支，并在 PR 描述中关联相关 Issue 编号。

5. 等待项目维护者进行 Code Review，根据反馈意见进行修改直至 PR 被合并。

## 常见问题

**Q：索引构建时扫描到大量无关文件，如何排除特定目录或文件类型？**

A：在 config/default.yaml 中配置 exclude_patterns 字段，支持通配符匹配。例如添加 "*/tests/*" 可排除所有测试目录，添加 "*.tmp" 可排除临时文件。修改配置后重新运行 build_index.py 即可生效。

**Q：健康检查模块报告大量链接超时，但浏览器中可正常访问，如何解决？**

A：部分外部服务可能对自动化请求的 User-Agent 或访问频率有限制。可在 config/custom.yaml 中调整 check_timeout 参数增加单次请求超时时间，同时设置 request_interval 参数降低请求频率。若问题持续存在，可切换至 head_only 模式仅发送 HEAD 请求以减少服务端负担。

**Q：如何将索引服务部署至生产环境并提供持久化存储？**

A：推荐使用 Gunicorn 或 uWSGI 作为生产级 WSGI 服务器，并将 index.json 文件挂载至持久化存储卷。若使用 Docker 部署，可通过环境变量 INDEX_FILE_PATH 指定索引文件路径，并确保该路径对应的宿主机目录进行了持久化挂载。

## 许可证

MIT

> 外链数量: 100 | 生成时间: 2026-08-09 00:01:36
