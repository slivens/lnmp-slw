## lnmp项目搭建
1. 首先进入docker-compose的配置文件下
2. 进行命令docker-compose up -d 另外再执行docker-compose build 载入dockfile
3. 运行docker-compose exec php-fpm bash 进入此容器中
4. 在 /var/www 下执行laravel new blog 然后exit退出
5. 来到当前www的目录中，此时就可以看到blog目录cd中 执行php artisan make：Auth 然后执行 php artisan migrate
6. vim 编辑 隐藏的.env文件配置如下

DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=blog
DB_USERNAME=root
DB_PASSWORD=123456

BROADCAST_DRIVER=log
CACHE_DRIVER=file
SESSION_DRIVER=redis
SESSION_LIFETIME=120
QUEUE_DRIVER=sync

REDIS_HOST=redis
REDIS_PASSWORD=123456
REDIS_PORT=6379

7.启动过程中可能遇到的小坑：

如果碰到：==The stream or file "/var/www/blog/storage/logs/laravel.log" could not be opened: failed to open stream: Permission denied==的权限问题
设置 chmod 777 -R /var/www/blog/storage

8.如果碰到：“predis/client” 请在laravel目录下执行 conposer require 'predis/predis'
9.项目打开http//：lcoalhost/index.php
