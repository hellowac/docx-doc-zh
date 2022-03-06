# 打开文档

最简单的开始方法是打开一个新文档而不指定要打开的文件：

```python
from docx import Document

document = Document()
document.save('test.docx')
```

这会从内置的默认模板创建一个新文档，并将其原封不动地保存到名为`“test.docx”`的文件中。所谓的`“默认模板”`其实就是一个没有内容的Word文件，和安装的`python-docx`包一起存放。它与您在选择 Word 的文件 > 从模板中新建...菜单项后选择Word 文档 模板大致相同。