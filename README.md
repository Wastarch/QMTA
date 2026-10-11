# 量子力学：理论与应用

> Quantum Mechanics: Theory and Application

《量子力学：理论与应用》讲义的 LaTeX 源代码，基于 [一个LaTeX的数学笔记模板](https://zhuanlan.zhihu.com/p/604236564) 编写。


## 章节结构

| 文件夹 | 章节 | 内容 |
| --- | --- | --- |
| `chap0` | 第零章 | 数学基础 |
| `chap1` | 第一章 | 重要实验及重要物理常数 |
| `chap2` | 第二章 | 波函数与薛定谔方程 |
| `chap3` | 第三章 | 一维定态问题 |
| `chap4` | 第四章 | 量子力学中的力学量 |
| `chap5` | 第五章 | 态和力学量的表象 |
| `chap6` | 第六章 | 中心力场 |
| `chap7` | 第七章 | 微扰论 |
| `chap8` | 第八章 | 自旋与全同粒子 |

其中第一至第八章归入「第一部分 理论基础」（由 `chap1/chap.tex` 中的 `\part{理论基础}` 开启）。

## 环境要求

- TeX 发行版：推荐 [TeX Live](https://tug.org/texlive/)（完整安装），需要支持中文的 `ctex` 宏集
- 编译引擎：**XeLaTeX**（文档类为 `ctexbook`，编码 UTF-8）
- 主要依赖宏包：`amsmath` / `amsthm` / `amssymb`、`tcolorbox`、`physics`、`graphicx`、`fancyhdr`、`geometry`、`hyperref`、`listings`、`stackengine`、`esint`、`yhmath` 等（完整清单见 `config/package.tex`）

## 编译方法

### 整书编译

```bash
xelatex main.tex
xelatex main.tex   # 再编译一次以生成正确的目录与交叉引用
```

输出 `main.pdf`（含封面、前言、目录及全部章节）。

### 单章独立编译

每个 `chapN/chap.tex` 都可以脱离主文件单独编译（正文用 `\ifx\allfiles\undefined` 包裹，单独编译时定义了独立的导言区）：

```bash
cd chap3
xelatex chap.tex
xelatex chap.tex
```

注释或放开 `chapN/chap.tex` 中的 `% \input{../config/cover}` 可控制单章编译时是否带封面。

### 在编辑器中编译

- **TeXstudio / TeXworks**：将默认编译器设为 XeLaTeX 后直接编译 `main.tex`
- **VS Code + LaTeX Workshop**：默认 recipe 已含 `xelatex`，直接构建 `main.tex` 即可

## 目录结构

```text
.
├── main.tex              # 主文件：引入配置、封面与各章节
├── main.pdf              # 整书编译产物
├── config/               # 配置目录
│   ├── _config.tex       # 总配置：串联各配置文件、定义书名/作者/日期/前言
│   ├── package.tex       # 宏包引入、页面布局、代码高亮、页眉页脚等全局设置
│   ├── theorem.tex       # 定理/定义/证明等彩色盒子环境（tcolorbox）
│   ├── custom.tex        # 自定义命令
│   ├── cover.tex         # 封面 + 前言 + 目录 + 页眉页脚版式
│   ├── cover_text.tex    # 封面版式（\maketitle 的具体实现）
│   └── cover_package.jpg # 封面图片
├── chap0/ … chap8/       # 各章节正文（chap.tex）
├── figure/               # 全局图片资源
└── chap1/figure/         # 章内图片资源
```

`main.tex` 中通过 `\include` 依次引入章节，注释掉对应行即可只编译部分章节：

```latex
\include{chap0/chap} % 数学基础
\include{chap1/chap}
\include{chap2/chap}
% ...
```


## 致谢

模板来自专栏文章：[一个LaTeX的数学笔记模板](https://zhuanlan.zhihu.com/p/604236564)，在此表示感谢。
