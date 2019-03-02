---
layout: posts
title:  "30 分钟快速入门 LaTex "
categories: latex
toc: true
toc_label: "Latex 入门"
toc_icon: "heart"
---
{% include toc %}   
本篇文章总结了 `LaTex` 最基本的语法，以及经常使用的语法，比如表格、图片、数学公式等。

首先从一篇论文最开始的部分来看。
## 头文件
{% highlight ruby %}
\documentclass[acmlarge]{acmart}
{% endhighlight %} 

这是在 `Latex` 中的第一行需要写的，表示这篇论文的排版布局，通常这个排版布局是和 `latex` 文件是在同一个文件夹下面。其中关键字`documentclass`后面有两个括号`[]{}`。先说`{}`这个是表示选择的那个布局文件，里面规定了排版布局，比如长宽比例，使用的字体，以及其他设置。但是通常一个排版布局文件里面可能包含好几种排版布局，这个时候可以通过`[]`这个符号来说明具体使用那个布局。还可以通过`[]`它来说明使用编码，比如`[UTF-8]{acmart}`，表示使用支持中文编码。

在往下面是关于使用的那些包以及设置一些环境，如果是在对应期刊下载的`latex`模版，那么下载之后这些相关的设置已经在对应的布局文件设置好了，就不需要在进行设置，如果想改变部分布局的话或者是引入新的包，可以通过以下格式来进行修改和添加。  
{% highlight ruby %}
\usepackage[left=2.50cm, right=2.50cm, top=2.50cm, bottom=2.50cm]{geometry} %页边距
\usepackage{epsfig}
\usepackage{algorithm}
\usepackage{algorithmic}
\usepackage{mathrsfs}
\setmainfont{KaiTi}    % 楷体
{% endhighlight %}   
上面主要包含两个部分，一个是`userpackage`，一个是`setmainfont`。`userpackage`表示使用指定的包，这些包都是系统支持的，需要引入哪些包直接在关键词后面`{}`里加上就可以使用。比如在论文中需要写一些伪算法，那么需要引入相应的算法包。另外一个看第一个包里面其实前面还多了一些设置，在`[]`里面有具体的指定多少，`{}`指定了使用页面距，但是可以通过在前面`[]`括号里去覆盖默认的数据。
可以直接在 `latex`里面进行修改，不需要到相应的排版布局文件中在去修改。`setmainfont`是表示使用什么字体，关于字体中英文都可以指定，这里的字体是我们电脑中自带的字体，如果电脑中没有相应的字体，那么引人之后，进行编译的时候，可能会出现错误，找不到对应的字体模块。下面是一些中文常用的字体，如果想指定英文字体，可以直接在`{}`里面写上，比如`{times}`英文字体。  
{% highlight ruby %}
\setmainfont{Microsoft YaHei}  % 微软雅黑
\setmainfont{YouYuan}  % 幼圆    
\setmainfont{NSimSun}  % 新宋体
\setmainfont{SimSun}   % 宋体
\setmainfont{SimHei}   % 黑体
{% endhighlight %}    
包和相应的设置已经完成，那么在往下就应该是论文的标题和作者相关的设置。如果是下载的模版，那么在模版中应该是用设置好的格式，只需要在它指定的地方填写相应的信息。下面是对一篇没有指定格式的说明，可以在`latex`文件中进行添加。  
{% highlight ruby %}
\title{\textbf{这是论文的标题}}
\author{ 作者信息 }
\date {日期信息}
{% endhighlight %}     
`latex`中表示论文标题是通过`title`来指定的，`textbf`是对字体进行加粗。作者信息是通过`author`来表示，如果想对其中的信息进行高亮之类的，可以在前面加上对应的修饰。`date`表示日期。
## 正文
以上部分如果完成之后，那么一个论文的最前面的部分已经完成，通常这部分都是属于标题部分，接下来就可以写论文的正文，包括摘要、介绍部分、相关工作、提出的内容、实验部分、总结部分、致谢、参考文献。开始写正文的使用需要包含两个关键词。  
{% highlight ruby %}
\begin{document}
    \maketitle
