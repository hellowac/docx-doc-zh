# ColorFormat对象

[RGBColor]: ../api/shared_rgbcolor_object.md
[MSO_THEME_COLOR_INDEX]: ../api/enum_mso_theme_color_index.md
[MSO_COLOR_TYPE]: ../api/enum_mso_color_type.md

**class docx.dml.color.ColorFormat**

提供对颜色设置的访问，例如 RGB 颜色、主题颜色和亮度调整。

- **rgb**

    如果未指定 RGB 颜色，则为 [RGBColor] 值或 `None`。

    当 `type` 为 `MSO_COLOR_TYPE.RGB` 时，此属性的值将始终为 [RGBColor] 值。 如果类型为 `MSO_COLOR_TYPE.THEME`，它也可能是 [RGBColor] 值，因为 Word 在分配主题颜色时会写入主题颜色的当前值。 在这种情况下，RGB 值应该被解释, 只是一个好的猜测，因为主题颜色在渲染时优先。 只要 `type` 为 `None` 或 `MSO_COLOR_TYPE.AUTO` 时，其值为 `None`。

    分配 [RGBColor] 值会导致类型变为 `MSO_COLOR_TYPE.RGB` 并删除任何主题颜色。 分配 `None` 会导致删除任何颜色，以便从样式层次结构继承有效颜色。

- **theme_color**

    如果未指定主题颜色，则为[MSO_THEME_COLOR_INDEX]的成员 或 `None` 。 当 `type` 为 `MSO_COLOR_TYPE.THEME` 时，此属性的值将始终是 [MSO_THEME_COLOR_INDEX] 的成员。 当 `type` 有任何其他值时，此属性的值为 `None`。

    分配 `MSO_THEME_COLOR_INDEX` 的成员会导致类型变为 `MSO_COLOR_TYPE.THEME`。 任何现有的 RGB 值都会保留，但会被 Word 忽略。 分配 `None` 会导致删除任何颜色规范，以便从样式层次结构继承有效颜色。

- **type**

    只读。 [MSO_COLOR_TYPE] 的成员，`RGB`、`THEME` 或 `AUTO` 之一，对应于定义此颜色的方式。 如果在此级别未应用颜色，则其值为 `None`，这会导致从样式层次结构继承有效颜色。
