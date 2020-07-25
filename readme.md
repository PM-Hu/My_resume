# 简历，Resume

### 写在前面

一年一度的毕业季快来了，求职自然避免不了个人简历的投递。刚好前段时间学了学 Latex，想着用 Latex 写份简历，动手后发现这个不是有点难度，自己起手的念头也就打消了。

不甘心又上网搜索，果然大佬无处不在。一番选择后，fork，download 一气呵成，而后粗粗将大佬的 `.tex` 运行，成功迈出一小步。然后开始了我的魔改。

运行版本 TeX Live 2020，如需安装，这里有一个腾讯云的源，[点击](https://mirrors.cloud.tencent.com/CTAN/systems/texlive/Images/texlive2020.iso)。

### 模板

LaTeX 简历模板来自于 [billryan](https://github.com/billryan/resume/) 的 resume，非常好用。

另外，好像现在都是以**电子简历**为主流了，适当添加点配色应该有眼前一亮的效果。

### 改动

简历整体的布局没有改动，主要是细节处的变化，如字体，背景等。整理如下：

- 更改了**标题样式**
- 添加了一种字体，姓名的呈现更加**个性化**
- 个人联系方式进行了**本地化**
- 支持 **FontAwesome 5**
- 添加了**校徽（滑稽）背景**，或许更有辨识度

### 输出
请用 XeLaTeX 编译：

![resume](D:\研究生\20寒假\typro\图例\resume.png)

### 字体

添加了一个字体（因为，总感觉【**姓名**】那个地方的字体怪怪的）：

- 方正字迹-张颢硬笔楷书，来自 [http://zitixiazai.taofont.com/]

   ![方正字迹-张颢硬笔楷书](https://github.com/pro4Hu/My_resume/blob/master/%E6%96%B9%E6%AD%A3%E5%AD%97%E8%BF%B9-%E5%BC%A0%E9%A2%A2%E7%A1%AC%E7%AC%94%E6%A5%B7%E4%B9%A6.jpg)

如果你不满意这个字体，想要**添加自己的字体**，打开`ressume-zh_CN.tex`文件，选中命令`\fangzheng 你的名字}`，将`\fangzheng`改为**你想要的字体名称**，如果删除后不添加字体名称，会使用默认字体：**黑体**。

**你想要的字体**可以来源于：

- **系统默认**
- **自己添加**

> 由于调用了`zh_CN-Adobefonts_external`宏包，下面的中文字体，可以在全文中**直接使用**：
>
> - 宋体，`\songti`
> - 黑体，`\heiti`
> - 楷书，`\kaishu`
> - 仿宋，`\fangsong`
> - 方正，`\fangzheng`
>
> 想要自己添加喜欢的字体怎么办？以方正字体为例：
>
> 1. 将下载的字体文件，`fangzheng.ttf`，放到文件夹`..\fonts\zh_CN-Adobe`下
> 2. 打开`zh_CN-adobefonts_external.sty`
> 3. 添加命令，写入字体：`\setCJKfamilyfont{fangzheng}{fangzheng.ttf}`
> 4. 命名字体为`fangzheng`：`\newcommand*{\fangzheng}{\CJKfamily{fangzheng}} % 方正`
> 5. 保存，关闭，就可以在`ressume-zh_CN.tex`中使用方正字体了

### FontAwesome 5

图标字体 [FontAwesome 5](https://fontawesome.com/icons?from=io) 基于旧版本添加了一些新图标，如 Researchgate 等

还可以查阅文件 `fontawesome5.pdf`，`ctrl+F` 搜索图标名称，获得使用命令。

### 校徽背景

将你的背景图片放到主目录下，在`ressume-zh_CN.tex`中换掉文件名即可。

### License

[The MIT License (MIT)](http://opensource.org/licenses/MIT)

Copyrighted fonts are not subjected to this License.

### 最后 --- 个人的一点了解

#### 1

Latex 下**文档类 **(document class) 文件的扩展名是 `.cls`，**宏包** (package) 的扩展名是 `.sty`

个人理解：`.cls` 是某一类型的文档，如简历，文章，报告等的模板，基础格式都已经设置好了，每次排版几乎只使用一次，使用方式：`\documentclass{}`；`.sty` 是用来控制某一特定格式，用来控制如字号，字体，标题等，每次排版可多次使用，使用方式：`\usepackage{}`。

> 例如，中文环境下常用的 [CTeX](http://mirrors.ibiblio.org/CTAN/language/chinese/ctex/ctex.pdf) 宏集的主要功能由这两类文件构成
>
> 具体也可参考  [What are .cls and .sty files?How are they different?](https://tug.org/pracjourn/2005-3/asknelly/nelly-sty-&-cls.pdf)

#### 2 

TeX - LaTeX - pdfTeX - pdfLaTeX  - XeTeX - XeLaTeX 

刚开始接触的时候，我被这几个名词整的一愣一愣的，然后我看到了这篇文章 [一份其实很短的 LaTeX 入门文档](https://liam.page/2014/09/08/latex-introduction/#TeX-%E5%AE%B6%E6%97%8F)，仔细捋了捋。

**TeX 是一个排版引擎**，这个引擎所能直接识别的控制命令也叫 TeX 标记语言，后来 Donald Ervin Knuth 教授为了方便用户，基于 TeX 定义了一种宏包/格式 plain TeX（一个宏代码集，封装了 TeX 排版命令，简化排版操作，但最终还得解释成 TeX 命令，再用 TeX 引擎运行），用着用着， **plain TeX 就成了 TeX 的同义词**。

但是 plain TeX 依然十分晦涩，L. Lamport 教授开发了 LaTeX，基于 plain TeX 格式（套中套，>.<）。**因为一般人不会特地去掌握排版细节，上手 TeX 也就十分困难，LaTeX 封装了这些排版操作，只需要用易懂的 LaTeX 命令就能实现晦涩难懂的排版操作，降低了上手难度**。但是 LaTeX 还是基于 TeX 命令的，LaTeX 命令最终也要解释成 TeX 命令。

**pdfTeX 就是补充后的 TeX 引擎**，不同于 TeX 只能输出 `.dvi` 排版文件，pdfTeX 引擎可以直接输出 `.pdf` 文件。

但是 pdfTeX 和 TeX 引擎**不支持 Unicode 字符**，对于非 ASCII 字符不支持，因此 **XeTeX** 出现了，中文用户也可以直接排版中文。（但是中文排版和英文排版有区别，因此还得借助其他宏包）

pdfLaTeX 和 XeLaTeX 就是基于pdfTeX 和 XeTeX 这两个引擎，使用 LaTeX 格式的命令来实现排版操作的编译方式。

