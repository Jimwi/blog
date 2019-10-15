

# dubbo配置

## dubbo配置UML ![1](../img/dubbo-config.jpg)

### 1. ApplicationConfig

```xml
    <dubbo:application name="demo-application" version="1.0.0" owner="xun" organization="qudian" architecture="" environment="dev" compiler="javassist" logger="slf4j" monitor="" registry=""/>
```

##### 配置项解释 

| 名称    |类型| 解释 |
| :------ |-------| ---------|
| id   |String| 应用的ID，随便取名 |
| name   |String| 应用的名称，随便取名 |
| version| String | 应用的版本       |
| owner | String | 应用负责人 |
| organization | String | 组织名称 估计就是个名称 |
| architecture | String | __不懂__ |
| environment | String | 环境，比如：dev，test，product |
| compiler | String | jdk或javassist。生成动态代理的时候用的 |
| logger | String | 使用哪种日志框架，比如：slf4j,jcl,log4j,log4j2,jdk |
| monitor | String | ref   see monitorConfig，可以不填 |
| registry | String | ref    see registryConfig，可以不填 |


### 2. MonitorConfig

```xml
<dubbo:monitor protocol="" address="" interval="" username="" password="" group="" version="" default=""/>
```

#####  配置项解释

| 名称     | 类型    | 解释                                   |
| -------- | ------- | -------------------------------------- |
| protocol | String  | RPC协议类型，dubbo，registry           |
| address  | String  | 监控中心地址，比如 10.20.130.230:12080 |
| interval | Integer | 向监控中心汇报的时间间隔，单位：毫秒   |



### 3. RegistryConfig

```xml
<dubbo:registry id="registry1" address="" protocol="" port="" version="" password="" username="" transport="" timeout="" session="" file="" wait="" check="" register="" subscribe="" dynamic="" group="" simplified="" extra-keys="" cluster="" client="" forks="" server="" transporter="" />
```

##### 配置项解释

| 名称        | 类型    | 解释                                                         |
| ----------- | ------- | ------------------------------------------------------------ |
| id          | String  | 注册中心的ID，因为一个应用可以有多个注册中心（多个集群），   |
| address     | String  | 比如 zookeeper://127.0.0.1:2181，这个地址带协议和端口        |
| protocol    | String  | 比如dubbo(这个是直连吗？)   multicast，zookeeper，redis      |
| port        | Integer     | address配置了，port就不用配置                                |
| username    | String  | 登录注册中心的用户名，有的注册中心需要                       |
| password    | String  | 登录注册中心的密码                                           |
| transport   | String  | 网络传输方式，curator，这里只连接zookeeper时使用的客户端 |
| transporter | String  | 和transport一样的                                        |
| client | String | 和transport一样的，客户端单独配置 |
| server      | String  | ????                              |
| timeout     | Integer     | 请求注册中心的超时时间，默认5秒                      |
| session     | Integer     | 注册中心会话的超时时间                                       |
| file        | String  | 本地保存注册中心数据的文件名，默认在~/.dubbo目录下           |
| wait        | Integer     | 停止之前等待的时间                                           |
| check       | Boolean | 是否检查注册中心是否存在，默认true                           |
| register    | Boolean | 是否向该注册中心注册，默认true。如果是false，只订阅不注册    |
| subscribe   | Boolean | 是否订阅从该注册中心订阅服务，默认true。                     |
| dynamic     | Boolean | 默认true，服务启动时自动注册，服务停止时自动取消注册。       |
| group       | String  | dubbo分组                                                    |
| simplified  | Boolean | ？？？since 2.7.0                                            |
| extra-keys  | String  | ？？？与simplified一起的                                     |
| cluster     | String  | ？？？                                                       |
| forks       | String  | ？？？                                                       |



### 4. ModuleConfig

```xml
<dubbo:module id="" name="" organization="" owner="" version="" registry="" monitor="" />
```

##### 配置项解释

| 名称         | 类型   | 解释                      |
| ------------ | ------ | ------------------------- |
| id           | String | module1                   |
| name         | String |                           |
| organization | String |                           |
| owner        | String |                           |
| version      | String | 1.0.0                     |
| registry     | String | 有多个 see RegistryConfig |
| monitor      | String | see MonitorConfig         |


### 5. ConfigCenterConfig

```xml
<dubbo:config-center protocol="" address="" highest-priority="" namespace="" cluster=""  group=""  check=""  config-file="" timeout="" username="" password=""  include-spring-env="" app-config-file="" />
```

##### 配置项解释

