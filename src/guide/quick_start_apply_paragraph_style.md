# 应用段落样式

如果您不知道 Word 段落样式是什么，您绝对应该检查一下。基本上，它允许您一次将一整套格式选项应用于段落。如果您知道它们是什么，它很像 CSS 样式。

您可以在创建段落时应用段落样式：

```python
document.add_paragraph('Lorem ipsum dolor sit amet.', style='ListBullet')
```

这种特殊的样式使段落显示为项目符号，这是一件非常方便的事情。您也可以在之后应用样式。这两行相当于上面的那一行：

```python
paragraph = document.add_paragraph('Lorem ipsum dolor sit amet.')
paragraph.style = 'List Bullet'
```

该样式是使用其样式名称指定的，在此示例中为 **“List Bullet”**。通常，样式名称与 Word 用户界面 (UI) 中的样式名称完全相同。
