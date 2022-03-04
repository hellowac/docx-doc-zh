# 处理文档

`python-docx`允许您创建新文档以及对现有文档进行更改。实际上，它只允许您对现有文档进行更改；只是如果您从一个没有任何内容的文档开始，一开始可能会觉得您是从头开始创建一个文档。

这个特性是一个强大的特性。文档的外观很大程度上取决于删除所有内容时留下的部分。样式、页眉和页脚等内容与主要内容分开包含，允许您在起始文档中进行大量自定义，然后出现在您生成的文档中。

让我们逐步完成创建文档的步骤，一次创建一个示例，从您可以对文档执行的两项主要操作开始，将其打开并保存。

## 打开文档

最简单的开始方法是打开一个新文档而不指定要打开的文件：

```python
from docx import Document

document = Document()
document.save('test.docx')
```

这会从内置的默认模板创建一个新文档，并将其原封不动地保存到名为`“test.docx”`的文件中。所谓的`“默认模板”`其实就是一个没有内容的Word文件，和安装的`python-docx`包一起存放。它与您在选择 Word 的文件 > 从模板中新建...菜单项后选择Word 文档 模板大致相同。

## 真正打开一个文档

如果您想对最终文档进行更多控制，或者如果您想更改现有文档，您需要打开一个带有文件名的文档：

```python
document = Document('existing-document-file.docx')
document.save('new-file-name.docx')
```

**注意事项：**

- 您可以通过这种方式打开任何 Word 2007 或更高版本的文件（来自 Word 2003 和更早版本的 `.doc` 文件将不起作用）。虽然您可能还无法操作所有内容，但其中已经存在的任何内容都可以正常加载和保存。功能集仍在构建中，因此您还不能添加或更改诸如页眉或脚注之类的内容，但如果文档有它们，python-docx则足够礼貌，可以不理会它们，并且足够聪明，可以在不真正了解它们是什么的情况下保存它们。
- 如果使用相同的文件名打开和保存文件，python-docx会乖乖地覆盖原文件而不保存原文件。您需要确保这是您想要的。

## 打开“类文件”文档

python-docx可以从所谓的类文件对象打开文档。它还可以保存到类似文件的对象。当您想通过网络连接或从数据库获取源文档或目标文档并且不想（或不允许）与文件系统交互时，这会很方便。实际上，这意味着您可以传递打开的文件或 StringIO/BytesIO 流对象来打开或保存文档，如下所示：

```python
f = open('foobar.docx', 'rb')
document = Document(f)
f.close()

# or

with open('foobar.docx', 'rb') as f:
    source_stream = StringIO(f.read())
document = Document(source_stream)
source_stream.close()
...
target_stream = StringIO()
document.save(target_stream)
```

`'rb'`并非所有操作系统都需要文件打开模式参数。默认情况下有`'r'`就足够了，但在 Windows 和至少某些版本的 Linux 上需要`“b”`（选择二进制模式）以允许 `Zipfile` 打开文件。

好的，所以您已经打开了一个文档，并且很确定您可以稍后将其保存在某个地方。接下来请参阅其他内容……
