# 定义字符格式

[font]: ../api/use_style_define_character_style.md
[Font]: ../api/text_font_object.md
[WD_UNDERLINE]: ../api/enum_wd_underline.md

字符、段落和表格样式都可以指定要应用于具有该样式的内容的字符格式。 所有可以直接应用于文本的字符格式都可以在样式中指定。 示例包括字体字体和大小、粗体、斜体和下划线。

这三种样式类型中的每一种都有一个[font]属性，提供对 [Font] 对象的访问。 样式的 [Font] 对象提供用于获取和设置该样式的字符格式的属性。

这里提供了几个例子。 有关可用属性的完整集，请参阅 [Font] API 文档。

可以像这样访问样式的字体：

```python
>>> from docx import Document
>>> document = Document()
>>> style = document.styles['Normal']
>>> font = style.font
```

字体和大小设置如下：

```python
>>> from docx.shared import Pt
>>> font.name = 'Calibri'
>>> font.size = Pt(12)
```

许多字体属性是三态的，这意味着它们可以采用值 `True`、`False` 和 `None`。 `True` 表示该属性“开启”，`False` 表示该属性“关闭”。 从概念上讲， `None` 值意味着“继承”。 因为样式存在于继承层次结构中，所以能够在层次结构中的正确位置指定属性非常重要，通常在层次结构中尽可能远。 例如，如果所有标题都应采用 Arial 字体，则将属性设置为 `Heading 1` 样式并让 `Heading 2` 从 `Heading 1` 继承会更有意义。

粗体和斜体是三态属性，全大写、删除线、上标和许多其他属性也是如此。 有关完整列表，请参阅 [Font] API 文档：

```python
>>> font.bold, font.italic
(None, None)
>>> font.italic = True
>>> font.italic
True
>>> font.italic = False
>>> font.italic
False
>>> font.italic = None
>>> font.italic
None
```

下划线是一种特殊情况。 它是三态属性和枚举值属性的混合体。 `True` 表示单下划线，是迄今为止最常见的。 `False` 表示没有下划线，但如果不需要下划线，通常 `None` 是正确的选择，因为很少从基本样式继承它。 其他形式的下划线，例如双线或虚线，是使用 [WD_UNDERLINE] 枚举的成员指定的：

```python
>>> font.underline
None
>>> font.underline = True
>>> # or perhaps
>>> font.underline = WD_UNDERLINE.DOT_DASH
```
