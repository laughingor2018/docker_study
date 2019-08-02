# docker machine主要负责远程操作不同的节点，不需要切换
# 直接到github下载，增加执行权限，放在path路径下


# 节点首先要安装sshd，并且设置成root用户可以登录，并且是免密登录
# 本地machine主机需要ssh-keygen -r rsa生产秘钥，ssh-copy-id root@节点ip

# docker-machine create --driver generic --generic-ip-address 节点ip 节点名称
# 上述命令是创建节点
