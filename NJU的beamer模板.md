NJU的beamer模板

```latex
\documentclass[12pt,aspectratio=169,mathserif]{beamer}		
\usepackage{nju}			 %导入 nju 模板宏包
\usepackage[UTF8]{ctex}         %导入 ctex 宏包，添加中文支持
\usepackage{xeCJK}
\usepackage{amsmath,amsfonts,amssymb,bm}   %导入数学公式所需宏包
\usepackage{color}			 %字体颜色支持
\usepackage{graphicx,hyperref,url}	
\usepackage{tcolorbox}
\beamertemplateballitem		%设置 Beamer 主题
             %或者=13
\definecolor{blendedblue}{rgb}{0.2,0.2,0.7}

%将正文中的“.”号转换为“.”.

\title{Problem5 讲解}	%首页信息设置
\subtitle{一点点关于Hamel Basis的知识}


\author[人名]{                         %个人信息设置
    计算机科学与技术\quad 人名\\
  {\small 221502010\\
   }}

  

\date{\today}                                                 %日期信息

\begin{document}
\maketitle
\begin{frame}
	\frametitle{一些题外话}
	\begin{itemize}
	\item	一开始我自以为做出了T5,但是被lsa佬发现我一开始就翻译错了...
	\pause
	
	
\item	于是我赶紧学会了高等做法,但是初等的证明需要lsa老师来完善.
	
	\pause
	
	\item 时间原因我可能讲的快,但是结束后的课件会发到群里.
	\end{itemize}
	
\end{frame}
\begin{frame}
%\char65f8
\frametitle{前置知识:度量空间(Metric Space)}
	\begin{definition}[度量空间]
	$X $ 是集合.如果存在  $d: X \times X \rightarrow \mathbb{R}_{\geqslant 0}$  是 $ X$  上双变量的函数, 满足如下三条性质:
	
		a) 对任意的 $ x $ 和 $ y$, $d(x, y) \geqslant 0  $并且取等号当且仅当  $x=y$ ;
	
		b) 对任意的  $x $ 和 $ y$,$ d(x, y)=d(y, x)$ ;
	
		c) 三角不等式: 对任意的 $ x, y, z \in X $, 我们有 $ d(x, z) \geqslant d(x, y)+d(y, z)$  .
		我们就称二元组 $ (X, d)$  是一个距离空间或者度量空间.函数  $d $ 被称作该距离空间上的\textbf{距离函数}.
		\pause\\
		*\textbf{完备空间}或者完备度量空间是具有下述性质的空间：空间中的任何柯西序列都收敛在该空间之内.
	\end{definition} 
\end{frame}
\begin{frame}
	\frametitle{前置知识:开集与闭集}
	在$\mathbb{R}$中,我们可以定义开集为开区间的并,闭集为闭区间的并.\pause \\
	对于一般的度量空间$(X,d)$,我们有更一般的定义:\pause
	
	\begin{definition}
		$(X, d)$  是距离空间.对任意的点$  x \in X, r>0 ,$ 我们称  $B(x, r)=\{y \in X \mid d(y, x)<r\} $ 为以 $ x $ 为中心以 $ r  $为半径的开球.
		如果  $U \subset X$  是若干开球的并, 即 $$ U=\bigcup_{\alpha \in \mathcal{A}} B\left(x_{\alpha}, r_{\alpha}\right)  (\text{指标集}  \mathcal{A}  \text{是任意的})$$, 就称 $ X$  是距 离空间 $ (X, d)  $中的开集.
	\end{definition}
	\pause
	如果$F$的补集是开集,那么$F$是\textbf{闭集}.其中空集和全集都\textbf{既是开集又是闭集.}
\end{frame}
\begin{frame}
	\frametitle{前置知识:内点}
		接上一张: 闭的意思可以解释为对这个集合中的点列取极限是封闭的.\pause
		
	\begin{definition}[内点]
		 对于任意的集合  $Y \subset X$ , 如果对  $y \in Y $, 存在  $\varepsilon>0 $, 使得 $ B(y, \varepsilon) \subset Y $, 我们就称 $ y $ 是  $Y$  的 一个内点.我们用  $\dot{Y} $ 表示 $ Y $ 的内点所组成的集合并称之为 $ Y  $的内部.
	\end{definition}
\end{frame}
\begin{frame}
	\frametitle{前置知识:稠密集(Dense Set)}
	\begin{definition}[Dense Set]
		给定距离空间$(X, d)$，$Y \subset X$ 是子集.如果对任意的$x\in X$ 和任意的$\varepsilon > 0$，都存
		在$y \in Y$ ，使得$d(y,x) < \varepsilon,$我们就称$Y$ 在$X$ 中是稠密的.
	\end{definition}
\end{frame}
\begin{frame}
	\frametitle{贝尔范畴定理(Baire Category Theorem)}
	\begin{theorem}[Baire]
	$	(X, d)$  是完备的距离空间, 那么任意可数个稠密的开集的交仍然是稠密的, 即 若  $\left\{U_{n}\right\}_{n \geqslant 1}$  是可数个稠密的开集，那么 $ U_{\infty}=\bigcap_{n \geqslant 1} U_{n} $ 是稠密的.
	\end{theorem}
\end{frame}
\begin{frame}
	\frametitle{Hamel基}
	\begin{definition}[Hamel]
		(OTIS-Excerpts)$\mathbb{R}$有一个作为$\mathbb{Q}$里的向量空间的基.因此,存在无穷实数集合$\{e_\alpha\}$使得对于任意实数$x\in \mathbb{R}$,存在一种唯一的线性表示$$x=a_1e_{\alpha_1}+a_2e_{\alpha_2}+\cdots+a_ne_{\alpha_n}.$$
		这些数$\{e_{\alpha}\}$被叫做一组哈默尔基(Hamel basis).
		
		事实上,你可以这样想:$$
		\mathbb{R}=\{a_1+\sqrt{2}a_2+\sqrt{3}a_3+a_4\pi+a_5e+\cdots\mid a_1,\cdots \in \mathbb{Q}\}
		$$
	\end{definition}
	\pause
	题目是证明Hamel基的元素是不可数的.
\end{frame}
\begin{frame}
	\frametitle{解答}
	\begin{proof}
		设存在$\{e_i\}_{i=1,2,\cdots}$是完备空间$V$上的一组可数的基,那么对于任意的$k\ge1$ ,定义$V$的子空间$$
		V_k = \operatorname{span}\{e_1,e_2,\cdots,e_k\}.$$
		这里的$\operatorname{span}\{e_1,e_2,\cdots,e_k\}$可以看做$x=a_1e_{1}+a_2e_{2}+\cdots+a_ne_{k}.$构成的集合.
		\pause
		\\根据完备空间的定义,$V_k$是一个闭集.\pause 我们现在说明,对于任意的$k\ge1$,$V_k$的内部是空集.\pause \\
		任取$v\in V,\varepsilon>0$有$v+\varepsilon e_{k+1}\notin V_k$,说明$v$不是$V_k$的内点.\pause\\
		根据定义,有$$
		V=\bigcup_{k \geqslant 1} V_{k} $$
	\end{proof}

\end{frame}
\begin{frame}
	\frametitle{解答}
	\begin{proof}
		我们设$U_n = V-V_n$,根据定义,$U_n$是一个闭集的补集,所以是开集.因为$V_n$的内部为空集,所以这是\textbf{稠密的}.\\ \pause
		根据Baire定理,$U=\bigcap_{n \geqslant 1} U_{n}$是稠密的.\\ \pause
		我们注意到$V=\bigcup_{k \geqslant 1} V_{k} $的补集恰好就是$U$,所以$V$的内部为空.\\ \pause
		但是$V$的内部不为空,这就导出了矛盾.
	\end{proof}
\end{frame}
\begin{frame}
	时间原因,Baire定理的证明不说了.但是在附录里有Baire定理的证明.\\
	感谢大家!
\end{frame}
\begin{frame}
	\frametitle{附录:Baire定理的证明}
	\begin{proof}[Baire]
		任选 $ x \in X $ 和 $ \varepsilon_{0}$ , 我们将在  $U_{\infty}  $中找到一个点  $x_{\infty}$ , 使得  $d\left(x_{\infty}, x\right)<2 \varepsilon_{0}$  .为此, 我们将 归纳地构造 $ X $ 中的点列  $\left\{x_{n}\right\}_{n \geqslant 1}  $.\pause
		
		首先, 根据  $U_{1} $ 的稠密性, 存在 $ x_{1} \in U_{1} $, 使得  $d\left(x_{1}, x\right)<\varepsilon_{0} $ .再根据 $ U_{1}$  是开集, 我们可以找到$  \varepsilon_{1}>0$ , 使得  $\overline{B\left(x_{1}, 2 \varepsilon_{1}\right)} \subset U_{1} $, 其中 $ \overline{B\left(x_{1}, 2 \varepsilon_{1}\right)} $ 是闭球, 即  $\overline{B\left(x_{1}, 2 \varepsilon_{1}\right)}=\left\{y \in X \mid d(y, x) \leqslant 2 \varepsilon_{1}\right\} $ .\pause
	
	 另外, 通过缩小 $ \varepsilon_{1}$ , 我们还可以要求 $ 2 \varepsilon_{1}<\varepsilon_{0}$  .
		我们用 $ x_{1}$  代替  $x $, 用 $ \varepsilon_{1}$  代替  $\varepsilon_{0} $, 重复上面的过程: 根据  $U_{2} $ 的稠密性, 存在$  x_{2} \in U_{2} $, 使得 $ d\left(x_{2}, x_{1}\right)<\varepsilon_{1} $ .根据 $ U_{2}$  是开集, 我们可以找到 $ \varepsilon_{2}>0 $, 使得 $ \overline{B\left(x_{2}, 2 \varepsilon_{2}\right)} \subset U_{2} $ 并且可以进一步要 求  $2 \varepsilon_{2}<\varepsilon_{1} $ .\pause
			\end{proof}
	\end{frame}
\begin{frame}
	\frametitle{附录:Baire定理的证明}
	\begin{proof}
	重复以上过程, 我们就得到了$  \left\{x_{n}\right\}_{n \geqslant 0} $ 和数列 $ \left\{\varepsilon_{n}\right\}_{n \geqslant 0}$  (其中  $x_{0}=x, \varepsilon_{0}=\varepsilon $ ), 使得对任意 的  $n \geqslant 0$ , 有
	\begin{itemize}
		\item[1)]$ x_{n+1} \in U_{n+1}$  并且 $ d\left(x_{n+1}, x_{n}\right)<\varepsilon_{n}$;
		\item[2)]$ \overline{B\left(x_{n+1}, 2 \varepsilon_{n+1}\right)} \subset U_{n+1} $;
		\item[3)]$0<2 \varepsilon_{n+1}<\varepsilon_{n} $
	\end{itemize}
\pause
特别地, 根据第三条, 我们有  $\varepsilon_{n+k}<2^{-k} \varepsilon_{n}$  .

	\end{proof}
\end{frame}
		\begin{frame}
		\frametitle{附录:Baire定理的证明}
		\begin{proof}
			我们现在说明 $ \left\{x_{n}\right\}_{n \geqslant 1}$  是 Cauchy 列.对任意的自然数 $ n$  和 $p $, 我们有
			$$
			\begin{aligned}
				d\left(x_{n+p}, x_{n}\right) & \leqslant d\left(x_{n+p}, x_{n+p-1}\right)+d\left(x_{n+p-2}, x_{n+p-2}\right)+\cdots+d\left(x_{n+1}, x_{n}\right) \\
				&<\varepsilon_{n+p}+\varepsilon_{n+p-1}+\cdots+\varepsilon_{n+1} \\
				&<2^{-p-1} \varepsilon_{n}+2^{-p-2} \varepsilon_{n}+\cdots+\varepsilon_{n} \\
				&<2 \varepsilon_{n} .
			\end{aligned}
			$$
			\pause
			这表明, 对一切  $p \geqslant 0,\left\{x_{n+p}\right\}_{p \geqslant 1}$  都落在 $ \overline{B\left(x_{n}, 2 \varepsilon_{n}\right)}  $中.我们注意到, 上面的不等式直接给出
			$$
			d\left(x_{n+p}, x_{n}\right)<2^{-n+p} \varepsilon+2^{-n+p-1} \varepsilon+\cdots+2^{-n+1} \varepsilon=2^{-n} \varepsilon
			$$
		\end{proof}
		\end{frame}
	\begin{frame}
		\frametitle{附录:Baire定理的证明}
		\begin{proof}
		所以 $ \left\{x_{n}\right\}_{n \geqslant 1} $ 是 Cauchy 列, 根据 $ X$  的完备性, 存在 $ x_{\infty} \in X $, 使得 $ \lim _{n \rightarrow \infty} x_{n}=x_{\infty} $ .\pause
		
		 特别地, 根据 $ \left\{x_{n+p}\right\}_{p \geqslant 1} \subset \overline{B\left(x_{n}, 2 \varepsilon_{n}\right)}$ , 我们知道$  x_{\infty} \in \overline{B\left(x_{n}, 2 \varepsilon_{n}\right)} $ (这是闭集).从而对任意的 $ n \geqslant 1, x_{\infty} \in U_{n} $, 所以, $ x_{\infty} \in U_{\infty}  $.\pause
		 
		 特别地, 在最后一个不等式中取 $ n=0 $, 我们有
		$$
		d\left(x_{p}, x_{0}\right)<\varepsilon .
		$$
		令 $ p \rightarrow \infty$ , 我们就得到  $d\left(x_{\infty}, x\right)<2 \varepsilon  $.\\
		我们完成了证明.
		\end{proof}
	\end{frame}

\end{document}

```

