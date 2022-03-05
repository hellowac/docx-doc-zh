# WD_UNDERLINE

指定应用于一系列字符的下划线样式。

- **NONE**

    没有下划线。 此设置覆盖任何继承的下划线值，因此可用于从继承其包含段落的下划线的运行中删除下划线。 请注意，这与将 `None` 分配给 `Run.underline` 不同。 `None` 是一个有效的赋值，但会导致运行继承其下划线值。 分配 `WD_UNDERLINE.NONE` 会导致无条件关闭下划线。

- **SINGLE**

    单行。 请注意，此设置是只写的，即为具有此设置的运行返回 `True`（而不是 `WD_UNDERLINE.SINGLE`）。

- **WORDS**

    仅在单个单词下划线。

- **DOUBLE**

    一条双线。

- **DOTTED**

    点。

- **THICK**

    一条粗线。

- **DASH**

    破折号。

- **DOT_DASH**

    交替的点和破折号。

- **DOT_DOT_DASH**

    交替的点点划线图案。

- **WAVY**

    单波浪线。

- **DOTTED_HEAVY**

    重点。

- **DASH_HEAVY**

    沉重的破折号。

- **DOT_DASH_HEAVY**

    交替的重点和重破折号。

- **DOT_DOT_DASH_HEAVY**

    交替的重点-点-划线图案。

- **WAVY_HEAVY**

    沉重的波浪线。

- **DASH_LONG**

    长破折号。

- **WAVY_DOUBLE**

    双波浪线。

- **DASH_LONG_HEAVY**

    长而沉重的破折号。
