# 添加header定义(通常情况)

通过将 `False` 分配给其 `.is_linked_to_previous` 属性，可以为缺少的部分提供显式`header`定义：

```python
>>> header.is_linked_to_previous
True
>>> header.is_linked_to_previous = False
>>> header.is_linked_to_previous
False
```

新添加的`header`定义包含一个空段落。 请注意，以这种方式保留`header`有时很有用，因为它有效地“关闭”了该`Section`的`hdaer`以及之后的`header`，直到具有已定义`header`的下一个部分。

在已经具有`header`定义的`header`上将 `False` 分配给 `.is_linked_to_previous` 不会执行任何操作。

## 继承的内容自动定位

编辑`hdaer`的内容会编辑源`hdaer`的内容，同时考虑任何“继承”。 例如，如果第 2 个`section`的`hdaer`继承自第 1 个`section`并且您编辑第 2 个`section`的`header`，你实际上更改了第 1 个`section`的`header`的内容。 除非您首先明确地将 `False` 分配给其 `.is_linked_to_previous` 属性，否则不会为第 2 个`section`添加新的`header`定义。
