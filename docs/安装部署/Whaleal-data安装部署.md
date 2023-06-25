
## Whaleal-data安装部署


###     安装要求

#### 		硬件要求

    操作系统：Windows 10 或更高版本、Linux 发行版（如Ubuntu、CentOS）、MacOS。
    
    处理器：Intel Core i5 或更高级别的处理器。
    
    内存：至少 8GB RAM。
    
    存储空间：至少 100GB 的可用磁盘空间。
    
    网络适配器：支持有线或无线连接的网络适配器。

#### 		网络要求

##### 				网络访问要求

    根据自身需求配置。

##### 				端口要求

    需要开放指定的端口（如 80 端口用于 HTTP 通信，程序启动所用端口）。

#### 		软件要求

##### 				操作系统要求

    支持 Windows Server 2016 或更高版本。

##### 				浏览器支持

    Google Chrome 版本 80 或更高、Mozilla Firefox 版本 75 或更高。

### 	服务器高可用部署

将服务在多个机器进行部署使用负载均衡器将流量分发到多个服务器上，以实现请求的平衡和分担。常见的负载均衡算法包括轮询、最少连接和哈希算法等。在系统中使用多个相同配置的服务器，以便在一个服务器发生故障时，其他服务器可以接管其工作并保持系统的连续性。常见的冗余备份模式包括主备模式、活动-活动模式和N+1模式等。

### 	docker容器快速部署
```
进入docker-compose.yml同级目录，使用 `docker-compose up -d`启动。

docker服务启动成功后，可通过`docker logs -f root_whaleal-data_1`命令查看whaleal-data服务运行日志。
本地服务器需绑定域名解析登录web端，命令：`sudo sh -c 'echo "docker服务器ip  whaleal-data.com" >> /etc/hosts'`

登录whaleal-data服务
`http://docker服务器ip` 或者`http://whaleal-data.com`

首次用户登录
user:"admin"
pwd:"123456"
系统强制要求用户修改密码后登录
```


Tips:
冷数据归档：
冷数据归档默认填写路径为/whalealdb。docker服务映射外部路径为/opt/whalealdb。

### 	 快速访问

docker容器化启动whaleal-data服务。该服务依赖于`mysql`,`mongodb`,`redis`,`zookeeper`服务启动，通过`nginx`服务代理转发在本地浏览器中运行。
