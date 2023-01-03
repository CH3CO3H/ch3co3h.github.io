---
title: 
category: casual
layout: post
tag: mathjax
---

# 写数学公式的麻烦

学过电磁学的人应该都见过 Maxwell's equations:

$$
\nabla \times \mathbf H =\mathbf J+\frac{\partial \mathbf D}{\partial t}\\
\nabla \times \mathbf D=-\frac{\partial \mathbf B}{\partial t}\\
\nabla \cdot \mathbf B=0\\
\nabla \cdot \mathbf D=\rho
$$

这个方程组用笔在纸上写还算容易，但如果要展现在电子文档或者网页中，就梢显麻烦。几乎所有的数学方程式写起来都很麻烦。如果只是单行结构，只靠插入特殊符号勉强可以解决，但稍微立体化的形式，比如一个分式，就不太容易。正因如此，我们偶尔会看到用对勾符号来代替根号的情形，就像这样：

i=√-1

其实它应该写成这样：

$$
\text i=\sqrt {-1}
$$

但要表现出比较完美的数学公式，就要费一番相当麻烦的额外工夫。比如上面那个 Maxwell's equations，在我的 Markdown 编辑器 MarkText 里，使用 latex 语法，源代码是这样的：

```
\nabla \times \mathbf H =\mathbf J+\frac{\partial \mathbf D}{\partial t}\\
\nabla \times \mathbf D=-\frac{\partial \mathbf B}{\partial t}\\
\nabla \cdot \mathbf B=0\\
\nabla \cdot \mathbf D=\rho
```

在数学公式处理软件 LibreOffice Math 里，源代码是这样的：

```
nabla times bold H  = bold J + frac { partial bold D } { partial t } newline 
nabla times bold E = - frac { partial bold B } { partial t } newline
nabla cdot bold B=0 newline
nabla cdot bold D= %rho 
```

在网页上展示，还需要页面引入 mathjax 脚本文件。

实际使用时我发现，对于行内公式，MarkText 的界定符号是美元符 `$...$`，而 mathjax 默认的界定符是 `\(...\)`。解决这个矛盾的办法有两种：一种是在 MarkText 里这样写：

```markdown
Imaginary number unit: \\( \text {i} = \sqrt {-1} \\)
```

这样 markdown 文件转换为 html 文件时，双反斜线 `\\` 会转为单反斜线 `\`，然后 mathjax 再将 `\(` 及 `\)` 作为行内公式界定符。但这样会导致行内公式在 MarkText 中无法预览。

另一种方法是遵从 MarkText 的界定规则。

```markdown
Imaginary number unit: $ \text {i} = \sqrt {-1} $
```

它看上去会是这样：

Imaginary number unit: $\text {i} = \sqrt {-1}$

然后在网页中插入以下代码：

```javascript
MathJax = {
  tex: {
    inlineMath: [['$', '$'], ['\\(', '\\)']]
  }
};
```

因为 MathJax 认为美元符算是个常见符号，如果不小心忘了它界定行内公式的作用，可能会出现一些莫名其妙的错误。这的确值得注意。

在研究 MathJax 的时候我还发现一个叫做 AsciiMath 的东西。它的语法倒是稍微简单些，但功能也更弱。另外 AsciiMath 使用象形文字的思路来表示符号，比如用两个字母 o 来表示无穷（oo → ∞），这可真是令人绝望。

这些麻烦的原因，自然是数学符号和公式书写格式的发明时间，早于计算机时代到来的时间。用笔在纸上书写是二维操作，比较自由。于是各种符号时大时小，上下翻飞，结构错落有致，写一组方程式堪比绘画。但对于计算机而言，键盘输入是一维线性的，从左到右一条路。所以我们要么使用另外的工具，要么掌握二维到一维的翻译方法。有的公众号文章会使用图片来展示数学公式，这种做法多少显得有点扭曲，但我也理解编辑的无奈。公众号文章本身是一个网页，但我们并不能随意操作它，想要稍微搞的花一点还要借助第三方工具，虽说图片的数据量和加载时间跟纯文本代码有数量级的差别，但直接用图片至少确实能解决问题。

不愿放弃传统做法大概是刻在人类基因中的缺陷。我最近在看复变函数教材时（重新）发现，不但复数域的基本运算符号沿用实变函数，连某些特殊函数也直接重复实变函数中的写法。比如复变函数中的指数函数 $e^z$ 与实变函数中的 $e^x$ 虽格式一样，但含义完全不同；更甚者，像 ln(-1) 这样的写法在实变函数中根本不允许，而在复变函数中就有意义，这可真是令人抓狂。

我认为我们应该发明新的数学规律表示法，一劳永逸地解决以上所有问题，而不是满足于产生新的中间转换接头。要想一个好点子让人们阅读、书写数学公式像编辑普通文本文件一样清晰便捷。其实这是有现成东西可以挪用的，就是编程语言。

编程语言本身的出现早于计算机的到来。从实用角度讲，人们正是在不断追求代码的简洁清晰易读，并且纯文本格式本身就保证了平滑输入。即便有些编程语言支持用特殊字符做标识符，但没有哪个脑子正常的正常的程序员会在变量名中使用一个⊕。所以按照程序语言的思路，设计一套伪代码用于数学逻辑的日常表达，绝对是一件造福人类的事。

举个例子，想要表达 n 的阶乘的含义，常规方法是这样：

n!=n*(n-1)\*...\*1; 另外 0!=1。

而按照编程语言的方式，就会是这样：

```
frac (n)
    if n=0 return 1;
    return n*frac(n-1);
```

虽然一行变成了三行，但我个人觉得后面这种方式清晰准确，并且很有美感，表现力完胜常规方式。

教科书有些地方会使用这样的写法：

$$
v=v(t)
$$

用同一个符号既表示变量也表示函数。虽然这不会引起歧义，但我以为这也没有好处。如果像编程语言那样引入类型系统，我们就可以在表达函数关系时避免出现应变量名称，函数的写法就会是这样：

```
real v (real t);
int upper (real x);
```

既然要借用编程语言的思路，不妨就把 C 标准库里的函数名直接拿过来。我们在终端输入 `man complex` 可以发现很多函数名，其中就有 clog, cexp 和 csin 等各种函数。编程语言中一般要求标识符在同一命名空间内唯一，根本不会出现实数与复数使用同一函数符号这样的事。

希望早日得见各种希腊字母及奇形怪状的符号从教科书中消失。
