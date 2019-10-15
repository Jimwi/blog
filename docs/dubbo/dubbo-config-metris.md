# MetricsConfig

```xml
<dubbo:metrics port="" protocol="" />
```

接com.alibaba.metrics用的。用于服务的监控。实现方式是加了一个filter，在接口调用结束之后，记录下调用次数。

具体看Alibaba的Metrics吧

