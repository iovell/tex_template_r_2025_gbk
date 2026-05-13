# LaTeX 数学笔记模板

一个美观、实用的 LaTeX 数学笔记模板，支持中英文，提供丰富的定理环境和自定义命令。

原文章链接：https://zhuanlan.zhihu.com/p/604236564，作者：到底

## 目录

- [快速开始](#快速开始)
- [项目结构](#项目结构)
- [定理环境](#定理环境)
- [数学符号](#数学符号)
- [配置说明](#配置说明)


## 快速开始

### 编译主文档

```bash
xelatex main.tex
xelatex main.tex  # 第二次编译以生成正确的目录和书签
```

### 单独编译章节

每个章节文件也可以单独编译：

```bash
cd chap0
xelatex chap.tex
```


## 项目结构

```
.
├── main.tex              # 主文件
├── config/
│   ├── _config.tex       # 配置文件
│   ├── package.tex       # 宏包引入
│   ├── custom.tex        # 自定义命令
│   ├── theorem0.tex      # 无框英文定理环境
│   ├── theorem0_zh.tex   # 无框中文定理环境
│   ├── theorem1.tex      # 带框英文定理环境
│   ├── theorem1_zh.tex   # 带框中文定理环境
│   └── cover*.tex        # 封面相关文件
├── chap0/
│   └── chap.tex          # 第0章（模板使用示例）
├── chap1/
│   └── chap.tex          # 第1章（数学公式示例）
└── figure/               # 图片文件夹
```

## 英文版

需要将`main.tex`以及`chap.tex`文件`\documentclass`参数中的`ctexbook`改为 `book`，以及引入对应的英文定理环境即可。

##  图片

全部放在`figure`文件夹下，引入时无需书写图片件路径

```latex
\begin{figure}[htbp]
    \centering
    \includegraphics[scale=0.5]{0-1.png}
    \caption{示例}
\end{figure}
```

## 定理环境

### 带框版本（推荐）

在 `_config.tex` 中引入 `theorem1.tex` 或 `theorem1_zh.tex`。

#### 定义 (Definition)

```latex
\begin{defn}
设 $f: \R^n \to \R^m$ 是一个函数，若对于任意 $\varepsilon > 0$，存在 $\delta > 0$，使得当 $\|\bs{x} - \bs{a}\| < \delta$ 时，有 $\|f(\bs{x}) - f(\bs{a})\| < \varepsilon$，则称 $f$ 在点 $\bs{a}$ 处 \textbf{连续}。
\end{defn}
```

定义环境单独编号

#### 定理 (Theorem)

```latex
\begin{thm}
设 $f$ 在 $[a, b]$ 上连续，则 $f$ 在 $[a, b]$ 上必取得最大值和最小值。即存在 $x_1, x_2 \in [a, b]$，使得对一切 $x \in [a, b]$，有
$$f(x_1) \leq f(x) \leq f(x_2).$$
\end{thm}
```

定理、引理、准则公用一个编号

#### 引理 (Lemma)

```latex
\begin{lemma}
若函数 $f$ 在区间 $[a, b]$ 上连续，且在 $(a, b)$ 内可导，则存在 $\xi \in (a, b)$，使得
$$f'(\xi) = \frac{f(b) - f(a)}{b - a}.$$
\end{lemma}
```

#### 准则 (Criterion)

```latex
\begin{criterion}
级数 $\sum_{n=1}^\infty a_n$ 收敛的充要条件是：对于任意 $\varepsilon > 0$，存在正整数 $N$，当 $n > N$ 时，对任意正整数 $p$，有
$$|a_{n+1} + a_{n+2} + \cdots + a_{n+p}| < \varepsilon.$$
\end{criterion}
```

#### 推论 (Corollary)

```latex
\begin{corollary}
由上述定理可知，闭区间上的连续函数必有界。
\end{corollary}
```

#### 命题 (Proposition)

```latex
\begin{proposition}
设 $V$ 是数域 $\mathbb{F}$ 上的线性空间，$W \subseteq V$。若 $W$ 对 $V$ 中的加法和数乘封闭，则 $W$ 是 $V$ 的子空间。
\end{proposition}
```

#### 注 (Remark)

```latex
\begin{rmk}
注意上述命题的逆命题也成立，即子空间必对加法和数乘封闭。
\end{rmk}
```

#### 证明 (Proof)

```latex
\begin{proof}
我们来证明 Lagrange 中值定理。构造辅助函数
$$F(x) = f(x) - f(a) - \frac{f(b) - f(a)}{b - a}(x - a).$$
易知 $F(a) = F(b) = 0$，且 $F$ 在 $[a, b]$ 上连续，在 $(a, b)$ 内可导。由 Rolle 定理，存在 $\xi \in (a, b)$，使得 $F'(\xi) = 0$，即
$$f'(\xi) = \frac{f(b) - f(a)}{b - a}.$$
\qed
\end{proof}
```

#### 例题 (Example)、解 (Solution)

```latex
\begin{example}     
求函数 $f(x) = x^3 - 3x + 1$ 的极值。
\end{example}

\begin{solution}
首先求导得 $f'(x) = 3x^2 - 3 = 3(x^2 - 1)$。令 $f'(x) = 0$，解得 $x = \pm 1$。

- 当 $x < -1$ 时，$f'(x) > 0$，函数单调递增；
- 当 $-1 < x < 1$ 时，$f'(x) < 0$，函数单调递减；
- 当 $x > 1$ 时，$f'(x) > 0$，函数单调递增。

因此，$f(x)$ 在 $x = -1$ 处取得极大值 $f(-1) = 3$，在 $x = 1$ 处取得极小值 $f(1) = -1$。
\end{solution}
```

说明、解、证明环境不编号，命题、例题独立编号

需要注意，在使用 `theorem1` 的配置定理环境时，无法在环境内部使用`figure` 环境，会报错。

### 无框版本

在 `_config.tex` 中引入 `theorem0.tex` 或 `theorem0_zh.tex`，环境名称与带框版本相同。

## 数学符号（自定义命令）

本文档 `config/custom.tex`自定义了一些常用命令

### 数集

| 命令 | 效果         | 说明     |
| ---- | ------------ | -------- |
| `\R` | $\mathbb{R}$ | 实数集   |
| `\Z` | $\mathbb{Z}$ | 整数集   |
| `\N` | $\mathbb{N}$ | 自然数集 |
| `\Q` | $\mathbb{Q}$ | 有理数集 |
| `\C` | $\mathbb{C}$ | 复数集   |

### 向量与矩阵

| 命令       | 效果                  | 说明              |
| ---------- | --------------------- | ----------------- |
| `\bs{A}`   | $\boldsymbol{A}$      | 加粗（向量/矩阵） |
| `\ora{AB}` | $\overrightarrow{AB}$ | 向量箭头          |

### 微积分

| 命令       | 效果                           | 说明     |
| ---------- | ------------------------------ | -------- |
| `\d`       | $\mathrm{d}$                   | 微分算子 |
| `\dive`    | $\mathrm{div}\;\boldsymbol{F}$ | 散度     |
| `\rotn`    | $\mathrm{rot}\;\boldsymbol{A}$ | 旋度     |
| `\grad{f}` | $\nabla\boldsymbol{f}$         | 梯度     |

### 其他命令

| 命令                          | 说明          |
| ----------------------------- | ------------- |
| `\myspace{n}`                 | 插入 n 个空行 |
| `\pll`                        | 平行符号 //   |
| `\tabincell{c}{内容 \\ 内容}` | 表格内换行    |
| `\xrowht`                     | 调整表格高度  |

#### \tabincell

```latex
\begin{table}[htbp!]
    \centering
    \begin{tabular}{|c|c|}
        \hline
        特征方程的根                                        & 微分方程通解中的对应项                                                                 \\
        \hline
        单实根$r$                                           & 给出一项：$Ce^{rx}$                                                                    \\
        \hline
        一对单复根$r_{1,2} = \alpha \pm \beta\mathrm{i}$    & 给出两项：$e^{\alpha{x}}(C_1\cos\beta{x}+C_2\sin\beta{x})$                             \\
        \hline
        $k$重实根$r$                                        & 给出$k$项：$e^{rx}(C_1+C_2x+\dots+C_kx^{k-1})$                                         \\
        \hline
        一对$k$重复根$r_{1,2} = \alpha \pm \beta\mathrm{i}$ & 给出$2k$项：\tabincell{c}{$e^{\alpha{x}} \big[(C_1+C_2x+\dots+C_kx^{k-1})\cos\beta{x}$ \\ $+ (D_1+D_2x+\dots+D_kx^{k-1})\sin\beta{x} \big]$} \\
        \hline
    \end{tabular}
\end{table}
```

#### \xrowht

```latex
\begin{table}[htbp!]
    \centering
    \begin{tabular}{|c|c|}
        \hline\xrowht{25pt}
        $\displaystyle\int{\tan{x}\d x} = -\ln{|\cos{x}|}+C$                                  & $\displaystyle\int{\cot{x}\d x} = \ln{|\sin{x}|}+C$                                       \\
        \hline\xrowht{25pt}
        $\displaystyle\int{\sec{x}\d x} = \ln{|\sec{x}+\tan{x}|}+C$                           & $\displaystyle\int{\csc{x}\d x} = \ln{|\csc{x}-\cot{x}|}+C$                               \\
        \hline\xrowht{25pt}
        $\displaystyle\int{\frac{1}{a^2+x^2}\d x} = \frac{1}{a}\arcsin{\frac{x}{a}}+C$        & $\displaystyle\int{\frac{1}{x^2-a^2}\d x} = \frac{1}{2a}\ln{\Big|\frac{x-a}{x+a}\Big|}+C$ \\
        \hline\xrowht{25pt}
        $\displaystyle\int{\frac{1}{\sqrt{x^2+a^2}}\d x} = \ln{\Big(x+\sqrt{x^2+a^2}\Big)}+C$ & $\displaystyle\int{\frac{1}{\sqrt{a^2-x^2}}\d x} = \arcsin{\frac{x}{a}}+C$                \\
        \hline\xrowht{25pt}
        $\displaystyle\int{\frac{1}{\sqrt{x^2-a^2}}\d x} = \ln{\Big|x+\sqrt{x^2-a^2}\Big|}+C$ &                                                                                           \\
        \hline
    \end{tabular}
\end{table}
```

### 自定义环境

```latex
%  cases 环境
\begin{ca}              % 默认 1 倍行高
    x + y = 1 \\
    x - y = 0
\end{ca}

% 自定义行高的 cases 环境
\begin{ca}[1.5]
    x + y = 1 \\
    x - y = 0
\end{ca}

% 自定义行高的 vmatrix 环境
\begin{vx}[1.5]
    a & b \\
    c & d
\end{vx}

自定义命令只定义了 cases 和 vmatrix，有需要可自定义：pmatrix、bmatrix……
```

### Mathematica

注：该命令的定义写在`package.tex`中，使用如下

```latex
\begin{lstlisting}
    Plot[{0.5^x, 2^x, 5^x, 7^x}, {x, -E, E}, PlotLegends -> "Expressions"]
\end{lstlisting}
```

### 添加自定义命令

在 `config/custom.tex`中，添加你的命令，类似：

```latex
\newcommand{\yourcmd}[1]{定义内容}
```

## 配置说明

### 修改定理环境

编辑 `config/_config.tex`，修改引入的定理环境文件：

```latex
% 带框英文
\input{\path/theorem1.tex}

% 带框中文
\input{\path/theorem1_zh.tex}

% 无框英文
\input{\path/theorem0.tex}

% 无框中文
\input{\path/theorem0_zh.tex}
```

### 修改封面

编辑 `config/_config.tex`，只需修改 `\myIndex` 的值：

```latex
% 0: 默认封面
% 1, 2, 3: 预设的三种封面
\def\myIndex{0}
```

| myIndex 值 | 封面类型   |
| ---------- | ---------- |
| 0          | 默认封面   |
| 1          | 封面样式 1 |
| 2          | 封面样式 2 |
| 3          | 封面样式 3 |

模板会自动判断 `myIndex` 的值并引入对应的封面文件

### 修改文章信息

在 `config/_config.tex` 中修改：

```latex
\def\myTitle{你的标题}
\def\myAuthor{作者名称}
\def\myDateCover{\today}
\def\myForeword{前言标题}
\def\myForewordText{前言内容...}
\def\mySubheading{副标题}
```

### 添加新章节

1. 创建文件夹 `chap2/`
2. 创建文件 `chap2/chap.tex`，使用以下模板：

```latex
\ifx\allfiles\undefined
\documentclass[12pt, a4paper, oneside, UTF8]{ctexbook}
\def\path{../config}
\input{../config/_config}
\begin{document}
%\input{../config/cover}        % 这行注释与否，决定单章编译时是否编译封面，通常不需要
\else
\fi

\chapter{章节标题}

% 你的内容...

\ifx\allfiles\undefined
\end{document}
\fi
```

3. 在 `main.tex` 中添加：

```latex
\include{chap2/chap}
```

## 宏包

模板已包含以下常用宏包：

- `amsmath`, `amssymb`, `amsthm` - 数学公式与定理
- `graphicx` - 图片
- `geometry` - 页面布局
- `hyperref` - 超链接
- `xcolor` - 颜色
- `fancyhdr` - 页眉页脚
- `listings` - 代码
- `enumitem` - 列表
- `ctexbook` - 中文支持
- `esint` - 积分符号

## 示例文档

- `chap0/chap.tex` - 模板使用完整示例
- `chap1/chap.tex` - 数学公式与矩阵示例

直接编译 `main.tex` 即可查看效果！

## 许可

本模板可供任何人学习和使用。