| 名称               | 类型    | 解释                                                         |
| ------------------ | ------- | ------------------------------------------------------------ |
| protocol           | String  | 注册中心的协议，比如：apollo、zookeeper、nacos               |
| address            | String  | 比如zookeeper://127.0.0.1:2222。address中有协议头，protocol可以不写 |
| highest-priority   | Boolean | 来自注册中心的配置是否有最高优先级                           |
| namespace          | String  | 命名空间？？用于隔离                                         |
| cluster            | String  | ？？？                                                       |
| group              | String  | ？？？                                                       |
| check              | Boolean | 是否检查配置中心是否活着                                     |
| config-file        | String  | 在配置中心中，配置文件的名称                                 |
| timeout            | Integer     | 获取配置中心配置的超时时间                                   |
| username           | String  | 登录配置中心的用户名                                         |
| password           | String  | 登录配置中心的密码                                           |
| include-spring-env | Boolean | 是否从Spring Environment中读取配置。？？？                   |
| app-config-file    | String  | 在配置中心中，这个应用的配置文件的名称                       |



### 6. MetricsConfig

 (加监控用的，接入Alibaba Metrics时候用的)

```xml
<dubbo:metrics port="" protocol="" />
```

##### 配置项解释

| 名称               | 类型    | 解释                                                         |
| ------------------ | ------- | ------------------------------------------------------------ |
| port               | Integer     |                                                            |
| protocol           | String  |                                                            |



### 7. MetadataReportConfig

```xml
    <dubbo:metadata-report id="" address="" timeout="" cluster="" group="" username="" password="" cycle-report="" retry-period="" retry-times="" sync-report="" />
```

##### 配置项解释

| 名称         | 类型    | 解释                       |
| ------------ | ------- | -------------------------- |
| id           | String  |                            |
| address      | String  | zookeeper://127.0.0.1:2181 |
| timeout      | Integer     | 超时时间                   |
| cluster      | String  | ？？？                     |
| group        | String  | 分组                       |
| username     | String  |                            |
| password     | String  |                            |
| cycle-report | Boolean | 是否周期性保存             |
| retry-period | Integer     | 重试间隔                   |
| retry-times  | Integer     | 重试次数                   |
| sync-report  | Boolean | 是否异步保存，默认true     |



### 8. AbstractMethodConfig

##### 配置项解释

| 名称        | 类型           | 解释                                                         |
| ----------- | -------------- | ------------------------------------------------------------ |
| timeout     | Integer            | 调用的超时时间                                               |
| retries     | Integer            | 调用异常的重试次数，默认3次                                  |
| actives     | Integer            | 最大同时调用的次数，默认                                     |
| loadbalance | String         | 负载均衡算法，比如：consistenthash，leastactive，random，roundrobin。默认random |
| async       | Boolean        | 是否异步，默认false                                          |
| sent        | Boolean        | ？？？                                                       |
| mock        | String         | mockClass的BeanName，当服务掉不通的时候，会调用mockClass     |
| merger      | String         | ？？？                                                       |
| cache       | String/Boolean | lru，threadlocal，jcache。默认false。最好还是不要cache       |
| validation  | Boolean        | 校验参数 默认false                                           |
| forks       | Integer            | 跟cluster的参数有关？？？                                    |



### 9. AbstractIntegererfaceConfig

##### 配置项解释

| 名称                 | 类型                  | 解释                                                     |
| -------------------- | --------------------- | -------------------------------------------------------- |
| stub                 | String/Boolean        | 本地代理类？？？？用于在客户端执行本地逻辑               |
| monitor              | MonitorConfig         | ref                                                      |
| proxy                | String                | jdk， javassist （和application.complier有啥关系）       |
| cluster              | String                | cluster类型，failover/failfast/failsafe/failback/forking |
| filter               | String                | 自定义过滤器，多个用逗号隔开                             |
| listener             | String                | 自定义listener，多个用逗号隔开                           |
| owner                | String                | xun                                                      |
| connections          | Integer                   | 最大连接数，dubbo是长连接                                |
| layer                | String                | The layer of service providers ？？？                    |
| application          | ApplicationConfig     | ref                                                      |
| module               | ModuleConfig          | ref                                                      |
| registries           | List\<RegistryConfig> | ref                                                      |
| registryIds          | String                | ???                                                      |
| onconnect            | String                | ???                                                      |
| ondisconnect         | String                | ???                                                      |
| metrics              | MetricsConfig         | ref                                                      |
| metadataReportConfig | MetadataReportConfig  | ref                                                      |
| configCenter         | ConfigCenterConfig    | ref                                                      |
| callbacks            | Integer                   | 回调次数？？                                             |
| scope                | String                | the scope for referring/exporting a service              |
| tag                  | String                | ？？？                                                   |



### 10. ProtocolConfig

