# Dubbo基础概念

### 1.Dubbo核心组件
+ Provider： 暴露服务的服务提供方
+ Consumer： 调用远程服务的消费方
+ Register： 服务注册与发现注册中心
+ Monitor：  监控中心和访问调用统计
+ Container：服务运行时容器

### 2.Dubbo服务器注册与发现流程
- a. Container负责启动，加载，运行服务提供者
- b. Provider启动时，向注册中心注册自己并提供服务
- c. Consumer启动时，向注册中心订阅自已需调用服务
- d. Register返回服务提供者地址列表给服务消费者，如运行期间，服务提供者发生变动，将通过长连接推送至服务消费者
- e. Consumer通过负载均衡算法(软方式)，选取注册中心所返回的服务提供者列表中的一个节点进行调用，如果调用失败将尝试其他节点进行调用
- f. Consumer、Provider将调用次数、时间记录于内存中，并定时每分钟发送至Monitor监控中心

### 3.Dubbo项目结构
```shell
$ tree -L 1
.
├── dubbo-all
├── dubbo-bom
├── dubbo-build-tools
├── dubbo-cluster               # 集群容错模块，涵盖负载均衡策略、集群容错策略及路由
├── dubbo-common                # 通用逻辑模块，提供工具类和通用类型
├── dubbo-compatible            # 兼容性模块
├── dubbo-config                # 配置模块，主要实现API配置、属性配置、XML配置等
├── dubbo-configcenter          # 动态配置中心模块
├── dubbo-container             # 容器运行时，采用Main方法加载Spring容器
├── dubbo-demo                  # 三种远程调用方式实例
├── dubbo-dependencies          # 
├── dubbo-dependencies-bom
├── dubbo-distribution
├── dubbo-filter                # 过滤器
├── dubbo-metadata              # 元数据信息
├── dubbo-monitor               # 监控模块，主要监控接口调用次数及时间等信息
├── dubbo-plugin                # 插件拓展模块
├── dubbo-registry              # 服务发现与注册中心模块
├── dubbo-remoting              # 远程通信模块，为消费者、生产者间提供远程调用能力
├── dubbo-rpc                   # 抽象各种通信协议以及动态代理(易混淆remoting)
├── dubbo-serialization
```