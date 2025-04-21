# Latex(Overleaf)论文撰写经验总结

#### 论文模板

每个期刊或会议，在他的官网上都能找到论文模板连接，里面会有word版本，会有离线latex模板（都是打包好为.zip文件），也会有在线overleaf模板链接。

<img src="graph\image-20241001211128385.png" alt="image-20241001211128385" style="zoom:50%;" />

最不建议的就是使用word，因为论文有严格的template，word编辑会涉及很多麻烦的步骤。

拿IEEE作为例子，点进链接就可以看到各种模板，有期刊模板，会议模板，选择自己需要的即可进入。

<img src="graph\image-20241001211331246.png" alt="image-20241001211331246" style="zoom:50%;" />

有些出版社没有直接的overleaf链接，如Elsevier，也可以下载官网latex模板文件`zip`包，在overleaf中`upload project`，点击上传.zip文件即可。

<img src="graph\屏幕截图 2024-10-09 100952.png" alt="屏幕截图 2024-10-09 100952" style="zoom: 67%;" />

#### Latex数学公式

这里不写那么多，自行查看网页，里面很详细：

[如何优雅地在Markdown中输入数学公式 - 不爱喝橙子汁的橙子 - 博客园 (cnblogs.com)](https://www.cnblogs.com/syqwq/p/15190115.html)

补充一下，p'

```
d^{\prime}
```

#### 数学公式的格式

数学公式由

```
\begin{equation}
% content
\begin{equation}
```

包裹。

可以在内容中使用`\tag{xxx}`来自定义公式标号，即{}内内容将会在公式后方显示。使用`\label{xxx}`则是隐式标签，即在撰写时方便作者check的标号，并不会在pdf文章中显式的表示出来。

##### 数学公式等号对齐

```
\begin{equation}
\begin{aligned}
cmt_A &= COMM_{bc}(addr_A, value_A, sn_A, r_A); \\
sn_A &= PRF(sk_A, r_A); \\
value_A &\geq v; \\
cmt^*_A &= COMM_{bc}(addr_A, value_A + v, sn^*_A, r^*_A); \\
sn^*_A &= PRF(sk_A, r^*_A)
\end{aligned}	\tag{2-18}
\end{equation}
```

基本格式如上。需要注意的是，可以再使用一个、

```
\begin{aligned}
% content
\end{aligned}
```

来表示公式对齐格式，在`% content`部分，使用`&`占位符来表示公式对其的部位，如果希望等号对齐，则在等号前加上`&`。

##### 公式太大，缩小一些

```
\begin{equation}
\small

% content

\label{xxx}
\end{equation}
```

在 `\begin{equation}` 下添加 `\small` 会将公式的大小缩小到小号文本。如果你希望进一步缩小，甚至可以使用 `\footnotesize` 或 `\scriptsize`：

- `\small`: 稍小于正文字体
- `\footnotesize`: 比 `\small` 更小
- `\scriptsize`: 更小

##### 公式中加上阴影

前置导入：

```
\usepackage{xcolor} % For coloring and shading
```

使用`\fcolorbox{gray}{lightgray}{$xxx$}`在句中给`xxx`打上阴影，注意`$`和`{}`的使用。

#### 文章布局

整篇文章的结构不碍乎就是下面的布局，每个板块，板块的分点，板块分点的分点，都靠

```
\section{}
\subsection{}
\subsubsection{}
```

来进行定义。

例如：

```
% 前置导言部分
\begin{document}

\title{xxx\\
\thanks{xxx} %这个是致谢部分，会在标题页左下角显示这段文字
}

\author{ %作者信息
}

\maketitle
\begin{abstract}
% 这里写摘要
\end{abstract}

\begin{IEEEkeywords}
% 这里是关键词
\end{IEEEkeywords}

\section{A}

\section{B}
\subsection{B1}
\subsection{B2}
\subsection{B3}

\section{C}
\subsection{C1}
\subsubsection{C1.}
\subsubsection{C1..}
\subsubsection{C1...}
\subsection{C2}
\subsection{C3}

\section{D}
\subsection{D1}

\section{E}

\bibliographystyle{IEEEtran}
\bibliography{IEEEabrv,ref} % 参考文献部分，后面针对这部分有教程

\end{document}
```

#### Overleaf多作者对齐

例如3个作者，采用\author{第一作者信息 \\ 第三作者信息 \and 第二作者信息}；
例如4个作者，采用\author{第一作者信息 \\ 第三作者信息 \and 第二作者信息 \\ 第四作者信息}；
以此类推，即换栏用\and, 换行用\\， 先第一栏，后第二栏。

```
\author{
\IEEEauthorblockN{Yichen Tan$^\&$}
\IEEEauthorblockA{
\textit{Sichuan University, Pittsburgh Institute} \\
Chengdu, China \\
xxxxxxxx@qq.com} \\
\IEEEauthorblockN{xx xxxx}
\IEEEauthorblockA{
\textit{xxxxxxxxxxx} \\
Kunming, China \\
xxxxxxxxxx@qq.com}
\and
\IEEEauthorblockN{Yuyang Cheng$^\&$}
\IEEEauthorblockA{
\textit{Sichuan University, School of Cyber Science and Engineering} \\
Chengdu, China \\
xxxxxxxxxx@qq.com} \\
\IEEEauthorblockN{Yong Zhao}
\IEEEauthorblockA{
\textit{Sichuan University, Pittsburgh Institute} \\
Chengdu, China \\
xxxxx@xxxxx.cn}
}
```

#### 加粗

使用 \textbf{xxx}，xxx即为加粗的内容

#### 字体颜色

```
\textcolor{red}{xxx}
```

#### 字体大小和居中

```
\begin{center}
    \textbf{\fontsize{14}{16}\selectfont xxx}
\end{center}
```

14pt font size and 16pt line spacing（行高）

#### 行间距

段内行间距，这里有两种：

第一是在导言部分加入：

```
\usepackage{setspace}
% 设置全局行间距为 1.2 倍
\renewcommand{\baselinestretch}{1.2}
```

第二种是局部调整行间距，如果只希望某一部分内容是 1.2 倍行间距，可以在局部用 `\begin{spacing}` 和 `\end{spacing}` 环境包裹。

```
\usepackage{setspace}

% 局部调整行间距
\begin{document}

xxx普通行间距的内容。

\begin{spacing}{1.2}
这是 1.2 倍行间距的段落。
这是 1.2 倍行间距的段落。
\end{spacing}

xxx普通行间距的内容。

\end{document}
```

段后行间距

```
\setlength{\baselineskip}{1.5em}
```

#### 插入罗马数字

在导言区加入以下代码：

```
\makeatletter
\newcommand{\rmnum}[1]{\romannumeral #1}
\newcommand{\Rmnum}[1]{\expandafter\@slowromancap\romannumeral #1@}
\makeatother
```

然后在文中直接使用即可，\Rmnum{1}即为大写罗马数字1，\rmnum{1}即为小写罗马数字1，以此类推

#### 图表放置位置

```
\begin{figure}[htbp]
\centering
\includegraphics[width=0.75\linewidth]{xxx.png}
\caption{xxx}
\label{fig}
\end{figure}
```

默认情况下使用的是 `[htbp]` 参数，表示 LaTeX 可以选择 "here" (当前位置), "top" (页面顶部), "bottom" (页面底部), 或 "page" (单独一页)。如果你希望图片严格按照你在代码中的位置插入，可以使用 `float` 宏包并使用 `H` 参数。

首先在导言区添加 `\usepackage{float}`，然后修改 `figure` 环境为：

```
\usepackage{float}

\begin{figure}[H]
\centering
\includegraphics[width=\linewidth]{xxx.png}
\caption{xxx}
\label{fig}
\end{figure}
```

图表默认是浮动的，有时 LaTeX 会在有太多空行时将图片放置在不合适的地方，最好还是建议手动调整。比如说死抠排版、换行。有时删掉几个词让掉尾的内容提上去，排版就好了。

#### 列表

通过下面的语句来实现

```
% Unnumbered list
\begin{itemize}
\item 
\item 
\item 
\end{itemize}  

% Description list
\begin{description}
\item[] 
\item[] 
\item[] 
\end{description}  
```

其中，Description list方括号中放置序号或者标题，后面接着内容。比如说，`\item[a)] bbb`，就是 **a)** bbb

