# 访问Section的header

[Section]: ../api/section_section.md
[_Header]: ../api/section_header.md
[Section.header]: ../api/section_section.md#header
[_Header.is_linked_to_previous]: ../api/section_header.md#is_linked_to_previous

页眉和页脚链接到一个[Section]； 这允许每个部分具有不同的页眉和/或页脚。 例如，横向部分的标题可能比纵向部分更宽。

每个`section`对象都有一个 `.header` 属性，提供对该部分的 [_Header] 对象的访问：

```python
>>> document = Document()
>>> section = document.sections[0]
>>> header = section.header
>>> header
<docx.section._Header object at 0x...>
```

[_Header] 对象始终存在于 [Section.header] 上，即使没有为该部分定义标题。 [_Header.is_linked_to_previous] 表示存在实际的标头定义：

```python
>>> header.is_linked_to_previous
True
```

`True` 值表示 [_Header] 对象不包含标题定义，并且该部分将显示与前一部分相同的标题。 这种“继承”行为是递归的，因此“链接”标头实际上是从具有标头定义的第一个先前部分获取其定义。 此“链接”状态在 Word UI 中指示为“与以前相同”。

新文档没有标题（在它包含的单个部分上），因此 `.is_linked_to_previous` 在这种情况下为 `True`。 请注意，这种情况可能有点违反直觉，因为没有前一个节标题可以链接到。 在这种“没有前一个标题”的情况下，不显示任何标题。
