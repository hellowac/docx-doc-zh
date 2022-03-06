# 应用字符样式

除了指定一组段落级别设置的段落样式之外，Word 还具有指定一组运行级别设置的字符样式。一般来说，您可以将字符样式指定为特别的字体样式，包括其`字体`、`大小`、`颜色`、`粗体`、`斜体`等。

与段落样式一样，字符样式必须已经在您使用`Document()`调用打开的文档中定义（请参阅 [理解样式]）。

添加新运行时可以指定字符样式：

```python
paragraph = document.add_paragraph('Normal text, ')
paragraph.add_run('text with emphasis.', 'Emphasis')
```

您还可以在创建运行后将样式应用到运行。此代码产生与上面几行相同的结果：

```python
paragraph = document.add_paragraph('Normal text, ')
run = paragraph.add_run('text with emphasis.')
run.style = 'Emphasis'
```

与段落样式一样，样式名称与 Word UI 中显示的名称相同。
