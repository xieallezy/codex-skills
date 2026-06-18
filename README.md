# Codex Skills

这个仓库用于分享可复用的 Codex Skills。

## 安装方式

把对应 Skill 的 GitHub 目录链接发给 Codex，并要求安装。例如：

```text
请从这个 GitHub 地址安装 Skill：
https://github.com/xieallezy/codex-skills/tree/main/skills/analyze-data
```

安装完成后，重启 Codex 或新开线程，再使用 `$技能名` 调用。

## analyze-data

面向 Excel、WPS、CSV 和其他表格数据的数据分析工作流。

主要能力：

- 在处理前检查字段、数据粒度、缺失值、分类和业务口径。
- 保护原始数据，并按需建立分析底表、原生数据透视表和展示表。
- 统一占比口径、分母、差值方向和业务排序。
- 正确使用色阶、数据条、百分比和百分点格式。
- 校验明细覆盖、分组总数、指标计算、透视表和展示格式。
- 根据当前数据选择方法，不写死年级、复购分类或固定指标。

安装地址：

```text
https://github.com/xieallezy/codex-skills/tree/main/skills/analyze-data
```

调用示例：

```text
$analyze-data 请分析这个 WPS 表格，先确认业务口径，再建立适合的透视表和对外展示页。
```

## reading-card

面向中文伴读学习卡 PowerPoint 的周度制作和更新流程。

主要能力：

- 基于已有周度 PPT 模板更新五天伴读内容。
- 保留模板布局、字体、字号、文本框、图标和装饰元素。
- 更新故事、题目、选项、词语、拼音和学习进度。
- 检查中文与拼音字体、行距、文本溢出和图文遮挡。
- 默认先处理文字，不在用户未要求时生成图片或导出全部页面。

使用前需要准备对应的 PPT 模板、每周内容和模板所需字体。

安装地址：

```text
https://github.com/xieallezy/codex-skills/tree/main/skills/reading-card
```

调用示例：

```text
$reading-card 请根据上一周模板制作下一周五天伴读学习卡，先更新文字并保持原格式。
```

## 更新与同步

- 修改本机 `~/.codex/skills/` 中的 Skill，不会自动更新 GitHub。
- 修改 GitHub 中的 Skill，也不会自动覆盖本机版本。
- 别人已经安装的 Skill，不会随着本仓库更新而自动变化。
- 每次修改后，需要重新发布到 GitHub；使用者需要重新安装或更新该 Skill。
- 发布前应检查是否包含账号、密钥、私人文件、本机绝对路径或不应公开的业务内容。

