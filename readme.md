华东师范大学博士（硕士）论文模板
===
LaTeX Template for Doctor (Master) Thesis of ECNU
---

本Latex模版从[Jarvis](https://github.com/Jarvis-K)处获取，原创始祖作者不详，本文使用Texifier（原Texpad）实现本地编译，已跑通博士论文毕业流程。

以博士学位论文为例，预答辩之后的论文有4个版本。



**评阅版**、**盲审版**（学校代码\_学号\_LW）、**查重版**（学生姓名\_学号\_院系加学位类别），其中**盲审版**和**查重版**内容一致，仅文件名需要按照规范命名。



答辩完成后，纸质**A版**、纸质+电子**B版**、摘要前内容的顺序请参考每年[研究生院相关文件](https://yjsy.ecnu.edu.cn/8a/bf/c42079a625343/page.htm)中的《归档论文涉及签名页》，本项目压缩包仅代表2024-2025学年第一学期的规范情况。

### 修改内容

对参考文献在目录中的页码错误问题做了修改。

对算法标题英文“Algorithm”，重命名为“算法”。

### 其他建议

参考文献使用bib文件，建议所有论文的cite-bibtex从同一源头下载，注意inproceedings和article的参数是不完全共用的。

\ref和\eqref的区别使用。

### 毕业论文目录结构
+ abstract					-(中英文摘要目录)
	+ abstract.tex			-(中文摘要)
	+ abstract-en.tex		-(英文摘要)
+ achievements				-(科研成果目录)
	+ achievements.tex		-(科研成果)
+ acknowledgement			-(致谢目录)
        + acknowledgement-tmlc.tex	-(查重版致谢，通常仅需保留标题)
	+ acknowledgement.tex	-(致谢)
+ chapters					-(章节目录)
	+ fig-0					-(校徽,校名图片目录)
	+ fig					-(图片目录，可任意增加多个文件夹)
	+ Introduction.tex		-(章节一)
	+ Relatedwork.tex		-(章节二)
	+ chapter-3.tex			-(章节三)
	+ chapter-4.tex			-(章节四)
	+ chapter-5.tex			-(章节五)
	+ chapter-6.tex			-(章节六)
	+ Discussion.tex		-(章节七)
+ format					-(格式目录)
	+ format.tex			-(引用,定义)
	+ graphic.tex			-(图表格式)
+ preface					-(序言目录)
	+ copyright.tex			-(原创性声明)
	+ inner-cover.tex		-(中文封面)
	+ inner-cover-en.tex	-(英文封面)
	+ member-list.tex		-(答辩成员名单)
+ references				-(参考文献引用目录)
	+ paper.bib				-(manual格式参考文献)
	+ paper-manual.bib      -(auto格式参考文献)
	+ GBT7714-2005.bst		-(参考文献格式)
	+ GBT7714-2005NLang.bst	-(参考文献格式)
+ main.tex					-(latex入口文件)
+ readme.md                 -(本说明文件)

### 毕业论文参数配置
以下的配置均在`main.tex`的前三行中完成。由于各年级、各院系的标准不同，同时专硕、学硕、博士间也有很大差异，因此，请务必仔细核对其中的每一项是否按照标准配置。如有必要，请修改`main.tex`中的代码以保证正确显示。

> 提示1：请提前咨询是否可以使用latex进行毕业论文的编写，部分学位在查重时仅支持word格式！
> 提示2：务必注意除default的各选项的拼写！任何拼写错误均会导致其**自动**转化为default参数，从而导致指定模式失效！

####  draftfigure
`\def \draftfigure {off} % on,off`

该参数用于描述是否开启草稿模式。在开启模式下，所有图片均以框线的形式展现，不显示具体图片，从而降低预览时间。

> 已知的问题：（1）在草稿模式下部分溢出右边界的字符会再多显示一个黑色的矩形框，关闭该模式即可消除。（2）由于还是需要读取整张图片的数据以获取其长和宽，因此实际上只是节约了图片在pdf模式下的渲染时间（即预览速度），而不是编译时间。

该参数接受两种输入：

- `on`：开启草稿模式，仅显示外框。其代码为：`\def \draftfigure {on} `。
- `off(default)`：关闭草稿模式，显示完整图片。其代码为：`\def \draftfigure {off} `。

#### docstyle
`\def \docstyle {normal} % normal,tmlc,anonymous`

该参数用于返回指定版本的论文，其接受三种输入：

- `tmlc`：该参数返回查重版本的论文，其开启了查重模式，并关闭盲审模式。
- `anonymous`：该参数返回盲审版本的论文，其开启了盲审模式。
- `normal(default)`：所有不属于上述模式的参数（不局限于normal）均会进入该模式，返回终稿版本的论文。

#### refstyle
`\def \refstyle {manual} % auto,manual`

该模板支持两种文献导入方式。仅在auto情况下采用bst自动模式录入文献，其余情况（不局限于manual）均使用用户自定义模式。

> 已知的问题：在overleaf中，该模式的切换不会消除切换前的warning。尽管无需处理，但是如果需要清除xxx is not found in database的warnings，请先点击“日志和生成的文件”中的“清除缓存文件”，再重新编译即可。

该参数接受两种输入：

- `auto`：指bst自动模式，其文献需要在`paper.bib`中修改。在输入后，由latex排版相关格式，由于部分文献可能缺少一定字段或格式不规范，可能导致实际输出与要求有细微差异，可自行检查并调整bst代码或bib的对应key。文献格式为：`@type{ref, key= {value}}`。
- `manual(default)`：指bib手动模式，其文献需要在`paper-manual.bib`中修改。在输入后，该模式不经过latex自动排版，由作者自行编辑所有参考文献格式。可通过第三方文献软件预览参考文献格式是否符合学校标准。在确保格式正确后，再复制到文章中。文献格式为\bibitem{ref}{按学校要求输入正确格式}。