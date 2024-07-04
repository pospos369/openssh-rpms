# 在CentOS7系统环境编译最新版本 OpenSSH 并安装升级示例

## 1、安装编译环境
```shell
yum groupinstall -y "Development Tools"

yum install -y imake rpm-build pam-devel krb5-devel zlib-devel libXt-devel libX11-devel gtk2-devel perl-CPAN perl-IPC-Cmd
```
当输出 Complete! 后完成安装。

## 2、克隆 OpenSSH 编译 rpm 包项目
```shell
git clone https://github.com/pospos369/openssh-rpms
```

## 3、编译 OpenSSH，安装 OpenSSH
```shell
# 切换到打包rpm项目目录下
cd openssh-rpms

# 执行脚本，下载需要编译安装的源码
./pullsrc.sh

# 执行脚本，开始编译
./compile.sh

# 查看编译结果
ls -l el7/RPMS/x86_64/
```
## 4、安装升级 OpenSSH
```shell
# 本机升级OpenSSH版本
rpm -Uvh el7/RPMS/x86_64/*.rpm

# 删除本机现有的密钥
rm -rf /etc/ssh/ssh_host_*

# 重启sshd服务
systemctl restart sshd
```



