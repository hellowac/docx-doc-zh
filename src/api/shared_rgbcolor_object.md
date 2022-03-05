# RGBColor对象

**class docx.shared.RGBColor(r, g, b)**

定义特定 RGB 颜色的不可变值对象。

`r`、`g` 和 `b` 都是 `0-255` 范围内的整数，包括 `0-255`。 使用十六进制整数表示法，例如 `0x42` 可以增强使用十六进制 RGB 值的可读性：

```python
>>> lavender = RGBColor(0xff, 0x99, 0xcc)
```

- classmethod from_string(rgb_hex_str)

    从 RGB 颜色十六进制字符串（如`“3C2F80”`）返回一个新实例。
