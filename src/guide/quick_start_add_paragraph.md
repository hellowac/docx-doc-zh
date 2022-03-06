# 添加段落

段落是文字的基础。它们用于正文，也用于标题和列表项，如项目符号。

下面是添加一个段落最简单的方法：

```python
paragraph = document.add_paragraph('Lorem ipsum dolor sit amet.')
```

此方法返回对段落的引用，即文档末尾新添加的段落。在本例中新段落的引用赋值给 `paragraph` ，除非我有需要，否则我将在下面的示例中省略这一点。在您的代码中，通常在添加项之后您不会对其执行任何操作，因此将引用保留下来没有太大意义。

也可以使用一个段落作为“光标”并在其正上方插入新段落：

```python
prior_paragraph = paragraph.insert_paragraph_before('Lorem ipsum')
```

这允许在文档的中间插入一个段落，这在修改现有文档而不是从头生成文档时非常重要。