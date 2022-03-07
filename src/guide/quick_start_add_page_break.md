# 添加分页符

每隔一段时间，你会希望下一页的文字放在另一页上，即使你所在的那一页还没有满。一个 **“硬”** 分页符就可以完成：

```python
document.add_page_break()
```

如果您发现自己经常使用它，这可能表明您可以通过更好地理解段落样式而受益。 您可以设置的一个段落样式属性是在具有该样式的每个段落之前立即分页。 因此，您可以将标题设置为某个级别以始终开始新页面。 稍后会详细介绍样式。 事实证明，它们对于真正充分利用 Word 至关重要。