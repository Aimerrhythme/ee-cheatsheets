# 速查表规范

## 命名
- `sheets/<slug>.md`，slug 小写短横线，如 `per-unit.md`。

## 结构

```markdown
# <中文标题>（<English term>）

> 一句话定义。

## 核心公式
$$ Z_{pu} = \frac{Z}{Z_B},\quad Z_B = \frac{U_B^2}{S_B} $$

## 典型数值 / 量纲
| 量 | 典型值 | 单位 |

## 课堂提示
- 易错点 / 口诀，2–4 条

## 相关工具
- [ee-lab-toolkit/tools/...](https://github.com/Aimerrhythme/ee-lab-toolkit)
```

## 公式写法（KaTeX 友好）
- 行内 `$...$`，独立 `$$...$$`；`$$` 前后各空一行。
- 避免 `\begin{align}` 等 GitHub 渲染不稳的环境，多行用多个 `$$` 块或 `aligned`。
- 下标用 `_{}`，单位用 `\mathrm{kV}`。

## 篇幅
- 控制在**打印一页 A4** 内（约 60 行 Markdown）。
