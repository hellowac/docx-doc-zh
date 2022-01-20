# 安装

> **注意:** `python docx`版本`0.3.0`和更高版本与以前的版本不兼容。

**python-docx** 托管在`PyPI`上，所以安装相对简单，并且取决于您安装了什么安装实用程序。

**python-docx** 可与 `pip` 如果你有空的话：

```bash
pip install python-docx
```

**python-docx** 也可以使用 `easy_install` ，尽管不鼓励这样做：

```bash
easy_install python-docx
```

如果既不使用 `pip` 也不使用 `easy_install` 它可以通过从`PyPI`下载发行版、解包`tarball`并运行来手动安装 `setup.py` ：

```bash
tar xvzf python-docx-{version}.tar.gz
cd python-docx-{version}
python setup.py install
```

**python-docx** 取决于 lxml 包裹。两者兼而有之 pip 和 easy_install 将负责满足这些依赖项，但如果您使用最后一种方法，则需要自己安装这些依赖项。

## 依赖关系

* `Python2.6`、`2.7`、`3.3`或`3.4`
* `lxml>=2.3.2`
