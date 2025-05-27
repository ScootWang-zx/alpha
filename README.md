# alpha
car & life 
1.项目采用微服务架构，主要分为以下层次：
┌─────────────────────────────────────────────────┐
│                   客户端层                      │
│  (Web/H5/Android/iOS/小程序)                   │
└───────────────┬───────────────┬───────────────┘
                │               │               
┌───────────────▼───────────────▼───────────────┐
│                   网关层                      │
│  (API Gateway/负载均衡/路由/限流/鉴权)        │
└───────────────┬───────────────┬───────────────┘
                │               │               
┌───────────────▼───────┬───────▼───────────────┐
│       业务微服务      │      基础服务         │
│                       │                       │
│  ┌─────────────────┐ │ ┌─────────────────┐   │
│  │   用户服务       │ │ │   消息服务      │   │
│  └─────────────────┘ │ └─────────────────┘   │
│  ┌─────────────────┐ │ ┌─────────────────┐   │
│  │   商品服务       │ │ │   支付服务      │   │
│  └─────────────────┘ │ └─────────────────┘   │
│  ┌─────────────────┐ │ ┌─────────────────┐   │
│  │   订单服务       │ │ │   文件服务      │   │
│  └─────────────────┘ │ └─────────────────┘   │
│  ┌─────────────────┐ │ ┌─────────────────┐   │
│  │   社区服务       │ │ │   通知服务      │   │
│  └─────────────────┘ │ └─────────────────┘   │
│  ┌─────────────────┐ │ ┌─────────────────┐   │
│  │   车辆服务       │ │ │   搜索服务      │   │
│  └─────────────────┘ │ └─────────────────┘   │
│                       │                       │
└───────────────┬───────┴───────┬───────────────┘
                │               │               
┌───────────────▼───────────────▼───────────────┐
│                   数据层                      │
│  (MySQL集群/Redis/Elasticsearch/MongoDB)      │
└───────────────────────────────────────────────┘


2. 技术栈选择
后端技术栈
框架: Spring Boot + Spring Cloud Alibaba
网关: Spring Cloud Gateway
服务注册与发现: Nacos
配置中心: Nacos
RPC: Dubbo
数据库:
主库: MySQL集群(分库分表)
缓存: Redis集群
搜索: Elasticsearch
文档: MongoDB(用于存储聊天记录等非结构化数据)
消息队列: RocketMQ
分布式事务: Seata
监控: Prometheus + Grafana
链路追踪: SkyWalking
日志: ELK
文件存储: 阿里云OSS + CDN
实时通信: Netty(WebSocket) + Socket.IO
前端技术栈
Web端: Vue.js/React + Element UI/Ant Design
小程序: 原生小程序 + Taro框架
App端: Flutter(跨平台方案)或原生(Android/iOS)

3.项目目录划分
alpha-project/
├── alpha-common/                  # 通用模块
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/alpha/common/
│   │   │   ├── resources/
│   │   └── test/
│   ├── pom.xml
├── alpha-gateway/                 # API网关
│   ├── src/
│   ├── pom.xml
├── alpha-user-service/            # 用户服务
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/alpha/user/
│   │   │   ├── resources/
│   │   └── test/
│   ├── pom.xml
├── alpha-product-service/         # 商品服务
│   ├── src/
│   ├── pom.xml
├── alpha-order-service/           # 订单服务
│   ├── src/
│   ├── pom.xml
├── alpha-community-service/       # 社区服务
│   ├── src/
│   ├── pom.xml
├── alpha-vehicle-service/         # 车辆服务
│   ├── src/
│   ├── pom.xml
├── pom.xml                        # 父POM





4.各模块目录划分
alpha-user-service/
├── src/
│   ├── main/
│   │   ├── java/com/alpha/user/
│   │   │   ├── config/                # 配置类
│   │   │   ├── controller/            # 控制器
│   │   │   ├── domain/                # 领域模型
│   │   │   ├── dto/                   # 数据传输对象
│   │   │   ├── enums/                 # 枚举类
│   │   │   ├── exception/             # 异常处理
│   │   │   ├── mapper/                # MyBatis映射
│   │   │   ├── service/               # 服务层
│   │   │   │   ├── impl/              # 服务实现
│   │   │   ├── util/                  # 工具类
│   │   │   └── UserServiceApplication.java # 启动类
│   │   ├── resources/
│   │   │   ├── mapper/                # MyBatis XML文件
│   │   │   ├── application.yml        # 应用配置
│   │   │   └── application-dev.yml    # 开发环境配置
│   └── test/                          # 测试代码
└── pom.xml