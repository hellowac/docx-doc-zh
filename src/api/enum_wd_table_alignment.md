# WD_TABLE_ALIGNMENT

指定表格对齐类型。

例子：

```python
from docx.enum.table import WD_TABLE_ALIGNMENT

table = document.add_table(3, 3)
table.alignment = WD_TABLE_ALIGNMENT.CENTER
```

- **LEFT**

    左对齐

- **CENTER**

    居中对齐。

- **RIGHT**

    右对齐。
