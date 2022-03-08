# 添加Section

[Document.add_section()]: ../api/document.md#add_section
[Section]: ../api/section_section.md

该 [Document.add_section()]方法允许在文档末尾开始一个新[Section]。调用此方法后添加的段落和表格将出现在新的[Section]中：

```python
>>> current_section = document.sections[-1]  # last section in document
>>> current_section.start_type
NEW_PAGE (2)
>>> new_section = document.add_section(WD_SECTION.ODD_PAGE)
>>> new_section.start_type
ODD_PAGE (4)
```
