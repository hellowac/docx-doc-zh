# WD_CELL_VERTICAL_ALIGNMENT

别名：WD_ALIGN_VERTICAL

指定表格的一个或多个单元格中文本的垂直对齐方式。

例子：

```python
from docx.enum.table import WD_ALIGN_VERTICAL

table = document.add_table(3, 3)
table.cell(0, 0).vertical_alignment = WD_ALIGN_VERTICAL.BOTTOM
```

- **TOP**

    文本与单元格的上边框对齐。

- **CENTER**

    文本与单元格的中心对齐。

- **BOTTOM**

    文本与单元格的底部边框对齐。

- **BOTH**

    这是 OpenXml 规范中的一个选项，但在 Word 本身中没有。 目前尚不清楚此设置会产生什么 Word 行为。 如果您发现了，请告诉我们，我们将更新此文档。 否则，最好避免使用此选项。
