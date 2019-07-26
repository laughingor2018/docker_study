# docker部署lnmp

## docker run --name myredis -p 6379:6379 -v $PWD/redis/data:/data  -d redis:latest redis-server --appendonly yes
## docker run --name mymysql -p 3306:3306 -d -v $PWD/conf:/etc/mysql/conf.d -v $PWD/logs:/logs -v $PWD/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 mysql:5.7.27
## docker run --name myphp -v $PWD/nginx/www:/var/www/html --link mymysql:mysql --link myredis:redis -d php:5.6-fpm
## docker run --name mynginx -p 8080:80 -d -v $PWD/nginx/www:/usr/share/nginx/html -v $PWD/nginx/conf/conf.d/default.conf:/etc/nginx/conf.d/default.conf -v $PWD/nginx/logs:/var/log/nginx --link myphp:php nginx:latest


注意事项：
1. php镜像没有安装mysql扩展，需要手动安装
安装方式有三种：

a.源码安装方式
curl -L -o /tmp/redis.tar.gz https://github.com/phpredis/phpredis/archive/4.0.0.tar.gz \
    && tar xfz /tmp/redis.tar.gz \
    && rm -r /tmp/redis.tar.gz \
    && mkdir -p /usr/src/php/ext \
    && mv phpredis-4.0.0 /usr/src/php/ext/redis \
    && docker-php-ext-install redis \
    && rm -rf /usr/src/php #如果这段不加构建的镜像将大100M
    
b.pecl
第三方扩展安装方式
  pecl install redis
  
  
c.直接利用docker命令安装
官方扩展一般可以安装，例如mysql
docker-php-ext-install redis


安装扩展一般通过dockerfile或直接进去容器安装再更新容器


2. nginx需要外部link php，php需要外部link mysql和redis
在php配置文件链接mysql和redis时，直接在host中使用外部链接名
