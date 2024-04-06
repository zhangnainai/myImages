# svn转到git项目方式（使用git自带的方式进行转换）

在对应位置打开git命令行控制窗口
![image-20240406184208674](https://cdn.jsdelivr.net/gh/zhangnainai/myImages@main/img/image-20240406184208674.png)

``` javascript
输入代码
git svn clone [svn地址：]
例如：
git svn clone svn://192.168.190.2/traditionalBusiness/courseware/med66/lib/domain/cware-domain

```

之后会弹出窗口

![img](https://cdn.jsdelivr.net/gh/zhangnainai/myImages@main/img/6d13dd6c07714e26e965ea2af911b202.png)

输入* 之后再次弹出窗口，输入svn账号密码

![image-20240406184459303](https://cdn.jsdelivr.net/gh/zhangnainai/myImages@main/img/image-20240406184459303.png)

开始跑了，此时在git上创建对应的项目并复制地址（特别慢，特别慢，特别慢，可以使用```svn2git```这个工具，但是我没有搞明白）

![image-20240406184533603](https://cdn.jsdelivr.net/gh/zhangnainai/myImages@main/img/image-20240406184533603.png)

创建好了

![image-20240406184624899](https://cdn.jsdelivr.net/gh/zhangnainai/myImages@main/img/image-20240406184624899.png)

之后复制这两种形式的一种，取决于使用什么方式拉取代码，这里我用的是http

跑完了

![image-20240406185855734](https://cdn.jsdelivr.net/gh/zhangnainai/myImages@main/img/image-20240406185855734.png)

如果SVN项目有忽略文件，执行如下命令转换SVN:ignore属性为 .gitignore文件。

```javascript
cd g:/医学网
git svn show-ignore > .gitignore
git add .gitignore
git commit -m 'Convert svn:ignore properties to .gitignore.'
```

如果clone完成后，SVN仓库还有更新，可执行以下命令同步SVN更新：

```bash
$ git svn rebase
```

之后需要添加远程地址

```java
$ git remote add origin "[刚刚复制的地址]"
例如：
   git remote add origin "http://gitlab.cdel.local/cware_jar/med66/cware-domain-med66.git" 
验证是否添加完成
$ git remote show origin
* remote origin
  Fetch URL: http://gitlab.cdel.local/cware_jar/med66/cware-domain-med66.git
  Push  URL: http://gitlab.cdel.local/cware_jar/med66/cware-domain-med66.git
  HEAD branch: (unknown)
显示链接则添加完成
```

推送

```java
使用代码推送到master
$  git push origin master:master --force
显示如下即为推送成功
Enumerating objects: 233, done.
Counting objects: 100% (233/233), done.
Delta compression using up to 6 threads
Compressing objects: 100% (159/159), done.
Writing objects: 100% (233/233), 68.65 KiB | 1.16 MiB/s, done.
Total 233 (delta 68), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (68/68), done.
To http://gitlab.cdel.local/cware_jar/med66/cware-domain-med66.git
 * [new branch]      master -> master
```

然后就可以在git上看到代码和所有的log日志了

![image-20240406191433172](https://cdn.jsdelivr.net/gh/zhangnainai/myImages@main/img/image-20240406191433172.png)

![image-20240406191427148](https://cdn.jsdelivr.net/gh/zhangnainai/myImages@main/img/image-20240406191427148.png)