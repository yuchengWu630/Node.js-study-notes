# npm - 入门

<br>

> 很幸福,我们能生活在中国,这样一个美丽的国家,既安全又自由.
> 所以导致我们和外界水深火热的地区不一样
> 基于这样的情况,我们在download外界的东西时,非常的不方便
> 感谢淘宝为我们撑起了异次元的镜像,让我们能愉快的download.

OK,总而言之就是npm默认的下载链接太慢,我们要换成淘宝提供的源镜像.

<br>


<br>

## npm - 学习换源

1. **临时使用**

```npm --registry https://registry.npm.taobao.org install(安装命令) express(要安装的模块)```

2. **持久使NPM用**

```npm config set registry https://registry.npm.taobao.org```
主要就是通过config配置registry的路由

3. **通过cnpm使用(推举)**
 
``` install -g cnpm --registry=https://registry.npm.taobao.org```
这个 -g 是在全局安装一个cnpm的模块,然后你要使用就直接
cnpm install(安装命令) express(需要安装的模块)

**这里要注意 因为我们使用nvm安装了很多个版本的node  所以安装cnpm在全局时,也只是将cnpm安装在你当前使用的node版本中**

<br>


<br>


## npm - 学习建立package.json


<br>


<br>



>* 每一个项目的根目录下,一般都有一个package.json,它是定义这个项目所需要的各种模块,以及项目的配置信息(比如名称,版本,许可证的元数据). ```npm install``` 命令根据这个配置文件下载所需要的模块,也就是配置环境.
>* 相反的在 ```npm install``` 所需要的文件后,也会自动的更新package.json的信息.


<br>

package.json文件可以手工json文档编写,也可以使用 ```npm init``` 进行填写,还可以使用 ```npm init -y```生成默认的.
将会在当前目录安装所需要的模块.
```
$ npm init
```
```
$ npm init -y
```
<br>

****

下面是两个最简单的package.json文件
```
{
	"name":"yuchengWu",
	"Version":"0.0.0",
}
```
它是典型的JSON对象,一个表示项目名字,一个表示项目版本,这两个都是必填项.(其中 ```version``` 要遵守“大版本.次要版本.小版本”的格式)

<br>

下面是比较完整的package.json文件.
```
{
	"name": "Hello World",
	"version": "0.0.1",
	"author": "张三",
	"description": "第一个node.js程序",
	"keywords":["node.js","javascript"],
	"repository": {
		"type": "git",
		"url": "https://path/to/url"
	},
	"license":"MIT",
	"engines": {"node": "0.10.x"},
	"bugs":{"url":"http://path/to/bug","email":"bug@example.com"},
	"contributors":[{"name":"李四","email":"lisi@example.com"}],
	"scripts": {
		"start": "node index.js"
	},
	"dependencies": {
		"express": "latest",
		"mongoose": "~3.8.3",
		"handlebars-runtime": "~1.0.12",
		"express3-handlebars": "~0.5.0",
		"MD5": "~1.2.0"
	},
	"devDependencies": {
		"bower": "~1.2.8",
		"grunt": "~0.4.1",
		"grunt-contrib-concat": "~0.3.0",
		"grunt-contrib-jshint": "~0.7.2",
		"grunt-contrib-uglify": "~0.2.7",
		"grunt-contrib-clean": "~0.5.0",
		"browserify": "2.36.1",
		"grunt-browserify": "~1.3.0",
	}
}
```
所以我们来详细解释下package.json文件的各个字段.

**1.普通字段**
 * Name (必须字段) 项目名字
 不要在name中包含js, node字样,这个名字最终会是URL的一部分，命令行的参数，目录名，所以不能以点号或下划线开头；这个名字可能在require()方法中被调用，所以应该尽可能短；
 
 * Version (必须字段) 项目版本
 
 * Description (可选字段) 项目描述

 * Keywords (可选字段) 关键字
 
 * Repository (可选字段) 代码存放位置和方式 

 * Bugs (可选字段) 问题追踪系统的URL或邮箱地址
 
 * license (可选字段) 许可证

 * engines (可选字段) 指定node版本
 
 * Author,contributors (可选字段)开发人,  author是一个人，contributors是一组人

 * main (可选字段) 指定看加载入口文件,该字段默认值是index.js

<br>


**2. scripts字段**

scripts指定了运行脚本命令的npm命令行缩写，我们可以通过 ```npm run``` 查看当前所有配置的scripts运行脚本命令,然后通过,例如: ```npm run (配置好的命令名)``` 运行.或者直接把 ```run``` 也省略,直接 ```npm (配置好的命令名)``` 运行.
```
"scripts": {
    "preinstall": "echo here it comes!",
    "postinstall": "echo there it goes!",
    "start": "node index.js",
    "test": "tap test/*.js"
}
```

<br>

**3.dependencies字段，devDependencies字段**

>* devDepandencies是开发环境(程序猿用于开发的服务器环境,配置随意,调试方便,错误报告全开),保存在这里的模块只用于开发.
>* dependencies是生产环境(正式提供对外的服务，一般会关掉错误报告，打开错误日志),保存在这里的模块只用于生产.

所以顾名思义, ```dependencies``` 字段指定了项目运行所依赖的模块， ```devDependencies``` 指定项目开发所需要的模块.

```
"devDependencies": {
    "html-webpack-plugin": "^2.29.0",
    "webpack": "^3.0.0",
    "webpack-dev-server": "^2.5.0"
  }
```

<br>


> * 指定版本：比如1.2.2，遵循“大版本.次要版本.小版本”的格式规定，安装时只安装指定版本。
>
> * 波浪号（tilde）+指定版本：比如~1.2.2，表示安装1.2.x的最新版本（不低于1.2.2），但是不安装1.3.x，也就是说安装时不改变大版本号和次要版本号。
> * 插入号（caret）+指定版本：比如ˆ1.2.2，表示安装1.x.x的最新版本（不低于1.2.2），但是不安装2.x.x，也就是说安装时不改变大版本号。需要注意的是，如果大版本号为0，则插入号的行为与波浪号相同，这是因为此时处于开发阶段，即使是次要版本号变动，也可能带来程序的不兼容。
> * latest：安装最新版本。

<br>

**4.bin字段**
>bin项用来指定各个内部命令对应的可执行文件的位置。

```
"bin": {
  "LookMe": "./bin/LookMe.js"
}
```
上面代码指定了LookMe命令的可执行文件是bin子目录下的LookMe.js.所以npm会找到它并建立符号链接.

**这里要注意, ```node_modules/.bin/``` 目录会在运行时会加入系统的PATH变量,所以在运行npm是,就可以不带命令来调用这些脚本**

```
scripts: {  
  start: './node_modules/LookMe/LookMe.js build'
}
// 简写为
scripts: {  
  start: 'LookMe build'
}
```
所有node_modules/.bin/目录下的命令，都可以用 ```npm run [命令]``` 的格式运行。在命令行下，键入 ```npm run``` ，然后按tab键，就会显示所有可以使用的命令。








