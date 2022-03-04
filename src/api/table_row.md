# _Row对象

[_Cell]: ../api/table_cell.md
[Length]: ../api/shared_length_object.md
[WD_ROW_HEIGHT_RULE]: ../api/enum_wd_row_height_rule.md
[Table]: ../api/table_table_object.md

**class docx.table._Row[tr, parent]**

表格行

- **cells**

    与该行中的单元格对应的 [_Cell] 实例序列。

- **height**

    返回表示此单元格高度的 [Length] 对象，如果未设置显式高度，则返回 `None`。

- **height_rule**

    返回此单元格的高度规则作为 [WD_ROW_HEIGHT_RULE] 枚举的成员，如果未设置显式的 `height_rule`，则返回 `None`。

- **table**

    引用该行所属的 [Table] 对象。
