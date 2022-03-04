# Run对象

[Run]: #
[Font]: ../api/text_font_object.md
[InlineShape]: ../api/shapes_inline_shape.md
[_CharacterStyle]: ../api/style_character_style.md
[WD_UNDERLINE]: ../api/enum_wd_underline.md

**class docx.text.run.Run**

包装 `<w:r>` 元素的代理对象。 [Run] 上的一些属性采用三态值，`True`、`False` 或 `None`。 `True` 和 `False` 分别对应 `on` 和 `off`。 `None` 表示该属性不是直接在`run`中指定的，其有效值取自样式层次结构。

- **add_break(break_type=6)**

    在此 `run` 中添加一个 `break_type` 的中断元素。 `break_type` 可以采用值 `WD_BREAK.LINE`、`WD_BREAK.PAGE` 和 `WD_BREAK.COLUMN`，其中 **WD_BREAK** 是从 `docx.enum.text` 导入的。 `break_type` 默认为 `WD_BREAK.LINE`。

- **add_picture(image_path_or_stream, width=None, height=None)**

    返回包含由 `image_path_or_stream` 标识的图像的 [InlineShape] 实例，添加到此`run`的末尾。 `image_path_or_stream` 可以是路径（字符串）或包含二进制图像的类似文件的对象。 如果既没有指定宽度也没有指定高度，则图片以其原始大小显示。 如果只指定了一个，则它用于计算缩放因子，然后将其应用于未指定的维度，保留图像的纵横比。 图片的原始尺寸是使用图像文件中指定的每英寸点数 (`dpi`) 值计算的，如果没有指定值，则默认为 `72 dpi`，通常情况下。

- **add_tab()**

    在`run`结束时添加 `<w:tab/>` 元素，Word 将其解释为制表符。

- **add_text(text)**

    将新附加的 **_Text** 对象（对应于新的 `<w:t>` 子元素）返回到`run`，其中包含文本。 与将文本直接分配给 [Run.text](#text) 属性相比较，该方法可能更友好。

- **bold**

    读/写。 使`run`的文本以粗体显示。

- **clear()**

    删除所有内容后返回对此`run`的引用。 保留所有`run`格式。

- **font**

    [Font] 对象提供对该运行的字符格式属性的访问，例如字体名称和大小。

- **italic**

    读/写三态值。 如果为 `True`，则使运行的文本以斜体显示。

- **style**

    读/写。 一个 [_CharacterStyle] 对象，表示应用于此运行的字符样式。 如果运行没有直接应用的字符样式，则返回文档的默认字符样式（通常为默认字符字体）。 将此属性设置为 `None` 会删除任何直接应用的字符样式。

- **text** <a name="text"></a>

    通过将每个运行内容子元素的等效文本连接成 Python 字符串而形成的字符串。 每个 `<w:t>` 元素添加它包含的文本字符。 `<w:tab/>` 元素添加了一个 `\t` 字符。 `<w:cr/>` 或 `<w:br>` 元素每个都添加一个 `\n` 字符。 请注意，`<w:br>` 元素可以指示分页符或分栏符以及换行符。 所有 `<w:br>` 元素都转换为单个 `\n` 字符，无论其类型如何。 所有其他内容子元素，例如 `<w:drawing>`，都会被忽略。

    将文本分配给此属性具有相反的效果，将每个 `\t` 字符转换为 `<w:tab/>` 元素，将每个 `\n` 或 `\r` 字符转换为 `<w:cr/>` 元素。 任何现有的运行内容都会被替换。 `run`格式被保留。

- **underline**

    此 [Run] 的下划线样式，`None`、`True`、`False` 之一或来自 [WD_UNDERLINE] 的值。 `None` 值表示运行没有直接应用的下划线值，因此将继承其包含段落的下划线值。 将 `None` 分配给此属性会删除任何直接应用的下划线值。 `False` 值表示直接应用的无下划线设置，覆盖任何继承的值。 `True` 值表示单个下划线。 [WD_UNDERLINE] 中的值用于指定其他轮廓样式，例如双线、波浪线和点线。
