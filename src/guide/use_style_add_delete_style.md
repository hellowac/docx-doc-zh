# 添加或删除样式

[delete()]: ../api/style_base_style_object.md#delete

可以通过指定唯一名称和样式类型将新样式添加到文档中：

```python
>>> from docx.enum.style import WD_STYLE_TYPE
>>> styles = document.styles
>>> style = styles.add_style('Citation', WD_STYLE_TYPE.PARAGRAPH)
>>> style.name
'Citation'
>>> style.type
PARAGRAPH (1)
```

使用 `base_style` 属性来指定新样式应该继承格式设置的样式：

```python
>>> style.base_style
None
>>> style.base_style = styles['Normal']
>>> style.base_style
<docx.styles.style._ParagraphStyle object at 0x10a7a9550>
>>> style.base_style.name
'Normal'
```

只需调用其 [delete()] 方法即可从文档中删除样式：

```python
>>> styles = document.styles
>>> len(styles)
10
>>> styles['Citation'].delete()
>>> len(styles)
9
```

> **注意**
>
> [Style.delete()] 方法从文档中删除样式的定义。 它不会影响应用该样式的文档中的内容。 文档中未定义样式的内容使用该内容对象的默认样式呈现，例如 在段落的情况下为“Normal”。
