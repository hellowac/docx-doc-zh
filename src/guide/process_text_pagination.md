# 分页属性

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
