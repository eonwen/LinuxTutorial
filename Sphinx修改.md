1. 修改 `site-packages\sphinx_py3doc_enhanced_theme\themes\sphinx_py3doc_enhanced_theme\staticpydoctheme.css` 文件， 添加：

```
div.body {
    padding: 0 0 0 1.2em;
    background-color: #f0fff0;
}
body {
    background-color: white;
    margin-left: 1em;
    margin-right: 1em;
    background-color: #fffaf0;
}
blockquote {
    margin-inline-start: 0px;
    margin-inline-end: 40px;
}
ul {
    padding-inline-start: 20px;
}
```

2. 修改 `conf.py`

```
html_theme = 'sphinx_py3doc_enhanced_theme'
import sphinx_py3doc_enhanced_theme
html_theme_path = [sphinx_py3doc_enhanced_theme.get_html_theme_path()]

# 修改一部分默认配置，以使生成的文档更好用
html_copy_source = False
html_show_sourcelink = False
html_show_copyright = False
html_show_sphinx = False
html_use_modindex = False
keep_warnings = False

# HTML Search Options
import os
html_search_options = {
    'dict': os.path.join(os.path.abspath('.'), 'jiebaDict.txt'),
}
```

test