# TabStop对象

[TabStops]: ../api/text_tab_stops_object.md
[WD_TAB_ALIGNMENT]: ../api/enum_wd_tab_alignment.md
[WD_TAB_LEADER]: ../api/enum_wd_tab_leader.md
[Length]: ../api/shared_length_object.md

**class docx.text.tabstops.TabStop**

应用于段落或样式的单个制表位。 使用列表语义对其包含的 [TabStops] 对象进行访问。

- **alignment**

   读/写。 指定此制表位的对齐设置的 [WD_TAB_ALIGNMENT] 的成员。

- **leader**

    读/写。 [WD_TAB_LEADER] 的成员，指定用作“前导”的重复字符，填充此选项卡跨越的空间。 分配 `None` 产生与分配 *WD_TAB_LEADER.SPACES* 相同的结果。

- **position**

    读/写。 一个 [Length] 对象，表示此制表位距段落内边缘的距离。 可能是正的或负的。
