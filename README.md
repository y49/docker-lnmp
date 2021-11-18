### 目录结构
```
├─dock-lnmp           
│  ├─build              构建模块
│  │  └─ php             
│  │  │  ├─Dockerfile    
│  │  │  └─resource     php扩展
│  ├─data               数据目录
│  │  ├─formality       服务配置文件
│  │  │  ├─mysql   
│  │  │  ├─nginx   
│  │  │  ├─php   
│  │  │  └─redis   
│  ├─docker-compose.yml 
│  ├─docker-compose-more.yml 
│  └─env-example.env    基础配置
```

### 准备

```shell
# 安装 Docker 和 Docker-Compose
yum -y install epel-release 
yum -y install docker docker-compose

# 启动 Docker 服务
service docker start

# 配置阿里云 Docker 镜像加速器（建议配置加速器, 可以提升 Docker 拉取镜像的速度）
mkdir -p /etc/docker
vim /etc/docker/daemon.json

# 新增下面内容
{
  "registry-mirrors": [
    "https://hub-mirror.c.163.com",
    "https://mirror.baidubce.com"
  ]
}

# 重新加载配置、重启 Docker
systemctl daemon-reload 
systemctl restart docker 

#检查加速器是否生效
执行 $ docker info，如果从结果中看到了如下内容，说明配置成功。
    Registry Mirrors:
     https://hub-mirror.c.163.com/
```


### 安装

```shell
# 克隆项目
git clone git@github.com:y49/docker-lnmp.git
# 进入目录
cd docker-lnmp
# 修改配置项
cp env-example.env .env
vim .env  //修改为个人配置
# 自行构建
docker-compose -f docker-compose.yml up -d  // nginx php mysql redis 
或
docker-compose -f docker-compose-more.yml up -d  // nginx php mysql redis mongodb memcached rabbitmq
```

### 运行
```shell
访问ip查看结果
```

