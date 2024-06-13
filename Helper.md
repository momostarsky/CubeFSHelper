### 查看系统版本： 
```
lsb_release -a
```
```
o LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.6 LTS
Release:        20.04
Codename:       focal
```
### 安装依赖项
```
apt install  gcc g++    make cmake maven
```
### 安装GO
```
wget https://go.dev/dl/go1.22.4.linux-amd64.tar.gz

sudo tar -zxvf go1.22.4.linux-amd64.tar.gz -C /usr/local/lib/

sudo ln -s /usr/local/lib/go/bin/* /usr/bin/
```
### 设置 GO 的环境变量
```
sudo tee -a ~/.bashrc << EOF
export GOROOT=/usr/local/lib/go/
export GOPATH=/home/${USER}/sdk/go
export PATH=\$PATH:\$GOROOT/bin:\$GOPATH/bin
EOF
```
#### 设置GO的国内代理
```
go env -w GO111MODULE=on
go env -w GOPROXY=https://goproxy.cn,direct
```
### 开始编译
```
git clone https://github.com/cubeFS/cubefs.git
cd cubefs
git checkout  v3.3.2
make build
```
### 如果编译失败 ，修复错误
```
cd  build
rm  include/ lib/ out/ bin -rf
cd  ..
go mod tidy
make build 
```


