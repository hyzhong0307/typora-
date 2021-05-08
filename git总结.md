### git总结

#### 1. 自报家门：你的名字 和地址

在你创建文件的目录中进行git bash 输入以下的代码

```
$ git config --global user.name "Your Name"
```

```
$ git config --global user.email "email@example.com"
```

#### 2. git init 把这个目录变成Git可以管理的仓库

```
Administrator@XTZJ-2020EOWEHF MINGW64 /e/前端练习/es6/git (master)
$ git init
Initialized empty Git repository in E:/前端练习/es6/git/.git/

```

#### 3. git add 文件  ——把文件添加到仓库外（暂存区）

> - **git add .**  表示将当前目录下的所有文件全部拿到仓库外排队

```
Administrator@XTZJ-2020EOWEHF MINGW64 /e/前端练习/es6/git (master)
$ git add demo.html

```

#### 4. git commit -m '添加或修改的描述'  ——  告诉Git，把文件提交到仓库

> - git commit 会将所有在仓库add排队的文件一次性添加到仓库
> - -m 后面输入的是本次提交的说明，可以输入任意内容，当
>   然最好是有意义的，这样你就能从历史记录里方便地找到改动记录

```
Administrator@XTZJ-2020EOWEHF MINGW64 /e/前端练习/es6/git (master)
$ git commit -m '添加文件'
[master (root-commit) ecf0111] 添加文件
 1 file changed, 12 insertions(+)
 create mode 100644 demo.html

```

#### 5. git diff  可以查看与上次比较修改的代码

```
Administrator@XTZJ-2020EOWEHF MINGW64 /e/前端练习/es6/git (master)
$ git diff
diff --git a/demo.html b/demo.html
index 3cdd9dd..e7056de 100644
--- a/demo.html
+++ b/demo.html
@@ -7,6 +7,6 @@
   <title>Document</title>
 </head>
 <body>
-  <h1>git练习</h1>
+  <h1>我修改了内容</h1>
 </body>
 </html>
\ No newline at end of file

```

#### 6. git log  查看提交的日记

```
Administrator@XTZJ-2020EOWEHF MINGW64 /e/前端练习/es6/git (master)
$ git log
commit d88b582a162e6133d345576c412dc7257a695e78 (HEAD -> master)
Author: hyz <467916635@qq.com>
Date:   Thu May 6 21:43:30 2021 +0800

    代码修改了

commit ecf011141396126afbfa35d4f748653f75ed1995
Author: hyz <467916635@qq.com>
Date:   Thu May 6 21:28:38 2021 +0800

    添加文件

```

#### 7. git 回退  和 指定版本前进

> - 必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本
> - _**git reset --hard HEAD^**_  回退到上个版本
> - git reset --hard  指定版本号   在窗口未关闭的情况下可以查看该版本号
> - git reflog 
>   - 在 Git bash 窗口关闭后，可以通过git reflog 查看记录你每一次命令

```
Administrator@XTZJ-2020EOWEHF MINGW64 /e/前端练习/es6/git (master)
$ git reset --hard HEAD^
HEAD is now at ecf0111 添加文件

```

#### 8. git restore  可以丢弃工作区的修改(是修改了内容但没有add到暂存区)

```
git restore demo.html
```

#### 9.git reset HEAD 文件名

> - 当文件修改了内容并且add添加到暂存区时
>   - git reset HEAD 文件名    --- 可以把暂存区的修改撤销掉
>     （unstage），重新放回工作区
>   - git restore 文件名  把工作区的文件进行撤销



#### 10.本地仓库文件传递到远程仓库方式一

> - 将github中的代码库下载到本地 git clone '地址'
> - git push 
> - 输入提示的账号密码

#### 11. 本地仓库文件传递到远程仓库方式二

> - git remote add origin 'github代码地址'
> - git push -u origin master
> - 输入提示的账号密码

