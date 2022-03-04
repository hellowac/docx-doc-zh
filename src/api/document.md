
[docx.Document()]: ../api/document_constructor.md
[Paragraph]: ../api/text_paragraph_object.md
[Section]: ../api/section_section.md
[WD_SECTION_START]: ../api/enum_wd_section_start.md
[CoreProperties]: ../api/document_core_properties.md
[InlineShapes]: ../api/shapes_inline_shapes.md
[Paragraph]: ../api/text_paragraph_object.md
[Sections]: ../api/section_sections_object.md
[Settings]: ../api/document_settings_object.md
[Styles]: ../api/style_styles_object.md
[Table]: ../api/table_table_object.md

# Document对象

**class docx.document.Document**

WordprocessingML (WML) 文档。

不打算直接构建。 使用 [docx.Document()] 打开或创建文档。

- **add_heading(text=u'', level=1)** <a name="add_heading"></a>

    返回一个新添加到文档末尾的标题段落。

    标题段落将包含文本，其段落样式由级别决定。 如果 `level` 为 `0`，则样式设置为 `Title`。 如果级别为 `1`（或省略），则使用标题 `1`。 否则样式设置为标题 `{level}`。 如果级别超出范围 `0-9`，则引发 **ValueError**。

- **add_page_break()** <a name="add_page_break"></a>

    返回仅包含分页符的新 [Paragraph] 对象。

- **add_paragraph(text=u'', style=None)** <a name="add_paragraph"></a>

    返回一个新添加到文档末尾的段落，其中填充了文本并具有段落样式样式。 `text` 可以包含制表符 (\\t) 字符，这些字符被转换为适当的 XML 格式的制表符。 `text` 还可以包含换行符 (\\n) 或回车符 (\\r)，每个字符都转换为换行符。

- **add_picture(image_path_or_stream, width=None, height=None)** <a name="add_picture"></a>

    返回在文档末尾自己的段落中添加的新图片形状。 图片包含位于 `image_path_or_stream` 的图像，根据宽度和高度进行缩放。 如果既没有指定宽度也没有指定高度，则图片以其原始大小显示。 如果只指定了一个，则它用于计算缩放因子，然后将其应用于未指定的维度，保留图像的纵横比。 图片的原始尺寸是使用图像文件中指定的每英寸点数 (`dpi`) 值计算的，通常情况下，如果没有指定值，则默认为 `72 dpi`。

- **add_section(start_type=2)** <a name="add_section"></a>

    返回一个 [Section] 对象，该对象表示在文档末尾添加的新部分。 可选的 `start_type` 参数必须是 [WD_SECTION_START] 枚举的成员，如果未提供，则默认为 `WD_SECTION_START.NEW_PAGE`。

- **add_table(rows, cols, style=None)** <a name="add_table"></a>

    添加一个表格，该表格分别具有行数和列数以及表格样式的样式。 `style` 可以是段落样式对象或段落样式名称。 如果 `style` 为 `None`，则表格继承文档的默认表格样式。

- **core_properties** <a name="core_properties"></a>

    一个 [CoreProperties] 对象，提供对该文档核心属性的读/写访问。

- **inline_shapes** <a name="inline_shapes"></a>

    一个 [InlineShapes] 对象，提供对本文档中的内联形状的访问。 内联形状是一个图形对象，例如图片，包含在一系列文本中，表现得像字符字形，像段落中的其他文本一样流动。

- **paragraphs** <a name="paragraphs"></a>

    与文档中的段落相对应的[Paragraph]实例列表，按文档顺序排列。 请注意，修订标记内的段落（例如 `<w:ins>` 或 `<w:del>`）不会出现在此列表中。

- **part** <a name="part"></a>
  
    此文档的 [DocumentPart] 对象。

- **save(path_or_stream)** <a name="save"></a>

    将此文档保存到 path_or_stream，它可以是文件系统位置的路径（字符串）或类似文件的对象。

- **sections** <a name="sections"></a>

    [Sections] 对象提供对本文档中每个部分的访问。

- **settings** <a name="settings"></a>

    一个 [Settings] 对象，提供对该文档的文档级设置的访问。

- **styles** <a name="styles"></a>

    一个 [Styles] 对象，提供对该文档中样式的访问。

- **tables** <a name="tables"></a>

    与文档中的表相对应的[Table]实例列表，按文档顺序排列。 请注意，只有出现在文档顶层的表格才会出现在此列表中； 不会出现嵌套在表格单元格内的表格。 `<w:ins>` 或 `<w:del>` 等修订标记内的表格也不会出现在列表中。