```xml
<dubbo:protocol id="dubbo" name="dubbo" port="20880" host="" threadpool="" threads="" iothreads="" accepts="" payload="" codec="dubbo" serialization="" accesslog="" path="" transporter=""	server="" client="" dispatcher="" queues="" charset="" buffer="" heartbeat="" telnet="" register="" contextpath="" 
<!-- 下面的官网没有给出解释 -->
corethreads="" exchanger="" extension="" keepalive="" networker="" optimizer="" prompt="" status="" default="" />
```

##### 配置项解释

| 名称          | 类型           | 解释                                                     |
| ------------- | -------------- | -------------------------------------------------------- |
| id            | String         | 默认dubbo                                                |
| name          | String         | 默认dubbo，见dubbo-rpc模块                               |
| port          | String         | 端口                                                     |
| host          | String         | 本机IP，自动查找本机IP                                   |
| threadpool    | String         | fixed，cached，limited，eager。见ThreadPool拓展          |
| threads       | Integer            | 线程池的大小，默认200                                    |
| iothreads     | Integer            | IO线程池的大小，默认cpu个数+1                            |
| accepts       | Integer            | 服务提供方最大可接受连接数，默认0（默认？？）            |
| payload       | Integer            | 请求及响应数据包大小限制，单位：字节。默认，8388608(=8M) |
| codec         | String         | 协议编码方式，默认dubbo，见Codec2拓展                    |
| serialization | String         | 序列化方式，dubbo协议默认是hessian2                      |
| accesslog     | String/Boolean | true时，想logger输出；文件路径时，直接向文件输出。       |
| path          | String         | 提供者上下文路径？？？                                   |
| transporter   | String         | netty，mina。可以server，client单独配置                  |
| server        | String         | netty，mina                                              |
| client        | String         | netty，mina                                              |
| dispatcher    | String         | 见Dispatcher拓展，协议的消息派发方式，默认all            |
| queues        | Integer            | 线程池队列大小，默认0                                    |
| charset       | String         | UTF-8                                                    |
| buffer        | Integer            | 网络读写缓冲区大小，默认8192                             |
| heartbeat     | Integer            | 默认0。？？？                                            |
| telnet        | String         | 所支持的telnet命令。？？？？                             |
| register      | Boolean        | 该协议的服务是否注册到注册中心，默认true                 |
| contextpath   | String         | ？？？                                                   |



### 11. AbstractReferenceConfig

##### 配置项解释

| 名称      | 类型    | 解释                                  |
| --------- | ------- | ------------------------------------- |
| check     | Boolean | 是否检查，如果Service不存在，是否报错 |
| init      | Boolean | eagle-init                            |
| generic   | Boolean | 是否泛化                              |
| injvm     | Boolean | 是否从本地JVM找服务                   |
| lazy      | Boolean | 是否懒加载                            |
| sticky    | Boolean | ？？                                  |
| stubevent | Boolean | ？？                                  |
| version   | String  |                                       |
| group     | String  |                                       |



### 12. ConsumerConfig

```xml
<dubbo:comsummer default="" client="" threadpool="" corethreads="" corethreads="" threads="" queues="" shareconnections="" />
```

##### 配置项解释

| 名称             | 类型   | 解释                                               |
| ---------------- | ------ | -------------------------------------------------- |
| isDefault        | String | 是否使用默认的协议                                 |
| client           | String | netty，mina                                        |
| threadpool       | String | 消费端线程池类型                                   |
| corethreads      | Integer    | 消费端核心线程数量                                 |
| threads          | Integer    | 线程池大小                                         |
| queues           | Integer    | 消费端等待队列大小，默认0                          |
| shareconnections | Integer    | 消费端和提供端的连接是可以共享的，共享连接数的大小 |



### 13. ReferenceConfig

```xml
<dubbo:reference id="" Integererface="" client="" protocol="">
	<dubbo:method ... />
</dubbo:reference>
```

##### 配置项解释

| 名称           | 类型   | 解释         |
| -------------- | ------ | ------------ |
| id             | String | 给接口取ID吧 |
| Integererface      | String | 接口全限定名 |
| client         | String | netty，mina  |
| ConsumerConfig | String | ref          |
| methods        | list   | ref          |
| protocol       | String | 默认dubbo    |



###  14. MethodConfig

```xml
<dubbo:reference Integererface="com.xxx.XxxService">
  <dubbo:method name="findXxx" executes="" deprecated="" sticky="" return="" oninvoke="" onreturn="" onthrow="" cache="" validation="">
  	<dubbo:argument .../>
  </dubbo:method>
</dubbo:reference>
```

##### 配置项解释

