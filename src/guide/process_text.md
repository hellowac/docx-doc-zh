- [处理文本](#处理文本)
  - [块级与内联文本对象](#块级与内联文本对象)
  - [段落属性](#段落属性)
    - [水平对齐（对齐）](#水平对齐对齐)
    - [缩进](#缩进)
    - [制表位](#制表位)
    - [段落间距](#段落间距)
    - [行距](#行距)
    - [分页属性](#分页属性)
  - [应用字符格式](#应用字符格式)
    - [字体颜色](#字体颜色)

# 处理文本

[type]: #
[Run]: #
[Font]: #
[ColorFormat]: #
[ParagraphFormat]: #
[paragraph_format]: #
[WD_PARAGRAPH_ALIGNMENT]: #
[Length]: #
[Inches]: #
[Pt]: #
[Cm]: #
[rgb]: #
[RGBColor]: #
[first_line_indent]: #
[ParagraphFormat]: #
[tab_stops]: #
[TabStops]: #
[add_tab_stop()]: #
[TabStop]: #
[space_before]: #
[space_after]: #
[LengthPt]: #
[line_spacing]: #
[line_spacing_rule]: #
[WD_LINE_SPACING]: #
[keep_together]: #
[keep_with_next]: #
[page_break_before]: #
[widow_control]: #
[WD_UNDERLINE]: #
[WD_TAB_LEADER]: #
[WD_TAB_ALIGNMENT]: #
[MSO_THEME_COLOR_INDEX]: #
[MSO_COLOR_TYPE]: #
[theme_color]: #

为了有效地处理文本，重要的是首先了解一些 **块级元素**（如段落）和内联级对象【**inline-level objects**】（如运行[Run]）。

## 块级与内联文本对象

段落【**paragraph**】是 Word 中的主要块级对象【**block-level object**】。

**块级元素** 在其左右边缘之间流动其包含的文本，每次文本超出其右边界时添加一个附加行。对于段落，边界通常是`页边距`，但如果页面按列布局，它们也可以是`列边界`，如果段落出现在表格单元格内，它们也可以是`单元格边界`。

**表** 也​​是块级对象。

**内联对象** 是出现在块级项目内的一部分内容。例如，以粗体显示的单词或全部大写的句子。最常见的内联对象是run。块容器内的所有内容都在一个内联对象内。通常，一个段落包含一个或多个运行，每个运行都包含段落文本的某些部分。

**块级元素** 的属性指定它在页面上的位置，例如缩进和段落前后的空格。内联项目的属性通常指定内容出现的字体，例如`字体族`、`字体大小`、`粗体`和`斜体`。

## 段落属性

段落具有多种属性，用于指定其在其容器（通常是页面）中的位置以及将其内容划分为单独行的方式。

一般来说，最好定义一个`段落样式`，将这些属性收集到一个有意义的组中，并将适当的样式应用于每个段落，而不是重复地将这些属性直接应用于每个段落。这类似于`级联样式表` (CSS) 如何与 HTML 一起工作。此处描述的所有段落属性都可以使用样式设置，也可以直接应用于段落。

段落的格式属性是通过访问[paragraph_format]属性来使用[ParagraphFormat]段落属性。

### 水平对齐（对齐）

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

### 缩进

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

### 制表位

制表位决定段落文本中制表符的呈现方式。特别是，它指定制表符后面的文本将开始的位置，它将如何与该位置对齐，以及一个可选的前导符，它将填充制表符跨越的水平空间。

段落或样式的制表位包含在使用 [ParagraphFormat] 上的 [tab_stops] 属性访问的 [TabStops] 对象中：

```python
>>> tab_stops = paragraph_format.tab_stops
>>> tab_stops
<docx.text.tabstops.TabStops object at 0x106b802d8>
```

使用以下[add_tab_stop()]方法添加新的制表位：

```python
>>> tab_stop = tab_stops.add_tab_stop(Inches(1.5))
>>> tab_stop.position
1371600
>>> tab_stop.position.inches
1.5
```

对齐默认为左对齐，但可以通过提供 [WD_TAB_ALIGNMENT] 枚举的成员来指定。前导字符默认为空格，但可以通过提供[WD_TAB_LEADER] 枚举的成员来指定：

```python
>>> from docx.enum.text import WD_TAB_ALIGNMENT, WD_TAB_LEADER
>>> tab_stop = tab_stops.add_tab_stop(Inches(1.5), WD_TAB_ALIGNMENT.RIGHT, WD_TAB_LEADER.DOTS)
>>> print(tab_stop.alignment)
RIGHT (2)
>>> print(tab_stop.leader)
DOTS (1)
```

使用序列语义访问现有的制表位[TabStops]：

```python
>>> tab_stops[0]
<docx.text.tabstops.TabStop object at 0x1105427e8>
```

更多详细信息可在API文档[TabStops]中找到[TabStop]

### 段落间距

[space_before] 和 [space_after] 属性控制后续段落之间的间距，分别控制段落前后的间距。页面布局时，段落间距是折叠的，这意味着两个段落之间的间距是第一段的 [space_after] 和第二段的 [space_before] 的最大值。段落间距被指定为一个值，通常使用 ：[LengthPt]

```python
>>> paragraph_format.space_before, paragraph_format.space_after
(None, None)  # inherited by default

>>> paragraph_format.space_before = Pt(18)
>>> paragraph_format.space_before.pt
18.0

>>> paragraph_format.space_after = Pt(12)
>>> paragraph_format.space_after.pt
12.0
```

### 行距

行距是段落行中后续基线之间的距离。行距可以指定为绝对距离或相对于行高（本质上是所用字体的磅值）。典型的绝对衡量标准是 18 分。典型的相对度量将是双倍行距（2.0 行高）。默认行距是单行距（1.0 行高）。

行间距由 [line_spacing] 和 [line_spacing_rule] 属性的交互控制。 [line_spacing] 是长度值、（小）浮点数或 `None`。 长度值表示绝对距离。 浮点数表示行高数。 `None` 表示行距是继承的。 [line_spacing_rule] 是 [WD_LINE_SPACING] 枚举的成员或 `None`：

```python
>>> from docx.shared import Length
>>> paragraph_format.line_spacing
None
>>> paragraph_format.line_spacing_rule
None

>>> paragraph_format.line_spacing = Pt(18)
>>> isinstance(paragraph_format.line_spacing, Length)
True
>>> paragraph_format.line_spacing.pt
18.0
>>> paragraph_format.line_spacing_rule
EXACTLY (4)

>>> paragraph_format.line_spacing = 1.75
>>> paragraph_format.line_spacing
1.75
>>> paragraph_format.line_spacing_rule
MULTIPLE (5)
```

### 分页属性

四个段落属性，[keep_together]、[keep_with_next]、[page_break_before] 和 [widow_control] 控制段落在页面边界附近的行为方式。

- [keep_together] 导致整个段落出现在同一页面上，如果它会在两页之间被打破，则在段落之前发出分页符。

- [keep_with_next] 将段落与后续段落保持在同一页上。例如，这可用于将节标题与节的第一段保持在同一页面上。

- [page_break_before] 导致段落被放置在新页面的顶部。这可以用于章节标题以确保章节从新页面开始。

- [widow_control] 分页以避免将段落的第一行或最后一行与段落的其余部分放在单独的页面上。

所有这四个属性都是三态的，这意味着它们可以取值 `True`,`False`或`None`。`None`表示属性值是从样式层次结构继承的。`True`表示“开”和`False`表示“关”：

```python
>>> paragraph_format.keep_together
None  # all four inherit by default
>>> paragraph_format.keep_with_next = True
>>> paragraph_format.keep_with_next
True
>>> paragraph_format.page_break_before = False
>>> paragraph_format.page_break_before
False
```

## 应用字符格式

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

### 字体颜色

每个 [Font] 对象都有一个 [ColorFormat] 对象，该对象提供对其颜色的访问，通过其只读颜色属性访问。

将特定的 RGB 颜色应用于字体：

```python
>>> from docx.shared import RGBColor
>>> font.color.rgb = RGBColor(0x42, 0x24, 0xE9)
```

还可以通过分配 [MSO_THEME_COLOR_INDEX] 枚举的成员将字体设置为主题颜色：

```python
>>> from docx.enum.dml import MSO_THEME_COLOR
>>> font.color.theme_color = MSO_THEME_COLOR.ACCENT_1
```

通过将 `None` 分配给 [ColorFormat] 的 [rgb] 或 [theme_color] 属性，可以将字体的颜色恢复为其默认（继承）值：

```python
>>> font.color.rgb = None
```

确定字体的颜色首先要确定其颜色类型：

```python
>>> font.color.type
RGB (1)
```

[type] 属性的值可以是 [MSO_COLOR_TYPE] 枚举的成员或 `None`。

- **MSO_COLOR_TYPE.RGB** 表示它是 RGB 颜色。
- **MSO_COLOR_TYPE.THEME** 表示主题颜色。
- **MSO_COLOR_TYPE.AUTO** 表示其值由应用程序自动确定，通常设置为黑色。 （这个值比较少见。）
- **None** 表示不应用颜色，颜色继承自样式层次； 这是最常见的情况。

当颜色类型为 **MSO_COLOR_TYPE.RGB** 时，[rgb] 属性将是表示 RGB 颜色的 [RGBColor] 值：

```python
>>> font.color.rgb
RGBColor(0x42, 0x24, 0xe9)
```

当颜色类型为 **MSO_COLOR_TYPE.THEME** 时，[theme_color] 属性将是 [MSO_THEME_COLOR_INDEX] 的成员，表示主题颜色：

```python
>>> font.color.theme_color
ACCENT_1 (5)
```
