- [使用潜在样式](#使用潜在样式)
  - [访问文档中的潜在样式](#访问文档中的潜在样式)
  - [更改潜在样式默认值](#更改潜在样式默认值)
  - [添加潜在样式定义](#添加潜在样式定义)
  - [删除潜在样式定义](#删除潜在样式定义)

# 使用潜在样式

[了解样式]: ../guide/understanding_styles.md
[内置样式]: ../guide/builtin_style.md
[潜在样式]: ../guide/latent_styles.md
[LatentStyles]: ../api/style_latent_styles.md
[_LatentStyle]: ../api/style_laten_style.md
[add_latent_style()]: ../api/style_latent_styles.md#add_latent_style

有关潜在样式如何定义尚未在 `.docx` 文件的 `styles.xml` 部分中定义的内置样式的行为属性的说明，请参阅[了解样式]中的[内置样式]和[潜在样式]部分。

## 访问文档中的潜在样式

文档中的潜在样式可从样式对象访问：

```python
>>> document = Document()
>>> latent_styles = document.styles.latent_styles
```

[LatentStyles] 对象支持按样式名称的 `len()`、迭代和字典样式访问：

```python
>>> len(latent_styles)
161

>>> latent_style_names = [ls.name for ls in latent_styles]
>>> latent_style_names
['Normal', 'Heading 1', 'Heading 2', ... 'TOC Heading']

>>> latent_quote = latent_styles['Quote']
>>> latent_quote
<docx.styles.latent.LatentStyle object at 0x10a7c4f50>
>>> latent_quote.priority
29
```

## 更改潜在样式默认值

[LatentStyles] 对象还提供对当前文档中内置样式的默认行为属性的访问。 这些默认值为 [_LatentStyle] 定义的任何未定义属性以及没有显式潜在样式定义的内置样式的所有行为属性提供值。 有关完整的可用属性集，请参阅 [LatentStyles] 对象的 API 文档：

```python
>>> latent_styles.default_to_locked
False
>>> latent_styles.default_to_locked = True
>>> latent_styles.default_to_locked
True
```

## 添加潜在样式定义

可以使用 [LatentStyles] 上的 [add_latent_style()] 方法添加新的潜在样式。 此代码为内置样式“List Bullet”添加了一个新的潜在样式，将其设置为出现在样式库中：

```python
>>> latent_style = latent_styles['List Bullet']
KeyError: no latent style with name 'List Bullet'
>>> latent_style = latent_styles.add_latent_style('List Bullet')
>>> latent_style.hidden = False
>>> latent_style.priority = 2
>>> latent_style.quick_style = True
```

## 删除潜在样式定义

可以通过调用其 **delete()** 方法来删除潜在样式定义：

```python
>>> latent_styles['Light Grid']
<docx.styles.latent.LatentStyle object at 0x10a7c4f50>
>>> latent_styles['Light Grid'].delete()
>>> latent_styles['Light Grid']
KeyError: no latent style with name 'Light Grid'
```
