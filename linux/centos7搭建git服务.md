## 安装git
```
yum -y install git
```

## 创建git相关用户与组

> 创建用户与组

```
useradd gogo  # 添加gogo用户
passwd gogo  # 为gogo用户修改密码
groupadd gitgroup # 添加gitgroup用户组

```

> 禁用git用户的shell登录，防止用户通过Git用户登录服务器。编辑/etc/路径下的passwd文件，将文件后边的bash改成git-shell，即
将

```
gogo:x:1002:1003::/home/gogo:/bin/bash
```

> 改为

```
gogo:x:1002:1003::/home/gogo:/bin/git-shell
```

> 将gogo添加到gitgroup用户组

```
uesrmod -G gitgroup gogo
```

## 创建git仓库

> 创建git父目录

```
mkdir /data/git  # 不能在root目录下，git clone 时会报错
chgrp -R gitgroup /data/git  # 将git目录添加到gitgroup用户组
chmod -R 777 /data/git/  # 将/data/
```

> 创建git仓库

```
mkdir -P /data/git/test.git  # 创建git仓库
git init --bare /data/git/test.git  # 初始化空的git仓库
chgrp -R gitgroup /data/git/  # 修改git仓库所属组
chmod -R 777 /data/git/  # 修改git仓库所有文件权限
```

## git简单用法

> 克隆，添加文件，上传

```
git clone gogo@ip:/data/git/test.git  # 创建的git仓库
cd test
touch a
git add .
git commit -m "添加a文件"
git push origin master  # 第一次push需要填写origin master，之后可以省略
```

> 回滚

```
git log  # 查看日志
git reset --hard 版本id # 将本地仓库回退到指定版本
git push origin HEAD --force # 将回退的版本上传
```

> 为单个项目添加用户名

```
git config user.name "geekgogo" (全局：git config --global user.name "geekgogo")

```

## 注意

**创建新的仓库时记得初始化并且修改目录权限**