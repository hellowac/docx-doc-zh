# WD_PARAGRAPH_ALIGNMENT

别名：WD_ALIGN_PARAGRAPH

指定段落对齐类型。

例子：

```python
from docx.enum.text import WD_ALIGN_PARAGRAPH

paragraph = document.add_paragraph()
paragraph.alignment = WD_ALIGN_PARAGRAPH.CENTER
```

- **LEFT**

    左对齐

- **CENTER**

    居中对齐。

- **RIGHT**

    右对齐。

- **JUSTIFY**

    合理。

- **DISTRIBUTE**

    段落字符分布以填充段落的整个宽度。

- **JUSTIFY_MED**

    以中等字符压缩率合理分布。

- **JUSTIFY_HI**

    以高等字符压缩率合理分布。

- **JUSTIFY_LOW**

    以较低字符压缩率合理分布。

- **THAI_JUSTIFY**

    根据泰语格式合理布局。
