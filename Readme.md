Github基本命令使用
=============

简介
-------------
用于Git初学者以及github使用尚不熟练时期(我)的参考。

SSH设置过程
-------------
本步是SSH传输协议的最初设置过程，没有设置的话可以参考以下链接进行设置：[ssh配置](http://blog.csdn.net/binyao02123202/article/details/20130891)。

拉代码基本流程
-------------
1、在你想要放代码的目录下打开git bash。

2、键入
```python
git init
```
这时你会看到这个文件夹下生成了.git目录

3、键入
```python
git remote add origin git@github.com:Lmerengues/Qmazon.git
```
其中最后一个参数地址是gitHub中你要拉下代码所在仓库的ssh地址

注：注意在这里我们使用的是ssh地址而非http,因为http对大文件的支持效果不佳，如果使用http传输经常会出现断掉的情况，所以我们使用ssh.

如果你是第一次使用ssh模式来传输，如果不幸出现错误，可以尝试键入
```python
git remote set-url git@github.com:oDevilo/Java-Base
```
这里修改了.git目录下的config文件，使其默认连接方式从http改为ssh。

4、键入
```python
git pull origin master
```
便可以将远程仓库master分支上的代码拉到你的目录下。到这里你就从远程仓库中得到了代码，可以进行开发了。

注：你也可以在第四步中不使用pull而使用fetch：

```python
Git fetch origin master
git log -p master..origin/master
git merge origin/master
```

 以上命令的含义：
   首先从远程的origin的master主分支下载最新的版本到origin/master分支上，
   然后比较本地的master分支和origin/master分支的差别，
   最后进行合并。

而与之相对的git pull指令则会自动进行合并，因此git fetch比git pull要更加安全些。


推代码基本流程
-------------
1、在你的项目目录下重复拉代码过程中的1、2步(git init)。

2、键入
```python
git add .
```

这里add .意为将该目录下所有文件都添加到索引库中，这里索引库可以理解成一个缓冲区。

3、键入
```python
git commit -m "xxx"
```

commit指令意为将上一步Add到缓冲区的代码全部提交到服务器上。-m指令意为添加备注，后面的字符串则是你添加的备注。如果不使用-m指令的话bash也会自动弹出输入器来让你输入备注。

4、键入
```python
git remote add origin git@github.com:Lmerengues/Qmazon.git
```

这一步是为了添加远程仓库的地址，最后一个参数便是在Github复制下来的远程仓库地址。

5、键入
```python
git push -u origin master
```

push命令用于将本地分支的更新，推送到远程主机。到这里你便已经将代码推到仓库的master分支上了。你也可以指定一个其他分支而不用master分支，因为master分支往往作为主版本的分支。关于分支的内容可以看下面的讲解。

到这里你便可以在Github上看到你推上去的代码了。

分支的创建与切换
------------- 
GitHub仓库默认有一个master的分支，当我们在master分支开发过程中接到一个新的功能需求，我们就可以新建一个分支同步开发而互不影响，开发完成后，在合并merge到主分支master上。

#### 关于分支的一些基本操作指令：

本地创建一个分支Branch1：
```python
git branch Branch1
```

切换到你的新分支
```python
git checkout Branch1
```

将新分支发布到Github上：
```python
git push origin Branch1
```

查看分支信息：
```python
git branch
```

分支合并：
```python
git merge Branch1
```

在master分支下使用此命令便可以将Branch1分支的版本合并到Master下

详情参考链接：
[https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000)


其他常用指令
-------------
#### 1、Git clone
将整个git库直接clone到本机上
```python
git clone git@github.com:Lmerengues/Qmazon.git
```

上面命令指clone全部分支 但只显示默认的master分支

如果想要查看一个其他分支如b1，则键入：
```python
git branch -r
git checkout b1
```
即可切换分支

而如果想要clone某个分支则键入：
```python
git clone -b b1 git@github.com:Lmerengues/Qmazon.git
```

#### 2、删除远程仓库

有时我们想要切换远程仓库，那么我们便需要先删除远程仓库后再添加一个新的远程仓库。删除指令如下：
```python
git remote rm origin
```

添加则使用remote add指令即可。

#### 3、Git pull强制覆盖本地项目
有时我们在拉代码时希望不管本地的版本如何，我们只要现在远程仓库的，那边需要pull指令来进行操作。

```python
git fetch --all  
git reset --hard origin/master 
git pull 
```



参考链接：

[在Github上创建新分支](http://blog.csdn.net/guang11cheng/article/details/37757201)

[Git fetch与Git pull的区别](http://blog.csdn.net/hudashi/article/details/7664457)

[删除远程仓库](http://blog.csdn.net/hello0370/article/details/41825407)

[github设置添加SSH](http://blog.csdn.net/binyao02123202/article/details/20130891)

[GitHub的SSH提交配置](http://blog.csdn.net/oDeviloo/article/details/52654590)

[Git提交大文件错误](http://www.cnblogs.com/hanxianlong/p/3464224.html)

[LF/CRLF](http://blog.csdn.net/feng88724/article/details/11600375)

[撤销commit](http://zhyq0826.iteye.com/blog/1671638)

[clone分支](http://blog.csdn.net/a513322/article/details/46998325)

[分支原理](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000)

[ssh key作用](https://segmentfault.com/q/1010000000118744)

[git push指令](http://www.yiibai.com/git/git_push.html)

[强制覆盖](http://blog.csdn.net/xyzchenxiaolin/article/details/51955221)