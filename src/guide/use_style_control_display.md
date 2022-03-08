- [控制样式在 Word UI 中的显示方式](#控制样式在-word-ui-中的显示方式)
  - [在样式库中显示样式](#在样式库中显示样式)
  - [从样式库中删除样式](#从样式库中删除样式)

# 控制样式在 Word UI 中的显示方式

[了解样式]: ../guide/understanding_styles.md
[样式行为]: ../guide/style_behavior.md

样式的属性分为两类，行为属性和格式属性。 它的行为属性控制样式出现在 Word UI 中的时间和位置。 其格式属性确定应用该样式的内容的格式，例如字体大小及其段落缩进。

风格有五个行为属性：

- [hidden](../api/style_base_style_object.md#hidden)
- [unhide_when_used](../api/style_base_style_object.md#unhide_when_used)
- [priority](../api/style_base_style_object.md#priority)
- [quick_style](../api/style_base_style_object.md#quick_style)
- [locked](../api/style_base_style_object.md#locked)

有关这些行为属性如何交互以确定样式在 Word UI 中出现的时间和位置的说明，请参阅[了解样式]中的[样式行为]部分。

`priority` 属性采用整数值。 其他四个样式行为属性是三态的，这意味着它们可以取值 `True`（打开）、`False`（关闭）或 `None`（继承）。

## 在样式库中显示样式

以下代码将实现 **“Body Text”** 段落样式首先出现在样式库中：

```python
>>> from docx import Document
>>> document = Document()
>>> style = document.styles['Body Text']

>>> style.hidden = False
>>> style.quick_style = True
>>> style.priorty = 1
```

## 从样式库中删除样式

此代码将从样式库中删除 **“Normal”** 段落样式，但允许它保留在推荐列表中：

```python
>>> style = document.styles['Normal']

>>> style.hidden = False
>>> style.quick_style = False
```
