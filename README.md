# 在 Windows 上配置 VS Code LaTeX 环境

## 1. 下载并安装 TeX Live

从[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)下载 TeX Live 镜像。

<img width="1047" alt="清华镜像站的 TeX Live 下载页面" src="https://github.com/user-attachments/assets/d1487d2e-9950-49e7-bc05-ed778f573119" />

下载完成后，双击打开镜像，找到 `install-tl-windows`，右键选择**以管理员身份运行**。

<img width="467" alt="Windows 安装程序所在位置" src="https://github.com/user-attachments/assets/b5f1285d-e287-41ef-a230-2f81bf2a9fd3" />

按照提示安装，并在安装界面按需修改安装路径。

<img width="248" alt="TeX Live 安装路径设置" src="https://github.com/user-attachments/assets/d1b1a9b2-5689-456e-86ff-3d55a0502317" />

下图所示的安装阶段耗时较长，请耐心等待。

<img width="444" alt="TeX Live 安装进度" src="https://github.com/user-attachments/assets/87d141c3-2811-45ca-a505-24fcfafca967" />

按 `Win + R`，输入 `cmd` 并回车。在命令提示符中运行 `xelatex -v`，确认安装成功。

<img width="835" alt="XeLaTeX 版本验证结果" src="https://github.com/user-attachments/assets/9bd2f21c-664c-40d5-b6b8-260a49230409" />

## 2. 安装 VS Code

前往 [VS Code 官网](https://code.visualstudio.com/)下载安装程序，按提示完成安装。

## 3. 安装并配置 LaTeX Workshop

打开 VS Code，在**扩展（Extensions）**面板中搜索 `LaTeX Workshop`，点击**安装（Install）**。

<img width="1060" alt="VS Code 扩展中的 LaTeX Workshop" src="https://github.com/user-attachments/assets/bc0f2b90-2c9f-4fec-909b-011f931e5a7b" />

打开 VS Code 设置，按下图找到并打开 `settings.json`。

<img width="1060" alt="打开 VS Code 设置" src="https://github.com/user-attachments/assets/5d5153f9-7cb3-40aa-a436-bd6287b9f9fc" />

<img width="1060" alt="在设置中找到 LaTeX Workshop" src="https://github.com/user-attachments/assets/ebcb87d0-dbf6-48bd-a985-f5410eea1334" />

<img width="1522" alt="打开 settings.json" src="https://github.com/user-attachments/assets/11e50c81-3471-4a48-a40c-7cc4865c8a98" />

如果 `settings.json` 为空，可以粘贴以下配置。

<details>
<summary>展开查看 settings.json 配置</summary>

```jsonc
{
    "latex-workshop.latex.autoBuild.run": "never",
    "latex-workshop.showContextMenu": true,
    "latex-workshop.intellisense.package.enabled": true,
    "latex-workshop.message.error.show": false,
    "latex-workshop.message.warning.show": false,
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
        },
    ],
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
    "latex-workshop.latex.autoClean.run": "onFailed",
    "latex-workshop.latex.recipe.default": "lastUsed",
    "latex-workshop.view.pdf.internal.synctex.keybinding": "double-click"
}
```

</details>

## 4. 编译 `.tex` 文件

打开要编译的 `.tex` 文件，按下图操作。

<img width="534" alt="在 VS Code 中编译 LaTeX 文件" src="https://github.com/user-attachments/assets/497122d1-a904-4fe2-aca3-63b543e8ff98" />

在窗口左下角查看编译进度。出现 `√` 表示编译成功。
