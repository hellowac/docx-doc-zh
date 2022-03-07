# TabStops对象

[TabStop]: ../api/text_tab_stop_object.md
[ParagraphFormat]: ../api/text_paragraph_format.md
[Length]: ../api/shared_length_object.md
[WD_TAB_ALIGNMENT]: ../api/enum_wd_tab_alignment.md
[WD_TAB_LEADER]: ../api/enum_wd_tab_leader.md

**class docx.text.tabstops.TabStops**

一系列 [TabStop] 对象，提供对段落或段落样式的制表位的访问。 支持迭代、索引访问、`del` 和 `len()`。 使用 [ParagraphFormat] 的 *tab_stops* 属性访问它； 它不打算直接构建。

- **add_tab_stop(position, alignment=WD_TAB_ALIGNMENT.LEFT, leader=WD_TAB_LEADER.SPACES)** <a name="add_tab_stop"></a>

    在 `position` 处添加一个新的制表位，一个 [Length] 对象，指定制表位相对于段落边缘的位置。 负位置值有效并出现在悬挂缩进中。 制表符对齐默认为左对齐，但可以通过传递 [WD_TAB_ALIGNMENT] 枚举的成员作为对齐方式来指定。 可以通过传递 [WD_TAB_LEADER] 枚举的成员作为领导者来指定可选的领导者字符。

- **clear_all()**

    删除所有自定义制表位。
