# 字体颜色

[Font]: ../api/text_font_object.md
[ColorFormat]: ../api/drawing_color_format.md
[MSO_THEME_COLOR_INDEX]: ../api/enum_mso_theme_color_index.md
[rgb]: ../api/drawing_color_format.md#rgb
[theme_color]: ../api/drawing_color_format.md#theme_color
[type]: ../api/drawing_color_format.md#type
[MSO_COLOR_TYPE]: ../api/enum_mso_color_type.md
[RGBColor]: ../api/shared_rgbcolor_object.md

每个 [Font] 对象都有一个 [ColorFormat] 对象，该对象提供对其颜色的访问，通过其只读颜色属性访问。

将特定的 RGB 颜色应用于字体：

```python
>>> from docx.shared import RGBColor
>>> font.color.rgb = RGBColor(0x42, 0x24, 0xE9)
```

还可以通过分配 [MSO_THEME_COLOR_INDEX] 枚举的成员将字体设置为主题颜色：

```python
>>> from docx.enum.dml import MSO_THEME_COLOR
>>> font.color.theme_color = MSO_THEME_COLOR.ACCENT_1
```

通过将 `None` 分配给 [ColorFormat] 的 [rgb] 或 [theme_color] 属性，可以将字体的颜色恢复为其默认（继承）值：

```python
>>> font.color.rgb = None
```

确定字体的颜色首先要确定其颜色类型：

```python
>>> font.color.type
RGB (1)
```

[type] 属性的值可以是 [MSO_COLOR_TYPE] 枚举的成员或 `None`。

- **MSO_COLOR_TYPE.RGB** 表示它是 RGB 颜色。
- **MSO_COLOR_TYPE.THEME** 表示主题颜色。
- **MSO_COLOR_TYPE.AUTO** 表示其值由应用程序自动确定，通常设置为黑色。 （这个值比较少见。）
- **None** 表示不应用颜色，颜色继承自样式层次； 这是最常见的情况。

当颜色类型为 **MSO_COLOR_TYPE.RGB** 时，[rgb] 属性将是表示 RGB 颜色的 [RGBColor] 值：

```python
>>> font.color.rgb
RGBColor(0x42, 0x24, 0xe9)
```

当颜色类型为 **MSO_COLOR_TYPE.THEME** 时，[theme_color] 属性将是 [MSO_THEME_COLOR_INDEX] 的成员，表示主题颜色：

```python
>>> font.color.theme_color
ACCENT_1 (5)
```
