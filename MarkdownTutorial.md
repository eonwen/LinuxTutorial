# Markdown 基本要素
这篇文件意在简要介绍 [GitHub Flavored Markdown 写作](https://guides.github.com/features/mastering-markdown/)。      

## 什么是 Markdown?  
`Markdown` 是一种文本格式。你可以用它来控制文档的显示。使用 markdown，你可以创建粗体的文字，斜体的文字，添加图片，并且创建列表 等等。基本上来讲，Markdown 就是普通的文字加上 `#` 或者 `*` 等符号。  

## 语法说明

### 标题
```markdown
# 这是 <h1> 一级标题
## 这是 <h2> 二级标题
### 这是 <h3> 三级标题
#### 这是 <h4> 四级标题
##### 这是 <h5> 五级标题
###### 这是 <h6> 六级标题
```

# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题

如果你想要给你的标题添加 `id` 或者 `class`，请在标题最后添加 `{#id .class1 .class2}`。例如：  
```markdown
# 这个标题拥有 1 个 id {#my_id}
# 这个标题有 2 个 classes {.class1 .class2}
```

# 这个标题拥有 1 个 id {#my_id}
# 这个标题有 2 个 classes {.class1 .class2}

> 这是一个 MPE 扩展的特性。  

### 强调
```markdown
*这会是 斜体 的文字*
_这会是 斜体 的文字_

**这会是 粗体 的文字**
__这会是 粗体 的文字__

_你也 **组合** 这些符号_

~~这个文字将会被横线删除~~
```

*这会是 斜体 的文字*
_这会是 斜体 的文字_

**这会是 粗体 的文字**
__这会是 粗体 的文字__

_你也 **组合** 这些符号_

~~这个文字将会被横线删除~~

### 列表
#### 无序列表
```markdown
* Item 1
* Item 2
  * Item 2a
  * Item 2b
```

* Item 1
* Item 2
  * Item 2a
  * Item 2b

#### 有序列表
```markdown
1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b
```

1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b

### 添加图片  
```markdown
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
```

### 链接  
```markdown
http://github.com - 自动生成！
[GitHub](http://github.com)
```

### 引用
```markdown
正如 Kanye West 所说：

> We're living the future so
> the present is our past.

```

正如 Kanye West 所说：

> We're living the future so
> the present is our past.

### 分割线  
```markdown
如下，三个或者更多的

---

连字符

***

星号

___

下划线
```

如下，三个或者更多的

---

连字符

***

星号

___

下划线

### 行内代码
```markdown  
我觉得你应该在这里使用
`<addr>` 才对。
```

我觉得你应该在这里使用
`<addr>` 才对。

### 代码块
你可以在你的代码上面和下面添加 <code>\`\`\`</code> 来表示代码块。

#### 语法高亮
你可以给你的代码块添加任何一种语言的语法高亮  

例如，给 ruby 代码添加语法高亮：

    ```ruby
    require 'redcarpet'
    markdown = Redcarpet.new("Hello World!")
    puts markdown.to_html
    ```

会得到下面的效果：

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

#### 代码块 class（MPE 扩展的特性）
你可以给你的代码块设置 `class`。

例如，添加 `class1 class2` 到一个 代码块：

    ```javascript {.class1 .class}
    function add(x, y) {
      return x + y
    }
    ```

##### 代码行数
如果你想要你的代码块显示代码行数，只要添加 `line-numbers` class 就可以了。

例如：

    ```javascript {.line-numbers}
    function add(x, y) {
      return x + y
    }
    ```

将会得到下面的显示效果：

```javascript {.line-numbers}
    function add(x, y) {
      return x + y
    }
```

##### 高亮代码行数

你可以通过添加 `highlight` 属性的方式来高亮代码行数：

````markdown
```javascript {highlight=10}
```

```javascript {highlight=10-20}
```

```javascript {highlight=[1-10,15,20-22]}
```
````

### 任务列表   
```markdown  
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
```

### 表格
```markdown  
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
```

## 扩展的语法
### 表格  

> 需要在插件设置中打开 `enableExtendedTableSyntax` 选项来使其工作。

![screen shot 2017-07-15 at 8 16 45 pm](https://user-images.githubusercontent.com/1908863/28243710-945e3004-699a-11e7-9a5f-d74f6c944c3b.png)

### Emoji & Font-Awesome

> 只适用于 `markdown-it parser` 而不适用于 `pandoc parser`。    
> 缺省下是启用的。你可以在插件设置里禁用此功能。  

```
:smile:
:fa-car:
```

### 上标
```markdown
30^th^
```

### 下标
```markdown
H~2~O
```

### 脚注
```markdown
Content [^1]

[^1]: Hi! This is a footnote
```

### 缩略  
```markdown  
*[HTML]: Hyper Text Markup Language
*[W3C]:  World Wide Web Consortium
The HTML specification
is maintained by the W3C.
```

### 标记  
```markdown
==marked==
```

### CriticMarkup  
CriticMarkup 缺省是禁用的，你可以通过插件设置来启动它。    
有关 CriticMarkup 的更多信息，请查看 [CriticMarkup 用户指南](http://criticmarkup.com/users-guide.php).    

这里有 5 种基本语法：

* 添加 `{++ ++}`
* 删除 `{-- --}`
* 替换 `{~~ ~> ~~}`
* 注释 `{>> <<}`
* 高亮 `{== ==}{>> <<}`

> CriticMarkup 仅可用于 markdown-it parser，不与 pandoc parser 兼容。  

## 参考
* [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
* [Daring Fireball: Markdown Basics](https://daringfireball.net/projects/markdown/basics)


# 图像

**Markdown Preview Enhanced** 内部支持 `flow charts`, `sequence diagrams`, `mermaid`, `PlantUML`, `WaveDrom`, `GraphViz`，`Vega & Vega-lite`，`Ditaa` 图像渲染。
你也可以通过使用 [Code Chunk](zh-cn/code-chunk.md) 来渲染 `TikZ`, `Python Matplotlib`, `Plotly` 等图像。

> Please note that some diagrams doesn't work well with file export like PDF, pandoc, etc.

## Flow Charts

这一特性基于 [flowchart.js](http://flowchart.js.org/)。
* `flow` 代码快中的内容将会被 [flowchart.js](http://flowchart.js.org/) 渲染。

```flow
st=>start: 法的概念争议
cond1=>condition: 是否与道德有关
op1=>operation: 实证主义法学
op2=>operation: 非实证主义法学
cond2=>condition: 首要要素
op3=>operation: 法社会学
op4=>operation: 法现实主义
sub1=>subroutine: My Subroutine 
cond=>condition: Yes or No?:>http://www.google.com io=>inputoutput: catch something... 
e=>end:>http://www.google.com 

st->cond1
cond1(yes)->op2
cond1(no)->op1->cond2(yes)->op3
cond1(no)->op1->cond2(yes)->op4

```

## Sequence Diagrams

这一特性基于 [js-sequence-diagrams](https://bramp.github.io/js-sequence-diagrams/)。
* `sequence` 代码快中的内容将会被 [js-sequence-diagrams](https://bramp.github.io/js-sequence-diagrams/) 渲染。
* 支持两个主题 `simple`（默认主题）和 `hand`。

![screenshot from 2017-11-25 21-47-41](https://user-images.githubusercontent.com/1908863/33236972-4f190f98-d22a-11e7-842f-d9c4a74d2118.png)


## Mermaid

Markdown Preview Enhanced 使用 [mermaid](https://github.com/knsv/mermaid) 来渲染流程图和时序图。
- `mermaid` 代码块中的内容将会渲染 [mermaid](https://github.com/knsv/mermaid) 图像。
- 查看 [mermaid 文档](http://knsv.github.io/mermaid/#flowcharts-basic-syntax) 了解更多如果创建图形。
![screen shot 2017-06-05 at 8 04 58 pm](https://cloud.githubusercontent.com/assets/1908863/26809423/42afb410-4a2a-11e7-8a18-57e7c67caa9f.png)

三个 mermaid 主题是支持的，并且你可以在 [插件设置](zh-cn/usages.md?id=package-settings) 中设置主题：
* `mermaid.css`
* `mermaid.dark.css`
* `mermaid.forest.css`
![screen shot 2017-06-05 at 8 47 00 pm](https://cloud.githubusercontent.com/assets/1908863/26810274/555562d0-4a30-11e7-91ca-98742d6afbd5.png)

你还可以通过 `Markdown Preview Enhanced: Open Mermaid Config` 命令打开 mermaid 配置文件。


## PlantUML

Markdown Preview Enhanced 使用 [PlantUML](http://plantuml.com/) 来创建各种图形。（**Java** 是需要先被安装好的）
- 你可以安装 [Graphviz](http://www.graphviz.org/)（非必需）来辅助生成各种各种图形。
- `puml` 或者 `plantuml` 代码块中的内容将会被 [PlantUML](http://plantuml.com/) 渲染。

![screen shot 2017-06-05 at 8 05 55 pm](https://cloud.githubusercontent.com/assets/1908863/26809436/65414084-4a2a-11e7-91ee-7b03b0496513.png)

如果代码中 `@start...` 没有被找到，那么 `@startuml ... @enduml` 将会被自动添加。

## WaveDrom

Markdown Preview Enhanced 使用 [WaveDrom](http://wavedrom.com/) 来渲染 digital timing diagram.
- `wavedrom` 代码块中的内容将会被 [WaveDrom](https://github.com/drom/wavedrom) 渲染。

![screen shot 2017-06-05 at 8 07 30 pm](https://cloud.githubusercontent.com/assets/1908863/26809462/9dc3eb96-4a2a-11e7-90e7-ad6bcb8dbdb1.png)

## GraphViz
Markdown Preview Enhanced 使用 [Viz.js](https://github.com/mdaines/viz.js) 来渲染 [dot 语言](https://tinyurl.com/kjoouup) 图形。
- `viz` 或者 `dot` 代码块中的内容将会被 [Viz.js](https://github.com/mdaines/viz.js) 渲染。
- 你可以通过 `{engine="..."}` 来选择不同的渲染引擎。 引擎 `circo`，`dot`，`neato`，`osage`，或者 `twopi` 是被支持的。默认下，使用 `dot` 引擎。

![screen shot 2018-03-18 at 3 18 17 pm](https://user-images.githubusercontent.com/1908863/37570596-a565306e-2abf-11e8-8904-d73306f675ec.png)

```viz{engine="dot"}
digraph G {
  法与道德->关系
  关系->分离
  关系->联结
  分离->法实证主义
  联结->非实证主义
  法实证主义->定义要素
  定义要素->社会实效
  定义要素->权威制定
  社会实效->法社会学
  社会实效->法现实主义
  权威制定->分析主义法学
  分析主义法学->不接受道德
  分析主义法学->接受道德
  不接受道德->排他性法律实证主义
  接受道德->包容型法律实证主义
  非实证主义->唯一制定要素
  唯一制定要素->传统自然法学
  非实证主义->三者结合
  三者结合->第三条道路

}
```

## Vega 和 Vega-lite
Markdown Preview Enhanced 支持 [vega](https://vega.github.io/vega/) 以及 [vega-lite](https://vega.github.io/vega-lite/) 的**静态**图像.
* `vega` 代码块中的内容将会被 [vega](https://vega.github.io/vega/) 渲染。
* `vega-lite` 代码块中的内容将会被  [vega-lite](https://vega.github.io/vega-lite/) 渲染。
* `JSON` 以及 `YAML` 的输入是支持的。

![screen shot 2017-07-28 at 7 59 58 am](https://user-images.githubusercontent.com/1908863/28718265-d023e1c2-736a-11e7-8678-a29704f3a23c.png)

你也可以 [@import](zh-cn/file-imports.md) 一个 `JSON` 或者 `YAML` 文件作为 `vega` 图像，例如：

```markdown
@import "your_vega_source.json" {as="vega"}
@import "your_vega_lite_source.json" {as="vega-lite"}
```

## Ditaa
Markdown Preview Enhanced 支持 [ditaa](https://github.com/stathissideris/ditaa)。

(**Java** 是需要先被安装好的)

`ditaa` 整合于 [code chunk](zh-cn/code-chunk.md), for example:
<pre>
  ```ditaa {cmd=true args=["-E"]}
  +--------+   +-------+    +-------+
  |        | --+ ditaa +--> |       |
  |  Text  |   +-------+    |diagram|
  |Document|   |!magic!|    |       |
  |     {d}|   |       |    |       |
  +---+----+   +-------+    +-------+
      :                         ^
      |       Lots of work      |
      +-------------------------+
  ```
</pre>

> <kbd>shift-enter</kbd> 来运行 code chunk。
> 设置 `{hide=true}` 来隐藏代码块。
> 设置 `{run_on_save=true}` 启动当文件保存时，渲染 ditaa 图像。

![screen shot 2017-07-28 at 8 11 15 am](https://user-images.githubusercontent.com/1908863/28718626-633fa18e-736c-11e7-8a4a-915858dafff6.png)

---

如果你只是想要显示代码块而不想画图，则只要在后面添加 `{code_block=true}` 即可：

    ```mermaid {code_block=true}
    // 你的 mermaid 代码
    ```

---

你可以为图像的容器添加属性。
例如：

    ```puml {align="center"}
    a->b
    ```

将会把 puml 的图像放在中间。

---

当你保存你的 markdown 文件到 [GFM Markdown](zh-cn/markdown.md) 时， 所有图像将会被保存为 png 文件到 `imageFolderPath` 文件夹。
你可以设置导出文件的文件名 `{filename="图片.png"}`。

例如：

    ```mermaid {filename="我的mermaid.png"}
    ...
    ```

# 导入外部文件

![doc-imports](https://cloud.githubusercontent.com/assets/1908863/22716507/f352a4b6-ed5b-11e6-9bac-88837f111de0.gif)

## 咋使呢？
仅仅

`@import "你的文件"`

就可以了，很简单对吧～ <code>d(\`･∀･)b</code>

`<!-- @import "your_file" -->` 的写法也是支持的。

## 刷新按钮
刷新按钮可以在你的预览右上角找到。
点击它将会清空文件缓存并且刷新预览。
这个功能将会十分有用如果你想要清除图片缓存 [#144](https://github.com/shd101wyy/markdown-preview-enhanced/issues/144) [#249](https://github.com/shd101wyy/markdown-preview-enhanced/issues/249)。

![screen shot 2017-02-07 at 5 48 52 pm](https://cloud.githubusercontent.com/assets/1908863/22716917/c7088ae0-ed5d-11e6-8db9-e1ab035a3a2b.png)

## 支持的文件类型
* `.jpeg(.jpg), .gif, .png, .apng, .svg, .bmp` 文件将会直接被当作 markdown 图片被引用。
* `.csv` 文件将会被转换成 markdown 表格。
* `.mermaid` 将会被 mermaid 渲染。
* `.dot` 文件将会被 viz.js (graphviz) 渲染。
* `.plantuml(.puml)` 文件将会被 PlantUML 渲染。
* `.html` 将会直接被引入。
* `.js` 将会被引用为 `<script src="你的 js 文件"></script>`。
* `.less` 和 `.css` 将会被引用为 style。目前 `less` 只支持本地文件。`.css` 文件将会被引用为 `<link rel="stylesheet" href="你的 css 文件">`。
* `.pdf` 文件将会被 `pdf2svg` 转换为 `svg` 然后被引用。
* `markdown` 将会被分析处理然后被引用。
* 其他所有的文件都将被视为代码块。

## 设置图片
```markdown
@import "test.png" {width="300px" height="200px" title="图片的标题" alt="我的 alt"}
```

## 引用在线文件
例如：
```markdown
@import "https://raw.githubusercontent.com/shd101wyy/markdown-preview-enhanced/master/LICENSE.md"
```

## 引用 PDF 文件
如果你要引用 PDF 文件，你需要事先安装好 [pdf2svg](zh-cn/extra.md)。
Markdown Preview Enhanced 支持引用本地或者在线的 PDF 文件。
但是，引用大的 PDF 文件是不推荐的。

例如：
```markdown
@import "test.pdf"
```

### PDF 设置
* **page_no**
显示第 `nth` 页。例如 `{page_no=1}` 将会只显示 PDF 文件的第 1 页。
* **page_begin**, **page_end**
包含的。例如 `{page_begin=2 page_end=4}` 将会显示第 2，3，4 页。

## 强制渲染为代码块
```markdown
@import "test.puml" {code_block=true class="line-numbers"}
@import "test.py" {class="line-numbers"}
```

## As（作为）代码块
```markdown
@import "test.json" {as="vega-lite"}
```

## 导入特定行数
```markdown
@import "test.md" {line_begin=2}
@import "test.md" {line_begin=2 line_end=10}
@import "test.md" {line_end=-4}
```

## 引用文件作为 Code Chunk
```markdown
@import "test.py" {cmd="python3"}
```

# Code Chunk
**未来可能会有变动**

**Markdown Preview Enhanced** 支持渲染代码的运行结果。

    ```bash {cmd=true}
    ls .
    ```

    ```javascript {cmd="node"}
    const date = Date.now()
    console.log(date.toString())
    ```

> ⚠️ **脚本运行默认是禁用的并且需要在 Atom 和 VSCode 的插件设置中开启来进行使用**
>
> 请小心使用这一特性，因为它很有可能造成安全问题！
> 当你的脚本运行设置是开启的，你的电脑很有可能被黑客攻击，如果有人使你运行了 Markdown 文档中的恶意代码。
>
> 设置名称： `enableScriptExecution`

## 命令 & 快捷键
* `Markdown Preview Enhanced: Run Code Chunk` 或者 <kbd>shift-enter</kbd>
运行你现在光标所在的一个 code chunk。
* `Markdown Preview Enhanced: Run All Code Chunks` 或者 <kbd>ctrl-shift-enter</kbd>
运行所有的 code chunks。

## 格式
你可以通过以下形式来设置 code chunk：<code>\`\`\`lang {cmd=your_cmd opt1=value1 opt2=value2 ...}</code>。

如果一个属性的值是 `true`，那么它可以被省略，（e.g. `{cmd hide}` 和 `{cmd=true hide=true}` 相同）。

**lang**
你想要代码所高亮的语言。
这个是要被放在最前面的。

## 基本设置
**cmd**
将要被运行的命令。
如果 `cmd` 没有被提供，那么 `lang` 将会被视作为命令。

例如：

		```python {cmd="/usr/local/bin/python3"}
		print("这个将会运行 python3 程序")
		```


**output**
`html`, `markdown`, `text`, `png`, `none`

设置你想要如何显示你的代码结果。
`html` 将会添加输出结果为 html。
`markdown` 将会添加输出结果为 markdown。（MathJax 以及 graphs 在这种情况下是不被支持的）
`text` 将会添加输出结果到 `pre` 块。
`png` 将会添加输出结果到 `base64` 图片。
`none` 将会隐藏输出结果。

例如：

    ```gnuplot {cmd=true output="html"}
    set terminal svg
    set title "Simple Plots" font ",20"
    set key left box
    set samples 50
    set style data points

    plot [-10:10] sin(x),atan(x),cos(atan(x))
    ```

![screen shot 2017-07-28 at 7 14 24 am](https://user-images.githubusercontent.com/1908863/28716734-66142a5e-7364-11e7-83dc-a66df61971dc.png)


**args**
需要被添加到命令的 args 。 例如：

    ```python {cmd=true args=["-v"]}
    print("Verbose will be printed first")
    ```

    ```erd {cmd=true args=["-i", "$input_file", "-f", "svg"] output="html"}
    # output svg format and append as html result.
    ```

**stdin**
如果 `stdin` 被设置为 true，那么代码将会被传递到 stdin 而不是作为文件。

**hide**
`hide` 将会隐藏代码块但是会显示运行结果，默认为 `false`。
例如：

    ```python {hide=true}
    print('you can see this output message, but not this code')
    ```

**continue**
如果设置 `continue: true`，那么这个 code chunk 将会继续运行上一个 code chunk 的内容。
如果设置`continue: id`，那么这个 code chunk 从拥有这个 id 的 code chunk 运行。
例如：

    ```python {cmd=true id="izdlk700"}
    x = 1
    ```

    ```python {cmd=true id="izdlkdim"}
    x = 2
    ```

    ```python {cmd=true continue="izdlk700" id="izdlkhso"}
    print(x) # will print 1
    ```

**class**
如果设置 `class="class1 class2"`，那么 `class1 class2` 将会被添加到 code chunk。
* `line-numbers` class 将会添加代码行数到 code chunk。

**element**
你想要添加的元素。
请查看下面的 **Plotly** 例子。

**run_on_save** `boolean`
当 markdown 文件被保存时，自动运行 code chunk。默认 `false`。

**modify_source** `boolean`
插入 code chunk 的运行结果直接到 markdown 文件。默认 `false`。

**id**
Code chunk 的 `id`。这个选项可以配合 `continue` 选项使用。

## 宏
* **input_file**
`input_file` 将会拷贝你的 code chunk 中的代码，然后在你的 markdown 文件的目录下生成一个临时文件，并且会在 code chunk 运行结束后被自动删除。
默认条件下，它被作为程序运行的最后一个参数。
但是，如果你想要改变 `input_file` 在你的 `args` 中的位置，你可以使用 `$input_file` 宏。例如：


    ```program {cmd=true args=["-i", "$input_file", "-o", "./output.png"]}
    ...your code here
    ```

## Matplotlib
如果设置 `matplotlib=true`，那么你的 python code chunk 将会在你的预览中绘制图像。
例如：

    ```python {cmd=true matplotlib=true}
    import matplotlib.pyplot as plt
    plt.plot([1,2,3, 4])
    plt.show() # show figure
    ```

![screen shot 2017-07-28 at 7 12 50 am](https://user-images.githubusercontent.com/1908863/28716704-4009d43a-7364-11e7-9e46-889f961e5afd.png)

## LaTeX
Markdown Preview Enhanced 也支持 `LaTeX` 编译。
在使用这个特性之前，你需要先安装好 [pdf2svg](zh-cn/extra.md?id=install-svg2pdf) 以及 [LaTeX engine](zh-cn/extra.md?id=install-latex-distribution)。
然后你就可以很简单的利用 code chunk 编写 LaTeX 了：


    ```latex {cmd=true}
    \documentclass{standalone}
    \begin{document}
       Hello world!
    \end{document}
    ```

![screen shot 2017-07-28 at 7 15 16 am](https://user-images.githubusercontent.com/1908863/28716762-8686d980-7364-11e7-9669-71138cb2e6e7.png)


### LaTeX 输出设置
**latex_zoom**
如果设置了 `latex_zoom=num`，那么输出结果将会被缩放 `num` 倍。

**latex_width**
输出结果的宽度。

**latex_height**
输出结果的高度。

**latex_engine**
就会被用来编译 `tex` 文件的 latex 引擎。默认下 `pdflatex` 是被使用的。你可以在 [插件设置](zh-cn/usages.md?id=package-settings) 中改变它的默认值。


### TikZ 例子
推荐使用 `standalone` 绘制 `tikz` 图形。

![screen shot 2017-07-14 at 11 27 56 am](https://user-images.githubusercontent.com/1908863/28221069-8113a5b0-6887-11e7-82fa-23dd68f2be82.png)

## Plotly
Markdown Preview Enhanced 支持你轻松的绘制 [Plotly](https://plot.ly/) 图形。
例如：
![screen shot 2017-10-20 at 10 41 25 am](https://user-images.githubusercontent.com/1908863/31829580-526a0c06-b583-11e7-82f2-09ea7a0b9672.png)

* 第一行中的 `@import "https://cdn.plot.ly/plotly-latest.min.js" ` 使用了 [文件引用](zh-cn/file-imports.md) 的特性来引用 `plotly-latest.min.js` 文件。但是，引用本地的 js 文件是推荐的，因为这样更快。
* 接着我们创建了 `javascript` code chunk.

## Demo
下面的例子展示了如何利用 [erd](https://github.com/BurntSushi/erd) 库绘制 ER diagram。

    ```erd {cmd=true output="html" args=["-i", "$input_file", "-f", "svg"]}

    [Person]
    *name
    height
    weight
    +birth_location_id

    [Location]
    *id
    city
    state
    country

    Person *--1 Location
    ```

`erd {cmd=true output="html" args=["-i", "$input_file", "-f", "svg"]}`
* `erd` 是我们将要用到的程序。 (*当然你得先安装好这个程序*)
* `output="html"` 意味着代码的输出结果将会被视作为 `html`。
* `args` 显示了我们将要用到的参数。

接着我们点击 `运行`按钮来运行我们的代码。

![erd](https://user-images.githubusercontent.com/1908863/28221395-bcd0bd76-6888-11e7-8c6e-925e228d02cc.gif)

## 展示
**bash**
![Screen Shot 2016-09-24 at 1.41.06 AM](http://i.imgur.com/v5Y7juh.png)

**gnuplot with svg output**
![Screen Shot 2016-09-24 at 1.44.14 AM](http://i.imgur.com/S93g7Tk.png)

## 局限
* 暂时不能在 `ebook` 工作。
* `pandoc document export` 中可能会有问题。

# 幻灯片制作  

![screen shot 2017-07-14 at 12 33 14 pm](https://user-images.githubusercontent.com/1908863/28223480-2c61461c-6891-11e7-9389-5adec0588c32.png)

Markdown Preview Enhanced 使用 [reveal.js](https://github.com/hakimel/reveal.js) 来渲染漂亮的幻灯片。  

[点击这里](https://rawgit.com/shd101wyy/markdown-preview-enhanced/master/docs/presentation-intro.html) 查看相关的介绍。  

![presentation](https://user-images.githubusercontent.com/1908863/28202176-caf103c4-6839-11e7-8776-942679f3698b.gif)


## Presentation Front-Matter
你可以通过 `front-matter` 来设置你的幻灯片。  
你需要将你的设置写在 `presentation` 部分下。  
例如：  
```markdown
---
presentation:
  width: 800
  height: 600
---

<!-- slide -->
在这里编写你的幻灯片。。。
```   
这个幻灯片将会拥有 `800x600` 的大小。  

### 设置    
```yaml
---
presentation:
  # presentation 主题
  # === 可选的主题 ===
  # "beige.css"
  # "black.css"
  # "blood.css"
  # "league.css"
  # "moon.css"
  # "night.css"
  # "serif.css"
  # "simple.css"
  # "sky.css"
  # "solarized.css"
  # "white.css"
  # "none.css"  
  theme: white.css

  # The "normal" size of the presentation, aspect ratio will be preserved
  # when the presentation is scaled to fit different resolutions. Can be
  # specified using percentage units.
  width: 960
  height: 700

  # Factor of the display size that should remain empty around the content
  margin: 0.1

  # Bounds for smallest/largest possible scale to apply to content
  minScale: 0.2
  maxScale: 1.5

  # Display controls in the bottom right corner
  controls: true

  # Display a presentation progress bar
  progress: true

  # Display the page number of the current slide
  slideNumber: false

  # Push each slide change to the browser history
  history: false

  # Enable keyboard shortcuts for navigation
  keyboard: true

  # Enable the slide overview mode
  overview: true

  # Vertical centering of slides
  center: true

  # Enables touch navigation on devices with touch input
  touch: true

  # Loop the presentation
  loop: false

  # Change the presentation direction to be RTL
  rtl: false

  # Randomizes the order of slides each time the presentation loads
  shuffle: false

  # Turns fragments on and off globally
  fragments: true

  # Flags if the presentation is running in an embedded mode,
  # i.e. contained within a limited portion of the screen
  embedded: false

  # Flags if we should show a help overlay when the questionmark
  # key is pressed
  help: true

  # Flags if speaker notes should be visible to all viewers
  showNotes: false

  # Number of milliseconds between automatically proceeding to the
  # next slide, disabled when set to 0, this value can be overwritten
  # by using a data-autoslide attribute on your slides
  autoSlide: 0

  # Stop auto-sliding after user input
  autoSlideStoppable: true

  # Enable slide navigation via mouse wheel
  mouseWheel: false

  # Hides the address bar on mobile devices
  hideAddressBar: true

  # Opens links in an iframe preview overlay
  previewLinks: false

  # Transition style
  transition: 'default' # none/fade/slide/convex/concave/zoom

  # Transition speed
  transitionSpeed: 'default' # default/fast/slow

  # Transition style for full page slide backgrounds
  backgroundTransition: 'default' # none/fade/slide/convex/concave/zoom

  # Number of slides away from the current that are visible
  viewDistance: 3

  # Parallax background image
  parallaxBackgroundImage: '' # e.g. "'https://s3.amazonaws.com/hakim-static/reveal-js/reveal-parallax-1.jpg'"

  # Parallax background size
  parallaxBackgroundSize: '' # CSS syntax, e.g. "2100px 900px"

  # Number of pixels to move the parallax background per slide
  # - Calculated automatically unless specified
  # - Set to 0 to disable movement along an axis
  parallaxBackgroundHorizontal: null
  parallaxBackgroundVertical: null

  # Parallax background image
  parallaxBackgroundImage: '' # e.g. "https://s3.amazonaws.com/hakim-static/reveal-js/reveal-parallax-1.jpg"

  # Parallax background size
  parallaxBackgroundSize: '' # CSS syntax, e.g. "2100px 900px" - currently only pixels are supported (don't use % or auto)

  # Number of pixels to move the parallax background per slide
  # - Calculated automatically unless specified
  # - Set to 0 to disable movement along an axis
  parallaxBackgroundHorizontal: 200
  parallaxBackgroundVertical: 50

  # Enable Speake Notes
  enableSpeakerNotes: false
---
```


## 自定义幻灯片样式  
你可以添加 `id` 以及 `class` 到一个特定的幻灯片：   
```markdown
<!-- slide id="my-id" class="my-class1 my-class2" -->
```

或者你也可以自定义第 `nth` 个幻灯片，编写你的 `less` 如下：

```less
.markdown-preview.markdown-preview {
  // 自定义 presentation 样式
  .reveal .slides {
    // 修改所有幻灯片
  }

  // 自定义 presentation 样式
  .slides > section:nth-child(1) {
    // 修改 `第 1 个幻灯片`
  }
}
```
# Pandoc
**Markdown Preview Enhanced** 支持类似于 `RStudio Markdown` 的 `pandoc 文档导出`特性。    
要使用这一特性，你需要安装好 [pandoc](http://pandoc.org/)。  
Pandoc 的安装说明可以参考 [这里](http://pandoc.org/installing.html)。    
你可以通过右键点击预览，然后在菜单中点击 `Pandoc` 使用 `pandoc document export`。

---

## Pandoc Parser
默认情况下， **Markdown Preview Enhanced** 使用 [markdown-it](https://github.com/markdown-it/markdown-it) 来转换 markdown。  
你也可以在插件设置中设置使用 `Pandoc Parser` 来转换 markdown。      

![Screen Shot 2017-03-07 at 10.05.25 PM](http://i.imgur.com/NdCJBgR.png)  

你还可以为单独的文件设置 pandoc 的参数通过编写 front-matter：  
```markdown
---
pandoc_args: ['--toc', '--toc-depth=2']
---
```

请注意，如果在你的 front-matter 中写有 `references` 或者 `bibliography`，那么 `--filter=pandoc-citeproc` 将会被自动添加 。  

**请注意**：这一特性依旧是实验性质的。请随意发表你的看法以及建议。  
**已知的问题 & 局限**:  
1. `ebook` 导出有问题。  
2. `Code Chunk` 有时候有问题。  

## Front-Matter   
`pandoc document export` 要求编写 `front-matter`。    
如果你想了解更多的关于如何编写 `front-matter` 的信息，请查看 [这里](https://jekyllrb.com/docs/frontmatter/)。

## 文档导出  

你不是必须使用我上面提到的 `Pandoc Parser` 才可以使用 Pandoc 导出文件。  

以下的文件类型是支持的，**更多的文件类型可能会在未来添加。**  
（一些例子引用于 [RStudio Markdown](http://rmarkdown.rstudio.com/formats.html)）   
点击以下的链接查看如何导出相应的文件类型。    

* [PDF](zh-cn/pandoc-pdf.md)  
* [Word](zh-cn/pandoc-word.md)
* [RTF](zh-cn/pandoc-rtf.md)
* [Beamer](zh-cn/pandoc-beamer.md)  


你还可以创建你自己的自定义文档：
* [custom](zh-cn/pandoc-custom.md)

## 保存时自动导出
添加 front-matter 如下：
```yaml
---
export_on_save:
  pandoc: true
---
```
这样每次当你保存你的 markdown 文件时，pandoc 将会自动运行。



## 文章  
* [Bibliographies and Citations](zh-cn/pandoc-bibliographies-and-citations.md)

## 注意
`mermaid，wavedrom` 将无法在 `pandoc document export` 中工作。        
[code chunk](code-chunk.md) 部分工作于 `pandoc document export`。      
