# 添加表

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
