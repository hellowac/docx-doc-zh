# 删除header

可以通过将 `True` 分配给其 `.is_linked_to_previous` 属性来删除不需要的标头：

```python
>>> header.is_linked_to_previous = True
>>> header.is_linked_to_previous
True
```

当 `True` 分配给 `.is_linked_to_previous` 时，标题的内容将被不可逆转地删除。
