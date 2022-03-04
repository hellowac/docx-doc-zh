# _Cell对象

[WD_CELL_VERTICAL_ALIGNMENT]: ../api/enum_wd_cell_vertical_alignment.md

**class docx.table._Cell(tc, parent)**

表格单元格

- **add_paragraph(text=u'', style=None)**

    返回一个新添加到此单元格内容末尾的段落。 如果存在，文本将在一次运行中添加到段落中。 如果指定，则应用段落样式样式。 如果 `style` 未指定或为 `None`，则结果就像应用了“正常”样式。 请注意，单元格中文本的格式可能会受到表格样式的影响。 `text` 可以包含制表符 (\t) 字符，这些字符被转换为适当的 XML 格式的制表符。 `text` 还可以包含换行符 (\n) 或回车符 (\r)，每个字符都转换为换行符。

- **add_table(rows, cols)**

    在任何现有单元格内容之后返回一个新添加到此单元格的表格，具有`rows`行和`cols`列。 因为 Word 需要一个段落元素作为每个单元格中的最后一个元素，所以会在表格后添加一个空段落。

- **merge(other_cell)**

    返回一个合并的单元格，该单元格通过跨越矩形区域而创建，该单元格和 `other_cell` 作为对角线的角。 如果单元格没有定义矩形区域，则引发 `InvalidSpanError`。

- **paragraphs**

    单元格中的段落列表。 表格单元格必须包含至少一个块级元素并以段落结尾。 默认情况下，新单元格包含一个段落。 只读

- **tables**

    单元格中的表格列表，按它们出现的顺序排列。 只读。

- **text**

    此单元格的全部内容为一串文本。 将字符串分配给此属性会在一次运行中将所有现有内容替换为包含分配文本的单个段落。

- **vertical_alignment**

    [WD_CELL_VERTICAL_ALIGNMENT]的成员 或 `None` 。

    `None` 的值表示此单元格的垂直对齐方式是继承的。 分配 `None` 会导致任何明确定义的垂直对齐被删除，从而恢复继承。

- **width**

    `EMU` 中此单元格的宽度，如果未设置显式宽度，则为 `None`。
