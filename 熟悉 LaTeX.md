# 熟悉 LaTeX

[TOC]

## "Happy TEXing" 排版

安装好所有的 LaTeX 运行环境后即可运行一个简单的例子。

```latex
\documentclass{article}

\begin{document}
	This is my first document
	
	Hello, \TeX ing!
\end{document}
```

编译结果为：

![](https://ooo.0o0.ooo/2017/06/25/594f6d6a4ddb1.png)

`\documentclass{artical}` 声明文档类型是一篇文章

`\begin{document}` 和 `\end{document}` 标志出正文的范围

`\TeX` 表示 TEX 符号

默认情况下，LaTeX 不能显示中文，要想显示中文必须先要导入相应的 LaTeX 宏包。常用的中文宏包为 CTEX。

```latex
\documentclass[UTF8]{ctexart}
\begin{document}
	\section{文字}
	文字
	\section{数学}
	\[
		a^2 + b^2 = c^2
	\]
\end{document}
```

编译完成后的显示结果为：

![](https://ooo.0o0.ooo/2017/06/25/594f6ede8baf8.png)

相比于上一段代码，这一段代码的 `\documentclass{}` 换成了 `ctexart` 使中文可以正确的显示。

两个 `section` 命令各生成了一节的标题。

数学公式由两个 `\[` 包裹。

由这两个简单的例子可以看出，LaTeX 的命令主要以反斜杠 `\` 开头，后接一个英文单词，有的可以带参数。 

## 从一个例子说起

### 确定目标

假设要写一篇有关勾股定理的短文，结构上包含 **标题**、**摘要**、**目录**、**正文** 及 **参考文献**。内容包括 **文字**、**公式**、**图形**、**表格** 等。

### 提纲

从提纲开始写，先写出文档的骨架，再填入内容。

例子的提纲：

```latex
\documentclass[UTF8]{ctexart}

\title{杂谈勾股定理}
\author{Suarez Lin}
\date{\today}

\bibliographystyle{plain}

\begin{document}
	\maketitle
	\tableofcontents
	\section{勾股定理在古代}
	\section{勾股定理的近代形式}
	\bibliography{math}
\end{document}
```

编译结果：

![](https://ooo.0o0.ooo/2017/06/25/594f71c2a3453.png)



* 第一行声明文档类型，为了显示中文使用 `ctexart` 。

* 第三行到第五行声明了文章的标题、作者与写作时间，`\today` 表示时间为今天的日期，这些信息需通过 `\maketitle` 来排版。

* 第七行的 `\bibliographystyle` 声明参考文献格式。

  以上部分即在 `begin{document}` 之前的部分称为导言区，通常用于对文档的性质做一些设置。

* 第十行的 `\maketitle` 输出文章标题。

* 第十一行的 `\tableofcontents` 输出文章目录。

* 十二、十三行的两个 `\section` 开始新的一节。

* 最后的 `\biblography{math}` 从文献数据库 math 中获取参考文献格式并打印参考文献列表。

### 填写正文

```latex
西方称勾股定理为毕达哥拉斯定理，将勾股定理的发现归功于公元 6 世纪的毕达哥拉斯学派。该学派得到一个法则，可以求出排成直角三角形三边的三元数组。毕达哥拉斯学派没有书面著作，该定理的严格表述和证明见于欧几里得《几何原本》的命题 47 ：“直角三角形斜边上的正方形等于两直角边上的正方形之和。” 证明是用面积做的。
	
	我国《周髀算经》载商高（约公元前 12 世纪）答周公问······
```

编译结果：

![](https://ooo.0o0.ooo/2017/06/25/594f757e7f044.png)

注意：

* 分段需要在两段之间加入空行，单纯换一行并不会使文字另起一段。空行只起分段作用，多余的空行并不会增加段间距。
* LaTeX 可以自动完成每一段前的首行缩进。
* 通常汉字前后的空格会被忽略，其他符号后面的空格则保留。

### 命令与环境

处理脚注与应用内容

脚注是