# 缩进

[Length]: ../api/shared_length_object.md
[Inches]: ../api/shared_inches_object.md

缩进是段落与其容器边缘之间的水平空间，通常是页边距。段落可以在左侧和右侧分别缩进。第一行也可以有与段落其余部分不同的缩进。比段落其余部分缩进的第一行具有首行缩进。缩进较少的第一行有一个`悬挂缩进`。

缩进是使用一个[Length]值指定的，例如[Inches]、[Pt]或[Cm]。负值是有效的，会导致段落与页边距重叠指定的量。值`None`表示缩进值是从样式层次结构继承的。分配`None`给缩进属性会删除任何直接应用的缩进设置并恢复样式层次结构的继承：

```python
>>> from docx.shared import Inches
>>> paragraph = document.add_paragraph()
>>> paragraph_format = paragraph.paragraph_format

>>> paragraph_format.left_indent
None  # indicating indentation is inherited from the style hierarchy
>>> paragraph_format.left_indent = Inches(0.5)
>>> paragraph_format.left_indent
457200
>>> paragraph_format.left_indent.inches
0.5
```

右侧缩进的工作方式类似：

```python
>>> from docx.shared import Pt
>>> paragraph_format.right_indent
None
>>> paragraph_format.right_indent = Pt(24)
>>> paragraph_format.right_indent
304800
>>> paragraph_format.right_indent.pt
24.0
```

第一行缩进使用[first_line_indent] 属性指定，并相对于左缩进进行解释。负值表示`悬挂缩进`：

```python
>>> paragraph_format.first_line_indent
None
>>> paragraph_format.first_line_indent = Inches(-0.25)
>>> paragraph_format.first_line_indent
-228600
>>> paragraph_format.first_line_indent.inches
-0.25
```
