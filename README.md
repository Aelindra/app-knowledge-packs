# app-knowledge-packs

**App business knowledge for AI to read.** A community catalog of per-app knowledge — entities, rules, flows, vocabulary, screen structure — written so an AI agent can understand how an application actually works.

Consumption-agnostic and device-agnostic: any AI agent may use this knowledge regardless of how it operates a device (screen+input tools, accessibility APIs, or purpose-built runtimes such as [mobile-agent-harness](https://github.com/Aelindra/mobile-agent-harness), whose `knowledge/` loader reads this format directly).

> 中文说明见下。

## 知识从哪来（聚合模式）

不自行从零体验。三层获取：

1. **聚合**：官方文档、社区 wiki、成熟攻略——这些社区已经在持续维护，直接引用
2. **综述**：AI 归纳为结构化知识，头部维护来源清单（链接 + 最后核对日期），矛盾与不确定处显式标注
3. **接地**：图标模板、选择器、状态判别式只在真机落地时生成——这是设备状态缓存，不是知识本体

## 适用筛选

**变动率低 × 敏感度低 × 存在社区维护的知识源 × 高频复用**。

- 适合：稳定的长青应用（核心规则与界面多年不变）、社区 wiki 活跃的领域、小众但稳定的工具
- 不适合：高频改版的界面（电商大促页）、风控敏感的账号型应用、教程型常识（模型已经会了，写了就贬值）

## 目录

```
packs/电商  游戏  社交  内容  生活服务  效率工具  测试  AI对话
```

各目录当前为空，等待首批贡献。

## 知识包格式

```
packs/<场景>/<app>/
  pack.json5     # 必需：{name: "<场景slug>.<appslug>", version, app: "<包名/标识>",
                 #         risk: "low"|"account"|"tos-grey"}
  business.md    # 必需：设备无关的业务语义——实体、规则、流程图、词表。
                 #        头部维护来源清单（链接 + 最后核对日期），
                 #        矛盾与不确定处显式标注
  variants/      # 可选：设备/客户端变体（variants/<device>/…）——
                 #        同一 app 在手机与桌面客户端上业务相同，仅映射不同
```

- 每个事实标注来源；无来源支持的内容放入"待验证"小节
- 与目标应用条款冲突的部分不得收录

## 规则

1. 只收事实性业务知识；策略与编排请写成工具或插件（可发布到各自的目录）
2. **不收录**对抗检测、风控规避、提权相关内容
3. **不收录**账号滥用类：群发、刷量、批量注册
4. `risk` 标签必填；`account` 级内容仅适用于个人粒度、低频使用
5. 聚合的社区内容需遵守其许可并注明出处

## 内容下架（Takedown）

本目录内容仅供个人研究使用。权利方认为某条目侵犯权益时，提交 issue 即下架对应内容，不争议、不留档。数据与商标版权归各自厂商。

## License

MIT（目录脚手架）。条目内容涉及厂商权利的部分按 Takedown 条款处理。

---

**EN**: A community catalog of per-app business knowledge written for AI to read —
entities, rules, flows, vocabulary, screen structure. Device-agnostic and
consumption-agnostic: knowledge is aggregated from existing community sources
(official docs, wikis, guides) with provenance and freshness tracking; grounding
templates are generated only when landing on a real device. Selection criteria:
low churn, low sensitivity, existing community sources, high personal reuse.
Risk labels mandatory; takedown on report.
