# git
##上传文件或文件夹
* 第一步：建立git仓库
cd到你的本地项目根目录下，执行git命令
~~~Bash
git init   
~~~
* 第二步：将项目的所有文件添加到仓库中
```Bash
git add filename/dir
```
* 第三步：将add的文件commit到仓库
~~~Bash
git commit -m "注释语句"
~~~
* 第四步：重点来了，将本地的仓库关联到github上
~~~Bash
git remote add origin https://github.com/starAnddream/php
~~~
`把URL换成自己的仓库`

* 第五步：上传github之前，要先pull一下，执行如下命令：
~~~Bash
git pull origin master
~~~
master为自己的分支，默认为master,新手无须更改


* 第六步，也就是最后一步，上传代码到github远程仓库
~~~Bash
git push -u origin master
~~~


执行完后，如果没有异常，等待执行完就上传成功了，中间可能会让你输入Username和Password，你只要输入github的账号和密码就行了

##更换远程仓库
* 我们在github上的仓库很多时候不止一个，我们需要更换远程仓库地址
```javascript
git remote rm origin
```
* 回车之后如果没有报错，那我们执行以下代码
~~~Bash
git remote add origin URL
~~~
如果git remote rm origin 报错：error:Could not remove config section 'remote.origin'

* 那我们执行
~~~Bash
git remote rm origin git remote add origin URL
~~~

##如何本地删除github上的文件/文件夹
对于github for Window或者Mac，有一个按钮，在右上角Sync,点击就可同步，所以比较方便，但对于使用git Bash的就需要命令行了

* 第一步：首先删除本地文件（本地文件与github上一致）如果不一致，执行 
~~~Bash
git fetch origin  //丢弃你在本地的所有改动与提交，可以到服务器上获取最新的版
~~~
之后执行删除不需要的文件
~~~Bash
git rm -r filename/dir
~~~
* 第二步：提交代码
~~~Bash
git commit //你的改动已经提交到了 HEAD，但是还没到你的远端仓库。
~~~
* 第三步：要更新你的本地仓库至最新改动

~~~Bash
 git pull
~~~
* 第四步：提交你的代码到仓库
~~~Bash
 git push
~~~
##同步本地代码到github仓库
* 第一步
```Bash
git add .
```
* 第二步：上传代码到HEAD
~~~Bash
git commit -m "注释"
~~~
* 第三步
~~~Bash
git remote add origin URL 
~~~
* 第四步
~~~Bash
git pull
~~~
* 第五步：提交到github仓库
~~~Bash
git push
~~~
