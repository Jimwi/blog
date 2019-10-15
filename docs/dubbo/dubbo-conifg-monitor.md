# MonitorConfig

```xml
<dubbo:monitor protocol="" address="" interval="" username="" password="" group="" version="" default=""/>
```



见org.apache.dubbo.monitor.MonitorFactory拓展。

Dubbo提供了DubboMonitor实现，DubboMonitor只是本地的实现，它会定时向监控中心发送监控数据。监控中心的也需要实现一个

MonitorService。这个dubbo没有实现。 



protocol="registry"  或者 protocol="dubbo" address="127.0.0.1:20880"

interval="60000"   向监控中心发送数据的时间间隔，默认1分钟

目前好像不用这个了，改用Metrics。