#### 跨栏

Take IEEE for example：

默认分为两栏行文，但是遇到很大的图表，我们可以同时占据两栏来放置。

##### 对于图：

```
\begin{figure}[htbp]
\centering
\includegraphics[width=0.75\linewidth]{xxx.png}
\caption{xxx}
\label{fig}
\end{figure}
```

Vs.

```
\begin{figure*}[htbp]
\centering
\includegraphics[width=0.75\linewidth]{xxx.png}
\caption{xxx}
\label{fig}
\end{figure*}
```

即加上*即可。

更改\linewidth前的数字大小可以调整图片的缩放

##### 对于表：

同理，使用 \begin{table}[htbp] 和 \begin{table*}[htbp]

#### 文献引用

用ref.bib加入引用

首先在左侧文件栏里创建一个ref.bib文件，然后在ref.bib中导入BibTex格式的引用：

<img src="graph\ddd6053839cc45d5a27de1e2bab0eb6a.png" alt="ddd6053839cc45d5a27de1e2bab0eb6a" style="zoom:50%;" />

BibTex引用格式在主流学术网站的论文界面基本都能找到，点击即可，再复制到ref.bib文件，大致内容如下：

<img src="graph\image-20241001211746610.png" alt="image-20241001211746610" style="zoom:50%;" />

