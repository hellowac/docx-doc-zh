# CoreProperties对象

[Document]: ../api/document.md
[CoreProperties]: ../api/document_core_properties.md
[str]: https://docs.python.org/3/library/stdtypes.html#str
[datetime.datetime]: https://docs.python.org/3/library/datetime.html#datetime.datetime
[int]: https://docs.python.org/3/library/functions.html#int
[core_properties]: ../api/document.md#core_properties

每个 [Document] 对象通过其 [core_properties] 属性提供对其 [CoreProperties] 对象的访问。 [CoreProperties] 对象提供对文档的所谓核心属性的读/写访问。 核心属性是作者、类别、评论、内容状态、创建、标识符、关键字、语言、最后修改人、最后打印、修改、修订、主题、标题和版本。

每个属性都是 [str]、[datetime.datetime] 或 [int] 三种类型之一。 字符串属性的长度限制为 `255` 个字符，如果未设置，则返回空字符串 `('')`。 日期属性作为没有时区的 [datetime.datetime] 对象分配和返回，即 `UTC`。 任何时区转换都是客户的责任。 如果未设置，则日期属性返回 `None`。

python-docx 不会自动设置任何文档核心属性，只会将核心属性部分添加到没有核心属性的演示文稿中（非常罕见）。 如果 python-docx 添加核心属性部分，它包含标题、最后修改人、修订和修改属性的默认值。 如果需要该行为，客户端代码应更新诸如修订和 最后修改人 之类的属性。

**class docx.opc.coreprops.CoreProperties**

- **author**

    string - 主要负责制作资源内容的实体。

- **category**

    string - 此包内容的分类。 示例值可能包括：简历、信函、财务预测、提案或技术演示。(Resume, Letter, Financial Forecast, Proposal, Technical Presentation.)

- **comments**

    string - 资源内容的说明。

- **content_status**

    string - 文档的完成状态，例如 '草案'(‘draft’)

- **created**

    datetime - 文档的初始创建时间

- **identifier**

    string - 在给定上下文中对资源的明确引用，例如 ISBN。

- **keywords**

    string - 可能用作本文档搜索词的描述性词或短语

- **language**

    string - 编写文档的语言

- **last_modified_by**

    string - 上次修改文档的人的姓名或其他标识符（例如电子邮件地址）

- **last_printed**

    datetime - 上次打印文档的时间

- **modified**

    datetime - 文档最后一次修改的时间

- **revision**

    int - 此修订的编号，每次保存文档时按 Word 递增。但是，注意python-docx在保存文档时不会自动增加修订号。

- **subject**

    string - 资源内容的主题。

- **title**

    string - 给资源的名称。

- **version**

    string - 自由格式的字符串
