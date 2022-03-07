# 应用字符格式

[Run]: ../api/text_run_object.md
[Font]: ../api/text_font_object.md
[WD_UNDERLINE]: ../api/enum_wd_underline.md

字符格式应用于运行级别。 示例包括字体字体和大小、粗体、斜体和下划线。

[Run] 对象具有只读字体属性，提供对 [Font] 对象的访问。 运行的 [Font] 对象提供了用于获取和设置运行的字符格式的属性。

这里提供了几个例子。 有关可用属性的完整集，请参阅 [Font] API 文档。

可以像这样访问[Run]的字体：

```python
>>> from docx import Document
>>> document = Document()
>>> run = document.add_paragraph().add_run()
>>> font = run.font
```

字体和大小设置如下：

```python
>>> from docx.shared import Pt
>>> font.name = 'Calibri'
>>> font.size = Pt(12)
```

许多字体属性是三态的，这意味着它们可以采用值 `True` 、`False` 和 `None`。 `True` 表示该属性“开启”，`False` 表示该属性“关闭”。 从概念上讲， `None` 值意味着“继承”。 样式继承层次结构中存在运行，默认情况下从该层次结构继承其字符格式。 使用 [Font] 对象直接应用的任何字符格式都会覆盖继承的值。

粗体和斜体是三态属性，全大写、删除线、上标和许多其他属性也是如此。 有关完整列表，请参阅[Font] API 文档:

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

下划线是一种特殊情况。 它是三态属性和枚举值属性的混合体。 `True` 表示单下划线，是迄今为止最常见的。 `False` 表示没有下划线，但如果不需要下划线，通常 `None` 是正确的选择。 其他形式的下划线，例如双线或虚线，是使用 [WD_UNDERLINE] 枚举的成员指定的：

```python
>>> font.underline
None
>>> font.underline = True
>>> # or perhaps
>>> font.underline = WD_UNDERLINE.DOT_DASH
```
