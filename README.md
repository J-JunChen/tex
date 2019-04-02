# tex论文编写技巧和制作这样。。

## ubuntu18.04 安装Tex-live 和 Texstudio
- 1、安装Tex-Live
```sudo apt-get install texlive-full```

- 2、安装XeLaTeX编译引擎（听说XeLaTex对中文比较友好）
``` sudo apt-get install texlive-xetex```

- 3、安装中文支持包xeCjk
```sudo apt-get install texlive-lang-chinese```

- 4、安装图形化界面Texstudio
```sudo apt-get install texstudio```

### 安装完成后，在Texstudio下配置默认编译器为XeLaTex
- 具体在Studio的 Options -> Configure TeXstudio -> build -> Default Compiler

### 配置中文环境
- Options -> Configure TeXstudio -> General -> Language -> zh-CN 

## VsCode配合Tex-live，并编写Tex
- 其实VsCode取代的功夫就是Texstudio所做的工作，当然各有所效益。
	
- 首先，根据以上1、 2、 3、步安装所需

- 4、在VsCode 只需要安装扩展 “LaTex Workshop”即可

- 5、配置LaTex Workshop，首先是快捷键

	- 5.1、latex-workshop.build 命令为Tex编译命令，我设置的快捷键成 F6

	- 5.2、latex-workshop.view 命令为Tex查看PDF格式命令，我设置的快捷键为 F7 

- 6、再者配置settings.json

	- 6.1、由于上面下载的Tex编译引擎是 XeLaTex，所以如下配置
	```
	"latex-workshop.latex.tools": [
        {
            // 编译工具和命令
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "%DOC%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
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
	```
	
	- 6.2 根绝 [知乎玩家](https://zhuanlan.zhihu.com/p/38178015) 的配置，添加编译链之类的，
	```
	"latex-workshop.latex.recipes": [
        {
            "name": "xelatex",
            "tools": [
                "xelatex"
            ]
        },
        {
            "name": "xe->bib->xe->xe",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        }
    ],
	```

### 之后就可以愉快地在VScode玩砖Tex了吧，呀嚯嚯～
