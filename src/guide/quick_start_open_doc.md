# 打开文档

你需要做的第一件事是一份文件。最简单的方法是：

```python
from docx import Document

document = Document()
```

这将打开一个基于默认“模板”的空白文档，这与使用内置默认值在Word中启动新文档时所获得的内容非常相似。可以使用打开并处理现有的Word文档 **python-docx** ，但我们暂时把事情简单化。
