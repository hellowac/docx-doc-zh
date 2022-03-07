# 访问Section

[Document]: ../api/document.md
[sections]: ../api/document.md#sections

[Document] 对象上的 [sections] 属性提供对文档部分的访问：

```python
>>> document = Document()
>>> sections = document.sections
>>> sections
<docx.parts.document.Sections object at 0x1deadbeef>
>>> len(sections)
3
>>> section = sections[0]
>>> section
<docx.section.Section object at 0x1deadbeef>
>>> for section in sections:
...     print(section.start_type)
...
NEW_PAGE (2)
EVEN_PAGE (3)
ODD_PAGE (4)
```

从理论上讲，文档可能没有任何明确的部分，尽管我还没有看到这种情况发生。 如果您正在访问不可预测的 `.docx` 文件，您可能需要使用 `len()` 检查或 `try` 块来提供这种可能性，以避免未捕获的 `IndexError` 异常停止您的程序。
