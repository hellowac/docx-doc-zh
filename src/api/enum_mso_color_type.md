# MSO_COLOR_TYPE

[RGBColor]: ../api/shared_rgbcolor_object.md

指定颜色规范方案

例子：

```python
from docx.enum.dml import MSO_COLOR_TYPE

assert font.color.type == MSO_COLOR_TYPE.THEME
```

- **RGB**

    颜色由 [RGBColor] 值指定。

- **THEME**

    颜色是预设的主题颜色之一。

- **AUTO**

    颜色由应用程序自动确定。
