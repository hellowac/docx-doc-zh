# Font对象

[ColorFormat]: ../api/drawing_color_format.md
[WD_COLOR_INDEX]: ../api/enum_wd_color_index.md
[Font]: #
[docx.shared.Pt]: ../api/shared_pt_object.md
[Length]: ../api/shared_length_object.md
[int]: https://docs.python.org/3/library/functions.html#int
[WD_UNDERLINE]: ../api/enum_wd_underline.md

**class docx.text.run.Font**

代理对象, 用于包装 `<w:rPr>` 元素的父元素，并提供对字符属性的访问，例如字体名称、字体大小、粗体和下标。

- **all_caps** <a name="all_caps"></a>

    读/写。 使此字体中的文本以大写字母显示。

- **bold** <a name="bold"></a>

    读/写。 使此字体中的文本以粗体显示。

- **color** <a name="color"></a>

    一个 [ColorFormat] 对象，提供了一种获取和设置此字体的文本颜色的方法。

- **complex_script** <a name="complex_script"></a>

    读/写三态值。 如果为 `True`，则导致`run`中的字符被视为复杂脚本，而不管其 `Unicode` 值如何。

- **cs_bold** <a name="cs_bold"></a>

    读/写三态值。 当为 `True` 时，会使运行中的复杂脚本字符以粗体字显示。

- **cs_italic** <a name="cs_italic"></a>

    读/写三态值。 当为 `True` 时，会导致运行中的复杂脚本字符以斜体字体显示。

- **double_strike** <a name="double_strike"></a>

    读/写三态值。 当为 `True` 时，会导致运行中的文本带有双删除线。

- **emboss** <a name="emboss"></a>

    读/写三态值。 当为 `True` 时，会使运行中的文本看起来好像浮雕般从页面上抬起。

- **hidden** <a name="hidden"></a>

    读/写三态值。 当为 `True` 时，会导致运行中的文本从显示中隐藏，除非应用程序设置强制显示隐藏的文本。

- **highlight_color** <a name="highlight_color"></a>

    [WD_COLOR_INDEX] 的成员，指示应用突出显示的颜色，如果未应用突出显示，则为 `None`。

- **imprint** <a name="imprint"></a>

    读/写三态值。 如果为 `True`，则使运行中的文本看起来好像被压入页面。

- **italic** <a name="italic"></a>

    读/写三态值。 如果为 `True`，则使运行的文本以斜体显示。 `None` 表示有效值是从样式层次结构继承的。

- **math** <a name="math"></a>

    读/写三态值。 如果为 `True`，则指定此运行包含 **WML**，应该像处理 **Office Open XML Math** 一样处理。

- **name** <a name="name"></a>

    获取或设置此 [Font] 实例的字体名称，如果找到匹配的字体，则使其控制的文本以命名字体显示。 `None` 表示字体是从样式层次结构继承的。

- **no_proof** <a name="no_proof"></a>

    读/写三态值。 如果为 `True`，则指定此运行的内容在扫描文档的拼写和语法时不应报告任何错误。

- **outline** <a name="outline"></a>

    读/写三态值。 当 `True` 时，通过在每个字符字形的内部和外部边框周围绘制一个像素宽的边框，使运行中的字符看起来好像它们有一个轮廓。

- **rtl** <a name="rtl"></a>

    读/写三态值。 当 `True` 导致运行中的文本具有从右到左的特征。

- **shadow** <a name="shadow"></a>

    读/写三态值。 当 `True` 时，会使运行中的文本看起来好像每个字符都有阴影。

- **size** <a name="size"></a>

    读/写[Length]值或无，以英制单位 (`EMU`) 指示字体高度。 `None` 表示应该从样式层次结构继承字体大小。 [Length] 是 [int] 的子类，具有便于转换为点或其他长度单位的属性。 [docx.shared.Pt] 类允许方便地指定点值：

    ```python
    >> font.size = Pt(24)
    >> font.size
    304800
    >> font.size.pt
    24.0
    ```

- **small_caps** <a name="small_caps"></a>

    读/写三态值。 当为 `True` 时，`run`中的小写字符显示为大写字母，比为`run`指定的字体大小小两点。

- **snap_to_grid** <a name="snap_to_grid"></a>

    读/写三态值。 当 `True` 时，会导致`run`在布置此`run`中的字符时使用 `docGrid` 元素中定义的每行文档网格字符设置。

- **spec_vanish** <a name="spec_vanish"></a>

    读/写三态值。 当为 `True` 时，指定给定的`run`应始终表现为隐藏，即使当前文档中显示隐藏文本也是如此。 该属性具有与目录相关的非常狭窄的专门用途。 有关更多详细信息，请参阅规范 (`§17.3.2.36`)。

- **strike** <a name="strike"></a>

    读/写三态值。 当为 `True` 时，会导致运行中的文本以一条穿过行中心的水平线出现。

- **subscript** <a name="subscript"></a>

    布尔值，指示此 [Font] 中的字符是否显示为下标。 `None` 表示下标/下标值是从样式层次结构继承的。

- **superscript** <a name="superscript"></a>

    布尔值，指示此字体中的字符是否显示为上标。 `None` 表示下标/上标值是从样式层次结构继承的。

- **underline** <a name="underline"></a>

    此[Font]的下划线样式，`None`、`True`、`False` 之一，或来自 [WD_UNDERLINE] 的值。 `None` 表示字体从样式层次结构继承其下划线值。 `False` 表示没有下划线。 `True` 表示单下划线。 [WD_UNDERLINE] 中的值用于指定其他轮廓样式，例如双线、波浪线和点线。

- **web_hidden** <a name="web_hidden"></a>

    读/写三态值。 当为 `True` 时，指定当文档在网页视图中显示时应隐藏此`run`的内容。
