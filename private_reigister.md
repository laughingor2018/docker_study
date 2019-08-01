docker仓库去除https

echo '{ "insecure-registries":["xxx.xxx.xxx.xxx:5000"] }' > /etc/docker/daemon.json
重启docker服务
