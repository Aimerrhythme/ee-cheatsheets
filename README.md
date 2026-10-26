# ee-cheatsheets · 电气术语与公式速查

**一页纸**速查表：每张只讲一个主题，公式 + 典型数值 + 课堂提示，适合打印或手机翻看。

## 目录

```
sheets/<slug>.md     # 一张速查表 = 一个 Markdown 文件
docs/sheet-convention.md
themes.md            # 主题队列
INDEX.md             # 总索引
```

## 速查表模板（摘要）
- 标题 + 一句话定义
- 核心公式（KaTeX 友好：`$...$` / `$$...$$`，GitHub 可直接渲染）
- 典型数值 / 量纲
- 课堂提示（易错点、口诀）
- 相关工具（链接 `ee-lab-toolkit` 等）

规范见 [`docs/sheet-convention.md`](docs/sheet-convention.md)。

## 说明

- **中文为主**，必要处附英文术语。
- 本仓由定时自动化**持续追加**内容：每次从 `themes.md` 取一条 `todo` 主题 → 生成条目 → 更新 `INDEX.md` 与 `CHANGELOG.md` → 将主题标为 `done`。
- 定位为**教学材料**，**不代写**毕业设计 / 课程设计 / 论文。
- 许可：MIT（见 `LICENSE`，含教学声明）。
