# [一个LaTeX的数学笔记模板](https://zhuanlan.zhihu.com/p/604236564)

## 使用	

### `main.tex` 主文件

```latex
\def\allfiles{}
\documentclass[12pt, a4paper, oneside, UTF8]{ctexbook}
\def\path{./config}
\input{config/_config}
\begin{document}
\include{config/cover}

\include{chap0/chap}
% \include{chap1/chap}
% \include{chap2/chap}
% ...通过上述方式引入对应章节

\end{document}
```

### `config/_config.tex` 配置文件

```latex
% 包以及配置【有需要添加其他包以及配置，添加在 package.tex 文件中】
\input{\path/package.tex}

% 定理环境，内置两种定理环境以及中英文版本，可通过修改引入文件改变
% theorem1.tex 及 theorem1_zh.tex / theorem0.tex 以 theorem0_zh.tex
\input{\path/theorem1.tex}

% 自定义命令【自定义命令，添加在 custom.tex 文件中】
\input{\path/custom.tex}

% 封面，可选 0 -> 3 四种， 0 为默认封面，无需引入其他文件
\def\myIndex{0}
% 不为 0 时，需引入下方的封面配置文件，取消注释即可
% \input{\path/cover_package_\myIndex.tex}

% ######################## 模板配置信息 ##########################

% #标题
\def\myTitle{一份 \LaTeX 的笔记模板}

% #作者名称
\def\myAuthor{Guo}

% #封面页面显示日期
\def\myDateCover{\today}

% #前言页面显示日期
\def\myDateForeword{2023 年 1 月 28 日}

% #前言标题
\def\myForeword{前言}

% 前言内容
\def\myForewordText{
    这里写前言内容
    
    第二行
}

% 副标题
\def\mySubheading{格物致知，慎思明辨}
```

### `config/custom.tex` 自定义命令

```latex
% 微分符号
\def\d{\mathrm{d}}

% 实数集
\def\R{\mathbb{R}}

% 加粗
\newcommand{\bs}[1]{\boldsymbol{#1}}

% 向量
\newcommand{\ora}[1]{\overrightarrow{#1}}

% 空行
\newcommand{\myspace}[1]{\par\vspace{#1\baselineskip}}

% 依赖 \usepackage{stackengine} 调整表格高度
\newcommand{\xrowht}[2][0]{\addstackgap[.5\dimexpr#2\relax]{\vphantom{#1}}}

% 自定义行高的 cases 和 vmatrix 环境
\newenvironment{ca}[1][1]{\linespread{#1} \selectfont \begin{cases}}{\end{cases}}
\newenvironment{vx}[1][1]{\linespread{#1} \selectfont \begin{vmatrix}}{\end{vmatrix}}

% 表格内长内容换行
\newcommand{\tabincell}[2]{\begin{tabular}{@{}#1@{}}#2\end{tabular}}

% 平行符号 //
\newcommand{\pll}{\kern 0.56em/\kern -0.8em /\kern 0.56em}

% 散度 旋度
\newcommand{\dive}[1][F]{\mathrm{div}\;\bs{#1}}
\newcommand{\rotn}[1][A]{\mathrm{rot}\;\bs{#1}}
```

### `chap[number]/chap.tex` 章节文件

```latex
\ifx\allfiles\undefined
\documentclass[12pt, a4paper, oneside, UTF8]{ctexbook}
\def\path{../config}
\input{../config/_config}
\begin{document}
% \input{../config/cover}        % 注释与否决定单独编译时，是否编译封面
\else
\fi
%  正文
%  正文
%  正文
\ifx\allfiles\undefined
\end{document}
\fi
```