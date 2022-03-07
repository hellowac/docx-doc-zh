# 段落间距

[space_before]: ../api/text_paragraph_format.md#space_before
[space_after]: ../api/text_paragraph_format.md#space_after
[Length]: ../api/shared_length_object.md
[Pt]: ../api/shared_pt_object.md

[space_before] 和 [space_after] 属性控制后续段落之间的间距，分别控制段落前后的间距。页面布局时，段落间距是折叠的，这意味着两个段落之间的间距是第一段的 [space_after] 和第二段的 [space_before] 的最大值。段落间距被指定为一个值，通常使用 ：[Length] [Pt]

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
