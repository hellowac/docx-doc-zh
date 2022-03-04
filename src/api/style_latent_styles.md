# LatentStyles对象

[_LatentStyle]: ../api/style_laten_style.md
[LatentStyles]: #

**class docx.styles.latent.LatentStyles**

提供对本文档中潜在样式的默认行为和 [_LatentStyle] 对象集合的访问，这些对象定义了对特定命名潜在样式的这些默认值的覆盖。

- **add_latent_style(name)**

    返回一个新添加的 [_LatentStyle] 对象，以覆盖在此潜在样式对象中为具有名称的内置样式定义的继承默认值。

- **default_priority**

    `0` 到 `99` 之间的整数，指定样式列表和样式库中潜在样式的默认排序顺序。 如果未指定任何值，则为`None`，这会导致 Word 使用默认值 99。

- **default_to_hidden**

    布尔值，指定是否隐藏潜在样式的默认行为。 隐藏的样式不会出现在推荐列表或样式库中。

- **default_to_locked**

    布尔值，指定是否要锁定潜在样式的默认行为。 锁定的样式不会出现在样式面板或样式库中，并且不能应用于文档内容。 仅当为文档打开格式保护时（通过“开发人员”菜单），此行为才有效。

- **default_to_quick_style**

    布尔值，指定潜在样式的默认行为是否在不隐藏时显示在样式库中。

- **default_to_unhide_when_used**

    布尔值，指定潜在样式的默认行为是否在首次应用于内容时不隐藏。

- **element**

    此对象代理的 lxml 元素。

- **load_count**

    整数，指定要初始化为此 [LatentStyles] 对象中指定的默认值的内置样式的数量。 如果 XML 中没有设置，则为`None`（非常罕见）。 默认 Word 2011 模板将此值设置为 `276`，说明 Word 2010 中的内置样式。
