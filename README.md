# crawler-compliance

中国网络爬虫数据采集合规规范 Claude Code 插件。在开发爬虫时自动触发合规检查流程，确保数据采集行为符合国内法律法规。

## 背景

数据采集是许多项目的基础能力，但国内对网络爬虫的法律法规日趋严格。2025年《反不正当竞争法》新增数据抓取专条，《网络数据安全管理条例》确立三阶层合法性判定标准，企业数据采集面临更高的合规要求。

本插件将这些合规要求封装为 Claude Code Skill，在每次爬虫开发前自动执行检查清单，避免开发过程中触碰法律红线。

## 功能

- **自动触发** — 当对话中出现"写爬虫"、"采集数据"、"爬取网页"等关键词时自动加载
- **合规红线** — 5 条触碰即涉刑的底线，明确告知不可逾越
- **三阶层判定** — 数据公开性 → 技术手段合法性 → 使用目的合法性，逐层审查
- **开发前 Checklist** — 采集前评估、技术约束、数据处理、运行维护共 16 项检查
- **数据源优先级** — 政府公开数据 → 行业数据 → 官方 API → 网页爬取，按风险排序
- **应急处理** — 收到停止通知、误采敏感数据等场景的标准应对方案
- **渐进式加载** — SKILL.md 约 1500 词（自动加载），详细法条索引按需加载，节省 token

## 包含的法律依据

| 法律法规 | 版本/时间 |
|---|---|
| 《网络安全法》 | 2017 |
| 《数据安全法》 | 2021 |
| 《个人信息保护法》(PIPL) | 2021 |
| 《反不正当竞争法》 | 2025 修订 |
| 《网络数据安全管理条例》 | 2025 |
| 《公共数据资源授权运营实施规范》 | 2025 试行 |
| 《刑法》第 285/286/253/219 条 | — |

## 安装

### 方式一：从本地目录安装

```bash
claude plugins install --plugin-dir /path/to/crawler-compliance
```

### 方式二：手动注册

编辑 `~/.claude/plugins/installed_plugins.json`，在 `plugins` 对象中添加：

```json
"crawler-compliance@local": [
  {
    "scope": "user",
    "installPath": "/path/to/crawler-compliance",
    "version": "1.0.0",
    "installedAt": "2026-05-06T00:00:00.000Z",
    "lastUpdated": "2026-05-06T00:00:00.000Z"
  }
]
```

## 使用

安装后重启 Claude Code，在对话中提出任何爬虫相关需求即可自动触发：

```
> 帮我写一个爬取 xx 网站数据的爬虫
```

插件会先暂停编码，强制执行合规检查清单，逐项确认通过后才进入开发阶段。

## 项目结构

```
crawler-compliance/
├── .claude-plugin/
│   └── plugin.json                        # 插件清单
├── skills/
│   └── crawler-compliance/
│       ├── SKILL.md                       # 核心合规清单（自动加载）
│       └── references/
│           └── legal-framework.md         # 详细法律框架（按需加载）
├── .gitignore
└── README.md
```

## 参考来源

- [厘定边界合理规制网络爬虫行为 — 最高人民检察院](https://www.spp.gov.cn/spp/llyj/202511/t20251129_712355.shtml)
- [爬取数据须遵规 — 最高人民检察院](https://www.spp.gov.cn/llyj/202202/t20220210_543998.shtml)
- [《反不正当竞争法》2025 年修订评析 — 环球律师事务所](https://www.glo.com.cn/Content/2025/10-24/1107527632.html)
- [网络数据爬取合法性判定的三阶层认定标准 — 上海交通大学](http://www.socio-legal.sjtu.edu.cn/wxzy/info.aspx?itemid=4987&lcid=30)
- [执法风暴下的大数据爬虫合规之路 — 中伦律师事务所](https://www.zhonglun.com/research/articles/7484.html)

## 许可证

MIT
