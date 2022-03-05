# WD_ORIENTATION

别名：WD_ORIENT

指定页面布局方向。

例子：

```python
from docx.enum.section import WD_ORIENT

section = document.sections[-1]
section.orientation = WD_ORIENT.LANDSCAPE
```

- **PORTRAIT**

    纵向。

- **LANDSCAPE**

    横向。
