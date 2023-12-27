# XJTU Beamer Template with annotated equations

- This is a general LaTeX Beamer template that I use for presentations. It is based on [this XJTU beamer template](https://www.overleaf.com/latex/templates/xjtu-beamer-theme/ddhzxgwqbvsy).
- On the bases of the original template, I have made some modifications to make it match my preferences.

## Main Changes

- I replaced the titles, footnotes, etc. of each slide with `PingFang SC` font.
- Apart from `xjtu.bst` bib style file, I provide support to `informs2014.bst` bib style file. The corresponding modification is made in `silde.tex`.

## Usage

- The main file is `slide.tex`. You can modify the content of each slide in `slide.tex`.
- See the sample `.pdf` in [this XJTU beamer template](https://www.overleaf.com/latex/templates/xjtu-beamer-theme/ddhzxgwqbvsy) for more details on how to use it.

### 环境配置

Windows操作系统，使用 `VSCode IDE` + `Latex Workshop by James Yu`插件 + `TexLive2023` ，

Windows环境变量安装python，以及安装[pygments](https://pygments.org/)，用于代码高亮。

### 致谢

本仓库模板基于这个包含公式注释功能的XJTU beamer 模板[annotate-equations-example](https://github.com/hjnnjh/annotate-equations-example)，因为我还没学习怎么使用GitHub的fork和pull这些的协作功能，就只能重新建了个仓库，基本上和[annotate-equations-example](https://github.com/hjnnjh/annotate-equations-example)仓库是一样的，改进的一些功能有：

1. 添加了 `.vscode`文件夹，放置VSCode工作区环境配置文件 `settings.json`，这个配置是参考的[XJTU Thesis Latex模板](https://github.com/obster-y/XJTU-thesis)的配置，但是我还没完全看懂。实现了一键清理多余文件的功能；
2. 修复了[annotate-equations-example](https://github.com/hjnnjh/annotate-equations-example)在Windows系统上编译缺少Mac自带的字体的问题，在 `slide.tex`文件里面注释掉了下面这两行：

```
\setsansfont{PingFang SC} % make sure your system has this font
\setCJKsansfont{STSongti-SC-Bold} % Chinese font, make sure your system has this font
```

3. 代码块高亮功能[minted](https://ctan.org/pkg/minted)，这个算不上改进，只是对环境配置做了更加详细的说明，这块去网上找前人资料花了我好多时间，过程中发现 `a. texstudio编辑器对环境路径支持配置似乎比vscode 要简单且好用`，`b.在CTAN网址上搜minted搜出来几个像listings、codebox、highlightlatex这些高亮的插件但是都没有minted强大、开发活跃`，找到展示伪代码[Pseudo](https://ctan.org/topic/pseudocode)的库，这里面[pseudo](https://ctan.org/pkg/pseudo)（学习库一是系统地看PDF文档，二是看github的readme入门）看着比较新。幸好最后Google搜关键词 `windows vscode安装 pygmentize`弄出来这个教程[VSCode LaTeX支持minted](https://blog.csdn.net/weixin_39278265/article/details/126907724)，只有这个教程最靠谱,需要在vscode中ctrl+shift+p调出：Python: Select Interpreter，选择自己的LaTeX项目，然后选择自己刚刚装Pygments库所在的conda(或者是python)环境,最后一步在windows**系统**环境变量里添加路径（注意环境变量是系统环境变量，不是用户环境变量；更改系统环境变量后电脑可以不重启，重启一下vscode就行；如果以后遇到要更改用户环境变量的话，就要重启电脑才生效）。我是用Everything软件搜索pygmentize.exe,然后我在系统变量->Path里面加的是pygmentize.exe所在的路径： `C:\Users\t\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.11_qbz5n2kfra8p0\LocalCache\local-packages\Python311\Scripts`，添加环境变量之前这个python我是从window的microsoft应用商店下载的，是我电脑命令行默认的python,下载完python11就打开powershell执行命令 `pip install Pygments` 以及 `pip install pygments[windows-terminal]`。

本模板更原始的来源链接一并在此列出：

* 模板可以追溯到[分享一个清华主题的beamer模版-2015年7月](https://www.latexstudio.net/archives/4051.html)
* 清华图书馆LaTeX入门讲座的Beamer:[thulib-latex-talk-活跃更新中](https://github.com/tuna/thulib-latex-talk)
* THU的模板到目前为止一直在活跃更新中：[THU Beamer](https://github.com/YangLaTeX/thubeamer)
* 第二代模板：[overleaf xjtu-beamer-theme-2022年上传](https://www.overleaf.com/latex/templates/xjtu-beamer-theme/ddhzxgwqbvsy)

## 编译方法

注意为了使`.vscode`工作空间配置`settings.json`生效，必须将本项目作为根目录在VSCode中打开[见VSCode官方教程User and Workspace Settings](https://code.visualstudio.com/docs/getstarted/settings#_workspace-settingsjson-location)。选择 `slide.tex`，然后点击侧栏tex插件图标，在 `COMMANDS`里面的 `Build LaTeX project`里面选择 `Recipe: latexmkbeamer`
或者在命令行切换到slide.tex所在文件夹，执行命令：

```
latexmk -xelatex -shell-escape slide.tex
```
## tex和pdf文件之间的正反向索引

在pdf内双击，以回到tex对应的位置；
在tex文件内按下快捷键`ctrl+alt+j`，或者鼠标右键菜单选择SyncTex from cursor，以转到pdf对应位置。

## 存在的不足

1. 缺少bib参考文献。[这个issue](https://github.com/st--/annotate-equations/issues/21)有讨论，问题尚未解决，猜测可能是用到的 `st--/annotate-equations`库和bibtex用xelatex之间不兼容，~~总之目前尚无法添加参考文献bib功能~~,见[Issue#1](https://github.com/txctxc/XJTU-Beamer-Template-with-annotated-equations/issues/1)。
2. 未添加表头和图名功能，还有许多其它的功能，其实在第二代模板里面[overleaf xjtu-beamer-theme-2022年上传](https://www.overleaf.com/latex/templates/xjtu-beamer-theme/ddhzxgwqbvsy)都有，后面会考虑怎么把这些功能加进来。
3. 若要实现VSCode在settings.json中配置使用外部SumatraPDF查看PDF，可以参考[这篇知乎的文章](https://zhuanlan.zhihu.com/p/166523064)。
```json
{
 //------------------------------LaTeX 配置----------------------------------
    // 设置是否自动编译
    "latex-workshop.latex.autoBuild.run":"never",
    //右键菜单
    "latex-workshop.showContextMenu":true,
    //从使用的包中自动补全命令和环境
    "latex-workshop.intellisense.package.enabled": true,
    //编译出错时设置是否弹出气泡设置
    "latex-workshop.message.error.show": false,
    "latex-workshop.message.warning.show": false,
    // 编译工具和命令
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    // 用于配置编译链
    "latex-workshop.latex.recipes": [
        {
            "name": "XeLaTeX",
            "tools": [
                "xelatex"
            ]
        },
        {
            "name": "PDFLaTeX",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "BibTeX",
            "tools": [
                "bibtex"
            ]
        },
        {
            "name": "LaTeXmk",
            "tools": [
                "latexmk"
            ]
        },
        {
            "name": "xelatex -> bibtex -> xelatex*2",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "pdflatex -> bibtex -> pdflatex*2",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        }
    ],
    //文件清理。此属性必须是字符串数组
    "latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk"
    ],
    //设置为onFaild 在构建失败后清除辅助文件
    "latex-workshop.latex.autoClean.run": "onFailed",
    // 使用上次的recipe编译组合
    "latex-workshop.latex.recipe.default": "lastUsed",
    // 用于反向同步的内部查看器的键绑定。ctrl/cmd +点击(默认)或双击
    "latex-workshop.view.pdf.internal.synctex.keybinding": "double-click",



    //使用 SumatraPDF 预览编译好的PDF文件
    // 设置VScode内部查看生成的pdf文件
    "latex-workshop.view.pdf.viewer": "external",
    // PDF查看器用于在\ref上的[View on PDF]链接
    "latex-workshop.view.pdf.ref.viewer":"auto",
    // 使用外部查看器时要执行的命令。此功能不受官方支持。
    "latex-workshop.view.pdf.external.viewer.command": "F:/SumatraPDF/SumatraPDF.exe", // 注意修改路径
    // 使用外部查看器时，latex-workshop.view.pdf.external.view .command的参数。此功能不受官方支持。%PDF%是用于生成PDF文件的绝对路径的占位符。
    "latex-workshop.view.pdf.external.viewer.args": [
        "%PDF%"
    ],
    // 将synctex转发到外部查看器时要执行的命令。此功能不受官方支持。
    "latex-workshop.view.pdf.external.synctex.command": "F:/SumatraPDF/SumatraPDF.exe", // 注意修改路径
    // latex-workshop.view.pdf.external.synctex的参数。当同步到外部查看器时。%LINE%是行号，%PDF%是生成PDF文件的绝对路径的占位符，%TEX%是触发syncTeX的扩展名为.tex的LaTeX文件路径。
    "latex-workshop.view.pdf.external.synctex.args": [
        "-forward-search",
        "%TEX%",
        "%LINE%",
        "-reuse-instance",
        "-inverse-search",
        "\"F:/Microsoft VS Code/Code.exe\" \"F:/Microsoft VS Code/resources/app/out/cli.js\" -r -g \"%f:%l\"", // 注意修改路径
        "%PDF%"
    ]
}
```
