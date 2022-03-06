# 应用粗体和斜体

为了理解粗体和斜体是如何工作的，你需要对段落中发生的事情有所了解。简短的版本是这样的：

1. 段落包含所有 **块级别格式**【`block-level`】，如`缩进`、`行高`、`制表符`等。
2. 以及在运行级别才应用的 **字符级格式** 【`Character-level`】，例如`粗体`和`斜体` 。段落中的所有内容都必须在一段中，但可以有多个。所以中间有一个粗体字的段落需要三个运行级别格式【`Run`】，一个正常的，一个包含单词的粗体，另一个正常的用于后面的文本。

当您通过向`.add_paragraph()`方法并提供文本来添加段落时，它会被放入一次`Run`中。您可以使用段落上的`.add_run()`方法添加更多内容：

```python
paragraph = document.add_paragraph('Lorem ipsum ')
paragraph.add_run('dolor sit amet.')
```

这会产生一个看起来就像从单个字符串创建的段落。除非您查看 `XML`，否则段落文本在何处被分成几行并不明显。注意第一个字符串末尾的尾随空格。您需要明确说明空格出现在运行开始和结束的位置。它们不会在运行之间自动插入。预计会被那个抓住几次:)。

[Run]对象同时具有一个 `.bold`和`.italic`属性，允许您为它们设置值：

```python
paragraph = document.add_paragraph('Lorem ipsum ')
run = paragraph.add_run('dolor')
run.bold = True
paragraph.add_run(' sit amet.')
```

这会产生如下所示的文本：“Lorem ipsum **dolor** sit amet。”

请注意，如果您不需要设置其他任何内容，您可以在`.add_run()`的结果上设置`粗体`或`斜体`：

```python
paragraph.add_run('dolor').bold = True

# is equivalent to:

run = paragraph.add_run('dolor')
run.bold = True

# except you don't have a reference to `run` afterward
```

不必为`.add_paragraph()`方法提供文本。如果您要通过[Run]构建段落，这可以使您的代码更简单：

```python
paragraph = document.add_paragraph()
paragraph.add_run('Lorem ipsum ')
paragraph.add_run('dolor').bold = True
paragraph.add_run(' sit amet.')
```
