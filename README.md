# git
## 上传文件或文件夹
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

## 更换远程仓库
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
## 同步本地代码到github仓库
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
### 报错：
```git
error: server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
```
* git下设置：
```git
* git config --global http.sslVerify false
```
## git版本回退
```git
git log
```
* 如果嫌弃输出太繁琐
```git
git log --pretty=oneline
```
* 首先，Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交3628164...882e1e0（注意我的提交ID和你的肯定不一样），上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
```git
 git reset --hard HEAD^
 ```
 * 好比你从21世纪坐时光穿梭机来到了19世纪，想再回去已经回不去了，肿么办？

* 办法其实还是有的，只要上面的命令行窗口还没有被关掉，你就可以顺着往上找啊找啊，找到那个append GPL的commit id是3628164...，于是就可以指定回到未来的某个版本：
```git
git reset --hard 3628164
```
* 版本号没必要写全，前几位就可以了，Git会自动去找。当然也不能只写前一两位，因为Git可能会找到多个版本号，就无法确定是哪一个了。
* 查看命令历史，以便确定要回到未来的哪个版本。
```git
git reflog
```
