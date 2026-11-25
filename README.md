# 中文数学建模论文 LaTeX 模板

一个适用于各类中文数学建模比赛的通用 LaTeX 论文模板。模板基于 XeLaTeX 编译，支持中文排版、数学公式、表格、参考文献和附录。

## 主要特点

- 适用于全国大学生数学建模竞赛及其他中文数学建模比赛
- 支持中文字体和中文数学建模论文排版
- 使用 XeLaTeX，中文兼容性较好
- 支持 BibTeX 参考文献管理
- 包含摘要、问题重述、问题分析、模型假设、符号说明、模型建立、结果分析、模型评价和结论等常用结构
- 已配置 VS Code + LaTeX Workshop 编译流程

## 项目结构

```text
.
├── paper/
│   ├── template.tex       # 论文主文件
│   ├── ref.bib            # 参考文献数据库
│   ├── cumcmthesis.cls    # 论文模板样式文件
│   └── gbt7714-numerical.bst
├── .vscode/
│   └── settings.json      # VS Code 编译配置
└── README.md
```

## 环境要求

- TeX Live 2023 或更高版本
- XeLaTeX
- BibTeX
- 推荐使用 Visual Studio Code 和 LaTeX Workshop 插件

Windows 用户可以安装 [TeX Live](https://www.tug.org/texlive/)，然后在 VS Code 中安装 `LaTeX Workshop` 插件。

## 快速开始

1. 克隆本项目：

   ```bash
   git clone https://github.com/你的用户名/你的仓库名.git
   cd 你的仓库名
   ```

2. 用 VS Code 打开项目根目录。

3. 编辑 `paper/template.tex`，替换标题、摘要、正文和公式。

4. 编辑 `paper/ref.bib`，加入实际使用的参考文献。

5. 在 VS Code 中执行：

   ```text
   LaTeX Workshop: Build LaTeX project
   ```

模板会自动执行：

```text
XeLaTeX → BibTeX → XeLaTeX → XeLaTeX
```

生成的 PDF 文件位于 `paper/template.pdf`。

## 命令行编译

进入 `paper` 目录后运行：

```bash
xelatex -interaction=nonstopmode template.tex
bibtex template
xelatex -interaction=nonstopmode template.tex
xelatex -interaction=nonstopmode template.tex
```

如果没有使用参考文献，也可以只运行：

```bash
xelatex template.tex
```

## 参考文献用法

在 `ref.bib` 中添加文献，例如：

```bibtex
@article{zhang2024,
  author  = {张三 and 李四},
  title   = {数学建模方法研究},
  journal = {数学的实践与认识},
  year    = {2024},
  volume  = {54},
  number  = {1},
  pages   = {1--10}
}
```

在正文中引用：

```latex
相关研究表明，该方法具有较好的稳定性\cite{zhang2024}。
```

注意：引用键必须与 `.bib` 文件中的键完全一致。出现问号时，请重新执行一次 BibTeX 和两次 XeLaTeX。

## 图片和表格

建议将图片放在 `paper/figures/` 目录中，并使用相对路径引用：

```latex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.8\textwidth]{figures/result.pdf}
  \caption{计算结果}
  \label{fig:result}
\end{figure}
```

表格可以使用 `booktabs` 和 `tabularx`：

```latex
\begin{table}[htbp]
  \centering
  \caption{主要结果}
  \begin{tabular}{ccc}
    \toprule
    指标 & 模型一 & 模型二 \\
    \midrule
    结果 & 0.85 & 0.91 \\
    \bottomrule
  \end{tabular}
\end{table}
```

## 常见问题

### 中文显示为乱码

请确认 `template.tex` 和 `ref.bib` 使用 UTF-8 编码。在 VS Code 右下角点击当前编码，选择“以编码重新打开”或“使用 UTF-8 保存”。

### 引用显示为问号

确认正文中的 `\cite{key}` 与 `ref.bib` 中的文献键一致，然后按以下顺序重新编译：

```text
XeLaTeX → BibTeX → XeLaTeX → XeLaTeX
```

### 字体警告

模板默认使用 `SimSun`、`SimHei` 和 `Times New Roman`。如果系统没有对应字体，XeLaTeX 通常会使用替代字体。可以在 `template.tex` 中修改字体设置。

### 编译失败

建议检查：

- 编译器是否选择为 XeLaTeX
- 文件是否使用 UTF-8 编码
- 花括号是否成对出现
- 图片路径和文件名是否正确
- `.bib` 文件中的字段是否完整

## 使用建议

- 每次比赛建议复制一份模板后再开始写作。
- 将图片、数据和代码按模块放置，避免文件名包含空格或特殊字符。
- 正式提交前删除示例文献，并替换为真实参考文献。
- 统一使用英文半角括号、逗号和数学符号，减少编译错误。
- 提交前检查 PDF 页码、目录、图片清晰度、参考文献和匿名要求。

## 许可

本项目仅用于学习、教学和数学建模论文写作。使用时请遵守所在比赛的格式要求和提交规范。
