# 访问样式

[Document.styles]: ../api/document.md#styles
[Styles]: ../api/style_styles_object.md
[BaseStyle]: ../api/style_base_style_object.md

使用 [Document.styles] 属性访问样式：

```python
>>> document = Document()
>>> styles = document.styles
>>> styles
<docx.styles.styles.Styles object at 0x10a7c4f50>
```

[Styles] 对象提供对按名称定义的样式的字典式访问：

```python
>>> styles['Normal']
<docx.styles.style._ParagraphStyle object at <0x10a7c4f6b>
```

> **注意**
>
> 内置样式使用其英文名称存储在 WordprocessingML 文件中，例如 “Heading 1”，即使使用本地化版本的 Word 的用户会在 UI 中看到母语名称，例如 'Kop 1'。 因为 `python-docx` 对 WordprocessingML 文件进行操作，所以样式查找必须使用英文名称。 此外部站点上提供的文档允许您在本地语言名称和英文样式名称之间创建映射：<http://www.thedoctools.com/index.php?show=mt_create_style_name_list>
>
> 用户定义的样式（也称为自定义样式）未本地化，并且使用与 Word UI 中显示的名称完全相同的名称进行访问。

[Styles] 对象也是可迭代的。 通过使用 [BaseStyle] 上的标识属性，可以生成已定义样式的各种子集。 例如，此代码将生成已定义段落样式的列表：

```python
>>> from docx.enum.style import WD_STYLE_TYPE
>>> styles = document.styles
>>> paragraph_styles = [
...     s for s in styles if s.type == WD_STYLE_TYPE.PARAGRAPH
... ]
>>> for style in paragraph_styles:
...     print(style.name)
...
Normal
Body Text
List Bullet
```
