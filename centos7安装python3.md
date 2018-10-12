# 编译安装
## 下载python3的安装包
`wget https://www.python.org/ftp/python/3.7.1/Python-3.7.1rc1.tar.xz`
## 解压
```xz -d Python-3.7.1rc1.tar.xz
tar -xf Python-3.7.1rc1.tar.xz```
## 编译安装前的准备
`yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make libffi-devel`
## 进入目录编译
```
cd Python-3.7.1rc1
./configure --prefix=/usr/local/python3
make && make install
```
## 将python3加入系统命令
**ps: 定义为python3便于与系统自带的python分别开**
```
ln -s /usr/local/python3/bin/python3 /usr/bin/python3
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
# 查看
python3 -V
pip3 -V
```