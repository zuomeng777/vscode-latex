# vscode-latex
vscode 配置 latex - windows


**步骤1.LeX Live下载与安装**
下载地址：https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/
<img width="1396" height="750" alt="image" src="https://github.com/user-attachments/assets/d1487d2e-9950-49e7-bc05-ed778f573119" />
下载好之后，双击打开，并找到**install-tl-windows** 文件，右键**以管理员身份运行**
<img width="622" height="539" alt="image" src="https://github.com/user-attachments/assets/b5f1285d-e287-41ef-a230-2f81bf2a9fd3" />

按照指示下载就好了，注意修改路径

<img width="331" height="376" alt="image" src="https://github.com/user-attachments/assets/d1b1a9b2-5689-456e-86ff-3d55a0502317" />

安装时，下图过程时间很长，耐心等待

<img width="592" height="419" alt="image" src="https://github.com/user-attachments/assets/87d141c3-2811-45ca-a505-24fcfafca967" />

win + R 打开终端，输入：xelatex -v 进行验证

<img width="1113" height="626" alt="image" src="https://github.com/user-attachments/assets/9bd2f21c-664c-40d5-b6b8-260a49230409" />

**步骤2.VScode安装**
官网：https://code.visualstudio.com/
按照提示下载即可。

**步骤3.安装插件并配置环境**
打开VScode，点击Extension--->输入"latex workshop"--->点击install
<img width="1413" height="933" alt="image" src="https://github.com/user-attachments/assets/bc0f2b90-2c9f-4fec-909b-011f931e5a7b" />

打开设置，进行latex环境配置

<img width="1413" height="933" alt="image" src="https://github.com/user-attachments/assets/5d5153f9-7cb3-40aa-a436-bd6287b9f9fc" />
<img width="1413" height="933" alt="image" src="https://github.com/user-attachments/assets/ebcb87d0-dbf6-48bd-a985-f5410eea1334" />
<img width="2029" height="349" alt="Snipaste_2026-11-23_16-04-26" src="https://github.com/user-attachments/assets/11e50c81-3471-4a48-a40c-7cc4865c8a98" />


文件里的内容一开始是空的。然后可以将下列代码加入进去
```
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
**步骤4 .tex文件编译**
找到.tex结尾的文件，然后按照下图编译。
<img width="712" height="776" alt="Snipaste_2026-11-23_16-08-45" src="https://github.com/user-attachments/assets/497122d1-a904-4fe2-aca3-63b543e8ff98" />
左下角将会显示编译进程，显示“√”则编译成功。
