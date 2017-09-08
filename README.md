# zPhal-dockerfiles
dockerfiles that support zPhal's working environment

## 简介
用docker容器服务的方式搭建zPhal环境，易于维护、升级。使用前需了解Docker的基本概念，常用基本命令。
可以一条条命令执行docker命令来构建镜像，容器。这里推荐使用docker-compose来管理，执行项目，下面是使用流程。

相关软件版本(2017.8.17更新)：
- PHP 7.1.8
- MySQL 5.7
- Nginx 1.12
- Memcached 1.5
- Redis 3.2

用到的PHP 拓展(2017.8.17更新)：
- redis 3.1.3
- memcached 3.0.3
- Phalcon 3.2.2

## 使用
### 1.安装Docker，Docker-compose  
- Docker，详见官方文档：
https://docs.docker.com/engine/installation/linux/docker-ce/centos/
- docker-compose
```
sudo pip install -U docker-compose
```
### 2.下载zPhal-dockerfiles
```
git clone git@github.com:ZpGuo/zPhal-dockerfiles.git
 
mv zPhal-dockerfiles zPhal
```
### 3.下载需要的拓展包
```
cd zPhal/dockerdir
  
wget https://pecl.php.net/get/redis-3.1.3.tgz -O php/redis.tgz  
wget https://codeload.github.com/phalcon/cphalcon/tar.gz/v3.2.2 -O php/cphalcon.tar.gz 
wget https://pecl.php.net/get/memcached-3.0.3.tgz -O php/memcached.tgz
```
### 4.docker-compose构建项目
命令：
```
docker-compose up
```  
如果没问题，下次启动时可以以守护模式启用，所有容器将后台运行：  
```
docker-compose up -d
``` 
使用docker-compose基本上就这么简单，Docker就跑起来了，用stop，start关闭开启容器服务。  
更多的是在于编写dockerfile和docker-compose.uyml文件。  
可以这样关闭容器并删除服务：
```
docker-compose down
```

### 4.docker-tools 工具
目前有composer
```
docker-compose -f docker-tools.yml  up -d
``` 