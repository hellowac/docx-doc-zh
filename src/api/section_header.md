# _Header和_Footer对象

[add_paragraph()]: #add_paragraph

**class docx.section._Header** <a name=“Header”></a>

页眉，用于所有三种类型（默认、偶数页和首页）。

请注意，与文档或表格单元格一样，标题必须至少包含一个段落，并且新的或“空”标题包含单个空段落。 第一段可以作为 `header.paragraphs[0]` 访问，以便向其中添加内容。 单独使用 [add_paragraph()] 添加内容会在新添加的段落上方留下一个空段落。

- **add_paragraph(text=u'', style=None)** <a name="add_paragraph"></a>

    返回一个新添加到此容器内容末尾的段落，如果存在则在单个运行中包含文本，并具有段落样式样式。 如果 `style` 为 `None`，则不应用任何段落样式，这与应用`“Normal”`样式的效果相同。

- **add_table(rows, cols, width)** <a name="add_table"></a>

    返回一个具有 `rows` 行和 `cols` 列的宽度表，新附加到此容器中的内容。 宽度均匀分布在表格列之间。

- **is_linked_to_previous** <a name="is_linked_to_previous"></a>

    如果此页眉/页脚使用上一节中的定义，则为`True`。

    如果此页眉/页脚有明确定义，则为 `False`。

    将 `True` 分配给该属性会删除该节的页眉/页脚定义，从而使其“继承”上一节的相应定义。 分配 `False` 会导致为此部分添加一个新的空定义，但前提是没有定义已经存在。

- **paragraphs** <a name="paragraphs"></a>

    只读。包含此容器中的段落的列表，按文档顺序排列。

- **tables** <a name="tables"></a>

    只读。包含此容器中的表的列表，按文档顺序排列。
