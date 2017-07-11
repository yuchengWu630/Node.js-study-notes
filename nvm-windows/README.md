# 快速安装nvm - 实现Node版本切换

<br>

> * 在node的学习中,不同的版本都会增加不同的新功能,而我们为了时刻了解最新的知识,需要更近版本的更迭.
> * 而在实际开发过程中,我们则不需要去追求这些新的功能,反而追求的是整个程序的稳定性和兼容性,所以我们需要较为稳定且兼容性较好的版本.
> * 而nvm正是能实现这一点,可以很轻松的切换node的版本,而且可以很灵活的在不同版本直接依赖不同的模块.

<br>

## 第一步 - 我们需要安装nvm

<br>

> nvm的作者现在已经在github上面维护nvm的各个版本了,所以我们可以直接去github上面搜索一个叫 "Corey Butler " 的用户,在他的code里,就有提供nvm-windows的下载.

<br>

* 或者你可以[点击这里,直接跳转下载](https://github.com/coreybutler/nvm-windows/releases)

<br>

选择最新版本的nvm-setup.zip就可以了
![download](http://wx1.sinaimg.cn/mw1024/006RjiPOly1fhfq5db40xj30ps0andgb.jpg)

1. 解压nvm-setup.zip文件后,我们得到nvm-setup.exe进行安装.
2. **安装到C盘根目录下即可,(这里会选择node的安装路径,默认即可)**
3. 安装完成后,我们就可以打开cmd / power shell / git  输入 ```nvm-v``` 查看版本,如果有显示,那么安装成功.

## 第二步 - 通过nvm安装node.js

<br>

>因为nvm默认的下载源是国外的服务器,所以我们这里需要更改配置文件,将默认下载源改为淘宝源.

<br>

1. 打开c盘找到根目录下settings.txt,我们只需要在后面加上两条url路径即可.
```
node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
```
2. 添加后保存关闭.**这里我们需要确保上面这两个网址的有效,如果浏览无效,那么我们后面通过nvm install 执行安装命令也无法找到我们需要安装的文件**

3. 然后打开cmd 输入nvm install (需要安装的版本号).
> 一般我们安装一个稳定版(LTS)和一个最新版(current)
区别就是LTS长期支持生命周期长兼容性好 而CURRENT则新内容多,可能产生不兼容的问题
决定好要安装的版本,就执行nvm install (版本号)

<br>

## 第三步 - 切换node版本

<br>

安装完成后需要 nvm use 选择运行你安装的版本.

> * 切换成功后我们输入node -v和npm -v查看node和npm版本 看看node和npm是否能正常运行
> 
> * ```nvm list``` 查看安装了哪些node.
```nvm use``` 切换需要使用的node.
