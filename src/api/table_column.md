# _Column对象

[_Cell]: ../api/table_cell.md
[Table]: ../api/table_table_object.md

**class docx.table._Column(gridCol, parent)**

表格列

- **cells**

    与此列中的单元格对应的 [_Cell] 实例序列。

- **table**

    引用该列所属的 [Table] 对象。

- **width**

    EMU 中此列的宽度，如果未设置显式宽度，则为 `None`。
