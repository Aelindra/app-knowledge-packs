# app-knowledge-packs

**长尾计算机应用的结构性综述目录，写给 AI 读。**

每个条目回答三个问题：这个应用是做什么的、业务流程长什么样（结构综述）；
AI 对它的先验有多不可靠（长尾度评定）；去哪里获取并核对最新事实（活跃信息源）。
条目是索引与综述，不是操作手册，也不绑定任何运行时格式或操控框架。

> 中文说明见下。

---

## 定位与范围

- 收录：**计算机（桌面/PC 为主）系长尾应用**的业务流程与使用（business flows & usage）
- 不收：通用知识、教程型常识（模型已掌握的内容）、设备/框架绑定的运行时格式
- 判断标准：AI 无知识面时的判定是否可靠——不可靠的应用才值得建条目（见"长尾度"）

## 条目结构

```
packs/<类别>/<app>/
  pack.json5     # 必需：{name: "<类别slug>.<appslug>", version, app?: "<可执行名/标识>",
                 #         risk: "low"|"account"|"tos-grey"}
  survey.md      # 必需：结构综述——应用定位、核心实体、业务流程骨架、词表。
                 #      只写结构性事实；每个事实标注来源
  tail-degree.md # 必需：长尾度评定——测量方法、无知识面判定与事实的偏差记录、
                 #      所用模型与评定日期
  sources.md     # 必需：活跃信息源——官方文档/社区 wiki/论坛版块等链接，
                 #      各附最后核对日期；失效源应移除
```

## 长尾度（tail-degree）

**定义**：无知识面时，AI 对该应用的判定与事实的偏差度。

**测量**：让零上下文 AI 仅凭界面观察判定业务状态（当前页面/正在进行的事/下一步），
与真实状态对照，记录偏差。偏差越大 = 先验越不可靠 = 该条目综述的价值越高。

**纪律**：评定结果依赖模型与版本，tail-degree.md 必须记录所用模型、版本与日期；
换模型应复测。未测量的应用不标长尾度。

## 目录

```
packs/开发工具  设计创作  专业软件  系统运维  办公协同  游戏  效率工具
```

各目录当前为空，等待首批贡献。

## 贡献

1. 按"条目结构"建目录，survey.md 的每个事实标注来源
2. 长尾度必须实测后填写，附方法与条件
3. 提交 PR；维护者核对来源有效性与结构完整性

## 规则

1. 只收事实性业务知识；策略与编排请写成工具或插件
2. **不收录**对抗检测、风控规避、提权相关内容
3. **不收录**账号滥用类：群发、刷量、批量注册
4. `risk` 标签必填；`account` 级内容仅适用于个人粒度、低频使用
5. 引用的社区内容需遵守其许可并注明出处

## 内容下架（Takedown）

本目录内容仅供个人研究使用。权利方认为某条目侵犯权益时，提交 issue 即下架对应内容，不争议、不留档。数据与商标版权归各自厂商。

## License

MIT（目录脚手架）。条目内容涉及厂商权利的部分按 Takedown 条款处理。

---

**EN**: A structural survey catalog of long-tail computer applications, written
for AI to read. Each entry answers three questions: what the app does and how
its business flows are structured (survey), how unreliable AI priors are about
it (tail-degree: measured deviation between zero-knowledge AI judgment and
fact, per app, with model and date recorded), and where to fetch and verify
current facts (active sources with last-checked dates). Entries are surveys and
indexes — no runtime formats, no binding to any automation framework. Scope:
business flows and usage of long-tail desktop/PC applications; general or
tutorial-level knowledge is excluded. Risk labels mandatory; takedown on report.
