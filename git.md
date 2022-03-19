<<<<<<< HEAD
## Git常见操作

git是一个版本控制的工具，文件修改的历史记录

1、安装与配置信息

```shell
#主要是作区分，邮箱不重要
git config --global user.name "yourName"
git config --global user.email "yourEmail"
#检查信息写入是否成功
git config --list
```

理论依据

git有三个仓库用作维护项目，分别是：

- 工作区域（Working Directory）
  - 存放项目代码的地方
- 暂存区域（stage）
  - 用于临时存放改动
- Git仓库（Repository)
  - 安全存放数据

工作流程：

1. 在工作目录中添加、修改文件
2. 将需要进行版本管理的文件放入暂存区域
3. 将暂存区域提交到Git仓库

与之对应的文件有三种状态：已修改（modified）、已暂存（staged）和已提交（committed）

## 实战

1、初始化Git

```shell
#在项目目录打开git

#初始化项目，创建.git后缀文件，git接管项目的版本控制
git init
#添加README.md文件
git add README.md
#提交README.md文件
git commit -m "yourMessage"
```

查看状态

```shell
#可以查看文件状态
git status
```



提交github

```shell
#设置url别名
git remote add [别名] [url]
#查看别名情况
git remote -v
#提交github
git push [url] [分支名]
```

拉取github

```shell
#拉取
git pull [url] [分支名]
#克隆 在指定项目目录
git clone [url]
```






=======
git常见操作
>>>>>>> e29f9f2cd39059aa03ca9b2d18a123e914ad7891

上传github

在github创建仓库并且拿到http格式

 ```git
 
 #将文件交给git管理
 git init 
 git add [profile]
 git commit -m "message commit"
 #查看git 目前文件信息
 git status 
 
 
 ```

