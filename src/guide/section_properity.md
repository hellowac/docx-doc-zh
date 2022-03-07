- [Section属性](#section属性)
  - [Section 开始类型](#section-开始类型)
  - [页面尺寸和方向](#页面尺寸和方向)
  - [页边距](#页边距)

# Section属性

[Section]: ../api/section_section.md
[Section.start_type]: ../api/section_section.md#start_type
[start_type]: ../api/section_section.md#start_type
[WD_SECTION_START]: ../api/enum_wd_section_start.md

该[Section]对象有十一个属性，允许发现和指定页面布局设置。

## Section 开始类型

[Section.start_type]描述该部分之前的中断类型：

```python
>>> section.start_type
NEW_PAGE (2)
>>> section.start_type = WD_SECTION.ODD_PAGE
>>> section.start_type
ODD_PAGE (4)
```

[start_type] 的值是 [WD_SECTION_START] 枚举的成员。

## 页面尺寸和方向

[Section] 上的三个属性描述页面尺寸和方向。 这些可以一起使用，例如，将部分的方向从纵向更改为横向：

```python
>>> section.orientation, section.page_width, section.page_height
(PORTRAIT (0), 7772400, 10058400)  # (Inches(8.5), Inches(11))
>>> new_width, new_height = section.page_height, section.page_width
>>> section.orientation = WD_ORIENT.LANDSCAPE
>>> section.page_width = new_width
>>> section.page_height = new_height
>>> section.orientation, section.page_width, section.page_height
(LANDSCAPE (1), 10058400, 7772400)
```

## 页边距

[Section] 上的七个属性共同指定了确定文本在页面上显示位置的各种边缘间距：

```python
>>> from docx.shared import Inches
>>> section.left_margin, section.right_margin
(1143000, 1143000)  # (Inches(1.25), Inches(1.25))
>>> section.top_margin, section.bottom_margin
(914400, 914400)  # (Inches(1), Inches(1))
>>> section.gutter
0
>>> section.header_distance, section.footer_distance
(457200, 457200)  # (Inches(0.5), Inches(0.5))
>>> section.left_margin = Inches(1.5)
>>> section.right_margin = Inches(1)
>>> section.left_margin, section.right_margin
(1371600, 914400)
```
