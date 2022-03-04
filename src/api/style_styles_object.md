# Styles对象

[Document.styles]: ../api/document.md#styles
[LatentStyles]: ../api/style_latent_styles.md
[_LatentStyle]: ../api/style_laten_style.md

**class docx.styles.styles.Styles**

提供对文档中定义的样式的访问。

使用 [Document.styles] 属性访问。 通过样式名称支持 `len()`、迭代和字典样式访问。

- **add_style(name, style_type, builtin=False)** <a name="add_style"></a>

    返回一个新添加的 **style_type** 样式对象，并由名称标识。 可以通过为可选的内置参数传递 `True` 来定义内置样式。

- **default(style_type)** <a name="default"></a>

    如果没有为该类型定义默认值（不常见），则返回 **style_type** 或 `None` 的默认样式。

- **element** <a name="element"></a>

    此对象代理的 `lxml` 元素。

- **latent_styles** <a name="latent_styles"></a>

    一个 [LatentStyles] 对象，提供对潜在样式的默认行为和 [_LatentStyle] 对象集合的访问，这些对象为特定命名的潜在样式定义了这些默认值的覆盖。
