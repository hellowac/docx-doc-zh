# ParagraphFormat对象

[WD_PARAGRAPH_ALIGNMENT]: ../api/enum_wd_paragraph_alignment.md
[WD_LINE_SPACING]: ../api/enum_wd_line_spacing.md
[Length]: ../api/shared_length_object.md
[Inches]: ../api/shared_inches_object.md
[Pt]: ../api/shared_pt_object.md
[Cm]: ../api/shared_cm_object.md
[pt]: ../api/shared_length_object.md#pt
[inches]: ../api/shared_length_object.md#inches
[TabStops]: ../api/text_tab_stops_object.md

**class docx.text.parfmt.ParagraphFormat**

提供对段落格式的访问，例如对正、缩进、行间距、前后空间以及寡/孤【widow/orphan】控制。

- **alignment**

    [WD_PARAGRAPH_ALIGNMENT] 枚举的成员，指定此段落的对齐设置。 `None` 值表示段落对齐是从样式层次结构继承的。

- **first_line_indent**

    指定段落第一行缩进的相对差异的[Length]值。 正值会使第一行缩进。 负值产生悬挂缩进。 `None` 表示第一行缩进是从样式层次结构继承的。

- **keep_together**

    如果段落应该保持“一体”并且在呈现文档时不跨越页面边界，则为`True`。 `None` 表示其有效值是从样式层次结构继承的。

- **keep_with_next**

    如果在呈现文档时该段落应与后续段落保持在同一页面上，则为`True`。 例如，此属性可用于将章节标题与其第一段保持在同一页面上。 `None` 表示其有效值是从样式层次结构继承的。

- **left_indent**

    [Length]值指定左边距和段落左侧之间的空间。 `None` 表示左缩进值是从样式层次结构继承的。 使用[Inches]值对象作为以英寸为单位应用缩进的便捷方式。

- **line_spacing** <a name="line_spacing"></a>

    浮点数或[Length]值，指定段落连续行中基线之间的空间。 `None` 值表示行距是从样式层次结构继承的。 一个浮点值，例如 `2.0` 或 `1.75`，表示间距以行高的倍数应用。 诸如 `Pt(12)` 之类的 [Length] 值表示间距是固定高度。 [Pt] 值类是一种以点为单位应用行距的便捷方式。 指定 None 会将行距重置为从样式层次结构继承。

- **line_spacing_rule**

    [WD_LINE_SPACING] 枚举的成员，指示应该如何解释 [line_spacing](#line_spacing) 的值。 分配任何 [WD_LINE_SPACING] 成员 `SINGLE`、`DOUBLE` 或 `ONE_POINT_FIVE` 将导致 [line_spacing](#line_spacing) 的值被更新以产生相应的行间距。

- **page_break_before**

    如果该段落应出现在上一段之后的页面顶部，则为`True`。 `None` 表示其有效值是从样式层次结构继承的。

- **right_indent**

    [Length]值，指定段落右边距和右边距之间的距离。 `None` 表示正确的缩进值是从样式层次结构继承的。 使用 [Cm] 值对象作为以厘米为单位应用缩进的便捷方式。

- **space_after**

    [Length]值，指定在此段落和后续段落之间出现的间距。 `None` 表示此值是从样式层次结构继承的。 [Length]对象提供方便的属性，例如 [pt] 和[inches]，可以轻松转换为各种长度单位。

- **space_before**

    指定在本段和前一段之间出现的间距的[Length]值。 `None` 表示此值是从样式层次结构继承的。 长度对象提供方便的属性，例如 [pt] 和 [cm]，可以轻松转换为各种长度单位。

- **tab_stops**

    [TabStops] 对象提供对为此段落格式定义的制表位的访问。

- **widow_control**

    当 Word 重新分页文档时，如果段落中的第一行和最后一行与该段落的其余部分保持在同一页上，则为`True`。 `None` 表示其有效值是从样式层次结构继承的。
