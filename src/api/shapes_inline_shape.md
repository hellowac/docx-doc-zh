# InlineShape对象

[InlineShape]: #
[Length]: ../api/shared_length_object.md
[Emu]: ../api/enum_index.md
[docx.enum.shape.WD_INLINE_SHAPE]: ../api/enum_wd_line_spacing.md

[InlineShape] 的 `width` 和 `height` 属性提供了一个 `length` 对象，它是 [Length] 的一个实例。 这些实例的行为类似于 `int`，但也具有内置的单位转换属性，例如:

```python
>>> inline_shape.height
914400
>>> inline_shape.height.inches
1.0
```

**class docx.shape.InlineShape(inline)**

<wp:inline> 元素的代理，代表内联图形对象的容器。

- **height**

    读/写。 此内联形状作为 [Emu] 实例的显示高度。

- **type**

    只读。此内联形状的类型作为 [docx.enum.shape.WD_INLINE_SHAPE] 的成员，例如 `LINKED_PICTURE`。

- **width**

    读/写。 此内联形状作为 [Emu] 实例的显示宽度。
