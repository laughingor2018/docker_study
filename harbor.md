
# 安装docker和docker-composer环境
# 到https://github.com/goharbor/harbor/releases查找最新harbor

# 按照需求下载下关程序解压

# 配置harbor.yml文件，启动install.sh自动安装


# 启动需要使用docker-compose up
# 停止需要使用docker-compose stop



# 使用harbor作为私有云仓库需要注意事项：

# 需要创建项目

# 需要创建用户，把用户指定角色并加入项目中

# 在命令行需要用户登录  docker login ip:port 按提示输入用户名和密码

# docker tag 源 ip:port/项目名/源


# docker push ip:port/项目名/源
