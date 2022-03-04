# _LatentStyle对象

[LatentStyles]: ../api/style_latent_styles.md

**class docx.styles.latent._LatentStyle**

`w:lsdException` 元素的代理，当该样式的定义尚未存储在 `styles.xml` 部分中时，该元素指定该样式的显示行为。 此元素中的值会覆盖父 `w:latentStyles` 元素中指定的默认值。

- **delete()**

    删除此潜在样式定义，以便包含 [LatentStyles] 对象中定义的默认值为其每个属性提供有效值。 在调用此方法后尝试访问此对象上的任何属性将引发 `AttributeError`。

- **element**

    此对象代理的 lxml 元素。

- **hidden**

    指定此潜在样式是否应出现在推荐列表中的三态值。 `None` 表示有效值是从父 `<w:latentStyles>` 元素继承的。

- **locked**

    指定此潜在样式是否被锁定的三态值。 锁定的样式不会出现在样式面板或样式库中，并且不能应用于文档内容。 仅当为文档打开格式保护时（通过“开发人员”菜单），此行为才有效。

- **name**

    此异常适用的内置样式的名称。

- **priority**

    Word UI 中此潜在样式的整数排序键。

- **quick_style**

    三态值，指定此潜在样式在不隐藏时是否应出现在 Word 样式库中。 `None` 表示应该从其父 [LatentStyles] 对象中的默认值继承有效值。

- **unhide_when_used**

    三态值指定此样式是否应在下次将样式应用于内容时将其隐藏属性设置为 `False`。 `None` 表示应该从其父 [LatentStyles] 对象指定的默认值继承有效值。
