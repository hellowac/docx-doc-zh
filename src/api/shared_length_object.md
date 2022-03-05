# Length对象

[Length]: ../api/shared_length_object.md

python-docx 中的长度值表示为标准化的[Length]值对象。 [Length] 是 `int` 的子类，具有 `int` 的所有行为。 此外，它具有内置的单位转换属性，例如：

```python
>>> inline_shape.height
914400
>>> inline_shape.height.inches
1.0
```

[Length]对象是使用一系列便利构造函数构造的，允许以最适合上下文的单位表示值。

**class docx.shared.Length**

长度构造函数类 [Inches]、[Cm]、[Mm]、[Px] 和 [Emu] 的基类。 表现为英制公制单位的 `int` 计数，`914,400` 英寸，`36,000` 毫米。 以只读属性的形式提供方便的单位转换方法。 不可变。

- **cm**

    以厘米（float）表示的等效长度。

- **emu**

    以英制公制单位 (int) 表示的等效长度。

- **inches**

    以英寸（float）表示的等效长度。

- **mm**

    以毫米（float）表示的等效长度。

- **pt**

    以点为单位的浮点长度.(float)

- **twips**

    以缇 (int) 表示的等效长度。
