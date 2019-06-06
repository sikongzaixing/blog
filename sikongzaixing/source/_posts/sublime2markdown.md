---
title: Sublime Text 3 编写 Markdown
date: 2019-06-03 20:47:40
tags: Sublime
categories: Sublime
---

##### 安装插件 : 

​		常规安装 : Markdown Preview , Markdown Editing, Markdown Extended 

Windows: shift+ctrl+p   /  macOS :  shift+command+p 或者点击 Preference -> Package Control  调出命令面板,

再输入 install , 选择  Package Control: install package

##### 1、安装 [Markdown Preview](https://packagecontrol.io/packages/MarkdownPreview) 支持在浏览器中预览markdown文件

 			使用方式:  调出 Package Control 命令面板,输入 mdp ( markdown preview) , 来预览md 文件


​			 设置快捷键, Preference-> key Bindings User 

​			`{ "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"}  }`

​			设置语法高亮和mathjax支持 : Preference->Color Scheme 

​			mathjax支持(MathJax 是一个能将 LaTeX，MathML 和 AsciiMath 表示的数学式在现代浏览器网页上正确呈现现出来的开源 JavaScript 显示引擎),需要添加代码,如下:

​			Preference->Package Setting -> Markdown Preview -> Setting User :

	{
	    /*
	        Enable or not mathjax support.
	    */
	    "enable_mathjax": true,
	
	    /*
	        Enable or not highlight.js support for syntax highlighting.
	    */
	    "enable_highlight": true,
	}

##### 2、安装[Markdown Editing](https://packagecontrol.io/packages/MarkdownEditing) 调出 Package Control 命令面板,输入 mdi , 选择相应的命令.		

##### 3、安装 [MarkdownTOC](https://packagecontrol.io/packages/MarkdownTOC)   (table of content)   

​		编写 heading 较多的长文档，希望能够自动生成目录方便跳转，MarkdownTOC 可以帮助我们实现

​		插件配置在。Setting - User

```
{
  "default_autolink": true,            // 目录以链接形式呈现
  "default_bracket": "round",         //目录以链接形式呈现
  "default_depth": 0                  // 无限目录深度
}
```

##### 4、安装 [Markdown Extended](https://packagecontrol.io/packages/Markdown%20Extended)  让 Markdown 格式在 Sublime 中支持高亮

##### 5、安装 [MarkdownLivePreview](https://packagecontrol.io/packages/MarkdownLivePreview) :实时预览Markdown文件，左侧为md文件，右侧为预览结果。

​	可配合MarkdownEditing一起使用。修改如下:

​	Preferences -> Package Settings -> MarkdownLivePreview -> Settings 的设置的右侧加一条 "markdown_live_preview_on_open": true,`，重启sublime即可。

##### 6、安装  [LiveReload](https://packagecontrol.io/packages/LiveReload) 实时刷新网页

##### 7、[Table Editor](https://packagecontrol.io/packages/Table%20Editor) 制表神奇 键入表格是个体力活，Table Editor 可以帮助我们减轻工作量

##### 8、 [OmniMarkupPreviewer](https://packagecontrol.io/packages/OmniMarkupPreviewer) 提供了LaTex的数学公式渲染的支持，用浏览器打开以后支持浏览器的实时渲染和更新预览

```
{
    "renderer_options-MarkdownRenderer":
    {
        "extensions": ["tables", "fenced_code", "codehilite"],
    	"parser": "markdown",
    	"enabled_parsers": ["markdown"]
	}
}
```

-  <font color=rgb(0,255,255) size="4">以下解决方案转载自:</font> http://roux.top/2017/10/11/Markdown编辑器/
- **注意：**这个插件在配置完成后，有可能会出现无法使用，并且报错：
-  <font color="#dd0000">404错误预览...“buffer_id（29）无效（关闭或不支持的文件格式）</font>

> - 这里给出解决方案(上面的配置文件已经好了)：
>
>   > - 如上面的配置去掉了原文件 `"extensions": ["tables", "strikeout", "fenced_code", "codehilite"]`的**“strikeout”**
>   >
>   > - 找到python-markdown Sublime Text3的包。
>   >
>   >   > - Mac: `subl "/Users/<username>/Library/Application Support/Sublime Text 3/Packages/OmniMarkupPreviewer/OmniMarkupLib/Renderers/libs/mdx_strikeout.py"`

> > - 用以下makeExtension()方法替换方法：
> >   `def makeExtension(*args, **kwargs): return StrikeoutExtension(*args, **kwargs)`
> > - 保存，退出并重新加载升级文本。

> - <font color= rgb(255,255,200)>链接</font>：https://github.com/timonwong/OmniMarkupPreviewer/issues/85

- [OmniMarkupPreviewer]续：
  - 打开OmniMarkupPreviewer的默认配置文件Setting-Default
  - 查看参数：
    `"server_host": "127.0.0.1",` (开启预览服务的 IP 地址, 默认为 localhost)
    `"html_template_name": "github",` (预览使用的模板名称，默认为 Github)
    `"browser_command": [],` (预览默认为跟随系统默认浏览器，[“open”, “-a”, “Google Chrome”, “{url}”]亦可利用这样的格式进行指定)
    `"ignored_renderers": ["LiterateHaskellRenderer"],`(忽略/关闭的标记语言渲染器)
    `"mathjax_enabled": false,`(公式的渲染使用了MathJax库，所以需要在OmniMarkupPreviewer的设置中，将”mathjax_enabled”设置为“true”)

