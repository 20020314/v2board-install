# V2board Docker部署教程
### 安装教程
- 拉取镜像
`docker pull chaikair/v2board`
- 运行镜像 (端口随意设置,格式为  你要设置的端口:80)
`docker run  -it -d  --name=voboard -p 80:80 chaikair/v2board`
### 持久化教程
- 请挂载容器`/www`文件夹为主机任意路径`/www`文件夹为容器工作目录
### 端口设置
- 容器默认运行端口为`80`
### 配置环境及安装(确保v2board容器运行中)
- 进入容器`docker exec v2board bash`  
- 执行配置命令（顺序执行）
`wget https://getcomposer.org/download/1.9.0/composer.phar`
`php composer.phar global require hirak/prestissimo`
`php -d memory_limit=-1 composer.phar install`
- 启动安装 （执行后请按提示输入数据库和账号信息）
`php artisan v2board:install`
### 启动程序队列服务
- 首次启动请于启动后重启容器，后续将会自启动。
`php artisan horizon &
#### 升级
- 进入容器 `docker exec v2board bash`
- 执行内置升级脚本 `sh update.sh`
- 重新启动队列服务 `php artisan horizon &`



`
