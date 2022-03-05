# WD_TABLE_DIRECTION

指定应用程序对指定表或行中的单元格进行排序的方向。

例子：

```python
from docx.enum.table import WD_TABLE_DIRECTION

table = document.add_table(3, 3)
table.direction = WD_TABLE_DIRECTION.RTL
```

- **LTR**

    表格或行以第一列在最左边的位置排列。

- **RTL**

    表格或行的第一列位于最右侧。
