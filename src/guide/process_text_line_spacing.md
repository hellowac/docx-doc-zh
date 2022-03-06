# 行距

行距是段落行中后续基线之间的距离。行距可以指定为绝对距离或相对于行高（本质上是所用字体的磅值）。典型的绝对衡量标准是 18 分。典型的相对度量将是双倍行距（2.0 行高）。默认行距是单行距（1.0 行高）。

行间距由 [line_spacing] 和 [line_spacing_rule] 属性的交互控制。 [line_spacing] 是长度值、（小）浮点数或 `None`。 长度值表示绝对距离。 浮点数表示行高数。 `None` 表示行距是继承的。 [line_spacing_rule] 是 [WD_LINE_SPACING] 枚举的成员或 `None`：

```python
>>> from docx.shared import Length
>>> paragraph_format.line_spacing
None
>>> paragraph_format.line_spacing_rule
None

>>> paragraph_format.line_spacing = Pt(18)
>>> isinstance(paragraph_format.line_spacing, Length)
True
>>> paragraph_format.line_spacing.pt
18.0
>>> paragraph_format.line_spacing_rule
EXACTLY (4)

>>> paragraph_format.line_spacing = 1.75
>>> paragraph_format.line_spacing
1.75
>>> paragraph_format.line_spacing_rule
MULTIPLE (5)
```