然后在.tex文件中（即编辑的主文件），在需要引用的地方使用：

```
\cite{xxx}
```

例如：

![image-20241001211925880](graph\image-20241001211925880.png)

xxx的内容即为BibTex中第一行后面的一串字符，可以理解为你自定义的要引用文章的名称。

最后，在文件末尾插入：

```
\bibliographystyle{IEEEtran}
\bibliography{IEEEabrv,ref}
```

<img src="graph\image-20241001212211384.png" alt="image-20241001212211384" style="zoom: 67%;" />

即可！

`\bibliographystyle{xxx}`中，xxx为xxx.bst文件，即为reference model文件，选用哪种引用风格就使用对应的bst文件。

若遇到文献引用没有超链接跳转，则在导言部分加上包：

`\usepackage[hidelinks]{hyperref}`

即可



甚至overleaf中有以下这8种自带的引用格式，直接把stylename的名字放在bst文件名的地方即可，不用上传任何bst文件。

| stylename | output                                                       |
| :-------- | :----------------------------------------------------------- |
| `abbrv`   | ![BibtexStylesEx1.png](https://sharelatex-wiki-cdn-671420.c.cdn77.org/learn-scripts/images/0/0c/BibtexStylesEx1.png) |
| `acm`     | ![BibtexStylesEx2.png](https://sharelatex-wiki-cdn-671420.c.cdn77.org/learn-scripts/images/9/97/BibtexStylesEx2.png) |
| `alpha`   | ![BibtexStylesEx3.png](https://sharelatex-wiki-cdn-671420.c.cdn77.org/learn-scripts/images/2/20/BibtexStylesEx3.png) |
| `apalike` | ![BibtexStylesEx4.png](https://sharelatex-wiki-cdn-671420.c.cdn77.org/learn-scripts/images/6/62/BibtexStylesEx4.png) |
| `ieeetr`  | ![BibtexStylesEx5.png](https://sharelatex-wiki-cdn-671420.c.cdn77.org/learn-scripts/images/2/2c/BibtexStylesEx5.png) |
| `plain`   | ![BibtexStylesEx6new.png](https://sharelatex-wiki-cdn-671420.c.cdn77.org/learn-scripts/images/7/79/BibtexStylesEx6new.png) |
| `siam`    | ![BibtexStylesEx7.png](https://sharelatex-wiki-cdn-671420.c.cdn77.org/learn-scripts/images/4/4d/BibtexStylesEx7.png) |
| `unsrt`   | ![BibtexStylesEx8.png](https://sharelatex-wiki-cdn-671420.c.cdn77.org/learn-scripts/images/f/f6/BibtexStylesEx8.png) |

**abbrv**：简化版样式，通常会缩写作者的名字和期刊名称。通常适用于简洁性要求较高的文献引用格式。

**acm**：适用于ACM（美国计算机协会）出版的文献。该样式强调出版物的详细信息，通常包括作者、文章标题、期刊/会议名称和日期等。

**alpha**：根据作者的姓氏和年份的字母顺序排列引用，引用样式较为独特。通常，作者的名字和出版年份会被合并为一个字母数字的组合，便于引用。

**apalike**：与APA格式类似，使用作者姓名和出版年份的引用方式。这是一种常见的学术引用格式，常见于社会科学领域。

**ieeetr**：适用于IEEE（电气与电子工程师协会）期刊的引用格式。它按顺序列出作者和文章的标题，强调引用顺序和一致性。

**plain**：标准的BibTeX格式，按字母顺序排列作者的姓氏。适用于一般的学术出版物，但没有过多的格式化，比较基础。

**siam**：适用于SIAM（工业与应用数学学会）出版的文献，特别注重数学领域的文献引用。类似于IEEE格式，但有一些特定的排版要求。

**unsrt**：按文献出现的顺序排列引用，而不是按作者的姓氏或年份排序。通常用于一些特定的科学和技术文献中，引用的顺序会反映它们在文献中的首次出现。



#### 缩小或增大图、表、式或文字的间距

使用

```
\vspace{-1em}
```

将`-1`调整为正数则是增大间距，使用更小的整数则进一步缩小间距。

但注意用多了会出现排版的bug，标题字会和正文重叠，建议不要使用太多。

公式和上一段文字之间空隙太大，可以直接尝试文字和\begin{equation}之间不要留空行，这样就可以不用\vspace{-1em}

#### 普通表格Vs.三线表

```
\begin{table*}[htbp]
\centering
\caption{Experimental data related to batch transfers}
\begin{tabular}{|l|c|c|c|c|c|}
\hline
\textbf{Function Type} & \textbf{Proving Key (MB)} & \textbf{Verification Key (B)} & \textbf{Initialization Time (s)} & \textbf{Proof Generation (s)} & \textbf{Proof Verification (ms)} \\ \hline
......content
\end{tabular}
\label{table:example}
\end{table*}
```

Vs.

```
\begin{table*}[htbp]
\centering
\caption{Experimental data related to batch transfers}
\begin{tabular}{lccccc}
\toprule
\textbf{Function Type} & \textbf{Proving Key (MB)} & \textbf{Verification Key (B)} & \textbf{Initialization Time (s)} & \textbf{Proof Generation (s)} & \textbf{Proof Verification (ms)} \\
\midrule
......content
\bottomrule
\end{tabular}
\label{table:example}
\end{table*}
```

![image-20241001204222329](graph\image-20241001204222329.png)



使用\usepackage{booktabs}，很美观的三线表

```
\begin{table}[ht]
\centering
\begin{tabular}{@{}ll@{}}
\toprule
\textbf{Repair Method}           & \textbf{Special Combination}                                                \\ \midrule
Filling Repair                   & - How to adjust uneven levels (such as sagging or rising) \\ 
                                  & - Purple line light reflection (Environmental tree resin) \\ 
                                  & - Salt acid reaction (Mud slurry material)                                    \\ \midrule
Local Replacement                & - How to adjust dimensional differences (e.g., differences in platform length) \\
                                  & - Microscopic material structure variations under the microscope \\ 
                                  & - Salt acid reaction and its origin                                           \\ \midrule
Surface Coating                  & - How to cover surface layers (e.g., coating thickness difference) \\
                                  & - Purple line detecting surface gloss (like modern oil painting)              \\ \midrule
Structural Reinforcement         & - How to handle abnormal thickening of structural joints \\ 
                                  & - Purple line indicating fusion of metal frame or connection \\ 
                                  & - Microscopic analysis of specific material or technology structure           \\ \bottomrule
\end{tabular}
\caption{Repair Methods and Their Special Combinations}
\end{table}
```



#### 表格Label换行

有时表格的Label太长，会导致图表超出界限或显示的很小，可以让Label在表格内换行以达到节省横向空间的效果。
可以将Label使用\makecell块打包

    	\toprule
    	\makecell{\textbf{Function} \\ \textbf{Type}} & 
    	\makecell{\textbf{Minimum} \\ \textbf{Value} (s)} & 
    	\makecell{\textbf{Maximum} \\ \textbf{Value} (s)} & 
    	\makecell{\textbf{Relation with} \\ \textbf{Key Pairs}} & 
    	\makecell{\textbf{Maximum} \\ \textbf{Growth} (s)} & 
    	\makecell{\textbf{Minimum} \\ \textbf{Growth} (s)} \\
        \midrule

Instead of:

```
\begin{table}[htbp]
  \centering
  \caption{Analysis of Initialization Time for Sigmint, Sigredeem, Sigsend, Sigdeposit}
  \label{tab:sigmint-initialization-time}
  \resizebox{\linewidth}{!}{
  \begin{tabular}{cccccc}
    \toprule
    \textbf{Function Type} & \textbf{Proving Key (MB)} & \textbf{Verification Key (B)} & \textbf{Initialization Time (s)} & \textbf{Proof Generation (s)} & \textbf{Proof Verification (ms)} \\
    \midrule
    ...contenrt
    \bottomrule
  \end{tabular}
  }
\end{table}
```

#### 两张图放在一排

```
\begin{figure}[htbp]
\centering
\begin{minipage}[b]{0.45\linewidth} % 控制每个图片的宽度
  \centering
  \includegraphics[width=\linewidth]{xxx.png}
  \caption{xxx}
  \label{fig:4-10}
\end{minipage}
\hspace{0.05\linewidth} % 控制两个图片之间的间距
\begin{minipage}[b]{0.45\linewidth}
  \centering
  \includegraphics[width=\linewidth]{xxx.png}
  \caption{xxx}
\end{minipage}
\end{figure}
```

Instead of

```
\begin{figure}[htbp]
\centering
\includegraphics[width=\linewidth]{xxx.png}
\caption{xxx}
\label{fig}
\end{figure}

\begin{figure}[htbp]
\centering
\includegraphics[width=0.6\linewidth]{xxx.png}
\caption{xxx}
\label{fig}
\end{figure}
```

<img src="graph\屏幕截图 2024-09-30 221849.png" alt="屏幕截图 2024-09-30 221849" style="zoom:50%;" />





#### 最后一页排版问题

Use the `\balance` command from the `balance` package to balance the content of the two columns on the last page.

```
\usepackage{balance}
...
\balance
\bibliographystyle{model1-num-names} % the .bst file
\bibliography{ref} % ref.bib name
\end{document}
```

#### 代码片段

插入代码片段并高亮不同编程语言的代码，首先，需要在导言区引入 `listings` 和 `xcolor` 宏包：

```
\usepackage{listings}
\usepackage{xcolor}
```

然后，可以在文档中用 `\lstinputlisting` 命令插入代码文件

```
\lstinputlisting[language=Matlab]{./code/1.m}
\lstinputlisting[language=C++]{./code/1.cpp}
```



#### 自动目录

可以使用下面的命令来自动生成目录，同时保证当页全为目录内容：

```
\tableofcontents
\clearpage
```

在 LaTeX 中，生成的目录默认是静态的，不能自动跳转到对应的章节。如果你希望目录中的各个条目变为超链接，可以使用 `hyperref` 宏包，它可以将目录项、章节标题等自动变成可点击的链接。

在导言区域直接加入下面的包即可：

```
\usepackage{hyperref}
```

你还可以定制 `hyperref` 的行为，设置超链接的颜色、链接的框线等。例如：

```
\usepackage[hidelinks]{hyperref} % 隐藏链接的框线
% 或者
\usepackage[colorlinks=true, linkcolor=blue]{hyperref} % 设置链接为蓝色
```



#### 交叉引用

在 LaTeX 中，交叉引用（cross-referencing）通常用于引用文档中的图表、章节、公式等内容。为了实现交叉引用，可以使用 `\label` 和 `\ref` 命令配合。

**使用 `\label` 命令**： 在你想引用的内容前使用 `\label` 命令。`label` 后面的内容是你定义的标识符，它用来标记该位置。

**使用 `\ref` 或 `\eqref` 命令**： 在文档的其他部分使用 `\ref{}` 或 `\eqref{}` 命令来引用前面设置的标识符。`ref` 命令引用章节、图表等，而 `eqref` 主要用于引用公式，自动加上括号。



#### 退出标号

很多内容，比如`\section*{}，\begin{equation*}`等等，特别是equation，在遇到复杂的算式又不算方程的情况下，用equation*即可不对其标号



#### 取消首行缩进

`\noindent`后面跟你这一段的内容，则这一整段都不缩进
