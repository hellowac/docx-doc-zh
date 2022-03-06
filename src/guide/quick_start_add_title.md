# 添加标题

除了短文档外，正文文本被分成多个部分，每个部分都以标题开头。以下是如何添加一个标题:

```python
document.add_heading('The REAL meaning of the universe')
```

默认情况下，这会添加一个顶级标题，在Word中显示为`“heading1”`。如果需要子节的标题，只需将所需级别指定为`1到9`之间的整数：

```python
document.add_heading('The role of dolphins', level=2)
```

如果指定级别为0，则会添加 **“标题”** 段落。这对于开始一个没有单独标题页的相对较短的文档非常方便。
