---
title: mood
date: 2020-07-06 10:37:15
tags:
---
# git和hexo创建自己的博客

> “当我们让自己的光芒闪耀，无意中我们也允许了他人散发光芒。一旦我们从自我的恐惧中解放出来，我们的存在，也会让他人得到解放。”
> 


<a name="XT0Fc"></a>
## 五分钟创建一个博客

1. 在GitHub上创建一个仓库，仓库名的格式为 `你的github上的username.github.io` 这是一个固定格式。
1. 创建完后找到 `setting` ，然后找到 `GitHub pages` ，如下图，绿色框里说**我的站点在https://刚刚创建的仓库名/，**访问就可以了，自己的博客已经创建成功，可以新建md文件发布新的博客。可能五分钟都不到~

![image.png](https://cdn.nlark.com/yuque/0/2020/png/564594/1594008365269-8ebd39f6-f5b5-40d9-ab0b-6f18b4045a5a.png#align=left&display=inline&height=300&margin=%5Bobject%20Object%5D&name=image.png&originHeight=462&originWidth=1148&size=39017&status=done&style=none&width=746)

3. 但是由于界面比较丑，所以要用到 `hexo` 框架，安装之前需要安装 `git` 以及 `node.js` ，可以看官方文档 [hexo安装](https://hexo.io/zh-cn/docs/)。
3. 可以在本地，在命令行输入 `hexo init blog ` ，创建一个博客文件夹blog，之后的步骤可以看下面的命令**8~10，**然后访问博客地址，就会发现变好看了，也可以自己修改一下框架让其更适合自己，用hexo的发布三部曲命令提交。**
3. 之后可以用  `hexo new 新的md文件的名字，比如hexo new hello` ,就是创建一个hello.md文件，然后编辑博客内容，用hexo的发布三部曲提交发布。 
<a name="9Ail6"></a>
## 使用到的命令


1. 查看是否生成ssh，若没有则为空<br />
```
cat ~/.ssh/id_rsa.pub
```


2. 生成ssh的命令<br />
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```


3. git的全局配置用户名和邮箱，只需配置一次<br />
```
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```


4. **克隆仓库到本地**<br />
```
git clone 仓库地址（用ssh）
```


5. 提交三部曲<br />

注意`git push`的时候，`origin`是默认的仓库名，如果有两个远程仓库比如GitHub和gitee，就需要写实际的仓库名。
```
第一步 选中所有
git add -A
或
git add .
第二步 提交的名称
git commit -m "修改的备注名称"
第三步 推到远程仓库(以下三种情况)
git push origin master(第一次提交)
git push (第2~n次提交)
git push origin b(提交到分支b)
```


6. 抓取远程仓库的所有内容<br />

在多人协同开发的时候会经常用到，在`push`之前先`git pull`是很好的习惯。（本地仓库和远程仓库是一方相对另一方是真子集的时候才能提交）
```
git pull
```


7. **将本地文件夹提交到远程仓库**时，一般需要先在远程仓库建立一个同名仓库。注意是创建一个空仓库。<br />

创建完空仓库后，要在本地的同名文件夹下进行git初始化
```
git init
```

<br />然后绑定远程仓库，初始化的文件夹一般都没有绑定过。而克隆的仓库都绑定过了。注意都是在同名文件夹下。
```
查看是否绑定过
git remote -v
绑定
git remote add origin 仓库地址
如果绑定错误
git remote remove origin
```


8. `hexo` 创建博客文件夹
```
hexo init 文件夹名称
```


9. 安装发布工具,注意要在博客文件夹里安装<br />
```
npm install hexo-deployer-git --save
```

<br />在博客文件夹里找到`_config.yml`文件,配置一下
```
theme: landscape
deploy:
  type: git
  repository: 你的GitHub仓库地址(ssh)
  branch: master
```


10. `hexo`提交的三个命令<br />
```
清除缓存，更快生效
hexo clean
```
```
生成新的静态文件，可简写为 hexo g
hexo generate
```
```
把生成的文件部署到博客上，可简写为hexo d
hexo deploy
```


11. `hexo`创建新博客，下面的命令会创建一个新的md文件，在文件里写好博客，然后利用提交命令发布新博客就可以了。<br />
```
hexo new 博客名字
```


12. 更换`hexo`的主题为`next`<br />
```
首先克隆仓库到本地博客文件夹下的主题文件夹下
git clone next主题的仓库地址 themes/next
git clone https://github.com/iissnan/hexo-theme-next themes/next
然后在配置文件_config.yml里更改一下主题的配置
theme: next
```


13. git分支<br />
```
创建分支
git branch dev(分支名)
切换到新分支，例如dev
git checkout dev
命令合并使用，创建分支dev并切换
git checkout -b dev
```


14. 安装 `hexo`(注意要先安装`git`以及`node`)
```
npm install -g hexo-cli
```


15. 克隆分支上的项目到本地
```
git clone -b 分支名 仓库地址
```


