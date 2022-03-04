# Table对象

[_Column]: ../api/table_column.md
[_Columns]: ../api/table_columns.md
[_Row]: ../api/table_row.md
[_Rows]: ../api/table_rows.md
[WD_TABLE_ALIGNMENT]: ../api/enum_wd_tab_alignment.md
[Cell]: ../api/table_cell.md
[_TableStyle]: ../api/style_table_style.md
[WD_TABLE_DIRECTION]: ../api/enum_wd_table_direction.md

**class docx.table.Table(tbl, parent)**

WordprocessingML `<w:tbl>` 元素的代理类。

- **add_column(width)**

    返回一个`width`为 [_Column] 的对象，新添加到表的最右侧。

- **add_row()**

    返回一个 [_Row] 实例，新添加到表的最底部。

- **alignment**

    读/写。 [WD_TABLE_ALIGNMENT] 或 `None` 的成员，指定此表在页边距之间的位置。 如果未指定设置，则为`None`，从而导致从样式层次结构继承有效值。

- **autofit**

    如果可以自动调整列宽以提高单元格内容的匹配度，则为`True`。 如果表格布局是固定的，则为 `False`。 如果总列宽超过页面宽度，则在任何一种情况下都会调整列宽。 读/写布尔值。

- **cell(row_idx, col_idx)**

    返回与第 `row_idx` 行、`col_idx` 交叉处的表格单元格对应的 [Cell] 实例，其中 `(0, 0)` 是最顶部、最左侧的单元格。

- **column_cells(column_idx)**

    此表中 `column_idx` 列中的单元格序列。

- **columns**

    [_Columns] 实例表示此表中的列序列。

- **row_cells(row_idx)**

    此表中 `row_idx` 行中的单元格序列。

- **rows**

    [_Rows] 实例包含此表中的行序列。

- **style**

    读/写。 一个 [_TableStyle] 对象，表示应用于此表的样式。 如果表格没有直接应用的样式，则返回文档的默认表格样式（通常是普通表格）。 将 `None` 分配给此属性会删除任何直接应用的表格样式，从而使其继承文档的默认表格样式。 请注意，表格样式的样式名称与用户界面中显示的样式名称略有不同； 如果出现连字符，则必须删除。 例如，`Light Shading - Accent 1` 变为 `Light Shading Accent 1`。

- **table_direction**

    [WD_TABLE_DIRECTION] 的成员，指示表格单元格的排序方向，例如 `WD_TABLE_DIRECTION.LTR`。 `None` 表示该值是从样式层次结构继承的。
