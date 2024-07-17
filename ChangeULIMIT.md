### 修改 ulimit 1024 的限制

ubuntu 20.04 验证过的。  
作者： https://blog.csdn.net/yjkhtddx/article/details/109166147
作者： https://www.cnblogs.com/zhanchenjin/p/18109456

```shell
#!/bin/bash

# 系统
echo 'fs.file-max = 65535' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

# 用户 cat /etc/security/limits.conf
sudo tee -a /etc/security/limits.conf << EOF
*               hard    nofile          65535
*               soft    nofile          65535
root            hard    nofile          65535
root            soft    nofile          65535
*               soft    nproc           65535
*               hard    nproc           65535
root            soft    nproc           65535
root            hard    nproc           65535
*               soft    core            unlimited
*               hard    core            unlimited
root            soft    core            unlimited
root            hard    core            unlimited
EOF

# Systemd  
# cd /etc/systemd/
# grep -rn -F "DefaultLimitNOFILE"

#然后，在下面的两文件中加入：DefaultLimitNOFILE=204800
#sudo vim /etc/systemd/user.conf 
#sudo vim /etc/systemd/system.conf


sudo sed -i '/DefaultLimitNOFILE/c DefaultLimitNOFILE=65535' /etc/systemd/user.conf
sudo sed -i '/DefaultLimitNOFILE/c DefaultLimitNOFILE=65535' /etc/systemd/system.conf
sudo systemctl daemon-reexec
```
