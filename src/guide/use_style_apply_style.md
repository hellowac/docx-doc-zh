# 应用样式

[Paragraph]: ../api/text_paragraph_object.md
[Run]: ../api/text_run_object.md
[Table]: ../api/table_object.md

[Paragraph]、[Run] 和 [Table] 对象各有一个样式属性。 将样式对象分配给此属性会应用该样式：

```python
>>> document = Document()
>>> paragraph = document.add_paragraph()
>>> paragraph.style
<docx.styles.style._ParagraphStyle object at <0x11a7c4c50>
>>> paragraph.style.name
'Normal'
>>> paragraph.style = document.styles['Heading 1']
>>> paragraph.style.name
'Heading 1'
```

也可以直接指定样式名称，在这种情况下，`python-docx` 将为您进行查找：

```python
>>> paragraph.style = 'List Bullet'
>>> paragraph.style
<docx.styles.style._ParagraphStyle object at <0x10a7c4f84>
>>> paragraph.style.name
'List Bullet'
```

样式也可以在创建时使用样式对象或其名称应用：

```python
>>> paragraph = document.add_paragraph(style='Body Text')
>>> paragraph.style.name
'Body Text'
>>> body_text_style = document.styles['Body Text']
>>> paragraph = document.add_paragraph(style=body_text_style)
>>> paragraph.style.name
'Body Text'
```
