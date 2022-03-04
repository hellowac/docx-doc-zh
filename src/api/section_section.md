# Section对象

[Length]: ../api/shared_length_object.md
[_Footer]: ../api/section_header_footer.md#Footer
[_Header]: ../api/section_header_footer.md#Header
[odd_and_even_pages_header_footer]: ../api/document_settings_object.md#odd_and_even_pages_header_footer
[WD_SECTION_START]: ../api/enum_wd_section_start.md
[WD_ORIENTATION]: ../api/enum_wd_orientation.md

**class docx.section.Section(sectPr, document_part)**

文档 section ，提供对 section 和页面设置的访问。

还提供对页眉和页脚的访问。

- **bottom_margin** <a name="bottom_margin"></a>

    [Length]对象，表示此`Section`中所有页面的下边距，以英制公制单位表示。

- **different_first_page_header_footer** <a name="different_first_page_header_footer"></a>

    如果此`Section`显示不同的首页页眉和页脚，则为 `True`。

    读/写。 分别使用 [first_page_header](#first_page_header) 和 [first_page_footer](#first_page_footer) 访问首页页眉和页脚的定义。

- **even_page_footer** <a name="even_page_footer"></a>

    [_Footer] 对象定义偶数页的页脚内容。

    除非文档设置 [odd_and_even_pages_header_footer] 设置为`True`，否则此页脚定义的内容将被忽略。

- **even_page_header** <a name="even_page_header"></a>

    [_Header] 对象定义偶数页的标题内容。

    除非文档设置 [odd_and_even_pages_header_footer] 设置为`True`，否则此标题定义的内容将被忽略。

- **first_page_footer** <a name="first_page_footer"></a>

    [_Footer] 对象定义本节第一页的页脚内容。

    除非属性 [different_first_page_header_footer](#different_first_page_header_footer) 设置为 `True`，否则此页脚定义的内容将被忽略。

- **first_page_header** <a name="first_page_header"></a>

    [_Header] 对象定义本节第一页的标题内容。

    除非属性 [different_first_page_header_footer](#different_first_page_header_footer) 设置为 `True`，否则此标题定义的内容将被忽略。

- **footer** <a name="footer"></a>

    [_Footer] 对象表示此部分的默认页脚。

    当启用单独的奇数/偶数页脚时，默认页脚用于奇数页。 否则，它用于奇数页和偶数页。

- **footer_distance** <a name="footer_distance"></a>

    [Length] 对象，表示从页面底部边缘到页脚底部边缘的距离。 如果 XML 中没有设置，则为`None`。

- **gutter** <a name="gutter"></a>

    [Length] 对象，表示本节中所有页面的页面装订线大小（以英制公制单位）。 页面装订线是在内部边距中添加的额外间距，以确保页面装订后的边距均匀。

- **header** <a name="header"></a>

    [_Header] 对象表示此部分的默认页眉。

    当启用单独的奇数/偶数页眉时，默认页眉用于奇数页。 否则，它用于奇数页和偶数页。

- **header_distance** <a name="header_distance"></a>

    [Length] 对象，表示从页面上边缘到页眉上边缘的距离。 如果 XML 中没有设置，则为`None`。

- **left_margin** <a name="left_margin"></a>

    [Length] 对象，表示本节中所有页面的左边距，以英制公制单位表示。

- **orientation** <a name="orientation"></a>

    [WD_ORIENTATION] 枚举的成员，指定此部分的页面方向，***WD_ORIENT.PORTRAIT*** 或 ***WD_ORIENT.LANDSCAPE*** 之一。

- **page_height** <a name="page_height"></a>

    此部分使用的总页面高度，包括所有边缘间距值，例如边距。 考虑了页面方向，例如，当方向为横向时，对于信纸大小的纸张，其预期值为 `Inches(8.5)`。

- **page_width** <a name="page_width"></a>

    此部分使用的总页面宽度，包括所有边缘间距值，例如边距。 考虑了页面方向，例如，当方向为横向时，对于信纸大小的纸张，其预期值为 `Inches(11)`。

- **right_margin** <a name="right_margin"></a>

    [Length] 对象，表示此部分中所有页面的右边距，以英制公制单位表示。

- **start_type** <a name="start_type"></a>

    [WD_SECTION_START] 枚举的成员对应于本节的初始中断行为，例如 ***WD_SECTION.ODD_PAGE*** 如果该部分应该从下一个奇数页开始。

- **top_margin** <a name="top_margin"></a>

    [Length] 对象，表示本节中所有页面的上边距，以英制公制单位表示。