| 名称       | 类型           | 解释                                                         |
| ---------- | -------------- | ------------------------------------------------------------ |
| name       | String         | 方法名，该标签写在dubbo:reference或者dubbo:service里面       |
| stat       | Integer            | ？？？                                                       |
| retry      | Boolean        | ？？？                                                       |
| reliable   | Boolean        | ？？？                                                       |
| executes   | Integer            | 最大使用线程数限制                                           |
| deprecated | Boolean        | 该方法是否过时                                               |
| sticky     | Boolean        | 设置true 该接口上的所有方法使用同一个provider                |
| return     | Boolean        | 异步调用时，是否需要返回                                     |
| oninvoke   | Boolean        | 方法执行前拦截                                               |
| onreturn   | Boolean        | 方法执行返回后拦截                                           |
| onthrow    | String         | 方法执行有异常拦截                                           |
| cache      | String/boolean | 以调用参数为key，缓存返回结果。lru, threadlocal, jcache，默认false |
| validation | Boolean        | 是否对方法上参数进行验证                                     |



### 15. ArgumentConfig

```xml
<dubbo:method name="findXXX">
	<dubbo:argument index="-1" type="" callback=""/>
</dubbo:method>
```

##### 配置项解释

| 名称     | 类型    | 解释                           |
| -------- | ------- | ------------------------------ |
| index    | Integer     | 参数的位置，-1表示没设置       |
| type     | String  | 参数类型，全限定名             |
| callback | Boolean | 参数是否为callback接口？？？？ |



### 16. AbstractServiceConfig

##### 配置项解释

| 名称          | 类型           | 解释                                             |
| ------------- | -------------- | ------------------------------------------------ |
| version       | String         |                                                  |
| group         | String         |                                                  |
| deprecated    | Boolean        | 默认false，                                      |
| delay         | Integer            | 延迟注册服务，单位：毫秒                         |
| export        | Boolean        | 是否注册服务                                     |
| weight        | Integer            | 服务权重？？？                                   |
| document      | String         | 服务文档URL                                      |
| dynamic       | Boolean        | 动态注册，默认true                               |
| token         | String/Boolean | 令牌的作用是防止消费者绕过注册中心直接访问??     |
| accesslog     | String/Boolean | true: 往logger里面输出；文件路径：往文件里面输出 |
| protocols/protocol | list           | ref                                              |
| protocolIds   | String         | ???                                              |
| executes      | String         | 服务提供者每服务每方法最大可并行执行请求数       |
| register      | Boolean        | 是否向注册中心注册服务                           |
| warmup        | Integer            | ？？？                                           |
| serialization | String         | 序列化协议                                       |



### 17. ProviderConfig

```xml
<dubbo:provider id="" host="" port="" contextpath="" threadpool="" threads="" iothreads="" queues="" accepts="" codec="" charset="UTF-8" payload="" buffer="" transporter="" exchanger="" dispatcher="" networker="" server="" client="" telnet="" prompt="" status="" wait="" default="" />
```

##### 配置项解释

| 名称        | 类型   | 解释 |
| ----------- | ------ | ---- |
| host        | String |      |
| port        | String |      |
| contextpath | String | 服务治理 ???? |
| threadpool  | String | 线程池类型 |
| threads     | Integer    | 服务线程池大小(固定大小)，默认200 |
| iothreads   | Integer | IO线程池大小，默认CPU + 1 |
| queues | Integer | 线程池队列大小，默认0 |
| accepts | Integer | 服务提供者最大可接受连接数。？？？ |
| codec | String | 协议编码方式，见Codec2拓展 |
| charset | String | UTF-8 |
| payload | Integer | 请求及响应数据包大小限制，单位：字节，默认8388608(=8M) |
| buffer | Integer | 网络读写缓冲区大小，默认8192 |
| server | String | 协议的服务器端实现类型 |
| client | String | 协议的客户端实现类型 |
| telnet | String | 所支持的telnet命令 ??? |
| prompt | String | |
| wait | String | |
| isDefault | Boolean | |
| layer | String | 服务提供者所在的分层。如：biz、dao、intl:web、china:acton。??? |



### 18. ServiceConfig

```xml
<dubbo:service id="" interface="" ref="" path="" generic="">
	<dubbo:method>
  	<dubbo:argument/>
  </dubbo:method>
</dubbo:service>
```

##### 配置项解释

| 名称        | 类型   | 解释     |
| ----------- | ------ | -------- |
| id          | String |          |
| interface   | String |          |
| ref         | String |          |
| path        | String | ???      |
| methods     | list   | ref      |
| provider    | ref    |          |
| providerIds | String | ???      |
| generic     | String | 是否泛化 |

