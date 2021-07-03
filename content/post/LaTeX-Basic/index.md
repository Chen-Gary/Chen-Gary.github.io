---
title: "LaTeX Basic"
subtitle: ""
summary: "Tutorial Link: https://liam.page/2014/09/08/latex-introduction/"
authors:
- admin
tags:
- LaTeX
categories:
date: 2021-07-03T12:13:12+08:00
featured: false
draft: false

image:
  placement: 2
  caption: ""
  focal_point: ""
  preview_only: false

projects: []
---


这篇文章是对[这份教程](https://liam.page/2014/09/08/latex-introduction/)的笔记，虽说是笔记，很多地方都直接复制了原文，强烈建议大家进入原教程查看。



（注：以下文档默认使用XeLaTeX进行编译）

**控制序列**：`\`开头，e.g. `\documentclass`。以第一个**空格或非字母** 的字符结束

**注释**：`%`

```latex
\documentclass{article}
% 这里是导言区
\begin{document}
Hello, world!
\end{document}
```



控制序列`begin`和`end`总是成对出现。这两个控制序列以及他们中间的内容被称为「环境」，它们之后的第一个必要参数总是**一致的**，被称为环境名。

只有在 `document` 环境中的内容，才会被正常输出到文档中去或是作为控制序列对文档产生影响。

从 `\documentclass{article}` 开始到 `\begin{document}` 之前的部分被称为导言区。在导言区出现的控制序列，往往会影响整篇文档的格式。



**宏包**：一系列控制序列的合集。`\usepackage{}` 可以用来调用宏包



## 中英文混排

```latex
\documentclass[UTF8]{ctexart}
\begin{document}
你好，world!
\end{document}
```

## 组织你的文章

### 作者、标题、日期

```latex
\documentclass[UTF8]{ctexart}
\title{你好，world!}
\author{Liam}
\date{\today}
\begin{document}
\maketitle
你好，world!
\end{document}
```

### 章节和段落

```latex
\documentclass[UTF8]{ctexart}
\title{你好，world!}
\author{Liam}
\date{\today}
\begin{document}
\maketitle
\section{你好中国}
中国在East Asia.
\subsection{Hello Beijing}
北京是capital of China.
\subsubsection{Hello Dongcheng District}
\paragraph{Tian'anmen Square}
is in the center of Beijing
\subparagraph{Chairman Mao}
is in the center of 天安门广场。
\subsection{Hello 山东}
\paragraph{山东大学} is one of the best university in 山东。
\end{document}
```

在文档类 `article`/`ctexart` 中，定义了五个控制序列来调整行文组织结构。他们分别是

- `\section{·}`
- `\subsection{·}`
- `\subsubsection{·}`
- `\paragraph{·}`
- `\subparagraph{·}`

### 插入目录

在上一节的文档中，找到 `\maketitle`，在它的下面插入控制序列 `\tableofcontents`，保存并用 XeLaTeX 编译**两次**。



## 插入数学公式

在导言区加载 `amsmath` 宏包

```latex
\usepackage{amsmath}
```

### 数学模式

LaTeX 的数学模式有两种：行内模式 (inline) 和行间模式 (display)。

在行文中，使用 `$ ... $` 可以插入行内公式，使用 `\[ ... \]` 可以插入行间公式，如果需要对行间公式进行编号，则可以使用 `equation` 环境：

```latex
\begin{equation}
...
\end{equation}
```

示例：

```latex
\documentclass{article}
\usepackage{amsmath}
\begin{document}
Einstein 's $E=mc^2$.

\[ E=mc^2. \]

\begin{equation}
E=mc^2.
\end{equation}
\end{document}
```

行内公式和行间公式对标点的要求是不同的：行内公式的标点，应该放在数学模式的限定符之外，而行间公式则应该放在数学模式限定符之内。

* 上标：`^` （注意花括号 `{}`的运用）
* 下标： `_`
* 根式： `\sqrt{·}` 
* 分式： `\frac{·}{·}` （第一个参数为分子，第二个为分母）

在行间公式和行内公式中，分式的输出效果是有差异的。如果要强制行内模式的分式显示为行间模式的大小，可以使用 `\dfrac`, 反之可以使用 `\tfrac`

#### 运算符

```latex
\[ \pm\; \times \; \div\; \cdot\; \cap\; \cup\;
\geq\; \leq\; \neq\; \approx \; \equiv \]
```

连加、连乘、极限、积分等大型运算符分别用 `\sum`, `\prod`, `\lim`, `\int` 生成。他们的上下标在行内公式中被压缩，以适应行高。我们可以用 `\limits` 和 `\nolimits` 来强制显式地指定是否压缩这些上下标。

```latex
$ \sum_{i=1}^n i\quad \prod_{i=1}^n $
$ \sum\limits _{i=1}^n i\quad \prod\limits _{i=1}^n $
\[ \lim_{x\to0}x^2 \quad \int_a^b x^2 dx \]
\[ \lim\nolimits _{x\to0}x^2\quad \int\nolimits_a^b x^2 dx \]
```

多重积分可以使用 `\iint`, `\iiint`, `\iiiint`, `\idotsint` 等命令输入。

```latex
\[ \iint\quad \iiint\quad \iiiint\quad \idotsint \]
```

#### 定界符（括号等）

各种括号用 `()`, `[]`, `\{\}`, `\langle\rangle` 等命令表示；注意花括号通常用来输入命令和环境的参数，所以在数学公式中它们前面要加 `\`。因为 LaTeX 中 `|` 和 `\|` 的应用过于随意，amsmath 宏包推荐用 `\lvert\rvert` 和 `\lVert\rVert` 取而代之。

为了调整这些定界符的大小，amsmath 宏包推荐使用 `\big`, `\Big`, `\bigg`, `\Bigg` 等一系列命令放在上述括号前面调整大小。

```latex
\[ \Biggl(\biggl(\Bigl(\bigl((x)\bigr)\Bigr)\biggr)\Biggr) \]
\[ \Biggl[\biggl[\Bigl[\bigl[[x]\bigr]\Bigr]\biggr]\Biggr] \]
\[ \Biggl \{\biggl \{\Bigl \{\bigl \{\{x\}\bigr \}\Bigr \}\biggr \}\Biggr\} \]
\[ \Biggl\langle\biggl\langle\Bigl\langle\bigl\langle\langle x
\rangle\bigr\rangle\Bigr\rangle\biggr\rangle\Biggr\rangle \]
\[ \Biggl\lvert\biggl\lvert\Bigl\lvert\bigl\lvert\lvert x
\rvert\bigr\rvert\Bigr\rvert\biggr\rvert\Biggr\rvert \]
\[ \Biggl\lVert\biggl\lVert\Bigl\lVert\bigl\lVert\lVert x
\rVert\bigr\rVert\Bigr\rVert\biggr\rVert\Biggr\rVert \]
```

#### 省略号

省略号用 `\dots`, `\cdots`, `\vdots`, `\ddots` 等命令表示。`\dots` 和 `\cdots` 的纵向位置不同，前者一般用于有下标的序列。

```latex
\[ x_1,x_2,\dots ,x_n\quad 1,2,\cdots ,n\quad
\vdots\quad \ddots \]
```

#### 矩阵

`amsmath` 的 `pmatrix`, `bmatrix`, `Bmatrix`, `vmatrix`, `Vmatrix` 等环境可以在矩阵两边加上各种分隔符。

```latex
\[ \begin{pmatrix} a&b\\c&d \end{pmatrix} \quad
\begin{bmatrix} a&b\\c&d \end{bmatrix} \quad
\begin{Bmatrix} a&b\\c&d \end{Bmatrix} \quad
\begin{vmatrix} a&b\\c&d \end{vmatrix} \quad
\begin{Vmatrix} a&b\\c&d \end{Vmatrix} \]
```

#### 多行公式

##### 长公式

###### 不对齐

无须对齐的长公式可以使用 `multline` 环境。

```latex
\begin{multline}
x = a+b+c+{} \\
d+e+f+g
\end{multline}
```

如果不需要编号，可以使用 `multline*` 环境代替。

###### 对齐

需要对齐的公式，可以使用 `aligned` *次环境*来实现，它必须包含在数学环境之内。

```latex
\[\begin{aligned}
x ={}& a+b+c+{} \\
&d+e+f+g
\end{aligned}\]
```

##### 公式组

无需对齐的公式组可以使用 `gather` 环境，需要对齐的公式组可以使用 `align` 环境。他们都带有编号，如果不需要编号可以使用带星花的版本。

##### 分段函数

分段函数可以用`cases`次环境来实现，它必须包含在数学环境之内。

```latex
\[ y= \begin{cases}
-x,\quad x\leq 0 \\
x,\quad x>0
\end{cases} \]
```

辅助工具：https://www.latexlive.com/

## 插入图片和表格

### 图片

在 LaTeX 中插入图片，利用 `graphicx` 宏包提供的 `\includegraphics` 命令。

```latex
\documentclass{article}
\usepackage{graphicx}
\begin{document}
\includegraphics{a.jpg}
\end{document}
```

用 `\includegraphics` 控制序列的可选参数来控制图片输出效果：

```latex
\includegraphics[width = .8\textwidth]{a.jpg}
```

图片的宽度会被缩放至页面宽度的百分之八十，图片的总高度会按比例缩放。

### 表格

`tabular` 环境提供了最简单的表格功能。它用 `\hline` 命令表示横线，在列格式中用 `|` 表示竖线；用 `&` 来分列，用 `\\` 来换行；每列可以采用居左、居中、居右等横向对齐方式，分别用 `l`、`c`、`r` 来表示。

```latex
\begin{tabular}{|l|c|r|}
 \hline
操作系统& 发行版& 编辑器\\
 \hline
Windows & MikTeX & TexMakerX \\
 \hline
Unix/Linux & teTeX & Kile \\
 \hline
Mac OS & MacTeX & TeXShop \\
 \hline
通用& TeX Live & TeXworks \\
 \hline
\end{tabular}
```

### 浮动体

见原文。。。



## 版面设置

### 页边距

设置页边距，推荐使用 `geometry` 宏包。

比如我希望，将纸张的长度设置为 20cm、宽度设置为 15cm、左边距 1cm、右边距 2cm、上边距 3cm、下边距 4cm，可以在导言区加上这样几行：

```latex
\usepackage{geometry}
\geometry{papersize={20cm,15cm}}
\geometry{left=1cm,right=2cm,top=3cm,bottom=4cm}
```

### 页眉页脚

设置页眉页脚，推荐使用 `fancyhdr` 宏包。

比如我希望，在页眉左边写上我的名字，中间写上今天的日期，右边写上我的电话；页脚的正中写上页码；页眉和正文之间有一道宽为 0.4pt 的横线分割，可以在导言区加上如下几行：

```latex
\usepackage{fancyhdr}
\pagestyle{fancy}
\lhead{\author}
\chead{\date}
\rhead{152xxxxxxxx}
\lfoot{}
\cfoot{\thepage}
\rfoot{}
\renewcommand{\headrulewidth}{0.4pt}
\renewcommand{\headwidth}{\textwidth}
\renewcommand{\footrulewidth}{0pt}
```

### 首行缩进

CTeX 宏集已经处理好了首行缩进的问题（自然段前空两格汉字宽度）。因此，使用 CTeX 宏集进行中西文混合排版时，我们不需要关注首行缩进的问题。

### 行间距

我们可以通过 `setspace` 宏包提供的命令来调整行间距。比如在导言区添加如下内容，可以将行距设置为**字号的 1.5 倍**：

```latex
\usepackage{setspace}
\onehalfspacing
```

### 段间距

我们可以通过修改长度 `\parskip` 的值来调整段间距。例如在导言区添加以下内容

```latex
\addtolength{\parskip}{.4em}
```

则可以在原有的基础上，增加段间距 0.4em。如果需要减小段间距，只需将该数值改为负值即可。