\end{document}
{% endhighlight %}  
就是用`\begin{document}`表示正文的开始，`\end{document}`表示正文结束。`\maketitle`是表示编译上面设置的部分，包括布局、作者信息等。

### 摘要
摘要是一个论文必不可少的部分，如果是中文论文的话，可能还需要对应的中英文摘要。摘要的格式如下：
{% highlight ruby %}
\renewcommand{\abstractname}{摘要} 
\begin{abstract}
这是一篇中文小论文。这个部分用来写摘要。
\end{abstract}
{% endhighlight %}  
其中，第一行是表示把原来的摘要的表示是`abctract`改成中文摘要的名字。

### 章节
章节分为大章节和小章节，可以不断的缩小。比如第 1 章，第 1.1 章等。下面是章节的代码。
{% highlight ruby %}
\section{背景介绍}
\section{相关工作}
\section{模型和方法}
\subsection{模型 1}
\subsubsection{模型 1.1}
{% endhighlight %}  
其中`section`表示大章节，`subsection`表示在`section`下面的下章节，`subsubsection`表示在`subsection`章节下面的下章节。  
<img src="{{ '/assets/images/latex/section.jpg' }}" alt="section"/>

### 参考文献
#### 不引入文件
参考文献有两种添加方式，一种是直接在`latex`文件最后加入，另外一种通过引入`.bib`文件，把参考文献都放在另外一个文件中。第一种方式是直接在文件中加入。    
{% highlight ruby %}
\bibliographystyle{plain}
\begin{thebibliography}{9}
\bibitem{fr-cnn} 
Ren, Shaoqing, et al. "Faster r-cnn: Towards real-time object detection with region proposal networks." Advances in neural information processing systems. 2015.
\bibitem{r-cnn} 
Girshick, Ross. "Fast r-cnn." Proceedings of the IEEE international conference on computer vision. 2015.
\end{thebibliography}
{% endhighlight %}  
其中，`\bibliographystyle{plain}`表示参考文献的格式使用`plain`，不然编译的时候会报错。`\begin{thebibliography}{9}`表示参考文献的正式开始，`{9}`表示参考文献的个数。`\bibitem{fr-cnn} `表示参考文献的对应的名字，这个并不会显示出来，只是说明这个参考文献是什么内容，这个下面的内容才是参考文献，参考可以直接在网上复制。  
<img src="{{ '/assets/images/latex/reference.jpg' }}" alt="reference"/>
#### 引人文件
第二种方式可以通过引入一个文件，来使用参考文献，这种方式相对于第一种方式比较复杂一些，但是有一定的优势，比如当参考文献数量过多时，使用这种方式比较好管理，如果文献比较多，都放在同一个文件中，会显得臃肿。使用这种方式只需要在`latex`文件中加入下面两行。  
{% highlight ruby %}
\bibliographystyle{plain}
\bibliography{reference}
{% endhighlight %}   
第一行同样是声明对应的参考文献格式，`\bibliography{reference}`说明引用哪一个文件，`{}`这里面是引入`reference.bib`的文件名，也就是保存参考文献那个文件的名称。关于`reference.bib`文件中的格式可以通过网上直接复制。  
<img src="{{ '/assets/images/latex/reference2.jpg' }}" alt="reference"/>
文献内容填写好之后，通过下面的方式来进行编译，才会出现对应的参考文献。  
1. 用`LaTeX`编译你的`.tex`文件，这个就是选择工具栏第一个三角形符号的选项中选择`latex`，如果是中文就选择`xelatex`。  
2. 用`BibTeX`编译 `.bib` 文件。将第一步中的`latex`，换成`bibtex`在进行编译。  
3. 在切换到`latex`或者`xelatex`，进行编译两次，连续点击两次。  
4. 这个时候在看编译后的`pdf`文件就会出现参考文献。  

{% include comment-section.html %}


