# docker仓库去除https

# echo '{ "insecure-registries":["xxx.xxx.xxx.xxx:5000"] }' > /etc/docker/daemon.json
# 重启docker服务


# docker run -d -p 5000:5000 --restart=always --name registry -v 宿主机仓库目录:/var/lib/register registry:2
