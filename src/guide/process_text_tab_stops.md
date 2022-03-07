# 制表位

[ParagraphFormat]: ../api/text_paragraph_format.md
[tab_stops]: ../api/text_paragraph_format.md#tab_stops
[TabStops]: ../api/text_tab_stops_object.md
[add_tab_stop()]: ../api/text_tab_stops_object.md#add_tab_stop
[WD_TAB_ALIGNMENT]: ../api/enum_wd_tab_alignment.md
[WD_TAB_LEADER]: ../api/enum_wd_tab_leader.md
[TabStop]: ../api/text_tab_stop_object.md

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
