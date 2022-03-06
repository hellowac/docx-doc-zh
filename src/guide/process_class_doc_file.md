# 打开“类文件”文档

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
