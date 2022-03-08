# 使用特定于段落的样式属性

[next_paragraph_style]: ../api/style_paragraph_style.md#next_paragraph_style

段落样式具有 [next_paragraph_style] 属性，该属性指定要应用于在该样式的段落之后插入的新段落的样式。 当样式通常在一个序列中只出现一次时，这是最有用的，例如标题。 在这种情况下，段落样式可以在完成标题后自动设置回正文样式。

在最常见的情况下（正文段落），后续段落应采用与当前段落相同的样式。 如果未指定下一个段落样式，则默认通过应用相同的样式很好地处理这种情况。

下面是如何将标题 1 样式的下一段样式更改为正文文本的示例：

```python
>>> from docx import Document
>>> document = Document()
>>> styles = document.styles

>>> styles['Heading 1'].next_paragraph_style = styles['Body Text']
```

可以通过分配 `None` 或样式本身来恢复默认行为：

```python
>>> heading_1_style = styles['Heading 1']
>>> heading_1_style.next_paragraph_style.name
'Body Text'

>>> heading_1_style.next_paragraph_style = heading_1_style
>>> heading_1_style.next_paragraph_style.name
'Heading 1'

>>> heading_1_style.next_paragraph_style = None
>>> heading_1_style.next_paragraph_style.name
'Heading 1'
```
