# 水平对齐（对齐）

也称为对齐，段落的水平对齐方式可以设置为`左对齐`、`居中对齐`、`右对齐`或`完全对齐`（左右对齐），使用枚举值 [WD_PARAGRAPH_ALIGNMENT] 中的值：

```python
>>> from docx.enum.text import WD_ALIGN_PARAGRAPH
>>> document = Document()
>>> paragraph = document.add_paragraph()
>>> paragraph_format = paragraph.paragraph_format

>>> paragraph_format.alignment
None  # indicating alignment is inherited from the style hierarchy
>>> paragraph_format.alignment = WD_ALIGN_PARAGRAPH.CENTER
>>> paragraph_format.alignment
CENTER (1)
```
