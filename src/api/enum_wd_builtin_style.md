
- [WD_BUILTIN_STYLE](#wd_builtin_style)
  - [文本类](#文本类)
  - [格式](#格式)
  - [标题](#标题)
  - [HTML](#html)
  - [超链接](#超链接)
  - [索引](#索引)
  - [列表](#列表)
  - [列表项目符号](#列表项目符号)
  - [列表继续](#列表继续)
  - [列表编号](#列表编号)
  - [宏](#宏)
  - [表格](#表格)
  - [标题](#标题-1)

# WD_BUILTIN_STYLE

别名：WD_STYLE

指定内置的 Microsoft Word 样式。

例子：

```python
from docx import Document
from docx.enum.style import WD_STYLE

document = Document()
styles = document.styles
style = styles[WD_STYLE.BODY_TEXT]
```

## 文本类

- **BLOCK_QUOTATION**

    块文本。

- **BODY_TEXT**

    正文文本。

- **BODY_TEXT_2**

    正文文本 2.

- **BODY_TEXT_3**

    正文文本 3.

- **BODY_TEXT_FIRST_INDENT**

    正文文本第一个缩进.

- **BODY_TEXT_FIRST_INDENT_2**

    正文文本第二个缩进.

- **BODY_TEXT_INDENT**

    正文文本缩进.

- **BODY_TEXT_INDENT_2**

    正文文本缩进 2.

- **BODY_TEXT_INDENT_3**

    正文文本缩进 3.

## 格式

- **BOOK_TITLE**

    书名.

- **CAPTION**

    标题.

- **CLOSING**

    结束.

- **COMMENT_REFERENCE**

    评论参考.

- **COMMENT_TEXT**

    评论文本.

- **DATE**

    日期.

- **DEFAULT_PARAGRAPH_FONT**

    默认段落字体.

- **EMPHASIS**

    重点.

- **ENDNOTE_REFERENCE**

    尾注参考.

- **ENDNOTE_TEXT**

    尾注文本.

- **ENVELOPE_ADDRESS**

    信封地址.

- **ENVELOPE_RETURN**

    信封退回.

- **FOOTER**

    页脚.

- **FOOTNOTE_REFERENCE**

    脚注参考.

- **FOOTNOTE_TEXT**

    脚注文本.

## 标题

- **HEADER**

    标题.

- **HEADING_1**

    标题 1.

- **HEADING_2**

    标题 2.

- **HEADING_3**

    标题 3.

- **HEADING_4**

    标题 4.

- **HEADING_5**

    标题 5.

- **HEADING_6**

    标题 6.

- **HEADING_7**

    标题 7.

- **HEADING_8**

    标题 8.

- **HEADING_9**

    标题 9.

## HTML

- **HTML_ACRONYM**

    HTML 首字母缩略词.

- **HTML_ADDRESS**

    HTML 地址.

- **HTML_CITE**

    HTML 引用.

- **HTML_CODE**

    HTML 代码.

- **HTML_DFN**

    HTML 定义.

- **HTML_KBD**

    HTML 键盘.

- **HTML_NORMAL**

    常规 (Web).

- **HTML_PRE**

    HTML 预格式化.

- **HTML_SAMP**

    HTML 示例.

- **HTML_TT**

    HTML 打字机.

- **HTML_VAR**

    HTML 变量.

## 超链接

- **HYPERLINK**

    超链接.

- **HYPERLINK_FOLLOWED**

    关注的超链接.

## 索引

- **INDEX_1**

    索引 1.

- **INDEX_2**

    索引 2.

- **INDEX_3**

    索引 3.

- **INDEX_4**

    索引 4.

- **INDEX_5**

    索引 5.

- **INDEX_6**

    索引 6.

- **INDEX_7**

    索引 7.

- **INDEX_8**

    索引 8.

- **INDEX_9**

    索引 9.

- **INDEX_HEADING**

    索引标题

- **INTENSE_EMPHASIS**

    强烈强调。

- **INTENSE_QUOTE**

    强烈引用

- **INTENSE_REFERENCE**

    强烈参考

- **LINE_NUMBER**

    电话号码。

## 列表

- **LIST**

    列表.

- **LIST_2**

    列表 2.

- **LIST_3**

    列表 3.

- **LIST_4**

    列表 4.

- **LIST_5**

    列表 5.

## 列表项目符号

- **LIST_BULLET**

    列表项目符号.

- **LIST_BULLET_2**

    列表项目符号 2.

- **LIST_BULLET_3**

    列表项目符号 3.

- **LIST_BULLET_4**

    列表项目符号 4.

- **LIST_BULLET_5**

    列表项目符号 5.

## 列表继续

- **LIST_CONTINUE**

    列表继续.

- **LIST_CONTINUE_2**

    列表继续 2.

- **LIST_CONTINUE_3**

    列表继续 3.

- **LIST_CONTINUE_4**

    列表继续 4.

- **LIST_CONTINUE_5**

    列表继续 5.

## 列表编号

- **LIST_NUMBER**

    列表编号.

- **LIST_NUMBER_2**

    列表编号 2.

- **LIST_NUMBER_3**

    列表编号 3.

- **LIST_NUMBER_4**

    列表编号 4.

- **LIST_NUMBER_5**

    列表编号 5.

- **LIST_PARAGRAPH**

    列表段落.

## 宏

- **MACRO_TEXT**

    宏文本.

- **MESSAGE_HEADER**

    消息头.

- **NAV_PANE**

    文档地图.

- **NORMAL**

    常规.

- **NORMAL_INDENT**

    正常缩进.

- **NORMAL_OBJECT**

    正常（应用于对象）.

- **NORMAL_TABLE**

    正常（在表格中应用）.

- **NOTE_HEADING**

    注释标题.

- **PAGE_NUMBER**

    页码.

- **PLAIN_TEXT**

    纯文本.

- **QUOTE**

    引用.

- **SALUTATION**

    称呼.

- **SIGNATURE**

    签名.

- **STRONG**

    强调.

- **SUBTITLE**

    副标题.

- **SUBTLE_EMPHASIS**

    微强调.

- **SUBTLE_REFERENCE**

    微参考.

## 表格

- **TABLE_COLORFUL_GRID**

    彩色网格.

- **TABLE_COLORFUL_LIST**

    多彩列表.

- **TABLE_COLORFUL_SHADING**

    彩色底纹.

- **TABLE_DARK_LIST**

    黑色列表.

- **TABLE_LIGHT_GRID**

    光栅.

- **TABLE_LIGHT_GRID_ACCENT_1**

    浅色网格强调 1.

- **TABLE_LIGHT_LIST**

    浅色列表.

- **TABLE_LIGHT_LIST_ACCENT_1**

    浅色列表强调 1.

- **TABLE_LIGHT_SHADING**

    光影.

- **TABLE_LIGHT_SHADING_ACCENT_1**

    光影强调 1.

- **TABLE_MEDIUM_GRID_1**

    中网格 1.

- **TABLE_MEDIUM_GRID_2**

    中网格 2.

- **TABLE_MEDIUM_GRID_3**

    中网格 3.

- **TABLE_MEDIUM_LIST_1**

    介质列表 1.

- **TABLE_MEDIUM_LIST_1_ACCENT_1**

    介质列表 1 强调 1.

- **TABLE_MEDIUM_LIST_2**

    介质列表 2.

- **TABLE_MEDIUM_SHADING_1**

    中等阴影 1.

- **TABLE_MEDIUM_SHADING_1_ACCENT_1**

    中等阴影 1 强调 1.

- **TABLE_MEDIUM_SHADING_2**

    中等阴影 2.

- **TABLE_MEDIUM_SHADING_2_ACCENT_1**

    中等阴影 2 强调 1.

- **TABLE_OF_AUTHORITIES**

    权限表.

- **TABLE_OF_FIGURES**

    图表.

## 标题

- **TITLE**

    标题.

- **TOAHEADING**

    TOA 标题.

- **TOC_1**

    目录 1.

- **TOC_2**

    目录 2.

- **TOC_3**

    目录 3.

- **TOC_4**

    目录 4.

- **TOC_5**

    目录 5.

- **TOC_6**

    目录 6.

- **TOC_7**

    目录 7.

- **TOC_8**

    目录 8.

- **TOC_9**

    目录 9.
