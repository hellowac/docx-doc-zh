# 定义段落格式

[paragraph_format]: ../api/style_paragraph_style.md#paragraph_format
[ParagraphFormat]: ../api/style_paragraph_style.md

段落样式和表格样式都允许指定段落格式。 这些样式通过其 [paragraph_format] 属性提供对 [ParagraphFormat] 对象的访问。

段落格式包括布局行为，例如对齐、缩进、前后空格、前分页符和孤/孤控制。 有关可用属性的完整列表，请参阅 [ParagraphFormat] 对象的 API 文档页面。

下面是一个示例，说明如何创建具有 1/4 英寸悬挂缩进、上方 12 点间距和寡/孤控制的段落样式：

```python
>>> from docx.enum.style import WD_STYLE_TYPE
>>> from docx.shared import Inches, Pt
>>> document = Document()
>>> style = document.styles.add_style('Indent', WD_STYLE_TYPE.PARAGRAPH)
>>> paragraph_format = style.paragraph_format
>>> paragraph_format.left_indent = Inches(0.25)
>>> paragraph_format.first_line_indent = Inches(-0.25)
>>> paragraph_format.space_before = Pt(12)
>>> paragraph_format.widow_control = True
```
