# WD_SECTION_START

别名：WD_SECTION

指定分节符的开始类型。

例子：

```python
from docx.enum.section import WD_SECTION

section = document.sections[0]
section.start_type = WD_SECTION.NEW_PAGE
```

- **CONTINUOUS**

    连续分节。

- **NEW_COLUMN**

    新的列分节符。

- **NEW_PAGE**

    新的分页符。

- **EVEN_PAGE**

    甚至页面分节符。

- **ODD_PAGE**

    部分从下一个奇数页开始。
