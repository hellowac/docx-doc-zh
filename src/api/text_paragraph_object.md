# Paragraph对象

[WD_PARAGRAPH_ALIGNMENT]: ../api/enum_wd_paragraph_alignment.md
[ParagraphFormat]: ../api/text_paragraph_format.md
[Run]: ../api/text_run_object.md
[_ParagraphStyle]: ../api/style_paragraph_style.md

**class docx.text.paragraph.Paragraph**

代理对象, 用于包装 `<w:p>` 元素。

- **add_run(text=None, style=None)**

    向包含文本且字符样式由样式 ID 样式标识的此段落附加一个段落。 `text` 可以包含制表符 (\t) 字符，这些字符被转换为适当的 XML 格式的制表符。 `text` 还可以包含换行符 (\n) 或回车符 (\r)，每个字符都转换为换行符。

- **alignment**

    [WD_PARAGRAPH_ALIGNMENT] 枚举的成员，指定此段落的对齐设置。 `None` 值表示段落没有直接应用的对齐值，并将从其样式层次结构继承其对齐值。 将 `None` 分配给此属性会删除任何直接应用的对齐值。

- **clear()**

    删除所有内容后返回相同的段落。 保留段落级别的格式，例如样式。

- **insert_paragraph_before(text=None, style=None)**

    返回一个新创建的段落，直接插入到该段落之前。 如果提供了`text`，则新段落会在一次运行中包含该`text`。 如果提供了`style`，则将该`style`分配给新段落。

- **paragraph_format**

    [ParagraphFormat] 对象提供对该段落格式属性的访问，例如行距和缩进。

- **runs**

    与本段中的 `<w:r>` 元素对应的 [Run] 实例序列。

- **style**

    读/写。 [_ParagraphStyle] 对象，表示分配给此段落的样式。 如果没有为该段落分配明确的样式，则其值为文档的默认段落样式。 可以指定段落样式名称来代替段落样式对象。 指定 None 会删除任何应用的样式，使其有效值成为文档的默认段落样式。

- **text**

    通过连接段落中每个运行的文本形成的字符串。 XML 中的制表符和换行符分别映射到 `\t` 和 `\n` 字符。

    将文本分配给该属性会导致所有现有段落内容被替换为包含分配文本的单个`run`。 文本中的 `\t` 字符映射到 `<w:tab/>` 元素，每个 `\n` 或 `\r` 字符映射到换行符。 保留段落级别的格式，例如样式。 所有`run`级别的格式，例如粗体或斜体，都被删除。
