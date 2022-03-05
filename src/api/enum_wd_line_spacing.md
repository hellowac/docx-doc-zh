# WD_LINE_SPACING

指定要应用于段落的行距格式。

例子：

```python
from docx.enum.text import WD_LINE_SPACING

paragraph = document.add_paragraph()
paragraph.paragraph_format.line_spacing_rule = WD_LINE_SPACING.EXACTLY
```

- **ONE_POINT_FIVE**

    空格半行距。

- **AT_LEAST**

    行距始终至少为指定量。 金额单独指定。

- **DOUBLE**

    双倍行距。

- **EXACTLY**

    行距正好是指定的量。 金额单独指定。

- **MULTIPLE**

    行间距指定为行高的倍数。 更改字体大小将按比例更改行距。

- **SINGLE**

    单行距（默认）。
