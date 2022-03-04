
- [快速开始](#快速开始)
  - [打开文档](#打开文档)
  - [添加段落](#添加段落)
  - [添加标题](#添加标题)
  - [添加分页符](#添加分页符)
  - [添加表](#添加表)
  - [添加图片](#添加图片)
    - [图像尺寸](#图像尺寸)
  - [应用段落样式](#应用段落样式)
  - [应用粗体和斜体](#应用粗体和斜体)
  - [应用字符样式](#应用字符样式)

# 快速开始

原文: [Quickstart](https://python-docx.readthedocs.io/en/latest/user/quickstart.html)

[Run]: #
[理解样式]: ../guide/understanding_styles.md

使用 **python-docx** 很简单。让我们简单介绍一下基本知识。

## 打开文档

你需要做的第一件事是一份文件。最简单的方法是：

```python
from docx import Document

document = Document()
```

这将打开一个基于默认“模板”的空白文档，这与使用内置默认值在Word中启动新文档时所获得的内容非常相似。可以使用打开并处理现有的Word文档 **python-docx** ，但我们暂时把事情简单化。

## 添加段落

段落是文字的基础。它们用于正文，也用于标题和列表项，如项目符号。

下面是添加一个段落最简单的方法：

```python
paragraph = document.add_paragraph('Lorem ipsum dolor sit amet.')
```

此方法返回对段落的引用，即文档末尾新添加的段落。在本例中新段落的引用赋值给 `paragraph` ，除非我有需要，否则我将在下面的示例中省略这一点。在您的代码中，通常在添加项之后您不会对其执行任何操作，因此将引用保留下来没有太大意义。

也可以使用一个段落作为“光标”并在其正上方插入新段落：

```python
prior_paragraph = paragraph.insert_paragraph_before('Lorem ipsum')
```

这允许在文档的中间插入一个段落，这在修改现有文档而不是从头生成文档时非常重要。

## 添加标题

除了短文档外，正文文本被分成多个部分，每个部分都以标题开头。以下是如何添加一个标题:

```python
document.add_heading('The REAL meaning of the universe')
```

默认情况下，这会添加一个顶级标题，在Word中显示为`“heading1”`。如果需要子节的标题，只需将所需级别指定为`1到9`之间的整数：

```python
document.add_heading('The role of dolphins', level=2)
```

如果指定级别为0，则会添加 **“标题”** 段落。这对于开始一个没有单独标题页的相对较短的文档非常方便。

## 添加分页符

每隔一段时间，你会希望下一页的文字放在另一页上，即使你所在的那一页还没有满。一个 **“硬”** 分页符就可以完成：

```python
document.add_page_break()
```

如果您发现自己经常使用它，这可能表明您可以通过更好地理解段落样式而受益。 您可以设置的一个段落样式属性是在具有该样式的每个段落之前立即分页。 因此，您可以将标题设置为某个级别以始终开始新页面。 稍后会详细介绍样式。 事实证明，它们对于真正充分利用 Word 至关重要。

## 添加表

人们经常会遇到以表格形式呈现更为适合的内容，排成整齐的行和列。Word 在这方面做得很好。添加表的方法如下：

```python
table = document.add_table(rows=2, cols=2)
```

表格有几个属性和方法，您需要这些属性和方法来填充它们。访问单个单元格可能是一个不错的起点。作为基础，您始终可以通过其行和列的索引访问单元格：

```python
cell = table.cell(0, 1)
```

这为您提供了我们刚刚创建的表格顶行中的右侧单元格。请注意，行和列索引是从零开始的，就像在列表访问中一样。

一旦你有了一个单元格，你可以在里面放一些东西：

```python
cell.text = 'parrot, possibly dead'
```

通常，一次访问一行单元格会更容易，例如从数据源填充可变长度的表时。表的`.rows属性`提供对各个行的访问，每行都有一个`.cells属性`。基于`Row` 和 `Column` 两个类的`.cells属性`都支持索引访问，如列表：

```python
row = table.rows[1]
row.cells[0].text = 'Foo bar to you.'
row.cells[1].text = 'And a hearty foo bar to you too sir!'
```

表上的`.rows`和`.columns`集合是可迭代的，因此您可以直接在for循环中使用它们。与`.cells`行或列上的序列相同：

```python
for row in table.rows:
    for cell in row.cells:
        print(cell.text)
```

如果要计算表中的行数或列数，只需在序列上使用`len()`：

```python
row_count = len(table.rows)
col_count = len(table.columns)
```

您还可以像这样以增量方式将行添加到表中：

```python
row = table.add_row()
```

这对于我们上面提到的可变长度表的场景来说非常方便：

```python
# get table data -------------
items = (
    (7, '1024', 'Plush kittens'),
    (3, '2042', 'Furbees'),
    (1, '1288', 'French Poodle Collars, Deluxe'),
)

# add table ------------------
table = document.add_table(1, 3)

# populate header row --------
heading_cells = table.rows[0].cells
heading_cells[0].text = 'Qty'
heading_cells[1].text = 'SKU'
heading_cells[2].text = 'Description'

# add a data row for each item
for item in items:
    cells = table.add_row().cells
    cells[0].text = str(item.qty)
    cells[1].text = item.sku
    cells[2].text = item.desc
```

**这同样适用于列**，尽管我还没有看到它的用例。

Word 有一组预先格式化的表格样式，您可以从其表格样式库中选择。您可以将其中一个应用到表中，如下所示：

```python
table.style = 'LightShading-Accent1'
```

样式名称是通过删除表格样式名称中的所有空格而形成的。您可以通过将鼠标悬停在 Word 的表格样式库中的缩略图上来找到表格样式名称。

## 添加图片

Word 允许您使用菜单项将图像放置在文档中。通过菜单栏的 `Insert` > `Photo` > `Picture from file`...，以下是 python-docx 如何做到这一点：

```python
document.add_picture('image-filename.png')
```

此示例使用一个路径，该路径从本地文件系统加载图像文件。您还可以使用类似文件的对象【file-like object】，本质上是任何充当打开文件的对象。如果您从数据库或通过网络检索图像并且不想涉及文件系统，这可能会很方便。

### 图像尺寸

默认情况下，添加的图像以`原始`大小显示。这通常比您想要的要大。原生大小计算为 `pixels / dpi` 。因此，分辨率为 `300 dpi` 的 `300x300` 像素图像出现在一英寸的正方形中。问题是大多数图像不包含 `dpi` 属性，默认为 `72 dpi`。这将使相同的图像在一侧显示为 `4.167` 英寸，大约是页面的一半。

要获得所需大小的图像，您可以使用方便的单位指定其宽度或高度，例如英寸或厘米：

```python
from docx.shared import Inches

document.add_picture('image-filename.png', width=Inches(1.0))
```

您可以自由指定宽度和高度，但通常您不想这样做。如果您只指定一个，python-docx则使用它来计算另一个的正确缩放值。这样可以保留`纵横比`，并且您的图片看起来不会被拉伸。

提供`Inches`和`Cm`类以让您以方便的单位指定测量值。在内部，python-docx使用英制公制单位，914400 作为一英寸。所以如果你忘记了，只是放一些东西，`width=2`你会得到一个非常小的图像:)。您需要从 `docx.shared` 子包中导入它们。您可以在算术中使用它们，就像它们是整数一样，实际上它们是。所以像这样的表达就可以了: `width = Inches(3) / thing_count`

## 应用段落样式

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

## 应用粗体和斜体

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

## 应用字符样式

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
