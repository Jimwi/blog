# RegistryConfig

```xml
<dubbo:registry id="" address="" protocol="" port="" version="" password="" username="" transport="" transporter="" client="" timeout="" session="" file="" wait="" check="" register="" subscribe="" dynamic="" group="" simplified="" extra-keys="" cluster=""  forks="" server=""  />
```



见org.apache.dubbo.registry.RegistryFactory拓展，dubbo提供了很多种实现，consul，dubbo，etcd3，multicast，multiple，nacos，redis，sofa，zookeeper实现。默认使用dubbo直连的方式。我们常用的是zookeeper协议。zookeeper协议使用的是curator客户端连接的zookeeper。见org.apache.dubbo.remoting.zookeeper.ZookeeperTransporter拓展。dubbo只提供了curator一种实现。

check="true"  启动时默认会检查注册中心的状态，检查失败将启动失败，见org.apache.dubbo.common.status.StatusChecker拓展



register="true"，   是否向注册中心注册服务，RegistryProtocol#export  里面向注册中心注册服务。

subscribe="true"    是否订阅注册中心的服务，RegistryProtocol#refer 里面向注册订阅注册中心的服务。



cluster="failover"  将多个 服务集群 failover，failfast，failback

 