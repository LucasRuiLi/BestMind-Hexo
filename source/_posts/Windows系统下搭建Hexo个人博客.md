---
title: Windows系统下搭建Hexo个人博客
date: 2017/8/27 1:33:48
categories: 
- Hexo
tags:
- hexo
- 博客
comments: true
---
## 前提
### 依赖环境

* [Git](https://git-scm.com/)
* [Node.js](https://nodejs.org/)

直接单击链接进入下载最新版的 Git 和 Node.js 安装包,下载完毕之后安装

### 安装Hexo
在 CMD 或 PoweShell <font color=skyblue>( 建议在管理员权限下打开,下同 )</font>中键入
```bash
npm install -g hexo-cli
```

## 建站
### 初始化
在 CMD 或 PoweShell 中依次键入以下三条命令<font color=orange>( `<folder>` 替换为网站文件夹路径 )</font>
```bash
hexo init <folder>
cd <folder>
npm install
```
初始化完成后，指定文件夹的目录如下：

	.
	...._config.yml
	....package.json
	....scaffolds
	....source
	.  ...._drafts
	.  ...._posts
	....themes

### _config.yml
网站的 配置 信息，您可以在此配置大部分的参数。
### package.json
应用程序的信息。
### scaffolds
模版 文件夹。
### source
资源文件夹是存放用户资源的地方。
### themes
主题 文件夹。
## 配置
网站配置文件为Hexo工作目录下的_config.yml文件
<font color=skyblue>( * 为必填选项,其余按需更改 )</font>
### 网站
|参数|描述|
|---|---|
|title|网站标题|
|subtitle|网站副标题|
|description|网站描述|
|author|您的名字|
|language|网站使用的语言|
|timezone|网站时区|
### 网址
|参数|描述|默认值|
|---|---|---|
|*url|网址| |
|*root|网站根目录| |
|permalink|文章的永久链接格式|:year/:month/:day/:title/|
|permalink_defaults|永久链接中各部分的默认值| |
<font color=skyblue>如果您的网站存放在子目录中，例如 `http://yoursite.com/blog`，则请将您的 `url` 设为 `http://yoursite.com/blog` 并把 `root` 设为 `/blog/`。</font>
### 目录
|参数|描述|默认值|
|---|---|---|
|source_dir|资源文件夹，这个文件夹用来存放内容|source|
|public_dir|公共文件夹，这个文件夹用于存放生成的站点文件|public|
|tag_dir|标签文件夹|tags|
|archive_dir|归档文件夹|archives|
|category_dir|分类文件夹|categories|
|code_dir|Include code 文件夹|downloads/code|
|i18n_dir|国际化（i18n）文件夹|:lang|
|skip_render|跳过指定文件的渲染，您可使用 glob 表达式来匹配路径。| |

### 文章
|参数|描述|默认值|
|---|---|---|
|new_post_name|新文章的文件名称|:title.md|
|default_layout|预设布局|post|
|auto_spacing|在中文和英文之间加入空格	|false|
|titlecase|把标题转换为 title case|false|
|external_link|在新标签中打开链接|true|
|filename_case|把文件名称转换为小写或大写|0|
|render_drafts|显示草稿|false|
|post_asset_folder|启动 Asset 文件夹|false|
|relative_link|把链接改为与根目录的相对位址|false|
|future|显示未来的文章|true|
|highlight|代码块的设置| |

### 分类 & 标签
|参数|描述|默认值|
|---|---|---|
|default_category|默认分类|uncategorized|
|category_map|分类别名||
|tag_map|标签别名||
### 日期 / 时间格式
|参数|描述|默认值|
|---|---|---|
|date_format|日期格式|YYYY-MM-DD|
|time_format|时间格式|H:mm:ss|
### 分页
|参数|描述|默认值|
|---|---|---|
|per_page|每页显示的文章量(0 = 关闭分页功能)|10|
|pagination_dir	分页目录	|page|
### 扩展
|参数|描述|
|---|---|
|theme|当前主题名称。值为false时禁用主题|
|deploy|部署部分的设置|
## 命令
<font color=skyblue>( * 常用命令 )</font>
### init
```bash
hexo init [folder]
```
新建一个网站。如果没有设置 folder ，Hexo 默认在目前的文件夹建立网站。

### new
```bash
hexo new [layout] <title>
```
新建一篇文章。如果没有设置 layout 的话，默认使用 _config.yml 中的 default_layout 参数代替。如果标题包含空格的话，请使用引号括起来。

### generate *
```bash
hexo generate
```
生成静态文件。

|选项|描述|
|---|---|
|-d, --deploy|文件生成后立即部署网站|
|-w, --watch|监视文件变动|

该命令可以简写为
```bash
hexo g
```
### publish *
```bash
hexo publish [layout] <filename>
```
发表草稿。

### server *
```bash
hexo server
```
启动服务器。默认情况下，访问网址为： http://localhost:4000/。

|选项|描述|
|---|---|
|-p, --port|重设端口|
|-s, --static|只使用静态文件|
|-l, --log|启动日记记录，使用覆盖记录格式|
### deploy *
```bash
hexo deploy
```
部署网站。

|参数|描述|
|---|---|
|-g, --generate|部署之前预先生成静态文件|
该命令可以简写为：
```bash
hexo d
```
### render
```bash
hexo render <file1> [file2] ...
```bash
渲染文件。

|参数|描述|
|---|---|
|-o, --output|设置输出路径|
### migrate
```bash
hexo migrate <type>
```
从其他博客系统 迁移内容。

### clean
```bash
hexo clean
```
清除缓存文件 (db.json) 和已生成的静态文件 (public)。

在某些情况（尤其是更换主题后），如果发现您对站点的更改无论如何也不生效，您可能需要运行该命令。

### list
```bash
hexo list <type>
```
列出网站资料。

### version
```bash
hexo version
```
显示 Hexo 版本。

## 选项
### 安全模式
```bash
hexo --safe
```
在安全模式下，不会载入插件和脚本。当您在安装新插件遭遇问题时，可以尝试以安全模式重新执行。

### 调试模式
```bash
hexo --debug
```
在终端中显示调试信息并记录到 debug.log。当您碰到问题时，可以尝试用调试模式重新执行一次，并 提交调试信息到 GitHub。

### 简洁模式
```bash
hexo --silent
```
隐藏终端信息。

### 自定义配置文件的路径
```bash
hexo --config custom.yml
```
自定义配置文件的路径，执行后将不再使用 _config.yml。

### 显示草稿
```bash
hexo --draft
```
显示 source/_drafts 文件夹中的草稿文章。

### 自定义 CWD
```bash
hexo --cwd /path/to/cwd
```
自定义当前工作目录（Current working directory）的路径。


---
Reference : [Hexo Docs](https://hexo.io/docs/)

