# 了解多Section文档中header

[_Header.is_linked_to_previous]: ../api/section_header.md#is_linked_to_previous
[header.paragraphs]: ../api/section_header.md#paragraphs

“刚开始编辑”的方法适用于简单的案例，但要理解多节文档中的`header`行为，一些简单的概念会有所帮助。 简而言之：

1. 每个[Section]都可以有自己的`header`定义（但不是必须的）。
2. 缺少`header`定义的节会继承之前节的`header`。 [_Header.is_linked_to_previous] 属性仅反映标头定义的存在，当定义存在时为 `False`，不存在时为 `True`。
3. 缺少`header`定义是默认状态。 新文档没有定义的`header`，新插入的`section`也没有。 `.is_linked_to_previous` 在这两种情况下都报告 `True`。
4. 如果 [_Header] 对象具有`header`定义，则它的内容就是它自己的内容。 如果不是，则其内容是具有`header`定义的第一个先前部分的内容。 如果没有节具有`header`定义，则在第一个`section`上添加一个新节，并且所有其他节都继承该`section`。 `header`定义的添加发生在第一次访问`header`内容时，可能是通过引用 [header.paragraphs]。
