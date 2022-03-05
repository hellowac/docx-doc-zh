# WD_ROW_HEIGHT_RULE

别名：WD_ROW_HEIGHT

指定确定表格行高的规则

例子：

```python
from docx.enum.table import WD_ROW_HEIGHT_RULE

table = document.add_table(3, 3)
table.rows[0].height_rule = WD_ROW_HEIGHT_RULE.EXACTLY
```

- **AUTO**

    调整行高以适应行中的最高值。

- **AT_LEAST**

    行高至少是最小指定值。

- **EXACTLY**

    行高是一个精确值。
