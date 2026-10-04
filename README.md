# app-lore

**长尾计算机应用的结构综述，写给 AI 读。**

条目采用 Agent Skills 开放格式（SKILL.md）：简单应用一个综述文件即完整条目；
复杂应用按前台功能模块拆分，综述内引用；wiki 成熟的应用直接指路引用。
条目价值由"长尾度"量化——AI 无知识面时对该应用的判定偏差越大，条目越有价值。

> 中文说明见下。

---

## 定位与范围

- 收录：**计算机（桌面/PC 为主）系长尾应用**的业务流程与使用（business flows & usage）
- 不收：通用知识、教程型常识（模型已掌握的内容）、设备/框架绑定的运行时格式
- 价值判据：AI 无知识面时的判定是否可靠——不可靠的应用才值得建条目（见"长尾度"）
- 品类例外：**电商类为品类性收录**（risk=account 必填）——仅功能事实综述，
  不含操作自动化指导；规则/权益类事实变动频繁，用前核对当期来源

## 条目结构

```
packs/<类别>/<app>/
  pack.json5     # 必需：{name: "<类别slug>.<appslug>", version, app?: "<可执行名/标识>",
                 #         risk: "low"|"account"|"tos-grey"}
  SKILL.md       # 必需：综述（YAML frontmatter: name/description，Agent Skills 开放格式）。
                 #      简单应用：单文件即完整条目
  modules/       # 可选：复杂应用按前台功能模块拆分，每模块一个 .md，
                 #      在 SKILL.md 内列出模块清单并引用（粒度如：核心机制/角色/运营/模式）
  tail-degree.md # 必需：长尾度评定——测量方法、无知识面判定与事实的偏差记录、
                 #      所用模型与评定日期
  sources.md     # 必需：活跃信息源——官方文档/社区 wiki/论坛版块等链接，
                 #      各附最后核对日期；失效源应移除
```

## 加载模型（分层）

- **综述（SKILL.md）**：通用场景的默认加载——AI 知道前台是什么应用、有什么功能，
  多数操作到此足够。
- **功能模块（modules/）**：流程涉及特定功能模块的深层场景时按需加载（例如涉及
  模式相关流程才加载模式模块）。模块清单写在综述里；模块不重复综述内容。

## 内容策略

- **指路优先**：wiki/官方文档成熟的应用，sources.md 直接指路，不复制内容
- **长文只写给没有公开资料的**：未文档化的功能与经验才展开写
- 条目由资深用户编辑；引用的社区内容需遵守其许可并注明出处

## 长尾度（tail-degree）

**定义**：无知识面时，AI 对该应用的判定与事实的偏差度。

**测量**：让零上下文 AI 仅凭界面观察判定业务状态（当前页面/正在进行的事/下一步），
与真实状态对照，记录偏差。偏差越大 = 先验越不可靠 = 该条目综述的价值越高。

**纪律**：评定结果依赖模型与版本，tail-degree.md 必须记录所用模型、版本与日期；
换模型应复测。未测量的应用不标长尾度。

## 目录

```
packs/开发工具  设计创作  专业软件  系统运维  办公协同  游戏  效率工具  电商
```

各目录当前为空，等待首批贡献。

## 贡献

1. **选题**：估长尾度潜力——AI 先验不可靠的应用才值得建条目（判定标准见"长尾度"）
2. **建目录**：按"条目结构"；综述与模块由熟悉该应用的资深用户编写；wiki 成熟的应用指路优先，长文只写给没有公开资料的部分
3. **长尾度实测**：让零上下文 AI（禁用工具与搜索）回答 3-5 个关键事实问题，与来源核对，逐条记录偏差。**事实基线必须先经搜索核对当期来源，不得以出题人自身知识充当基准；考题必须包含现状题**（新近上线的功能模块、当期政策/权益、随版本变动的数值）——只考稳定头部功能测不出长尾
4. **合格线**：存在实质偏差（≥1 处关键事实错/含糊）才收录；AI 全对说明先验已覆盖，不建条目（实例：LocalSend 实测全对，落选）
5. **记录**：tail-degree.md 记录问题、AI 答案要点、事实核对、所用模型/版本/日期；sources.md 每链接附最后核对日期与活跃度判断，失效即移除
6. **提交 PR**；维护者核对来源有效性与结构完整性

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

**EN**: Structural surveys of long-tail computer applications, written for AI to
read. Entries follow the open Agent Skills format (SKILL.md): a single survey
file for simple apps; per-feature modules for complex ones, referenced from the
survey; apps with mature wikis are covered by linking, not duplicating. Entry
value is quantified by tail-degree — the measured deviation between
zero-knowledge AI judgment and fact. Scope: business flows and usage of
long-tail desktop/PC applications; general or tutorial-level knowledge is
excluded. Risk labels mandatory; takedown on report.
