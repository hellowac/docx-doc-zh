# _CharacterStyle对象

[docx.styles.style.BaseStyle]: ../api/style_base_style_object.md
[Run]: ../api/text_run_object.md
[font]: #font
[Font]: ../api/text_font_object.md

**class docx.styles.style._CharacterStyle**

继承自: [docx.styles.style.BaseStyle]

一种字符样式。 字符样式应用于 [Run] 对象，主要通过其[font]属性中的 [Font] 对象提供字符级格式。

- **base_style** <a name="base_style"></a>

    此样式继承的样式对象，如果此样式不基于其他样式，则为 `None`。

- **builtin** <a name="builtin"></a>

    只读。 如果此样式是内置样式，则为`True`。 `False` 表示它是自定义（用户定义的）样式。 请注意，此值基于 XML 中是否存在 *customStyle* 属性，而不是基于 Word 中内置了哪些样式的特定知识。

- **delete()** <a name="delete"></a>

    从文档中删除此样式定义。 请注意，调用此方法不会删除或更改应用于任何文档内容的样式。 具有已删除样式的内容项将使用默认样式呈现，与文档中未定义样式的任何内容一样。

- **font** <a name="font"></a>

    [Font] 对象提供对该样式的字符格式属性的访问，例如字体名称和大小。

- **hidden** <a name="hidden"></a>

    如果在样式库和推荐样式列表中禁止显示此样式，则为`True`。 否则为`False`。 为了在样式库中显示，此值必须为 `False`，并且 [quick_style] 必须为 `True`。

- **locked** <a name="locked"></a>

    读/写布尔值。 如果此样式已锁定，则为`True`。 锁定的样式不会出现在样式面板或样式库中，并且不能应用于文档内容。 仅当为文档打开格式保护时（通过“开发人员”菜单），此行为才有效。

- **name** <a name="name"></a>

    此样式的 UI 名称。

- **priority** <a name="priority"></a>

    在 Word UI 中控制此样式的显示顺序的整数排序键。 `None` 表示未定义任何设置，导致 Word 使用默认值 `0`。样式名称用作辅助排序键来解析具有相同优先级值的样式的排序。

- **quick_style** <a name="quick_style"></a>

    当[hidden]为`False`时, 此属性为`True`，则表示此样式应显示在样式库中. 读/写布尔值。

- **unhide_when_used** <a name="unhide_when_used"></a>

    如果应用程序应该在下次将其应用于内容时使此样式可见，则为`True`。 否则为`False`。 请注意，python-docx 在应用于内容时不会自动取消隐藏该属性为 `True` 的样式。
